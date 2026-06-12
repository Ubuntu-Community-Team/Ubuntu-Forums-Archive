---
title: "Sound conflict between Firefox Flash and the rest of the system."
date: 2009-12-30
forum: Multimedia Software
---

### Post by Aikimox on 2009-12-30
Hi, 
I have a strange sound problem in Ubuntu Karmic:
Whenever I open Firefox and play audio/video (eg. youtube) it works but the sound is gone from the rest of the system, can't play any music/movies with sound in any program (Rythmbox, MPlayer,VLC,Gxine, games etc) until I kill Firefox, then everything is fine again. Seems like alsa is controlled 100% by Firefox' flash plugin. If I remove the plugin, the sound in the system works but I need the plugin to display flash contents properly on various sites.
I tried installing the latest version (10) with 64-bit support but nothing changed.

Would really appreciate some help here as I have nowhere else to turn.:confused:
Thanks in advance,
Aikimox

---

### Post by l-x-l on 2009-12-31
I have the same issue. As a work around what I've done is get as many other apps as possible to use ALSA instead of PulseAudio. Unfortunately in 9.10 I don't think there's a way to get the browsers themselves to use ALSA.

Why Ubuntu removed the ability in the mixer to use ALSA is beyond me. PulseAudio has been nothing but trouble for me.

---

### Post by Aikimox on 2009-12-31
So if I remove pulseaudio and install esound instead, - will it solve the problem?

---

### Post by VertexPusher on 2009-12-31
Make sure that flashplugin-nonfree-extrasound is NOT installed. That package contains a library "libflashsupport.so" which makes Flash use OSS instead of ALSA. OSS does not support shared sound card access, so this may be the cause of your problem.

---

### Post by positron82 on 2010-01-14
The same issue here! 

flashplugin-nonfree-extrasound is NOT installed on my system.

I am using 
```
File name:  libflashplayer.so Shockwave Flash 10.0 r42
``````
Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
```

Karmic 32bit.

Any help appricieted!;)

---

### Post by Yellow Pasque on 2010-01-14
OSS4 might be an option: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by positron82 on 2010-01-14
Unfortunately it didn't work..:(

After following the procedure uninstalling ALSA and installing OSS4 only the left channel of my front speakers works(from 5.1)  on VLC. Flash plugin plays just noise..:(

I think i will revert to ALSA again..

---

### Post by jintachi on 2010-01-28
So what's next?
I've tried about every solution on a half dozen threads to fix this problem.
If I start firefox first I get no sound from any other application.
If I start another sound app first (e.g. rhythmbox) I can use sound on all apps except firefox.
Sounds like a firefox problem to me. Is there no solution out there?

---

### Post by jintachi on 2010-01-28
Could this bug be the cause of this sorrow?

[https://bugzilla.mozilla.org/show_bug.cgi?id=536996](https://bugzilla.mozilla.org/show_bug.cgi?id=536996)

---

### Post by sleepee on 2010-02-07
> **jintachi said:**
> So what's next?
I've tried about every solution on a half dozen threads to fix this problem.
If I start firefox first I get no sound from any other application.
If I start another sound app first (e.g. rhythmbox) I can use sound on all apps except firefox.
Sounds like a firefox problem to me. Is there no solution out there?

i have the exact same problem.
but it happened to me right after i upgraded alsa to version 1.0.22.1.
but i had also upgraded flash at the same time.. so i'm not sure which one is to blame here..

but l-x-l's workaround works for me.  if i make vlc use alsa, it'll play sound even with a flash video in firefox.

---

### Post by sleepee on 2010-02-07
> **VertexPusher said:**
> Make sure that flashplugin-nonfree-extrasound is NOT installed. That package contains a library "libflashsupport.so" which makes Flash use OSS instead of ALSA. OSS does not support shared sound card access, so this may be the cause of your problem.

so, is there a way to make flash use alsa to see if that resolves the conflict??

---

### Post by jintachi on 2010-02-10
> **sleepee said:**
> i have the exact same problem.
but it happened to me right after i upgraded alsa to version 1.0.22.1.
but i had also upgraded flash at the same time.. so i'm not sure which one is to blame here..

but l-x-l's workaround works for me.  if i make vlc use alsa, it'll play sound even with a flash video in firefox.


I've found a fix. Details follow:

1. I purged my system of pulseaudio and alsa
sudo apt-get remove --purge alsabase 
sudo apt-get remove --purge pulseaudio

(There may be a hyphen in alsabase i.e. alsa-base I don't remember)

2. Next I did a fresh install of alsa FROM SOURCE NOT THE REPOSITORY.
I used the latest version (1.0.22 at the time of this writing). You'll  need to download the compressed files into /usr/src/alsa. To do this open up a terminal:

cd /usr/src/alsa

if the folder doesn't exist:

cd /usr/src
sudo mkdir alsa
cd alsa

You can always find the latest version of alsa here: 

[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

Assuming the latest version is 1.0.22 then use the following commands to download drivers, libs, utils, and tools.

sudo wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2)
sudo wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.22.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.22.tar.bz2)
sudo wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.22.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.22.tar.bz2)
sudo wget [ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.22.tar.bz2](ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.22.tar.bz2)

3. Next unpackage the files. This is how I prefer to do it:

gksudo nautilus /usr/src/alsa

When the new window opens right click on each file and click on 'Extract here'

4. Now install everything:

 cd alsa-driver-1.0.22.1
sudo ./configure
sudo make
sudo make install

Now cd into each of the other folders and do the same thing:
sudo ./configure
sudo make
sudo make install


5. Then run alsaconf to configure your sound card:

sudo alsaconf

It will detect your sound card. Follow the on screen instructions.

6. Now we need to adjust /etc/modules.conf:

gksudo gedit /etc/modules.conf

Edit the file to remove the 'snd_' prefix from all module names (theres a script in the alsa-driver source package under 'utils' called 'module-options' which does this for you I just couldn't get it to work)

7. Reboot

8. Finally, initialize your sound card:

sudo alsactl init

Everything should be working at this point. You should be able to run sound on Firefox, rhythmbox, and any other program simultaneously. Make sure to change the sound settings on your other apps (virtualbox, skype, etc) to use 'Default Device' or 'ALSA Driver'

9. So that your sound card is initialized upon boot-up you can go to:

System->Preferences->Startup Applications

Click on Add, give any name or comment you want, but the command should read:

alsactl init


10. Enjoy!

Notice pulseaudio is no longer on your system. I haven't tried to reinstall it because ALSA comes with its own mixer which works perfectly fine. You can add alsamixergui to your panels to have quick access to volume control.

---

### Post by sleepee on 2010-02-10
wow.. that seems like somewhat of a long process..
i know i'm definitely going to need some time to do all that..

anyway, i'm scared of taking out pulse audio though.. i wish there was a way to just make flash use pulseaudio or just not hog the sound for itself.  there's got to be a way... i hope..

---

### Post by jintachi on 2010-02-11
You're right it does look like quite a bit of work, but in essence its quite simple:
you uninstall your old version of alsa and replace it with the latest version available and then you configure your sound card.

But if you've found a work around I wouldn't bother.

Also, I think there's a common misconception that pulseaudio is an integral part of the system but it's really not.

---

### Post by sleepee on 2010-02-11
> **jintachi said:**
> You're right it does look like quite a bit of work, but in essence its quite simple:
you uninstall your old version of alsa and replace it with the latest version available and then you configure your sound card.

But if you've found a work around I wouldn't bother.

Also, I think there's a common misconception that pulseaudio is an integral part of the system but it's really not.

hmm..  i guess i could give it a shot and let you all know if it works for me.
but i've already upgraded alsa v1.0.22.1
so i could just remove pulseaudio and should get the same result right?

---

### Post by kokonobs on 2010-02-26
I have flash10 now and had the same problem. 

I uninstalled libflashsupport and it all works now. Wine also works and i can now play several things at the same time. Not sure what else i've broken as a result.

---

### Post by sleepee on 2010-03-01
hey all, i found out how to fix this.. at least this worked for me.
check out my thread

[http://ubuntuforums.org/showthread.php?t=1412153](http://ubuntuforums.org/showthread.php?t=1412153)

it basically forces Flash use PA..  Flash was basically hogging all the sound for itsellf, bypassing PulseAudio..and if another program was already using PA for sound, Flash would be stubborn and not play any sound at all... it was like all or nothing for flash

but instead of taking out PA altogether, or using OSS, i made Flash play nice with PulseAudio and now everything works fine..

---

