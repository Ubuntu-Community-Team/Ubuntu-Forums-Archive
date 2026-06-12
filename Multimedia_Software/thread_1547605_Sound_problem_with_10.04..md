---
title: "Sound problem with 10.04."
date: 2010-08-07
forum: Multimedia Software
---

### Post by Detective RooTz on 2010-08-07
See on my windows side. When ever I install windows I have to manually install this

[http://support.gateway.com/support/drivers/getFile.asp?id=21212&dscr=Sigmatel%20HD%20Audio%20Driver%20version:%206.10.5290.0&uid=277462428](http://support.gateway.com/support/drivers/getFile.asp?id=21212&dscr=Sigmatel%20HD%20Audio%20Driver%20version:%206.10.5290.0&uid=277462428)

Well. I downloaded wine and tried it and it said Unknown error.

So, how would I go about getting my sound driver then? I really need sound ;)


I do not have anything under Hardware, Output or Input in the Sound preferences.
I've already tried OSS, I think I installed ALSA but I do not know how to work it.

I've downloaded a tar.bz2 pack for alsa, where is a deb. I hate configuring stuff, I want something I can click and install.

```

Audio
        Sound Card
            SigmaTel High Definition Audio CODEC
        Playback Devices
            Digital Output Device (S/PDIF) (SigmaTel High Definition Audio CODEC)
            Speakers (SigmaTel High Definition Audio CODEC)    (default)
        Recording Devices
            Rear Mic (SigmaTel High Definition Audio CODEC)    (default)
            Microphone (SigmaTel High Definition Audio CODEC)
            Line In (SigmaTel High Definition Audio CODEC)
```

That's my sound card, microphone plugged in etc.

So, yeah.[hr]
I checked it out and got this.

[http://ubuntuforums.org/archive/index.php/t-500759.html](http://ubuntuforums.org/archive/index.php/t-500759.html)

I'm looking further into this.

---

### Post by Detective RooTz on 2010-08-07
This is a urgent matter. Could someone help me?

---

### Post by jmfal on 2010-08-07
You can`t use windows sound drivers with ubuntu.

Read the stickies at the top of this forum section.

try  alsamixer   in a terminal and make sure your speakers aren`t muted

---

### Post by Detective RooTz on 2010-08-07
> **jmfal said:**
> You can`t use windows sound drivers with ubuntu.

Read the stickies at the top of this forum section.

try  alsamixer   in a terminal and make sure your speakers aren`t muted

I know my speakers are not muted.

What's the terminal code for alsamixer.

See someone told me to install alsa but I did not find a terminal/deb package. I have no clue how to install a .tar.bz2 file.

---

### Post by Detective RooTz on 2010-08-07
I did everything in this thread.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[SIZE=2]sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=[COLOR=blue]<enter driver name here e.g. via82xx> [/COLOR][COLOR=blue][COLOR=black]--with-oss=yes[/COLOR][/COLOR] [/SIZE]
[SIZE=2]sudo make  [/SIZE]
[SIZE=2]sudo make install[/SIZE]
^when I got there. I typed the sudo configure all that and I put --with-cards=hda-codec-sigmatel and on.

Well, my Sound card is a Sigmatel High Definition audio codec, so hda-codec-sigmatel must be it right?

well when I got to that line as said it said ./configure did not exist or something like that.

---

### Post by Detective RooTz on 2010-08-07
I hate to bother people but this is a serious matter.

I have important online work that requires me to listen to stuff and I can not pass/do my job if I can not hear it lol.

---

### Post by simosx on 2010-08-07
> **Detective RooTz said:**
> I hate to bother people but this is a serious matter.

I have important online work that requires me to listen to stuff and I can not pass/do my job if I can not hear it lol.

As it was said above, in Linux you do not get those separate drivers for devices. The proper way to do this is to work with the Linux kernel (sound subsystem: Alsa).

Step 1 is to extract detailed information of your sound hardware.
See [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) or
run
[FONT="Courier New"]wget [www.alsa-project.org/alsa-info.sh](www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh 
[/FONT]
You will be prompted to send the hardware information to the Alsa website, alsa-project.org. Select Yes and write down the URL you will be given. Give us that URL.

Depending on the output of alsa-info, you may need to upgrade your Alsa kernel driver to the latest version 1.0.23. You already tried something. The easy way to upgrade is to use the script AlsaUpgrade, found at [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by jmfal on 2010-08-07
open a terminal, type     alsamixer    press enter

did you add medibuntu repository as both stickies suggested??

it has some codecs that might help

---

### Post by Detective RooTz on 2010-08-08
Your ALSA information is located at [http://www.alsa-project.org/db/?f=e0cf03bafccedcf19ef121ec7bf5ee16bc19af73](http://www.alsa-project.org/db/?f=e0cf03bafccedcf19ef121ec7bf5ee16bc19af73)

Please inform the person helping you.

ganjafreak@ub3rl33tubuntu:~$ 


I got that.

---

### Post by jmfal on 2010-08-08
check out the hda intel snd by markbuntu, I went back and bumped it to the top of the forum.
  
There might be something there to help

---

### Post by simosx on 2010-08-08
> **Detective RooTz said:**
> Your ALSA information is located at [http://www.alsa-project.org/db/?f=e0cf03bafccedcf19ef121ec7bf5ee16bc19af73](http://www.alsa-project.org/db/?f=e0cf03bafccedcf19ef121ec7bf5ee16bc19af73)

Please inform the person helping you.

ganjafreak@ub3rl33tubuntu:~$ 


I got that.

There is a section in your alsa-info: 

[FONT="Courier New"]!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.22
Utilities version:  1.0.22
[/FONT]

What this says is that the kernel module for your audio hardware is not loaded for some reason. You will not be able to get sound unless you manage to get Alsa up and running.

You mentioned you tried to install manually the latest Alsa. The instructions you gave are for one part of Alsa, the 'driver' and you do not mention if you manage to complete it.

In this case what you can do is try to upgrade your Alsa to 1.0.23, by following the fine instructions at [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by Detective RooTz on 2010-08-08
> **simosx said:**
> There is a section in your alsa-info: 

[FONT=Courier New]!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.22
Utilities version:  1.0.22
[/FONT]

What this says is that the kernel module for your audio hardware is not loaded for some reason. You will not be able to get sound unless you manage to get Alsa up and running.

You mentioned you tried to install manually the latest Alsa. The instructions you gave are for one part of Alsa, the 'driver' and you do not mention if you manage to complete it.

In this case what you can do is try to upgrade your Alsa to 1.0.23, by following the fine instructions at [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

Okay. I'll try upgrading.

By me upgrading does that mean it will automatically find the right driver for me?

Also I think ubuntu should release there OS with all drivers possible on the system so you do not have to deal with this.

---

### Post by Detective RooTz on 2010-08-08
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9rc4a.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9rc4a.tar.bz2)


that is the latest and highest numbered in the page so therefore I got that one.

i'll try and follow those upgrade instructions.

---

### Post by Detective RooTz on 2010-08-08
I tried doing that.

I didn't download the same upgrade but I named the file the same.

so I did this. 

cd to my desktop

typed sudo ./filename -d and it did not work

so I didn't do that but I checked my .conf file and I got this.

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
```

It asys change something on the options thing right there. I have a hda-intel-sigmatel I think. What do I change?

That is what confusing me, I do nto know nothing about this.

---

### Post by simosx on 2010-08-08
> **Detective RooTz said:**
> [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9rc4a.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9rc4a.tar.bz2)


that is the latest and highest numbered in the page so therefore I got that one.

i'll try and follow those upgrade instructions.

Try AlsaUpgrade. Google 'AlsaUpgrade' and you will find the discussion in this forum.

You need the same version for 1) driver 2) library 3) tools, something that AlsaUpgrade does for you.

---

### Post by Detective RooTz on 2010-08-08
The only thing I know I installed is some alsa gui and player
The driver file. I never got any tools/utilities pack.

---

### Post by Detective RooTz on 2010-08-08
OMG. I have sound in firefox now, I just do nto have it on rythembox.

I was on musicbattle.com it's a game and I have a song on my profile and it started palying it.

so I know firefox will play songs, need to get the other rythembox to.

---

### Post by Detective RooTz on 2010-08-08
Still have yet to get this.. I can not use mint, arch or anything else because once I go to install it says my input is not supported.

Even on the live cd I do not think my gfx card or monitor is for linux.

---

### Post by Detective RooTz on 2010-08-09
So can anyone connect to me and help me with this?

---

### Post by Detective RooTz on 2010-08-09
Bumping this thread.....

---

### Post by utilitytrack on 2010-08-09
> **Detective RooTz said:**
> *See on my windows side. When ever I install windows I have to manually install this ([link to Windows Vista Sigmatel HD audio driver]("http://support.gateway.com/support/drivers/getFile.asp?id=21212&dscr=Sigmatel%20HD%20Audio%20Driver%20version:%206.10.5290.0&uid=277462428"))*

My God... I'm speechless.

> **Detective RooTz said:**
> [I]What's the terminal code for alsamixer.
See someone told me to install alsa but I did not find a terminal/deb package. I have no clue how to install a .tar.bz2 file.[/I]

Oh. Please read this [https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")


> **Detective RooTz said:**
> *Okay. I'll try upgrading. By me upgrading does that mean it will automatically find the right driver for me?*

This is very good thought. Please read this [https://help.ubuntu.com/community/UpgradeNotes]("https://help.ubuntu.com/community/UpgradeNotes") and this [http://en.wikipedia.org/wiki/Linux]("http://en.wikipedia.org/wiki/Linux")

> **Detective RooTz said:**
> So can anyone connect to me and help me with this?

No, probably. Sorry. Because because all that you do, leads us to despair.

---

### Post by lidex on 2010-08-09
Just use the alsa-upgrade link in my sig. Follow the insructions there and you should have a fully working alsa.

---

