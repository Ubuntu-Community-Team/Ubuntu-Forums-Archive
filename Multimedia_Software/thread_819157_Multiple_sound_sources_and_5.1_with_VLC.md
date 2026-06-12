---
title: "Multiple sound sources and 5.1 with VLC"
date: 2008-06-05
forum: Multimedia Software
---

### Post by miki_x on 2008-06-05
Hi,

I'm a hardy user and I've been haveing problems with my sound setup, since I can get either 5.1 or multiples ounds, but not both together.
I mainly use VLC, and when configured to output through ALSA 5.1 is working flawlessly but there is no way of having another sound. If I configure output through Esound in VLC, then I'll have multiples ounds, but 5.1 is gone and I get the same track duplicatd across all channels.

I'm using a Realtek ALC850 (integrated on a DFI Lanparty NF4).
Here's my asound.conf in case some of you get inspired ;)

Thanks for your help!

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

pcm.dmixer {
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

