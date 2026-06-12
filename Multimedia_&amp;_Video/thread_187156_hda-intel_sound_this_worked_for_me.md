---
title: "hda-intel sound: this worked for me"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by chubuntu on 2006-06-02
dist-upgraded my Sony Vaio VGN-S380P to dapper from breezy last night.  Soundcard was not detecting properly... some weird stuff.

With lspci and in Device Manager it showed up fine:
Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
but in System > Preferences > Sound, under default sound card, there was nothing.  alsamixer basically complained to the effect of no sound card.  Same stuff others have mentioned, like clicking on volume control, I got no sound card configured and some Gstreamer error.

I tried running alsaconf, it ran through everything just fine, reboot, but same thing, no sound card.

So I ended up downloading the 1.011 alsa driver, library, utilities, and oss from [http://www.alsa-project.org](http://www.alsa-project.org), basically:
  479  cd /home/jim/downloads/alsa-dapper-1.0.11/
  480  tar -xjvf alsa-driver-1.0.11.tar.bz2 
  481  tar -xjvf alsa-lib-1.0.11.tar.bz2 
  482  tar -xjvf alsa-oss-1.0.11.tar.bz2 
  483  tar -xjvf alsa-utils-1.0.11.tar.bz2 
  484  cd alsa-driver-1.0.11
  485  ./configure --with-oss=yes --with-cards=hda-intel
  486  make
  487  make install
  488  cd ../alsa-lib-1.0.11
  489  ./configure
  490  make install
  491  cd ../alsa-oss-1.0.11
  492  ./configure
  493  make install
  494  cd ../alsa-utils-1.0.11
  495  ./configure
  496  make install
  497  alsaconf
  498  shutdown -r now
  
And everything worked next boot.

---

### Post by ajack on 2006-06-05
Thaks for the infomation... I have an Acer 3624 which uses the ICH6/Realtek ALC655 sound chip and I have read in other threads that this version of the ASLA source solves the problems I am facing with my Dapper installation.  I am afraid of recompiling this as I also use VMware and Atheros bits which may break if I have to recompile things.

Is it possible for me to request that this be added to Dapper as a backport?  I have to play quake3 without sound and it's driving me crazy... ](*,)

---

### Post by ajack on 2006-06-05
An update:  I have requested that this version (1.0.11) of alsa be added into dapper.  My request was posted here at URL:

[https://launchpad.net/distros/ubuntu/+ticket/1000](https://launchpad.net/distros/ubuntu/+ticket/1000)

Waiting... :-\"

---

### Post by pinballkid on 2006-06-05
I think a lot of us would like to see 1.0.11 in dapper

---

### Post by pinballkid on 2006-06-05
I've tried this an unfortunately it doesn't work for me. lshw shows this card:

82801G (ICH7 Family) High Definition Audio Controller

I might give it a try with alsa cvs and see how that goes.

---

### Post by ktulu1115 on 2006-06-05
I have the same problem, with pretty much identical symptoms.

lspci & device manager show it, volume control says no gstreamer plugin, no sound card in sound preferences, etc...

Couldn't seem to find alsaconf, so I havn't tried that but pretty much everything else.  I'm about to download ALSA and try that next...

I started a thread about this here - [http://ubuntuforums.org/showthread.php?t=189565](http://ubuntuforums.org/showthread.php?t=189565)

---

### Post by chubuntu on 2006-06-05
Ajack, I play a lot of Enemy Territory (Q3 engine), and have to run this script at start-up for sound to work in game.

! /bin/sh
if [ -x /usr/local/games/enemy-territory/et.x86 ]; then
    echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
fi

exit 0

---

### Post by pinballkid on 2006-06-07
[QUOTE=chubuntu]
! /bin/sh
if [ -x /usr/local/games/enemy-territory/et.x86 ]; then
    echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
fi

exit 0[/QUOTE]

What does this script do?

---

### Post by ajack on 2006-06-11
[QUOTE=chubuntu]Ajack, I play a lot of Enemy Territory (Q3 engine), and have to run this script at start-up for sound to work in game.

! /bin/sh
if [ -x /usr/local/games/enemy-territory/et.x86 ]; then
    echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
fi

exit 0[/QUOTE]

What does "fi" do and what should the script be for quake3 and doom3?

---

### Post by systemgod on 2006-06-11
> 
Quote:
Originally Posted by chubuntu
Ajack, I play a lot of Enemy Territory (Q3 engine), and have to run this script at start-up for sound to work in game.

! /bin/sh
if [ -x /usr/local/games/enemy-territory/et.x86 ]; then
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
fi

exit 0

What does "fi" do and what should the script be for quake3 and doom3?

Actualy "fi" doesn't do much, it's just the end of "if" :-)

```
if  <condition>;
 then
    <commands>;
fi
```

---

### Post by dan4444 on 2006-06-11
I ran all commands chubuntu posted in the initial post of this thread, and it seemed to work like a charm, no errors, including alsaconf recognizing my sound card (a type of hda-intel).

When I rebooted, the volume control was added to my top system tray, but I got an error when clicking on it. And sure enough, when I went to System - Preferences - Sound, there was nothing listed under "Default sound cards:". However, both lspci and device manager show my card just fine.

What is going on here? Anyone have a reccomendation on what I should try next?

FYI: My card is a Realtek alc880

---

### Post by dan4444 on 2006-06-12
I found my solution! - see thread at [http://www.ubuntuforums.org/showthread.php?t=195434](http://www.ubuntuforums.org/showthread.php?t=195434)

---

### Post by dan4444 on 2006-06-12
Thanks again chubuntu, for your original post in this thread. That, together with upgrading to the latest kernal version 2.6.16, gave me my solution - see the thread at [http://www.ubuntuforums.org/showthread.php?t=195434](http://www.ubuntuforums.org/showthread.php?t=195434)

---

### Post by pkunal on 2006-06-14
Ok I am a newbie and started fresh with Ubuntu.-Dapper.

I updated my kernel to latest SMP version since I have a dual core processor.

I have Alsa 1.0.10 from the Ubuntu Dapper installation.

I have Intel Motherboard D945GTPLR with Intel High definition Audio and ICH7.  Sound works good thru speakers from Back Panel but **from the Front Panel (connected to Front Panel Audio Connector on-board), only the input mic is working. Headphones are not working.** Rest assured the Hardware is working I did a battery test to see if the headphone connection is good in the case. 

[Problem no. 2, which may be minor is Flash-plugin does not play audio shows video. I have read posts on this and it seems that "sudo apt-get alsa-oss" will fix it.]

OK will ALSA 1.0.11 installation fix it? I saw lot of Headphone fixes in the latest release documentation. The front panel audio connector is HDA but pin layout is same as AC'97, I verified by the Battery Test of the cable connector.

Intel recommended Asla 1.0.8a, but I assume ALSA is building from previous versions so the later version will be better. Please let me know.

Thanks,
pkunal

---

### Post by granada on 2006-06-15
[QUOTE=chubuntu]dist-upgraded my Sony Vaio VGN-S380P to dapper from breezy last night.  Soundcard was not detecting properly... some weird stuff.

With lspci and in Device Manager it showed up fine:
Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
but in System > Preferences > Sound, under default sound card, there was nothing.  alsamixer basically complained to the effect of no sound card.  Same stuff others have mentioned, like clicking on volume control, I got no sound card configured and some Gstreamer error.

I tried running alsaconf, it ran through everything just fine, reboot, but same thing, no sound card.

So I ended up downloading the 1.011 alsa driver, library, utilities, and oss from [http://www.alsa-project.org](http://www.alsa-project.org), basically:
  479  cd /home/jim/downloads/alsa-dapper-1.0.11/
  480  tar -xjvf alsa-driver-1.0.11.tar.bz2 
  481  tar -xjvf alsa-lib-1.0.11.tar.bz2 
  482  tar -xjvf alsa-oss-1.0.11.tar.bz2 
  483  tar -xjvf alsa-utils-1.0.11.tar.bz2 
  484  cd alsa-driver-1.0.11
  485  ./configure --with-oss=yes --with-cards=hda-intel
  486  make
  487  make install
  488  cd ../alsa-lib-1.0.11
  489  ./configure
  490  make install
  491  cd ../alsa-oss-1.0.11
  492  ./configure
  493  make install
  494  cd ../alsa-utils-1.0.11
  495  ./configure
  496  make install
  497  alsaconf
  498  shutdown -r now
  
And everything worked next boot.[/QUOTE]


I'm tried following this, and yes I'm extremely new to linux in general so forgive me if I'm being silly, but when I try to compile i get and error saying:

 "checking for kernal version... The file /usr/src/linux/include/linux/version.h does not exist"

what am I missing here?  I looked in the directory and there is no linux folder in /usr/src/, in fact there are no folders there.  could this be because I did not download the above files to that directory?  That's the only thing I can think of.  Thanks for the help guys.

---

### Post by mofodojodino on 2006-06-15
Hi Guys,

I went been through every post to do with sound not working and nothing has worked for me so far.

I then checked which groups I belonged to and found that I wasn't in the audio group anymore. I added myself back to it and logged out and in again and viola I have sound again.

The only reason I can think of why this occurred is that one of the packages in dapper is resetting the audio group in the /etc/group file, but that is just speculation on my part.

I hope this helps others out as this has been a problem for me for about a month ever since I upgraded to dapper.

Cheers

---

### Post by ViperAFK on 2006-06-15
I'm sorry, but im very new to linux and have absolutley no clue how to install the ALSA stuff

---

### Post by ViperAFK on 2006-06-15
[QUOTE=ViperAFK]I'm sorry, but im very new to linux and have absolutley no clue how to install the ALSA stuff[/QUOTE]
EDIT , and to above poster, how to you see if your in the audio group?

---

### Post by mofodojodino on 2006-06-16
> how to you see if your in the audio group?

Try this: 

```
cat /etc/group |grep audio
```

if your user name is one of the users at the end of this output then you are in the audio group. It should look something similar to this.

```
audio:x:29:dino
```

where my username is dino.

you can edit this file directly using

```
sudo gedit /etc/group
```

add your username to the end of the audio line and save. Then you will have to logout and in again to reset your audio system so that it works.

Cheers

---

### Post by thewanabee on 2006-06-23
I have a tower that I pieced together from scratch housing a MSI RSI482M-IL mobo with the onboard realtek alc655 and an AMD sempron 3100cpu. Prior to coming across your post I was getting the basic system sounds and when I went through system > prefrences > sound it was showing me my onboard sound card just fine, but for  some reason I couldnt get audio playback in amarok or kaffeine or apps like that. I did everything you said you did in your post and when I rebooted, I discovered that I had lost sound EVERYWHERE :(  and when I went to check the sound prefrences It was showing me nothing at all.

Basically I seem to have ended up right where you started. Any ideas?

> dist-upgraded my Sony Vaio VGN-S380P to dapper from breezy last night. Soundcard was not detecting properly... some weird stuff.

With lspci and in Device Manager it showed up fine:
Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
but in System > Preferences > Sound, under default sound card, there was nothing. alsamixer basically complained to the effect of no sound card. Same stuff others have mentioned, like clicking on volume control, I got no sound card configured and some Gstreamer error.

I tried running alsaconf, it ran through everything just fine, reboot, but same thing, no sound card.

So I ended up downloading the 1.011 alsa driver, library, utilities, and oss from [http://www.alsa-project.org](http://www.alsa-project.org), basically:
479 cd /home/jim/downloads/alsa-dapper-1.0.11/
480 tar -xjvf alsa-driver-1.0.11.tar.bz2
481 tar -xjvf alsa-lib-1.0.11.tar.bz2
482 tar -xjvf alsa-oss-1.0.11.tar.bz2
483 tar -xjvf alsa-utils-1.0.11.tar.bz2
484 cd alsa-driver-1.0.11
485 ./configure --with-oss=yes --with-cards=hda-intel
486 make
487 make install
488 cd ../alsa-lib-1.0.11
489 ./configure
490 make install
491 cd ../alsa-oss-1.0.11
492 ./configure
493 make install
494 cd ../alsa-utils-1.0.11
495 ./configure
496 make install
497 alsaconf
498 shutdown -r now

And everything worked next boot.

---

### Post by vevak on 2006-06-25
Hi,

I have recently installed Ubuntu 6.06 on my Dell 1300 Inspiron. Everything worked well except ipw2200 bg wireless card and problem detecting mic when inserted in mic jack. I just solved the ipw2200 bg problem with a nice howto guide given in this forum in Hoary 5.04 customization tips and tricks sectio.  Only thing left is detction of mic  so you guys have any tips or tricks up your sleeves please mention it. 

I am a complete newbie to linux therefore would need to know the solution in simple way. Thats a request.

---

### Post by jwickard on 2006-06-26
[QUOTE=granada]I'm tried following this, and yes I'm extremely new to linux in general so forgive me if I'm being silly, but when I try to compile i get and error saying:

 "checking for kernal version... The file /usr/src/linux/include/linux/version.h does not exist"

what am I missing here?  I looked in the directory and there is no linux folder in /usr/src/, in fact there are no folders there.  could this be because I did not download the above files to that directory?  That's the only thing I can think of.  Thanks for the help guys.[/QUOTE]

you need to make sure you have the linux kernel headers that match the kernel you are running installed, so that the drivers can compile against them.

So you should get a kernel version with:  uname -r
then it would be somethng like:  sudo apt-get install linux-headers-<version-from-uname>

for mine the package name was: linux-headers-2.6.15-25-386

---

### Post by jwickard on 2006-06-26
I'm having a similar problem with Intel-HDA alsa drivers.  My sound card is visible on the mixer, but inspite of that fact I cannot get any sound.  The system sees it correctly, nothing appears to be muted (through the mixer view).  But I cannot get the sound to work.  I've tried toggling back and forth between selecting the OSS and ALSA devices (same card) as suggested in another thread, but that doesn't seem to have helped at all.  I tried installing the 1.0.11 drivers but that didn't seem to help either.  When I was compiling the package I saw a reference that the sound was super low by default or something similar, how do you check / adjust that?  I'm not sure if that is what my problem would be.

---

### Post by pinballkid on 2006-06-27
[QUOTE=jwickard]how do you check / adjust that?  I'm not sure if that is what my problem would be.[/QUOTE]

alsamixer should let you change the various volumes.

For the record, I have the same card and I'm still having the same problems :P

---

### Post by wobster on 2006-06-28
I can confirm this problem for an Acer Travelmate 3020 series. hda-intel (ich-7). Soundcard was detected fine from the start. No errors but also no output. 
ALSA 1.0.11 drivers did not work out either. 

Hope this get fixed anytime soon. This is a brand new machine (3022wtmi) and now I have to run xp just for the music *sigh*

---

