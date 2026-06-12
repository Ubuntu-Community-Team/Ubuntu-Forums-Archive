---
title: "Speakers don't mute after plugging in headphones"
date: 2010-04-30
forum: Multimedia Software
---

### Post by alt.dev on 2010-04-30
Hello all,

I have a Dell Vostro 1014 laptop and I just installed Ubuntu 10.04. The problem I'm facing is that the sound output goes to both the built-in speakers and headphone jack.

Judging from some other threads I think this preliminary info would help in diagnosing the issue :

> $lspci -v

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Dell Device 0401
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f6afc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


> $aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0



> head -n 1 /proc/asound/card0/codec*
Codec: Conexant ID 5067


I've searched through /Documentation/sound/alsa/HD-Audio-Models.txt

But I can only see Conexant models upto 5066.

Can anyone help me out on this ?

---

### Post by alt.dev on 2010-05-03
bump ?

---

### Post by secondstage on 2010-05-03
Sounds like this guy has found a fix. 

[http://ubuntuforums.org/showpost.php?p=8591687&postcount=4](http://ubuntuforums.org/showpost.php?p=8591687&postcount=4)

---

### Post by alt.dev on 2010-05-06
Didn't work. Thanks for the info though. I think I'll wait for them to push the new ALSA driver through updates.

---

### Post by manojendu on 2010-05-12
Wow brother, I too have Dell Vostro 1014, and have had the same problem through Ubuntu 8.04 to 10.04, please let me know if and when a solution is found!!

---

### Post by manojendu on 2010-05-13
Well, the problem is solved (for me!!)
In the file /etc/modprobe.d/alsa-base.conf (you may open it with any editor), add the following line (make sure you prefix sudo to the command to make the file writable):

options snd-hda-intel model=dell-vostro

And then reboot.
:P

---

### Post by rowanq on 2010-05-13
Having the same issue here. HP G60-530US

Here's my output.

:~$ lspci -v

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
rowan@Narya-Ubuntu:~$ head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 5067

==> /proc/asound/card0/codec#2 <==
Codec: Intel G45 DEVCTG


Rowan

---

### Post by zeco on 2010-05-13
cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant ID 5067
Codec: Intel G45 DEVCTG

I am having the same problem.. hope someone finds a fix

---

### Post by alt.dev on 2010-05-13
> **manojendu said:**
> Well, the problem is solved (for me!!)
In the file /etc/modprobe.d/alsa-base.conf (you may open it with any editor), add the following line (make sure you prefix sudo to the command to make the file writable):

options snd-hda-intel model=dell-vostro

And then reboot.
:P

Didn't work bro. Do you have a Dell Vostro 1014 or something else ?

---

### Post by xeribii on 2010-05-15
Excellent.  This problem was solved for me too.  I'm running on Ubuntu 10.04, Conexant 5067, after installing the alsa backports that matches the linux kernal and adding the line options snd-hda-intel model=dell-vostro in the file /etc/modprobe.d/alsa-base.conf .

Thanks!  This thing has been troubled me for a while.  Finally it's got a great and convenient solution!

---

### Post by babarshahzad on 2010-05-25
> **xeribii said:**
> Excellent.  This problem was solved for me too.  I'm running on Ubuntu 10.04, Conexant 5067, after installing the alsa backports that matches the linux kernal and adding the line options snd-hda-intel model=dell-vostro in the file /etc/modprobe.d/alsa-base.conf .

Thanks!  This thing has been troubled me for a while.  Finally it's got a great and convenient solution!

How to get alsa backports?
I also have the same problem with my speaker and headphone.

---

### Post by babarshahzad on 2010-05-26
I also have del vostro 1014 with ubuntu 10.04 and my speaker do not mute when i connect headphone with it. Please help I have tried all the techneecs given above. Nothing seems to work for me.
Thanks very much!

---

### Post by The Noisiv Studio on 2010-06-02
Excellent fix for **Compaq Presario CQ60-615DX**.
Codec :** Conexant ID 5067**
Installed from Synaptic *backport that matched the name of the kernal *(e.g. Karmic, Lucid Lynx, etc..)
Added the line ....  options snd-hda-intel model=dell-vostro to the alsa-base.conf file at the end & rebooted.

Everything works the way it should now. 
Speakers on laptop provide sound and are muted when headphones are plugged in. 

Thanks for finding the fix and providing it to the rest of us. This was annoying. 

[B]Jordan Hall
Owner & Project Manager[/B]
[The Noisiv Studio]("http://www.thenoisiv.com")

---

### Post by kamalarora2kin on 2010-07-08
I have HP compaq dc7100 sff desktop. i have the same problem. i tried the solutions given above, none of them worked. Someone please find the solution and post the new code line which i can add to alsa base and fix the error.

```
lspci -v
```


[HTML]00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3006
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1000 [size=256]
	I/O ports at 1400 [size=64]
	Memory at cff40400 (32-bit, non-prefetchable) [size=512]
	Memory at cff40600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0[/HTML]

```
aplay -l
```


[HTML]**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/HTML]

[PHP]options snd-hda-intel model=dell-vostro[/PHP] this line did not work for me. i tried to add hp-compaq at the end, that even didn't work.

---

### Post by lidex on 2010-07-08
*kamalarora2kin*
You have completely different hardware, so it's not going to work.
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by kamalarora2kin on 2010-07-10
thanks lidex for your concern. i have solved it by following some other thread on lauchpad. Actually installing "gnome-alsamixer" solved my problem. it can solve most (may be all) muting problems.

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/90609](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/90609)

---

### Post by jjjjeremy on 2010-07-17
> **The Noisiv Studio said:**
> Excellent fix for **Compaq Presario CQ60-615DX**.
Codec :** Conexant ID 5067**
Installed from Synaptic *backport that matched the name of the kernal *(e.g. Karmic, Lucid Lynx, etc..)
Added the line ....  options snd-hda-intel model=dell-vostro to the alsa-base.conf file at the end & rebooted.

Everything works the way it should now. 
Speakers on laptop provide sound and are muted when headphones are plugged in. 

Thanks for finding the fix and providing it to the rest of us. This was annoying. 

[B]Jordan Hall
Owner & Project Manager[/B]
[The Noisiv Studio]("http://www.thenoisiv.com")

A step-by-step for those who need it (like me)

Compaq CQ60 615DX (for lucid)

1. Applications > Ubuntu Software Center > Edit > Software Sources
2. Password
3. Other Software > Add
4. paste: ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu > Add Source
5. Open Terminal > type: sudo apt-get install linux-backports-modules-alsa-lucid-generic  (installs alsa backports)
6. Password
7. Select Y (yes)
8. type: cd /etc/modeprobe.d  (just changes the folder you're working in)
9. type: sudo cp alsa-base.conf alsa-base-backup.conf (creates a backup of the file you are about to edit. To revert, delete alsa-base.conf and rename alsa-base-backup.conf to alsa-base.conf)
10. Password (if needed)
11. type: sudo gedit alsa-base.conf (opens alsa-base.conf for editing)
12. add the line " options snd-hda-intel model=dell-vostro " (without quotation marks) to the end of the file
13. Save
14. Reboot
15. Test

---

### Post by lidex on 2010-07-17
Thanks for that* jjjjeremy*. We in the community appreciate your feedback - it will benefit others. 
Remember though, when running GUI apps as root, best to use gksu/gksudo rather than sudo, which is preferred for terminal. 
Reference: [http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by noamb on 2010-08-07
i went through the same process, it all worked well and only now i noticed that it eliminates the mic. now when you plug in a mic nothing happens. any ideas? (talking about compaq presario CQ60 615 DX)
noam

---

### Post by badnaam on 2010-08-22
It seems I have the exact same models and i went through the same process of installing the backports and adding the dell-vostro line. Still no luck. I get sound from both headphone and speakers.

This is unbelievable, for version 10.4, even the very basic sound doesn't work!! Embarassing for Ubuntu, there is a reason why, Windows leads the desktop market, despite all the other goodness Ubuntu has.

---

### Post by lidex on 2010-08-22
> **badnaam said:**
> It seems I have the exact same models and i went through the same process of installing the backports and adding the dell-vostro line. Still no luck. I get sound from both headphone and speakers.

This is unbelievable, for version 10.4, even the very basic sound doesn't work!! Embarassing for Ubuntu, there is a reason why, Windows leads the desktop market, despite all the other goodness Ubuntu has.
Ubuntu is a community supported OS. Become part of the community and help make it better or get out your wallet and go back to MS. As for your problem,
try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by googeek on 2010-09-01
If you have a Conexant chip set,
your solution is easier than you can imagine. I spent a good four months looking for a solution to this problem, I tried everything under the sun. This driver is the only thing that worked for me. It also got my jack working so I could record music, yay!


[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

 Download the Deb and install it. Restart. Now check out your mixer. Add any new channels that aren't already there through settings. That's it.
Sometimes the mixer freaks out from this install, just restart it with command line.
Also, you will occasionally have to reinstall your awesome all fixing deb as sometimes the ubuntu updates set everything back to default. Not sure why. 
Good Luck!

---

### Post by majikins on 2011-05-02
Got a Dell Vostro with Conexant chip.  This download and install worked for me too.

Thanks

---

### Post by majikins on 2011-05-02
Got a Dell Vostro with Conexant chip.  This download and install worked for me too.

Thanks

---

### Post by eliasdev on 2011-09-09
Thank you jjjjeremy, it worked to me to, i have a toshiba qosmio and ubuntu 10.4 lts

---

