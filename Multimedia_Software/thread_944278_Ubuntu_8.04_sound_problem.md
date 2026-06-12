---
title: "Ubuntu 8.04 sound problem"
date: 2008-10-11
forum: Multimedia Software
---

### Post by Ivan452 on 2008-10-11
Hi everyone. 

I am new user of linux, and yesterday i have Ubuntu 8.04 installed. 
But I have encountered a problem. 

I have sound card AC97, and 5.1 speaker.
Now I had to change position of my cables(the ones that go from sound card to speakers) and when I do this command:
**speaker-test -Dplug:surround51 -c6 -l1 -twav**
it all works nice. every speaker is in place, and even subwoofer is working.
But when I start music it wont work. I dont hear last 2 speaker. I have tried with duplicate front and for a while it did work. And I heard sound from 2 speaker in the back, but now it just doesent.

hm. I got it like this. That duplicate front has to be on when Im listening to mp3 music, or watching regular .avi movies because they are 2ch standards, and when for example Im watching DVD with support for 5.1 i have to turn off duplicate front in order to get right sound?

And just to add when i use command:
**speaker-test -Dplug:surround51 -c6 -l1 -twav**
while duplicate front is turned on everything gets mixed up.

And does anyone has solution for that problem that i had to change places where cables go in? Because I would not want to change its place everytime i change from linux to windows and vice versa.

(and i have tried with **/etc/pulse/deamon.conf**)

---

### Post by Ivan452 on 2008-10-11
solved. 
fount this thingy:

```
pcm.!spdif {
    type plug
    slave.pcm "hw:0,2"
}

pcm.!surround51 {
type plug
slave.pcm "dmixer"
}

pcm.!default {
  type plug
  slave.pcm "dmixer"
  route_policy duplicate
}

pcm.dmixer  {
        type dmix
        ipc_key 321456
        ipc_key_add_uid true
        slave {
                pcm "hw:0,0"
                channels 6
                period_time 0
                period_size 1024
                buffer_size 4096
                rate 96000
        }

        ## 0 = Left, 1 = Right, 2 = Centre, 3 = Subwoofer , 4 = Rear Left, 5 = Rear right.
        bindings { 
            0 0
            1 1
            2 4
            3 5
            4 2
            5 3
        }
    }
 
    ctl.dmixer {
        type hw
        card 0
    }
```

---

