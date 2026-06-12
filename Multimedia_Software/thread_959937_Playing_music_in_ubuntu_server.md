---
title: "Playing music in ubuntu server"
date: 2008-10-26
forum: Multimedia Software
---

### Post by hellothere55 on 2008-10-26
Hello,

I want to play music on my ubuntu server 8.04.  I don't want to have to install any graphical clients.  I am running squeezecenter and I want to play the stream.mp3 on the same computer.  This way I can remotely manage the music. 

I tried to install alsa-base, but even after a reboot mp3blaster wouldn't output any audio.  I made sure alsamixer had everything maxed out and even tried all of the audio ports on the server, none of them played anything.  Any help is appreciated.  

Thanks,
Eric

---

### Post by cariboo on 2008-10-26
Could you post the output of:

```
sudo lshw -C multimedia
```

This way we can see what type of sound card you have and help you fix he problem.

Jim

---

### Post by hellothere55 on 2008-10-27
eric@wasp:~$ sudo lshw -C multimedia
  *-multimedia
       description: Multimedia audio controller
       product: nForce2 AC97 Audio Controler (MCP)
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0

---

