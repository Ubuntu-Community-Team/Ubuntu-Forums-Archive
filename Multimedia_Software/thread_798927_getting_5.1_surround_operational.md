---
title: "getting 5.1 surround operational"
date: 2008-05-18
forum: Multimedia Software
---

### Post by allmondjoy87 on 2008-05-18
just installed ubuntu and got my video card working right, now im just working on the sound card now.

i have a Sound Blaster Live 5.1, and after some browsing on the alsa site, i found out how to test speakers.

after typing
```
% speaker-test -Dplug:surround51 -c6 -twav
```
i can hear a voice over every speaker

but play back in rhythmbox gives only front left/right center sound. also its kind of hissy

anyone else have this problem? or a solution?

---

### Post by mc4man on 2008-05-18
what worked for my audigy was to go to preferences -> sound and change the  setting for music and movies from autodectect to alsa.

---

### Post by allmondjoy87 on 2008-05-18
yeah i've tried that, after looking around it looks like other people have the same problem

anybody get the soundblaster ca0106 to work the way they want it with 5.1 surround?

this is really the only thing keeping me in windows :(

---

### Post by oldsoundguy on 2008-05-18
I have managed (without too much effort) to get the LiveDrive 5.1 working in 7.10 .. BUT have NO VOLUME CONTROL that functions on the digital output (Analog volume control works) .. 87% is it for the digital!  Have to use the remote and control the volume with the amplifier.  Alsa is the setup, but you have to manually select what features you want to have turned on in order to get them to function.  Only feature I have not tested is the optical front input and the remote control .. Midi works and all other features work, though.

Sure would be nice if they would be able to actually make the card and front panel work as well as the did in Windows, but Creative is not one of the more co-operative hardware makers out there (to say the LEAST!), so the reverse engineering continues!

---

### Post by allmondjoy87 on 2008-05-19
hey i dunno what i did but i happened to work

went through my history and heres all the stuff i've entered, i dunno what any of it does but its stuff i found on google.  now i successfully have 5.1 using rhythmbox

```
sudo modprobe snd-emu10k1
```
```
cat /proc/asound/modules 
```
```
modinfo soundcore
```

only problem is now theres no sound in flash(youtube) after i open up rhythmbox...


:confused:

---

### Post by allmondjoy87 on 2008-05-22
this fixed it:)

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

