---
title: "No Sound VIA 8235 Digital"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by lab_rat on 2007-10-04
Hello,

My sounds seems to have dissapeared after updating my system.
I traced the cause to a malformed asound.conf file and changed it so it now looks like 

```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}
```

However i am still not able to hear anything

I have checked everything is unmuted in alsamixer 
I am connected by fibre to my amp which is registering the PCM connection

if i cat /proc/asound/pcm i get 

00-01: VIA 8235 : VIA 8235 : playback 1 : capture 1
00-00: VIA 8235 : VIA 8235 : playback 4 : capture 1

I am sure that everything is connected properly cos i can stil hear sounds from doze

any sugestions ?

---

### Post by American_Outcast on 2007-10-04
I am using a VIA 8237. Everything installed on mine with ease. I just had to play around with the volume control, Master, PCM and VIA DXS. I also have a VIA DXS 1, 2 and 3 that shows up in the volume control but I am not using those ones. Not sure if that gives you any ideas. I wish I had problems with it before so I can help you more now, (Thats how I learn with Linux, lol)

---

### Post by lab_rat on 2007-10-04
this makes things even weirder .. i unmuted the "mic boost" in the alsamixer and now i can hear static ?
This suggests to me that it is definately a setting file or something, now if i  only new which one

---

### Post by lab_rat on 2007-10-08
I still have no sound ... can anyone help me ?

---

