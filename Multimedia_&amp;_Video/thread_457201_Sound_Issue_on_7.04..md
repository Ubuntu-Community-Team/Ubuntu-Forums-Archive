---
title: "Sound Issue on 7.04."
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by mrwasabi on 2007-05-28
I have a problem with my sound when using 2 different devices that require sound. For example, I listen to music and use team speak in windows, but with ubuntu one or the other will work, not both, why is this? Either my music works and the ts sound is X out or appears to be muted, or I can talk and hear my ts contacts with no music. Any help will be greatly appreciated.

---

### Post by deadgobby on 2007-05-28
I am trying to understand what you are talking about. So I am going to wing it. If you have a sound card like Sound Blaster for example. If you do you'll need to go into your BIOS and disable the on board sound card. This will get sound to pipe %100 through the card. Ubie see both sound devices and if you do not disable one or the other. You'll get some apps play through the sound card and the others through the on board sound device.
Gobby

---

### Post by mrwasabi on 2007-05-29
Well when I first built this system I disabled the onboard ac97 so that isn't the problem. I'll try to be a little more definitive.

I have sound on my ubuntu desktop, everything works fine, amarok plays all of my music, I can listen to hbr1.com streams, all with no problem. The problem occurs when I try to use teamspeak and listen to music at the same time, either one or the other will work but not both at the same time. I do this in windows all the time with no problems at all. I'm sure it's a simple fix but I'm paranoid about making any changes without first consulting with someone. Thanks in advance for your time.

Rich

---

### Post by srt4play on 2007-06-01
I've never used teamspeak but you could try forcing teamspeak to cooperate by installing the package 'esound-clients' in Synaptic and then running teamspeak with 'esddsp teamspeak'.

---

### Post by fakie_flip on 2007-06-10
> **srt4play said:**
> I've never used teamspeak but you could try forcing teamspeak to cooperate by installing the package 'esound-clients' in Synaptic and then running teamspeak with 'esddsp teamspeak'.

Can you help? This is what I have done to try to get the game Legends working with Skype.
```

chris@ubuntu:/usr/games/legends$ killall esd
chris@ubuntu:/usr/games/legends$ esd &
[1] 8102
chris@ubuntu:/usr/games/legends$ ./runlegendsa 
chris@ubuntu:/usr/games/legends$ ERROR: ld.so: object '/usr/lib/esound/libesddsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libesd.so.0' from LD_PRELOAD cannot be preloaded: ignored.
open /dev/[sound/]dsp: Device or resource busy

chris@ubuntu:/usr/games/legends$ cat runlegendsa 
#!/bin/sh
if [ -L $0 ]; then
        LEGENDS_DIR="$(dirname $(readlink $0))"
else
        LEGENDS_DIR="$(dirname $0)"
fi
cd $LEGENDS_DIR
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:./
esddsp -m ./LinLegends $* &
chris@ubuntu:/usr/games/legends$ 
```

---

