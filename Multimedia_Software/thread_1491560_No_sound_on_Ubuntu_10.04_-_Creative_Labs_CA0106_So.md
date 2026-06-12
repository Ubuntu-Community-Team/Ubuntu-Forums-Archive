---
title: "No sound on Ubuntu 10.04 - Creative Labs CA0106 Soundblaster"
date: 2010-05-23
forum: Multimedia Software
---

### Post by fernandomm on 2010-05-23
Hi,

I have installed Ubuntu 10.04 but i get no sound at all. My sound card is Creative Labs CA0106 Soundblaster.

Some info

```

# lspci -v
04:05.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
    Subsystem: Giga-byte Technology Device a006
    Flags: bus master, medium devsel, latency 32, IRQ 22
    I/O ports at 9000 [size=32]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: CA0106
    Kernel modules: snd-ca0106

``````
$ sudo aplay -l
**** Lista de Dispositivos PLAYBACK Hardware ****
placa 0: CA0106 [CA0106], dispositivo 0: ca0106 [CA0106]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 0: CA0106 [CA0106], dispositivo 1: ca0106 [CA0106]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 0: CA0106 [CA0106], dispositivo 2: ca0106 [CA0106]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 0: CA0106 [CA0106], dispositivo 3: ca0106 [CA0106]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0

```I have checked sound config multiple times with alsamixer and it is not muted.

Any ideas of what is causing this problem and how i can get sound? It is the only thing that is not working here.

Thanks!

---

### Post by canadean84 on 2010-07-09
I have the same soundcard and the same problems.  I've run through many of the sound problem troubleshooting tutorials that people have written.  Ubuntu lucid lynx shows my soundcard in the Sysinfo program I downloaded through the Ubuntu Software Centre.

fernandomm, I notice that your post was back in May... have you found a solution yet?

---

### Post by fernandomm on 2010-07-10
Hello,

No, unfortunately i did not found any solution for this issue. I ended up installing and using Windows 7.

---

### Post by Sofox on 2010-07-10
I have the same issue.
It was working perfectly on a fresh install of Ubuntu, but somtime in the last few weeks it stopped working.

To test, I put in an Ubuntu Live CD and had the sound working perfectly on it, back to my install and no such luck.

EDIT: Solution: Uninstalled pulseaudio, restarted, deleted .pulse files in home directory, reinstalled pulseaudio, restarted.

It got everything working.

EDIT2: Also, previously I downgraded gstreamer0.10-pulseaudio from 0.10.21-1ubuntu3 to 0.10.21-1ubuntu2. I had tried that as a solution earlier before I tried the above. It may have been part of the solution, since I earlier suspected that upgrade of causing the damage.

---

### Post by gdesilva on 2010-07-12
I had Soundblaster Audigy NX2 working till yesterday - did a regular update and now it is not working.

It is still being detected as a USB device. I went through the tutorials and tried various suggestions but no luck. The device is in mute state although the audio control app and alsamixer both claim that it is not muted.

Any suggestions??

---

### Post by gdesilva on 2010-07-13
I just fixed my problem. When I started up alsamixer I noticed that the source for 'Digital Out' has been set to PCM instead of Front. Once this was corrected all came good.

---

### Post by cblair2k2 on 2010-10-17
> **Sofox said:**
> I have the same issue.
It was working perfectly on a fresh install of Ubuntu, but somtime in the last few weeks it stopped working.

To test, I put in an Ubuntu Live CD and had the sound working perfectly on it, back to my install and no such luck.

EDIT: Solution: Uninstalled pulseaudio, restarted, deleted .pulse files in home directory, reinstalled pulseaudio, restarted.

It got everything working.

EDIT2: Also, previously I downgraded gstreamer0.10-pulseaudio from 0.10.21-1ubuntu3 to 0.10.21-1ubuntu2. I had tried that as a solution earlier before I tried the above. It may have been part of the solution, since I earlier suspected that upgrade of causing the damage.
I just did that, uninstalled pulse, restart, delete home files, reinstalled and restarted and works perfectly.  I was having choppy audio and it would randomly quit!

Thanks! (on Ubuntu 10.10 w/ CA0106)

---

### Post by 3L33T on 2010-12-09
> **Sofox said:**
> 

EDIT2: Also, previously I [SIZE="6"]**downgraded**[/SIZE] gstreamer0.10-pulseaudio from 0.10.21-1ubuntu3 to 0.10.21-1ubuntu2. I had tried that as a solution earlier before I tried the above. It may have been part of the solution, since I earlier suspected that upgrade of causing the damage.


new kernel and pulseaudio updates ALWAYS HAS BEEN my the cause of my Ubuntu 10.04 LTS and CA0106 audio and mic issues.  Everytime there is a new update, I fear it will break an already working Ubuntu 10.04 pulseaudio machine.  IT NEVER fails!  and it is very frustrating because most of the time, I dont remember what I did the last time to fix this.  Very very frustrating!

Enough with the rant...

I HAD a working audio and mic, skype was working perfectly etc etc until the latest updates.  Now, my audio and mic isnt working at all.  I tried the above suggestions (remove pulseaudio, remove .pulseaudio, reboot...etc etc) but it didnt work for me.  THERE HAS GOT TO BE A BETTER WAY to use the CA0106 + Ubuntu 10.04 other than switching back to a Windows machine!

---

### Post by LuizMagnoGaloDoido on 2012-05-11
Guys read it:

Making Creative Labs CA0106 Soundblaster work on Ubuntu Linux

Steps:
Install GNOME Alsa Mixer
sudo apt-get install gnome-alsamixer
Now open GNOME ALSA Mixer from Applications -> Sound & Video -> GNOME ALSA Mixer
Choose the tab: “CA0106…”
Turn on “Audigy Analog/Digital Output Jack”
=> Deselect IEC958


Works fine for me...:lolflag:

---

### Post by csatlas on 2013-01-11
> **LuizMagnoGaloDoido said:**
> Guys read it:

Making Creative Labs CA0106 Soundblaster work on Ubuntu Linux

Steps:
Install GNOME Alsa Mixer
sudo apt-get install gnome-alsamixer
Now open GNOME ALSA Mixer from Applications -> Sound & Video -> GNOME ALSA Mixer
Choose the tab: “CA0106…”
Turn on “Audigy Analog/Digital Output Jack”
=> Deselect IEC958


Works fine for me...:lolflag:


Thank you for your post LuizMagnoGaloDoido
it works for me too, just installed gnome alsamixer + deactivated iec958
now I can hear sound and talk to mic!
using ubuntu 12.04.1 LTS with soundblaster CA0106

:D:D:D:D:D:D:D

---

### Post by axeman47 on 2013-04-11
> **LuizMagnoGaloDoido said:**
> Guys read it:

Making Creative Labs CA0106 Soundblaster work on Ubuntu Linux

Steps:
Install GNOME Alsa Mixer
sudo apt-get install gnome-alsamixer
Now open GNOME ALSA Mixer from Applications -> Sound & Video -> GNOME ALSA Mixer
Choose the tab: “CA0106…”
Turn on “Audigy Analog/Digital Output Jack”
=> Deselect IEC958


Works fine for me...:lolflag:

Thank you so much!!!  A recent set of updates broke it for me and it was maddening trying to figure it out.  Really appreciate pointing me to such a simple fix.

---

### Post by mmstick on 2013-04-11
I can't even launch gnome-alsamixer without it segfaulting. Can't get sound with my Creative Recon3D (CA0132). The best I can get is repeating static.

---

### Post by mmstick on 2013-05-15
Seems even with Ubuntu 13.10 installed (kernel 3.9), still no sound at all from CA0132.

---

### Post by Yellow Pasque on 2013-05-16
> I can't even launch gnome-alsamixer without it segfaulting
gnome-alsamixer is just alsamixer with a fancier GUI. Regular alsamixer works fine:
```
alsamixer
```

I'm guessing this is you: [https://bugs.launchpad.net/bugs/1131707](https://bugs.launchpad.net/bugs/1131707)
If you have the latest kernel and firmware, and still don't have it working, this is probably your best chance to get it working: [https://lists.sourceforge.net/lists/listinfo/alsa-user](https://lists.sourceforge.net/lists/listinfo/alsa-user)

---

### Post by mmstick on 2013-05-22
> **Temüjin said:**
> gnome-alsamixer is just alsamixer with a fancier GUI. Regular alsamixer works fine:
```
alsamixer
```

I'm guessing this is you: [https://bugs.launchpad.net/bugs/1131707](https://bugs.launchpad.net/bugs/1131707)
If you have the latest kernel and firmware, and still don't have it working, this is probably your best chance to get it working: [https://lists.sourceforge.net/lists/listinfo/alsa-user](https://lists.sourceforge.net/lists/listinfo/alsa-user)

And I'm afraid it was a fruitless effort. I got no reply from the mailing list over the week. There is simply absolutely no support despite kernel updates adding firmware patches for it in every kernel since 3.5

---

### Post by vladimir-loshchin on 2013-09-01
Disabling [COLOR=#000000]IEC958 works for me. Use gnome alsa mixer to do this. Thanks a lot for your answers! [/COLOR]

---

