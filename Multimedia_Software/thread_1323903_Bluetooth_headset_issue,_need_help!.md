---
title: "Bluetooth headset issue, need help!"
date: 2009-11-12
forum: Multimedia Software
---

### Post by linuzlover on 2009-11-12
Good morning!

Yesterday I tried using my bluetooth headset with my brand new Kubuntu 9.10! 

I got immediately in troubles because i couldn't pair my headset with PC, but... with blueman everything started working.

Now, after reading this [https://help.ubuntu.com/community/BluetoothHeadset/](https://help.ubuntu.com/community/BluetoothHeadset/),

I installed paman padev and everything needed (in primis pulseaudio-bluetooth module) but I can't see my headset in the devices tab (I've alredy created .asoundrc in my home directory specifying the right mac address). I don't know what to do :confused:.

 Please help me ! [-o<

Thanks 

Attilio

P.s. Kubuntu Karmic Koala 9.10 amd64 versione , usb stick (no branded but working) bluetooth headset (no branded but working)

---

### Post by linuzlover on 2009-11-13
^up

---

### Post by linuzlover on 2009-11-14
Using what I read in community help, I get

```

pactl load-module module-alsa-sink device=btheadset
Fallimento: Timeout (Error: Timeout)


```

Can it be  a keypass problem? My headset requires a 0000 keycode. Is it possible to specify it?

---

### Post by linuzlover on 2009-11-16
no way! Still need help

---

### Post by linuzlover on 2009-11-18
Solved! Bought a brand new bluetooth adapter and bluetooth headset (all made by conceptronics!) v 2.1

Have a nice day!

---

