<template>
    <div class="grid grid-cols-2">
        <div class="font-bold text-xl">
            {{ selected.name }} Chat
        </div>
        <div>
            <!-- onchange we fire the roomchanged event and pass selected to event launcher in parent -->
            <select
                v-model="selected"
                @change="$emit('roomchanged', selected)"
                class="float-right"
            >
                <option
                    v-for="(room, index) in rooms"
                    :key="index"
                    :value="room"
                    >
                        {{ room.name }}
                    </option>
            </select>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ChatRoomSelection',
        props: ["rooms", "currentRoom"],
        data: function(){
            return{
                selected: ''
            }
        },
        created(){
            this.selected = this.currentRoom;
        }
    }
</script>
