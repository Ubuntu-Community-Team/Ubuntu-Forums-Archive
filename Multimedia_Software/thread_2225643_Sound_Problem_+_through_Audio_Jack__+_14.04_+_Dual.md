---
title: "Sound Problem + through Audio Jack  + 14.04 + Dual boot with windows,"
date: 2014-05-22
forum: Multimedia Software
---

### Post by karna413.ms on 2014-05-22
Hej , I just re installed my Ubuntu linux version to fix Audio jack problem. But it still does not work, Ubuntu does not even detect audio jack.It Works fine on Ubuntu internal speakers and On windows it works fines through Internal speakers + headphones.I have Attached a picture when using ubuntu OS and headphones jack connected .

BTW , its alienware Laptop with 3 audio jacks , I connected to Only audio Jack port which means close to SD card Audio Port.

I am newbie to linux , Is it something missing with audio drivers or bug in new ubuntu version.??

I tried following : [http://askubuntu.com/questions/132440/headphone-jack-not-working](http://askubuntu.com/questions/132440/headphone-jack-not-working) 

but it does not help, Now i have fresh installed Linux , Still its same problem, Any help please ??




[IMG]http://postimg.org/image/8pgii9ct1/[/IMG]
[IMG]http://postimg.org/image/xk3tfqel5/[/IMG]

---

### Post by Yellow Pasque on 2014-05-22
> I tried following : [http://askubuntu.com/questions/13244...ck-not-working](http://askubuntu.com/questions/13244...ck-not-working)
Undo it. That code is for a different laptop and audio chipset.

> BTW , its alienware Laptop
What model specifically? It would be best if you could give full info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by karna413.ms on 2014-05-22
Thanks for the replay, its m14xR2 ,

---

### Post by Yellow Pasque on 2014-05-22
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1267675](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1267675)
> By default CA0132 has the HP/Speaker and HP/Speaker Auto Detect muted. Unmuting them by going into alsamixer and pressing M on their controls unmutes them and sound works.'
So, run alsamixer and unmute those controls.
```
alsamixer
```

---

### Post by karna413.ms on 2014-05-22
Hej , I just opened alsamixer and unmuted HP/speaker by pressing M on their controls, Restarted the computer , But still its same :(  :(  , attached Alsamixer screenshot

---

### Post by Yellow Pasque on 2014-05-22
They may have been reset to mute at reboot (check it).

---

### Post by karna413.ms on 2014-05-22
Nope , I took screen shot after reboot,

---

### Post by Yellow Pasque on 2014-05-22
Can you give the info?: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by karna413.ms on 2014-05-22
[http://www.alsa-project.org/db/?f=8d48a0a69d5179769d57de634a7537f274e02f00](http://www.alsa-project.org/db/?f=8d48a0a69d5179769d57de634a7537f274e02f00)

---

