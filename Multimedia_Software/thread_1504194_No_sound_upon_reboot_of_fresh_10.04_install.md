---
title: "No sound upon reboot of fresh 10.04 install"
date: 2010-06-07
forum: Multimedia Software
---

### Post by BoneChu on 2010-06-07
Hello

I have sound when i install Ubuntu 10.04. I then proceed with installing the following: Skype, Wine and VLC. Sound is still working, but it's the same session. Ok, Then I play a bit, watch some video and decide to finally do the updates it asks me to do. It wants me to reboot so I reboot. Then, no sound. And nothing seems to help.

So I've been trying for several hours on getting sound working having almost 0 fun or luck with it. No sound = useless system.

I've somehow accomplished this ingenious feat:

!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.23
Utilities version:  1.0.22
(The update script didn't work...)

So yeah.... sucks to be me... :confused:

Anyways I ran the ALSA info script and here's what came out:
[http://www.alsa-project.org/db/?f=d5cf0f8c06f21590bac4c113979d5278dcb4599d](http://www.alsa-project.org/db/?f=d5cf0f8c06f21590bac4c113979d5278dcb4599d)

```
aplay -l
**** Luettelo PLAYBACK laitteista ****
kortti 0: NVidia [HDA NVidia], laite 0: VT1708B Analog [VT1708B Analog]
  Alalaitteet: 2/2
  Alalaite #0: subdevice #0
  Alalaite #1: subdevice #1
kortti 0: NVidia [HDA NVidia], laite 1: VT1708B Digital [VT1708B Digital]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
```I am at a total loss as to how to reverse all the madness I have let unfold on my install... and how to get sound working. 

It's getting too late for me so I'll just write this one and hope someone can help me. All the guides just have made it messier....

help a newb

---

### Post by lidex on 2010-06-07
I'm guessing you installed alsa-backports. Uninstall that and run the upgrade script again. Then do this:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

### Post by BoneChu on 2010-06-08
Thanks. Tried that, it says file or directory doesn't exist. :(

no -backports packages in synaptic either.... ofc I have messed things up in the terminal....

How do I just remove everything sound related to start from a clean slate?

Have to go to work soon... trying this out now:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/]("http://http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")

---

### Post by BoneChu on 2010-06-08
Just got home from work.... while the commands for updating from that page I linked did not all work out 100% I now have sound... at least on my first startup. :popcorn:
It did not manage to compile and update the alsa-utils. The output of
```
cat /proc/asound/version
``` is now:```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun  8 2010 for kernel 2.6.32-22-generic (SMP)
```:lolflag:

However the alsa.info script output states:

```
!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.22
```For some reason it won't compile the .23 alsa-util
I'll try rebooting now to see whether sound stays on.:p

EDIT:
Sound stayed on upon reboot. Is it advisable to somehow workaround the alsa-utils to 1.0.23? Or does it really matter?

---

### Post by lidex on 2010-06-08
If it works, probably best not to tinker. The driver is of main concern.

---

### Post by BoneChu on 2010-06-09
> **lidex said:**
> If it works, probably best not to tinker. The driver is of main concern.

No need to fix what isn't broken, eh :p

Thanks Lidex!

Now to install Compiz, Karbon14, Flashplayer 64bit and Sun Java (need it for work) and then I'm all set for the holidays....

---

