---
title: "No sound in Ubuntu (7.04) using SB Xtreme Audio"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by MacMagnus on 2007-08-13
I have just installed Ubuntu 7.04 on my computer. I have two sound cards, one integrated with the motherboard ( Abit AV8 ), and a Sound Blaster Xtreme Audio.

It is the SB card that i want to use.

The OS tells me that it detects two cards. The first is the correct card that is embedded in the motherboard. The other is a SB Audigy. That is incorrect, it IS Xtreme Audio that i have.

Now to the point. I tried to solve this (using google), and saw the discussion at [http://ubuntuforums.org/showthread.php?t=239981](http://ubuntuforums.org/showthread.php?t=239981), but I have not solved it though. I tried downloading the files at [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi), but I just do not know how to compile stuff myself. I reckon that involves hour after hour trying to make it out.

One can of course say that if I am not willing to spend a few hours on making it work, I might as well be using Windows. But I is not that, nor the 0.00 && that attracts me.

I just do not want one of the most powerful man in the world to know what music I like, what political orientation I belong to, and etc.

But back to the point.

How do I solve this? Do I have to use the files on "Open Sound", and invest some hours to make the compiler work, or is there some other fix?

(I does not matter if the volume throttle button does not work. I like using the stereo amplifier anyway...)

---

### Post by renzokuken on 2007-08-13
the file on the link you gave is very easy to install.

download the **.DEB** file and save it to your home folder. (it is a debian installer file and since ubuntu is debian based it should work fine).....make sure you get the right architecture, if you are using 32 bit you want **linux 2.6 (x86) (DEB)**

once downloaded, open a terminal and run

```
sudo dpkg -i name_of_file_you_just_downloaded.deb
```

EDIT: apparently the latest alsa-driver supports your card, it may be better to try alsa first.

ubuntu ships with version 1.0.12 of alsa-driver, the latest is 1.0.14 which apprently has added support for X-Fi Xtreme

to update to the latest alsa do the following

download the latest **alsa-driver 1.0.14 from [www.alsa-project.org](www.alsa-project.org)** to your home folder

open a terminal and run the following

```
sudo apt-get install build-essential
tar xjf alsa*
cd alsa*
./configure
make
sudo make install
```

when its all finished reboot and see if your sound now works

---

### Post by MacMagnus on 2007-08-13
Thanks a lot! I actually made it work. It was not difficult at all...

I did not even have any problems with the volume-throttle, as some reported having on the first link I gave in the first post.

I am surprised that the file i downloaded that had the size of 2,5 MB became 150 MB after the compilation though...

---

### Post by renzokuken on 2007-08-13
congratulations dude, happy ubunting

just for clarification ......(for other users reading this thread looking for a solution).......which method worked?

the OSS deb or compiling te latest ALSA?

---

### Post by MacMagnus on 2007-08-13
I followed the latest advice you gave. I compiled the latest ALSA and installed it.

But regarding the volume-throttle: it actually don't work. You see, in my installation I have the opportunity to change between three "mixers". I chose the one namer "CA0106 (Alsa mixer)", and I COULD adjust the sound-volume using that one. But I soon noticed that the sound were horrible above speech-level. Absolutely horrible. So I had to switch to "VIA 8237 (Alsa mixer)".

Then the sound became OK. But the volume-throttle don't work. It don't matter what I do with the button actually. And the output-volume is so low that I have to turn the "volume-wheel" on my amplifier much longer than usual.

But that's it. All in all it's not big problems at all.

---

### Post by renzokuken on 2007-08-14
open a terminal and run ```
alsamixer
``` play with the settings in there (make sure nothing obvious is muted, press "m" to mute/unmute stuff, and other levels are acceptable

---

### Post by MacMagnus on 2007-08-14
Again: thanks a lot!

I'm hoping that the settings made there are the same when I reboot. They disappeared (it switched back to the default-values) once a couple of hours ago, but I think that was because I opened another application that adjust the settings in the sound-system.

---

### Post by Bunta on 2007-08-14
My sound icon at the top right corner of the screen has a red X mark on it. I have an onboard sound chip via8xx. I went to the link [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi) that magnus posted in the beginning of the message and downloaded the .deb package, ran, installed it and it froze during the installation. Now my computer won't boot up.

Is there a way to purge the package that I just installed?

edit: I got it to boot up in recovery mode and purge oss-linux. I then proceed to install alsa and my computer freeze at the "make" command.

---

### Post by ravo on 2007-08-22
just to let people know, latest ALSA driver worked for me. sound is good. getting 5.1 umpix  after editing .asoundrc file. happy days! thanks for your help!

---

### Post by HilliBilly on 2007-09-29
my X-Fi XtremeAudio doesn't work and i couldn't find a solution but this threads sounds that  some have it working?

i am on gutsy (2.6.22-10-generic, 64bit) and, yes, the alsa-driver 1.0.14 is installed.

that's how it looks:

$** aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

(sound is NOT muted, checked it by running alsamixer in a terminal)

$**lspci -v**
05:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs SB0790 X-Fi XA
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at d100 [size=32]
        Capabilities: <access denied>

(this means that ubuntu is detecting the presence of my soundcard)

MAYBE ... the drivers are not installed/running? but which driver? read somewhere that the sb x-fi xtremeaudio is not a "real" x-fi ([http://forums.creative.com/rss/message?board.id=soundblaster&message.id=79786](http://forums.creative.com/rss/message?board.id=soundblaster&message.id=79786)). someone else mentioned to me that the sb x-fi xtremeaudio is more like an audigy 4?!

here is the list of alsa supported cards ([http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)) if this is for help.

---

### Post by Temik on 2007-10-08
I bought this card some time ago and was first very dissapointed that it had no support under linux, but with ALSA 1.0.15rc2 (which I compiled and installed) sound finally came out from my speakers smile.gif There was no 5.1 or Line-in but I did not care because sound was great and I am not using Line-in and have a 2.1 system. But then, after a major glitch I upgraded to Ubuntu Gutsy from Feisty and there was no sound at all. I installed the drivers again, but still no use... sad.gif
I wiped the system and installed feisty again but the same problem occured ... And since then I am not able to get ANY sound from the card using alsa...
The OSS driver works, but sound is buggy and distorted.....

Does anyone know how to solve this problem? :confused:

---

### Post by HilliBilly on 2007-10-08
finally i've got this sound card to work.

don't miss to ...

1. unmute IEC958 in alsamixer. you must see a 'MM' instead of a '00'.
2. disable in >system>preferences>sound>sounds the ESD

otherwise you don't have sound.

look here:
[http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106)

------x-----

you could check if you really need 1.0.15 with:

**lspci -vvn**
05:01.0 0401: 1102:0007
Subsystem: 1102:[COLOR="Red"]1012[/COLOR]
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 32 (500ns min, 5000ns max)
Interrupt: pin A routed to IRQ 19
Region 0: I/O ports at d100 [size=32]
Capabilities: <access denied>

$dmesg | grep ca0106
[ 50.214475] snd-ca0106: Model [COLOR="Red"]1012[/COLOR] Rev 00000000 Serial 10121102

the red is important, only if your lspci output shows something like 1102:1013 then you have to use the 1.0.15rc1 release (afaik model 1102:1012 is handled by 1.0.14 correctly). btw ... the 1102 is the same for all cards, its the code for CL.

there are a lot of different card models, you could check your model here:
/usr/src/alsa/alsa-driver-1.0.14/alsa-kernel/pci/ca0106/ca0106_main.c

(more about this you'll find here
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=32](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=32)
Bug-ID:0003251)

-----x-----

and this is how i did it:

**modinfo soundcore**
filename: /lib/modules/2.6.22-12-generic/kernel/sound/soundcore.ko
alias: char-major-14-*
license: GPL
author: Alan Cox
description: Core sound module
srcversion: 548AA54AF08207316C104F8
depends:
vermagic: 2.6.22-12-generic SMP mod_unload

**apt-get install**
linux-headers-generic
build-essential
debconf
dh-make
fakeroot
gcc-3.4
libstdc++5
module-assistant
gcc-3.3
gcc-3.3-base
gcc-3.4
gcc-3.4-base
gcc-4.1
gcc-4.1-base
gcc-4.1-locales
gcc-4.1-multilib
gcc-4.2
gcc-4.2-base


[B]sudo mkdir /usr/src/alsa
cd /usr/src/alsa/
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2)
sudo bunzip2 alsa-driver-1.0.14.tar.bz2
sudo tar -xf alsa-driver-1.0.14.tar
sudo bunzip2 alsa-lib-1.0.14a.tar.bz2
sudo tar -xf alsa-lib-1.0.14a.tar
cd alsa-driver-1.0.14/
sudo ./configure --with-cards=ca0106 --with-sequencer=yes
sudo make
sudo make install
cd /usr/src/alsa/alsa-lib-1.0.14a/
sudo ./configure
sudo make
sudo make install[/B]


**modprobe snd-ca0106 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss**

create a file called **alsa** in **/etc/&#8203;modutils/** with this code:

# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-ca0106
# module options should go here

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss


**sudo update-modules**


create **~/.asoundrc **with this code:

pcm.dmix51 {
type dmix
ipc_key 1024
slave {
pcm "hw:0,0"
rate 44100
channels 6
period_time 0
period_size 1024
buffer_time 0
buffer_size 4096
}
}

pcm.20to51 {
type route
slave.pcm surround51
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}

pcm.duplex {
type asym
playback.pcm "20to51" #muss als pcm.20to51 definiert sein
capture.pcm "dsnooper"
}



create **/etc/asound.conf** with this code:

code:
pcm.ca0106 {
type hw
card 0
}

ctl.ca0106 {
type hw
card 0
}

pcm.snd_card {
type hw
card 0
device 0
}

ctl.snd_card {
type hw
card 0
device 0
}



pcm.dmixer {
type dmix
ipc_key 1024
ipc_perm 0666
slave.pcm "snd_card"
slave {
period_time 0
period_size 1024
buffer_size 4096
rate 44100
channels 6
}
bindings {
0 0
1 1
2 2
3 3
4 4
5 5
}
}

pcm.dsnooper {
type dsnoop
ipc_key 2048
ipc_perm 0666
slave.pcm "snd_card"
slave
{
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
bindings {
0 0
1 1
}
}

pcm.duplex {
type asym
playback.pcm "dmixer"
capture.pcm "dsnooper"
}

pcm.!default {
type plug
slave.pcm "duplex"
}

----------------

(note: .asoundrc and asound.conf are tricky issues, you could also try it without!)

[B]reboot
speaker-test -c 2 -t wav
speaker-test -c 6 -t wav -D surround51
aplay -vv /usr/share/sounds/ekiga/dialtone.wav[/B]

---

### Post by qler on 2007-10-08
HilliBilly, thanks a lot. At last a can listen to the music in linux :) 
The only thing is that there're some noise distortion, it's even heard “in silence” when nothing's playing. The only thing that differs is that in installed 1.0.15rc3 alsa, because  lspci -vvn showed me 1102:1013. Could this be the reason of this noise? Is everything fine with your card?

---

### Post by HilliBilly on 2007-10-08
cannot really talk about 1.0.15rc3 because i haven't installed that version but do not believe that this is the reason for your noise distortion. the 1.0.14 simply does not recognize that the 1102:1013 is a X-Fi XtremeAudio, afaik.

have you tried it without .asoundrc and asound.conf? make a copy of each file and remove the original, afterwards you could rename your copy back to the original. for testing you don't have to reboot, just run the speaker-test. eventually remove only one of the asound's.

yes, i have proper sound, no noise distortion.

just another idea: are you using headphones? if you have another one, try that too.

---

### Post by Temik on 2007-10-08
Thanks for the help! But did you run into the problem when Flash has no sound whatsoever in firefox?

---

### Post by Temik on 2007-10-14
Seriously... Doesn't anyone know how to make firefox use this card for the output?

---

### Post by HilliBilly on 2007-10-14
temik,

in the meanwhile i am using 1.0.15rc3 and sound is ok.

what is your problem with firefox exactly?

does this command work for you:
speaker-test -c 6 -t wav

---

### Post by Mentalor on 2007-10-30
> **renzokuken said:**
> the file on the link you gave is very easy to install...snip...
You da man, renzokuken.  I'm rather an ubunting noob and had been pulling my hair out trying to get sound.  After finally finding this thread, you made it all better.  Ta muchly.

---

### Post by renzokuken on 2007-10-31
glad i could help Mantalor

happy ubunting

---

### Post by jzchin on 2007-11-03
I DON'T KNOW WHO DID THIS DOCUMENT. BUT THE ONE WHO DID IT, IT'S THE BIG %^@%$#$

THANKS A LOOOOOTTT!!!!!!!!!!!!!!  :D :D :D :D

YOU DON'T KNOW HOW MANY TIME I'VE SPEND TRYING TO CONFIGURE THIS SOUND CARD.


Now I can listen to music  


One more reason to leave microsucks away!!!!!!
THANKS AGAIN

AN UBUNTU FAN

JOSE

---

### Post by warhammer39m on 2008-01-12
> **renzokuken said:**
> the file on the link you gave is very easy to install.

download the **.DEB** file and save it to your home folder. (it is a debian installer file and since ubuntu is debian based it should work fine).....make sure you get the right architecture, if you are using 32 bit you want **linux 2.6 (x86) (DEB)**

once downloaded, open a terminal and run

```
sudo dpkg -i name_of_file_you_just_downloaded.deb
```

EDIT: apparently the latest alsa-driver supports your card, it may be better to try alsa first.

ubuntu ships with version 1.0.12 of alsa-driver, the latest is 1.0.14 which apprently has added support for X-Fi Xtreme

to update to the latest alsa do the following

download the latest **alsa-driver 1.0.14 from [www.alsa-project.org](www.alsa-project.org)** to your home folder

open a terminal and run the following

```
sudo apt-get install build-essential
tar xjf alsa*
cd alsa*
./configure
make
sudo make install
```

when its all finished reboot and see if your sound now works

Thanks a lot, it worked for me (alsa drivers 1.0.15) on ubuntu Gutsy-Gibbon 7.10

I had to deactivate IEC958 for it to work. I can activate system sounds and software mixing and it all works without problems (since i only have a 2.0 speaker system, I din't test surround sound)

---

