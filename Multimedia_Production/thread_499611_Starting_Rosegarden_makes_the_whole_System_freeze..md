---
title: "Starting Rosegarden makes the whole System freeze."
date: 2007-07-12
forum: Multimedia Production
---

### Post by pitpat789 on 2007-07-12
Hello, I am an absolute noob, and I first experienced Linux just a few days ago.

I installed on my PC Ubuntu 7.04.

I Installed Rosegarden using the "Add/Remove" tool. when I tried to launch it, the system freezed. The mouse didn't work and neither the keyboard and there was no motion on the screen(only one still image).

My sound card is ESI Juli@.

Does anyone know what the problem is?

(sorry for my terrible English)

---

### Post by fredj on 2007-07-13
Rosegarden only works through the jack audio server. You need to install jack and qjackctl. 
Then setup and start jack using qjackctl and start rosegarden.

---

### Post by theblackkat on 2007-07-20
actually, even with jack running it will freeze the whole system during the "initializing view" part on startup...

seems to be some kind of incompatibility with my audiophile 192 soundcard.... if i disable it, rosegarden runs fine...

---

### Post by pkslot on 2007-07-20
If you are experiencing more problems with jack and rosegarden, it's very likely that installing the [lowlatency linux kernel]("http://packages.ubuntu.com/feisty/admin/linux-lowlatency") will help you.

---

### Post by fredj on 2007-07-21
Forget rosegarden for the moment. Does your audiophile soundcard work under alsa. To check this open
the Alsa mixer by double clicking on the speaker icon in the taskbar. Then go to the File->Change Device
menu and make sure that your audiophile card is selected as the default sound device. Then check that you
can play system sounds, wave files, mp3s etc through your audiophile card.
Open a teminal and type sudo lshw -class sound
Post the output from that here.

---

### Post by semyazas on 2007-12-17
UP!

Exactly the same problem but with a ESI Juli@ soundcard.
My system also freezes when I start Mixxx and winecfg, for example.
I have this problem only when my soundcard is plugged in.

I have this problem for 2 months and I tried many things, without any success. This problem also occurs with any other linux distro. :confused:

```
sudo lshw -class sound
```

gives :

```
*-multimedia            
       description: Multimedia audio controller
       product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
       vendor: VIA Technologies Inc.
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ICE1724 latency=32 module=snd_ice1724

```

Thanks...

---

