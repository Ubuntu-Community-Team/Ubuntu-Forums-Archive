---
title: "3 issues - audio skipping, x11vnc freezing X and battery indicator"
date: 2010-10-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mullens101 on 2010-10-01
Hi,
   I have Maverick on my desktop and Laptop.  On the laptop, my only issue is that the battery indicator applet shows up but when I click it all it says is "Calculating" and never displays the percentage.  (HP Proliant DV7)

   On the desktop, audio is skipping.  I've moved to the audio-dev ppa and still have the skipping.  running pulseaudio -vvvvv I get the following output when playing a song in Guayadeque (same in other players):

D: alsa-sink.c: Wakeup from ALSA!
I: alsa-sink.c: Underrun!
I: alsa-sink.c: Increasing wakeup watermark to 40.00 ms
D: protocol-native.c: Underrun on ''Gimme Three Steps' by 'Lynyrd Skynyrd'', 0 bytes in queue.
D: protocol-native.c: Requesting rewind due to rewrite.

lspci gives:
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

   Additionally, on the desktop, I had been running x11vnc server without issue on Lucid.  Now, if it's running, X randomly freezes and the only way to recover is to SSH into the box from another and reboot.  (command line continues to work fine via SSH but 'sudo service gdm restart' does nothing, nor does killing X processes ... which this is occurring, Xorg takes 100% of one core.)

Any thoughts for any of these issues?

Thanks,
   Sean

---

### Post by mullens101 on 2010-10-01
oh, a little more info - when I run any of the alsa command lines (aplay -l for example) I get shared library errors as follows:

[noparse]>aplay -l
ALSA lib conf.c:3288:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:882:(snd_ctl_open_noupdate) Invalid CTL hw:0
aplay: device_list:244: control open (0): No such file or directory
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/noparse]

---

### Post by James2k on 2010-10-03
While I can't help with your other two issues, but regarding the battery issue on your laptop, you are not alone. I've had the same problem since Ubuntu 10.10 BETA 2, my battery indicator simply says (estimating...) rather than the percentage available. Looks like they've changed the calculation on how to work out battery power since lucid which doesn't seem to work too well on HP and Compaq hardware. (I have a Compaq Presario CQ60)

Various bug reports about battery issues are on LaunchPad, hopefully it should be fixed soon.

Sorry I can't help you with your other problems.

---

### Post by cariboo on 2010-10-03
I noticed friday when I had my netbook running on AC that it did show an estimate for how long it would take to charge the battery, but at the time it estimated 20 hours to full charge from about 82%. 

Powertop was also giving some fairly strange estimates as far as time left was concerned, at one point it was saying 8 hours of charge left on a 3 hour battery.

I've never used this system with Windows, even though it came with it installed, so I have no idea of what the behavior in WIndows should be.

---

### Post by NightwishFan on 2010-10-03
For pulse try turning off glitch free:
```
sudo nano /etc/pulse/default.pa
```

Change the line that says:
```
load-module module-udev-detect
```
to:
```
load-module module-udev-detect tsched=0
```



Restart pulse for changes to take effect, perhaps reboot to be safe. It may also be called "load-module module-hal-detect" but I doubt it.

---

### Post by FuturePilot on 2010-10-03
Battery issue bug [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/633552]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/633552")

---

### Post by M4570D0N on 2010-10-05
I am also having this issue with the battery showing "(estimating...). What I find odd is that when I click on it and it opens up Power Statistics, it shows my battery capacity % and current percentage. I'm not sure why it can't display this when clicking on the icon if it shows it here. 

Additionally, the Power Statistics details now (since 10.10) lists my battery as Nickel Metal Hydride, rather than Lithium Ion. Neither of these issues existed with 10.04 or Linux Mint 9 gnome. Initially 10.10 beta gave me the same nickel metal hydride error but thought one of the updates resolved this as it read as lithium ion again. After upgrading to 10.10rc the issue came up again.

I took a look at the launchpad link above. The last comment links to another bug report and has a patch attached near the bottom that purportedly fixes the "estimating.." issue. Has anyone else confirmed this?

---

### Post by krunge on 2010-10-06
> **mullens101 said:**
> 
   Additionally, on the desktop, I had been running x11vnc server without issue on Lucid.  Now, if it's running, X randomly freezes and the only way to recover is to SSH into the box from another and reboot.  (command line continues to work fine via SSH but 'sudo service gdm restart' does nothing, nor does killing X processes ... which this is occurring, Xorg takes 100% of one core.)

The freezing problem reported in this thread might be due to this Xorg X server bug:

[INDENT][https://bugs.freedesktop.org/show_bug.cgi?id=30032](https://bugs.freedesktop.org/show_bug.cgi?id=30032)[/INDENT]

Until they fix that one can add the "-noxrecord" x11vnc option as a workaround.

Another workaround is to disable the RECORD extension in the X server (via xorg.conf I guess.)

Please report back here if either one fixes the system freezing problem or not.

---

### Post by mullens101 on 2010-10-07
Thanks for the info guys.  NightwishFan, thanks, the tsched setting did fix the audio issues.  Krunge, I'm trying the noxrecord and/or disabling Record extension now.  I'll let you know in a bit if it works.  I'm starting with the norecord.

---

### Post by mullens101 on 2010-10-08
Krunge, thanks for the tip on the noxrecord, it appears to have solved my issue.  Only the battery bug remains!

---

