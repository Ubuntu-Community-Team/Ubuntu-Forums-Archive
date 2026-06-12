---
title: "No sound via USB to Audio-divice (D/A-Converter)"
date: 2010-11-06
forum: Multimedia Software
---

### Post by klemi on 2010-11-06
Hallo,

I have a new USB-D/A-converter called Cantarta Music Center.

This device dont need a proprietary driver under Windows.

Now I will play audio-files from Computer to Cantarta Music Center via USB plug in under Linux.

I Have done follows:

```
klemens@klemens-laptop:~$ lsusb

Bus 008 Device 002: ID 046d:c041 Logitech, Inc. G5 Laser Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 221f:4d48  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1d74:0002  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

klemens@klemens-laptop:~$ ls -l /proc/asound
insgesamt 0
dr-xr-xr-x 5 root root 0 2010-10-17 13:08 card0
dr-xr-xr-x 3 root root 0 2010-10-17 13:08 card1
-r--r--r-- 1 root root 0 2010-10-17 13:08 cards
lrwxrwxrwx 1 root root 5 2010-10-17 13:08 Center -> card1
-r--r--r-- 1 root root 0 2010-10-17 13:08 devices
-r--r--r-- 1 root root 0 2010-10-17 13:08 hwdep
lrwxrwxrwx 1 root root 5 2010-10-17 13:08 Intel -> card0
-r--r--r-- 1 root root 0 2010-10-17 13:08 modules
dr-xr-xr-x 2 root root 0 2010-10-17 13:08 oss
-r--r--r-- 1 root root 0 2010-10-17 13:08 pcm
dr-xr-xr-x 2 root root 0 2010-10-17 13:08 seq
-r--r--r-- 1 root root 0 2010-10-17 13:08 timers
-r--r--r-- 1 root root 0 2010-10-17 13:08 version
```

"ls -l /proc/asound " show "lrwxrwxrwx 1 root root 5 2010-10-17 13:08 Center -> card1"

I think the Converter were identify as a graphic-card.

Someone friendly user said me I must create a file called asound.conf, put it in the /etc directory
with:

```
pcm.Center {
    type plug
    slave.pcm "card1"
}
ctl.Center {
    type hw
    card 1
}
pcm.card1 {
    type hw
    card 1
}
```

and reboot

In the next step, i use a simple music programm under Linux like "DeaDBeeF", I can see under "settings - output device" the following:

[URL="http://picpaste.de/5-11-10-Cantata_music-center-JlhSdvTc.png"]http:
//picpaste.de/5-11-10-Cantata_music-center-JlhSdvTc.png[/URL]

I have select any items which is detected with "Cantarta"-entry, but the player don't play some flac-files (no "play signs" appears in the player. --> Nothing happens.

What can I do?

Is something missing with alsa or plug-in-detection?

I think it must in principle operate!

Can someone help me?

Thanks

klemi

---

