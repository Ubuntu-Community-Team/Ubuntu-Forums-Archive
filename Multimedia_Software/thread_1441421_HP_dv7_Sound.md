---
title: "HP dv7 Sound"
date: 2010-03-28
forum: Multimedia Software
---

### Post by GilbertEvanG on 2010-03-28
Hello,

I've been struggling to get my sound to work properly in my HP dv7 laptop in Ubuntu 9.10 64-bit.

If I follow the instructions here ([https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/524802](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/524802)) then I can get my microphone to work.

My speakers worked fine right out of the box, but the headphone jack does not. When I follow the instructions here ([https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/490669](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/490669)) and install the alsa backports then my headphone jack works properly, but when I shutdown my computer I get a loud crackling/popping sound. Uninstalling the alsa backports stops the crackling, but then the headphone jack doesn't function.

Any ideas on how to get the headphones to work without making annoying sounds on shutdown?

Thanks.

---

### Post by lidex on 2010-03-30
You could try the alsa update script in my sig rather than backports. These threads may help:
[http://ubuntuforums.org/showthread.php?t=1184379]("http://ubuntuforums.org/showthread.php?t=1184379")
[http://ubuntuforums.org/showthread.php?t=904677]("http://ubuntuforums.org/showthread.php?t=904677")
[http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/]("http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/")

---

### Post by GilbertEvanG on 2010-03-30
Thanks for the response.

That first link is actually a thread by me. I had a similar problem in an older version of Ubuntu. I'm using Karmic now and those things I did to fix it last time don't seem to exist anymore, or I can't find the same menus at least.

I'm trying the alsa upgrade script right now. Its upgrading from 1.0.20 to 1.0.22.1 so maybe it will help.

---

### Post by GilbertEvanG on 2010-03-30
Alright, here's what I've found.

After updating alsa, my headphone jack did work. But, the popping sound I was experiencing on shutdown also returned. And, I noticed a new behavior after the upgrade. When I would play a youtube video in firefox, and then open up skype, skype would have no sound until I closed firefox.

I reverted the changes made by the update script, and then after I rebooted, my headphone jack was still working, and skype and firefox can play sounds simultaneously. But when I shutdown the popping sound was still there.

It turns out that when the update script reverted its changes, it installed the backports (even though I didn't have them installed prior to updating alsa the first time). Once I removed the backports, then my headphone jack no longer functions, and all popping sounds are no more.

It seems like I've isolated the problem of the popping sound to be from the backports. But it also seems necessary to get my headphone jack to function.

---

### Post by lidex on 2010-03-30
Did you try disabling the beep?
There is a chance that enabling the right widget in alsa-base.conf will clear that issue. What is the output of this command:
```
cat /proc/asound/card0/codec#* | grep Codec
```

Relevant threads:
[http://ubuntuforums.org/showthread.php?t=1043568]("http://ubuntuforums.org/showthread.php?t=1043568")

[http://ubuntuforums.org/showthread.php?t=820959]("http://ubuntuforums.org/showthread.php?t=820959")

[http://ubuntuforums.org/showthread.php?t=616845]("http://ubuntuforums.org/showthread.php?t=616845")

---

### Post by GilbertEvanG on 2010-03-30
The output of that command is:

```
Codec: IDT 92HD75B3X5
```

---

### Post by lidex on 2010-03-30
OK. Try this. In a terminal.
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

At the bottom of that file add this line:
```
options snd_hda_intel model=hp-dv5
```

Save. Close. Reboot.

---

### Post by GilbertEvanG on 2010-03-30
I've already done that. That's what got my microphone working a few days ago. Here is the contents of that file:

```

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
#options snd-hda-intel power_save=10 power_save_controller=N


#CUSTOM CHANGES
#options snd-hda-intel power_save=10 power_save_controller=N model=hp-dv5 enable_msi=1
options snd-hda-intel model=hp-dv5 enable_msi=1

```Is it supposed to be snd-hda-intel, or snd_hda_intel?

---

### Post by lidex on 2010-03-30
this is what I have on my Dv7:
> options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5

---

### Post by GilbertEvanG on 2010-03-31
That seemed to have the same behavior as what I had before. I didn't have any popping sounds on shutdown, but the headphone jack didn't work. I tried installing the backports with that configuration you posted and then the usual things happened: the headphones worked, but then I get those popping noises on shutdown most of the time.

---

### Post by lidex on 2010-03-31
What about the beep?
BTW I think you're right on the _ vs - issue. However it seems to work for me. I'll have to check when I get back to my laptop. Also the "stack" option is dependent on how many audio jacks you have. Mine has three, check yours.

---

### Post by GilbertEvanG on 2010-03-31
What beep are you talking about?

---

### Post by lidex on 2010-03-31
Run alsamixer:
```
alsamixer
```
Press F3 and scroll all the way to the right with the right-arrow key. Should be an option labelled "Beep". If so, mute it.

---

### Post by GilbertEvanG on 2010-03-31
I found a section called "PC Beep", and it looks like it was already at 0.

---

### Post by lidex on 2010-03-31
Yeah...I don't know, it worked for my crackling issue. Maybe a reboot. I'll see what else I can find and get back to you.

---

### Post by GilbertEvanG on 2010-03-31
Thanks, I appreciate it.

Here is a summary of what I've done:

Right now, there is no crackling noise. I just don't have my headphone jack working. When I play sound with headphones plugged in, the sound still comes out the speakers and nothing comes out the headphones.

My speakers work as expected when using applications such as firefox or skype. My microphone works fine once I followed the steps here ([https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/524802/comments/2](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/524802/comments/2)), which was essentially just adding the ```
options snd-hda-intel model=hp-dv5 enable_msi=1
``` line to my alsa-base.conf file.

I currently am using the alsa drivers that came with ubuntu 9.10. When I used the upgrade script I seemed to have other bad things happening so I reverted those changes (using the script). The only way I've been able to get my headphones to work is to install the alsa backports with:

```
sudo apt-get install linux-backports-modules-alsa-$(uname -r)
```but doing so makes the crackling sound to occur on shutdown.

The current state of my alsa-base.conf file is:
```

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
#options snd-hda-intel power_save=10 power_save_controller=N

#CUSTOM CHANGES
#options snd-hda-intel power_save=10 power_save_controller=N model=hp-dv5 enable_msi=1
options snd-hda-intel model=hp-dv5 enable_msi=1

#options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
#options snd-hda-intel model=3stack enable=yes
#options snd-hda-intel model=auto position_fix=1 enable=yes
#options snd-hda-intel enable_msi=1
#options snd_hda_intel model=hp-dv5 

```And the PC Beep is set to 0.

---

### Post by lidex on 2010-03-31
One thing before I pack it in maybe you can try enabling the line:
```
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0

```
and see if that gets headphones working.

Bug report for crackling:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/23984]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/23984")

---

### Post by GilbertEvanG on 2010-03-31
Unfortunately it did not. I tried putting it before the ```
options snd-hda-intel model=hp-dv5 enable_msi=1
``` line as well as after and neither seemed to have an effect that I could notice.

---

### Post by GilbertEvanG on 2010-05-01
Upgrading to Ubuntu 10.04 seemed to make all of my sound issues go away. My headphone jack worked immediately after the upgrade, and there is no crackling sound on shutdown.

Finally!

---

### Post by Jack-87 on 2010-07-18
thats odd.. in my dv7 boot up shut down my sound has crackling noise... and my internal mic and webcam do not work. I have not yet tested headphones jack or mic jack

---

### Post by lidex on 2010-07-18
> **Jack-87 said:**
> thats odd.. in my dv7 boot up shut down my sound has crackling noise... and my internal mic and webcam do not work. I have not yet tested headphones jack or mic jack

What are your vitals? Can you post the output of these terminal commands for me please:
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

### Post by Jack-87 on 2010-07-18
> **lidex said:**
> What are your vitals? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

My computer is an HP DV7-3183cl running ubuntu 10.04 Laptop the following out put is posted bellow. thanks for your time.

```
jack@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux
jack@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jack@ubuntu:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-24-generic 2.6.32-24.17                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.24.25                                    Backported drivers for alsa-driver snapshot.
jack@ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B3X5

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia GT21x HDMI

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia GT21x HDMI

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia GT21x HDMI

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia GT21x HDMI

```

I ended up installing the backport moduals still with no luck

---

### Post by lidex on 2010-07-18
OK. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-hda-intel model=3stack-6ch enable=yes
options snd-hda-intel position_fix=1 enable_msi=1

```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Jack-87 on 2010-07-18
> **lidex said:**
> OK. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert these lines at the bottom:
```
options snd-hda-intel model=3stack-6ch enable=yes
options snd-hda-intel position_fix=1 enable_msi=1

```Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

Thanks a ton for your help. I will report back after I reboot. However I never did mess with the preferences sound settings... so playing around in there it had the mic muted as input sound. of course in windows its nice to mute the mic so you dont hear an echo... but looks like in linux muting the mic disables it.. so I unmuted it and mic works fine now... and input about the web cam... or reference where to look?

---

### Post by lidex on 2010-07-18
Webcam? Have a look here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#webcam](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#webcam)

---

### Post by Jack-87 on 2010-07-19
> **lidex said:**
> Webcam? Have a look here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#webcam](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#webcam)

Oddly enough mine is supposed to be working out of the box.... and it didn't yesterday nor earlier... but it works now. oh well... I wont complain. I have not rebooted yet today since i made the changes earlier for the sound card (downloading junk) I will post my results sometime tomorrow. Thanks for all your help.

---

