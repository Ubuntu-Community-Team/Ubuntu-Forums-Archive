---
title: "Karmic pulse audio 'popping'  - nVidia MCP51 HDA"
date: 2009-11-02
forum: Multimedia Software
---

### Post by redxine on 2009-11-02
I just put karmic on an HP Pavilion dv9000 and all went well until the audio fired up. Audio will play just fine - and when pulse audio has no clients it doesn't open up the sound card. The problem is that when it does open the sound card, there is a loud 'pop' sound, much like it's being plugged in. I believe it has something to do with [this bug report ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536") 

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

I've thought of a simple work around - writing a script that will hold a connection to pulse audio, something like padsp (commandline-oss-player) silence.wav. Any suggestions?

---

### Post by alloutnow on 2009-11-02
I am having the same problem on my HP Pavilion DV6000 laptop.  These audio popping is very anoying!

I just recently installed Ubuntu 9.10 and the audio device is: MCP51 High Definition Audio.

Would be great to get a fix for this!

---

### Post by Kushkah on 2009-11-03
The problem is due to your laptop's powersave settings.  The pop your hearing is the speaker turning on as powersave has had it off while not playing any sounds.  Try this 
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
and change the line
```
options snd-hda-intel power_save=10 power_save_controller=N
```
to

```
options snd-hda-intel power_save=0 power_save_controller=N
```
If that doesn't work for you, you can try
```
sudo echo 0 > /sys/module/snd_hda_intel/parameters/power_save
```
as a temporary fix.

---

### Post by alloutnow on 2009-11-03
Thank you Kushkah, you have solved the problem for me!

Best wishes,

AON

---

### Post by lordL on 2009-11-05
I had the same issue on an Acer Aspire 5738ZG, with Intel 82801I HD audio controller. Kushkahs solution worked for me as well. Thanks a lot :)

---

### Post by kevinlong on 2009-11-09
worked for me too . my problem start with 9.10 upgrade.. intel integrated sound chip.

---

### Post by toopi on 2009-11-30
> **Kushkah said:**
> The problem is due to your laptop's powersave...

Thanks, Kushkah.  This worked!  

For me, the occasional popping appeared after installing a vanilla kernel, although the problem was not present with the default Ubuntu's kernel.

---

### Post by emdash on 2009-12-01
worked for me, also have an HP Pavillion dv6000

---

### Post by karlwilbur on 2009-12-26
I have an Acer Aspire 5920 with the Intel 82801H Audio Controller:

```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0121
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

This solved the popping with my laptop. (short version of [post #3]("http://ubuntuforums.org/showpost.php?p=8229317&postcount=3"))
```

sudo sed -i 's|^\(options snd-hda-intel power_save=\)[0-9]\+|\10|' /etc/modprobe.d/alsa-base.conf
sudo su -c "echo 0 > /sys/module/snd_hda_intel/parameters/power_save"

```


I am hoping that this also solves this issue with my desktop. I may post more on that later.

---

### Post by rknop on 2009-12-27
This did NOT work for me.  I'm on a HP Pavilion dv6000, using Wine and Skype through pulse.  I've rebooted with the module settings, and have also set the /proc/sys variable.  Yet, I'm still getting horrible audio popping.

Any other ideas?

---

### Post by karlwilbur on 2009-12-27
rknop,
Have you tried copy/paste of my second code block in [post #9]("http://ubuntuforums.org/showpost.php?p=8561882&postcount=9")?

I just did a copy/paste on my desktop and it worked like a charm. No more popping.

Custom desktop build with Foxconn mobo and integrated ATI audio chip. 

```

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Foxconn International, Inc. Device 0e0e
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f9ff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I am running Karmic which was upgraded from Jaunty (which was upgraded from Intrepid). Though my laptop mentioned in my other post was a clean install of Karmic.

---

### Post by karlwilbur on 2009-12-29
FWIW, I just built a new desktop and installed Karmic. There was popping from pulseaudio so I copy/pasted the two sudo commands from my previous post. Popping is gone. Easy.

ASUS MA4A79T mobo w/ integrated ATI audio

```

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 8357
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f7df8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

---

### Post by rknop on 2009-12-29
Yes, I've tried that.  (Not the exact block, but the same effects -- power_save=0 for snd-hda-intel, and 0 in /sys/module/snd_hda_intel/parameters/power_save.  I'm still getting a lot of popping.

---

### Post by QuikZ06 on 2010-01-15
I had tried changing the powersave option, but what finally worked for me is upgrading to [B]Kernel 2.6.32.xx

EDIT: Nevermind, apparently the songbird process was running in the back ground even though I hadn't open the program.
Popping is still there.
[/B]

---

### Post by commbot on 2010-01-15
> **Kushkah said:**
> The problem is due to your laptop's powersave settings.  The pop your hearing is the speaker turning on as powersave has had it off while not playing any sounds.  Try this 
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
and change the line
```
options snd-hda-intel power_save=10 power_save_controller=N
```
to

```
options snd-hda-intel power_save=0 power_save_controller=N
```
If that doesn't work for you, you can try
```
sudo echo 0 > /sys/module/snd_hda_intel/parameters/power_save
```
as a temporary fix.

The second option worked for me. 

Many thanks, this was extremely annoying and the fix, in hindsight, is blindingly simple. Great tip.

---

### Post by ntucker on 2010-03-08
This worked for me as well, but now I have to wonder: how much power is being wasted by disabling this power saving option?

---

### Post by alelopnog on 2010-03-22
Hi, got the same issue with an alc880 intel hda card. None of this solutions worked for me. Any help please?

---

### Post by rocuan on 2010-05-31
Modifying /etc/modprobe.d/alsa-base.conf from #3 worked for me
Thanx!

---

