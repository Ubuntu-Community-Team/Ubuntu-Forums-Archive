---
title: "[SOLVED] No sound, Znote 6625WD, ALC268"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by coninsan on 2008-03-17
Hi 

unfortunetly i had to reinstal ubuntu gutsy, because my dual boot got messed up.
so now im back to square one. :(

last time i got my sound running, but i had no control over it accept when i was in a program with volume control.
So this time i would like to know how i get in control of my master volume after installing a new version of alsa, 

So if you know how to just install alsa please tell me how in a step to step version :)

and please if you do know how to make the gnome soundmixer to control alsa master volume please do tell :)

Ps. i have a reatek ALC268 HD soundcard.

---

### Post by coninsan on 2008-03-17
Heres my lspci -v output

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f4300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

and my aplay -l output
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by xc3RnbFO8P on 2008-03-17
Did you install 32 bit

---

### Post by coninsan on 2008-03-17
i have never run 64bit in my life, plus i downloaded the 32bit version of ubuntu, so im pretty sure its 32bit. :)

---

### Post by xc3RnbFO8P on 2008-03-17
> sudo apt-get install linux-backport-modules
> sudo gedit /etc/moprobe.d/alsa-base
add this line: **model=toshiba** or chance it

---

### Post by coninsan on 2008-03-17
```
sudo gedit /etc/moprobe.d/alsa-base
```

only opened a blank page :(

---

### Post by xc3RnbFO8P on 2008-03-17
did you install backports

---

### Post by coninsan on 2008-03-17
```
E: could not find package linux-backport-modules
```

roughly translated.

---

### Post by xc3RnbFO8P on 2008-03-17
In Synaptic Package Manager: settings> repositories> software source check all boxes
un check cdrom.
Third party software  check all
reload

---

### Post by coninsan on 2008-03-17
it still cant find it :(

---

### Post by xc3RnbFO8P on 2008-03-17
you should get update sign on panel soon

---

### Post by xc3RnbFO8P on 2008-03-17
I forgot in software source: update check all

---

### Post by coninsan on 2008-03-17
nothing.. 

theres no notice showing, is there a software source i need to get via Wget for this to work?

---

### Post by coninsan on 2008-03-17
???

---

### Post by xc3RnbFO8P on 2008-03-17
did you read last post
in Synaptic P..

---

### Post by coninsan on 2008-03-17
yes but i dont know how or where to put what you said, i have been on linux for les then a week so please bear with me...

---

### Post by xc3RnbFO8P on 2008-03-17
OK.  In synaptic package manager: settings> Rep.. > updates check all boxes

---

### Post by xc3RnbFO8P on 2008-03-17
and reload Synaptic P..

---

### Post by xc3RnbFO8P on 2008-03-17
in synaptic p.. settings>rep..>third softw.> add+ this line: 
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main universe multiverse restricted
reload

---

### Post by xc3RnbFO8P on 2008-03-17
Did you get update?

---

### Post by coninsan on 2008-03-17
i got a list of updates, which made that i had to reboot, and added some boot choises in grub.

what now then :)

---

### Post by xc3RnbFO8P on 2008-03-17
this > sudo apt-get install linux-backport-modules

---

### Post by coninsan on 2008-03-17
same thing happened as before.. 

it cant find the package

---

### Post by coninsan on 2008-03-17
but there is some progress, i checked my sound settings to see if anything happened, and this was added under the choises for soundsettings: alc268 analog and alc268 digital, but when i test it, theres no sound.

---

### Post by xc3RnbFO8P on 2008-03-17
>  sudo gedit /etc/moprobe.d/alsa-base
and hopefully you see something.
 model=**toshiba** 
just chance **toshiba**

---

### Post by xc3RnbFO8P on 2008-03-17
In synaptic p.. search: linux-backport-modules    generic

---

### Post by coninsan on 2008-03-17
the packages that show up have been installed.

but could it have something to do with that i am still running alsa version 1.0.14?

---

### Post by xc3RnbFO8P on 2008-03-17
what about :
> sudo gedit /etc/moprobe.d/alsa-base

---

### Post by coninsan on 2008-03-17
still blank

---

### Post by xc3RnbFO8P on 2008-03-17
now this:
> sudo aptitude install linux-backports-modules-generic

---

### Post by mali2297 on 2008-03-17
> **Ringi said:**
> what about :

I think you mean
```

gksu gedit /etc/modprobe.d/alsa-base

```
Note the "d". :-)

---

### Post by coninsan on 2008-03-17
that did install/deinstall something. :)

---

### Post by coninsan on 2008-03-17
lol that opened it like a treat :)

---

### Post by xc3RnbFO8P on 2008-03-17
And now this:> gksu gedit /etc/modprobe.d/alsa-base

---

### Post by xc3RnbFO8P on 2008-03-17
Did you change** toshiba** and save
then restart the computer

---

### Post by coninsan on 2008-03-17
it worked!!!
i hear sound, and its rocking! :guitar:

im sitting with the biggest grin possible right now, thank you so much :)
im definatly saving a rekord over this if i have to reboot at any point.

---

### Post by xc3RnbFO8P on 2008-03-17
you are welcome, mark it as solved in treat tools

---

### Post by coninsan on 2008-03-17
Done

---

