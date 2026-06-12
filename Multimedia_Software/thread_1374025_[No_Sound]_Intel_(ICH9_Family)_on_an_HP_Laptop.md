---
title: "[No Sound] Intel (ICH9 Family) on an HP Laptop"
date: 2010-01-06
forum: Multimedia Software
---

### Post by glopal on 2010-01-06
So I'm running karmic on an HP G71 laptop. Was wicked impressed... wireless worked out of the box... but sound still isn't working.

I tried to follow the [COLOR=Navy]_               [**Comprehensive Sound Problem Solutions Guide**]("http://ubuntuforums.org/showthread.php?t=205449")_[/COLOR], but got stuck on step 3.

> [SIZE=2]**(3)** Check to see if the ALSA driver for your sound card exists. Go to [/SIZE][COLOR=Navy]_[[SIZE=2]http://www.alsa-project.org/alsa-doc/[/SIZE]]("http://www.alsa-project.org/alsa-doc/")_[/COLOR][SIZE=2] and search for your sound card (chipset) manufacturer in the dropdown box. [/SIZE]The link is bogus. No dropdown box in sight.

Anyways, if someone could help me to continue on with the guide, offer any suggestions based on the provided info, or get me to provide more info... that would be great. (I've heard good things about ubuntu community... one of the reasons for switching to it from openSUSE)

```
hoffman@hoffman-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````
hoffman@hoffman-laptop:~$ lspci -v
...
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 306b
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d4500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
...

```

[B]SOLUTION:
[/B]I found it [here]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Sound%20drivers%20need%20to%20be%20updated"). Apparently I just needed new alsa drivers, which were real easy to install.

Also I commented out all of the options I added to the alsa-base.config file, they weren't needed. Thanks everyone!

---

### Post by mhgsys on 2010-01-06
Hey

I noticed you are using a intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

To get sound working you need to add;
```


options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

```

in /etc/modprobe.d/alsa-base.conf

so; open up a terminal ;
typ;
```


sudo gedit /etc/modprobe.d/alsa-base.conf

```
and copy paste the options from above in it at the bottom of the file; save your file, reboot and all should be working.

info from here;
[http://ubuntuforums.org/showthread.php?t=940689&page=3](http://ubuntuforums.org/showthread.php?t=940689&page=3)

---

### Post by glopal on 2010-01-06
> **mhgsys said:**
> Hey

I noticed you are using a intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

To get sound working you need to add;
```


options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

```in /etc/modprobe.d/alsa-base.conf

so; open up a terminal ;
typ;
```


sudo gedit /etc/modprobe.d/alsa-base.conf

```and copy paste the options from above in it at the bottom of the file; save your file, reboot and all should be working.

info from here;
[http://ubuntuforums.org/showthread.php?t=940689&page=3](http://ubuntuforums.org/showthread.php?t=940689&page=3)

I added those lines to the file... just like you said, and then rebooted. Now for some reason my sound device isn't showing up...

```
hoffman@hoffman-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
```Heres the config file

```
hoffman@hoffman-laptop:~$ cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

#Fix for Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1
```

---

### Post by mhgsys on 2010-01-06
does it show up with 
```

lspci -v 

```


I don't have this card myself, But there's lots of info ;


[http://ubuntuforums.org/showthread.php?t=940689](http://ubuntuforums.org/showthread.php?t=940689) (about that card)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) (restoring to default card settings)

[http://ubuntuforums.org/showthread.php?t=1307320](http://ubuntuforums.org/showthread.php?t=1307320) (this is about the card not being detected)

srry to leave you hanging like this ; but I really got to get in my car right now , or I will have a angry girlfriend for leaving her at her parents.lol

Good luck,

---

### Post by glopal on 2010-01-06
> **mhgsys said:**
> does it show up with 
```

lspci -v 

```
I don't have this card myself, But there's lots of info ;


[http://ubuntuforums.org/showthread.php?t=940689](http://ubuntuforums.org/showthread.php?t=940689) (about that card)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) (restoring to default card settings)

[http://ubuntuforums.org/showthread.php?t=1307320](http://ubuntuforums.org/showthread.php?t=1307320) (this is about the card not being detected)

srry to leave you hanging like this ; but I really got to get in my car right now , or I will have a angry girlfriend for leaving her at her parents.lol

Good luck,

I appreciate the help but I'm in a worse spot now than I was before. The (restoring to default card settings) link is that comprehensive guide I linked to in my original post. Like I had said, step 3 is useless because the link is dead/wrong... thus I can't figure out what driver I should be using.

lspci -v still shows my card.

Do you know what driver I should use?

---

### Post by Yellow Pasque on 2010-01-06
snd-hda-intel is the driver you should use. It appeared to be loaded properly in your earlier post:
```
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel
```

---

### Post by glopal on 2010-01-06
After some tinkering aplay -l showing something again.

It seems as if
```
options snd-hda-intel single_cmd=1
```
was causing the problem.

Mind you... still no sound.

---

### Post by mhgsys on 2010-01-06
back > 
@glopal have you tried the irqpoll ?

[http://ubuntuforums.org/showthread.php?t=940689](http://ubuntuforums.org/showthread.php?t=940689)

---

### Post by glopal on 2010-01-06
> **mhgsys said:**
> back > 
@glopal have you tried the irqpoll ?

[http://ubuntuforums.org/showthread.php?t=940689](http://ubuntuforums.org/showthread.php?t=940689)

I was looking in to trying it... but karmic is using grub 2.0, which apparently doesn't have a menu.lst file... so I don't know where to put the irqpoll option...

---

### Post by mhgsys on 2010-01-06
> **glopal said:**
> I was looking in to trying it... but karmic is using grub 2.0, which apparently doesn't have a menu.lst file... so I don't know where to put the irqpoll option...

Ah, I'm sorry . But I cant help you with karmic, since I don't boot it myself ..
I'm sticking to 9.04 for a while , + all my work is located on this machine.

Maybe you'll have more luck with 9.04 although "downgrading" isn't what you should be looking for > Anyway; there will be more people with the same issues (soon) so the solution will come up on these forum sooner or later .

EDIT: (about being in a worse spot then before ; you can easily revert what we've done here; just edit the  /etc/modprobe.d/alsa-base.conf again, and put a # in front of the options you've added or delete those lines)

---

### Post by markbuntu on 2010-01-06
There is a lot of HP laptops listed here

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

