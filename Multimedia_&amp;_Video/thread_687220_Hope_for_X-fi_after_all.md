---
title: "Hope for X-fi after all"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by KhaaL on 2008-02-04
I just saw that the most recent release of OSS (v4.0 build 1013) has beta support for X-Fi cards. 

Looks like the FOSS is going to beat creative in supporting their own products, again :p I just hope that ALSA and PulseAudio will pick this up and also support the god-forsaken X-Fis.
[CENTER] _**_________________________**_ [/CENTER]

If you get no sound from *firefox*, there's a workaround on [post #8]("http://ubuntuforums.org/showpost.php?p=4268433&postcount=8")

---

### Post by ninjkiran on 2008-02-04
could anyone compile it and install it? see if it works?

---

### Post by KhaaL on 2008-02-04
there's a .deb for 32 and 64 bit kernels [here]("http://www.opensound.com/download.cgi").

---

### Post by ninjkiran on 2008-02-04
It works!!!!!!!!

I am running the X-Fi prelude, which uses the Creative X-Fi CA20K audio processor thus it should work for anyone with an x-fi card with that chip on it!

Only one problem which after a little research seems to be an OSS specific problem but might also be a driver issue is the fact that I get no sound under firefox what so ever.

---

### Post by KhaaL on 2008-02-04
Oh, i think i recognise that problem, what you need to do is:

> 	sudo apt-get install alsa-oss
After that, you need to edit  */etc//firefoxrc* with a root or super user. once there, change: **FIREFOX_DSP="none"** to: **FIREFOX_DSP="aoss"**
Do the same for /etc/mozilla-firefox/mozilla

Make sure to take backups in case of anything going haywire.

---

### Post by RomeReactor on 2008-02-04
Hi. Thanks for the news!

---

### Post by ninjkiran on 2008-02-04
> **KhaaL said:**
> Oh, i think i recognise that problem, what you need to do is:


After that, you need to edit  */etc//firefoxrc* with a root or super user. once there, change: **FIREFOX_DSP="none"** to: **FIREFOX_DSP="aoss"**
Do the same for /etc/mozilla-firefox/mozilla

Make sure to take backups in case of anything going haywire.

Unfortunately I tried that earlier last night after a quick search, but I think that trick only works for people having trouble with Alsa drivers since if I force it in the terminal (aoss Firefox) it complains that no alsa card found and the such.

I been looking for an OSS trick but there seems to be none~  It only effects flash as the very least so it is ok for now.  Atleast sound is working in all my other applications.

Thanks for the info though!  I'll come back if I find a fix that will work with these though~

---

### Post by ninjkiran on 2008-02-04
Just a quick postback,

First off if you set Mozilla Firefox to use alsa-oss (aoss), do a sudo apt-get remove alsa-oss (unless you still need it for something, but since these are OSS drivers you wont get the benefits you want in firefox).  Then remove the line you modified setting it back to none

**The following step works on both x86 and x64**
[COLOR="Red"]_**Step 1**_[/COLOR]
[http://www.4front-tech.com/forum/viewtopic.php?t=2461](http://www.4front-tech.com/forum/viewtopic.php?t=2461)
Download the file in the second thread ( libflashsupport.so )

*Alternatively you can manually compile a version for yourself, but the download does work just fine.  If you still prefer to compile on your own directories will be difference then what I have labeled.*

[COLOR="Red"]**_Step 2_**[/COLOR]
Using a root terminal or the sudo command, copy libflashsupport.so to /usr/lib

**The following step works for x86 but there are special instructions for x64**
[COLOR="Red"]**_Step 3_**[/COLOR]
```
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
```
or
```
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins
```

Depending on your browser I would guess, I did both for good measure.

That information was received from [http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60) **if you would like to read how he did it or get it to work on a 64bit OS.**

Anyway, have fun peoples! Now your sound should work in all of your applications.

---

### Post by KhaaL on 2008-02-04
excellent, nice going by finding that workaround! will update the first post with a link to it and update it with more common problems as they are reported / solved :)

---

### Post by ninjkiran on 2008-02-04
Yea, might as well bump this up to centralize discussion of the driver~

Might be a good idea to change the title if possible to OSS X-fi beta drivers and discussion.

---

### Post by Sciophobia on 2008-02-04
Guess I'll try here...

I installed the OSS deb and osstest plays sound as does MPlayer.  However in the sound settings only the onboard sound shows up.  Whats the trick to getting the X-Fi to show up there so system sounds and such will be played through the X-Fi?

---

### Post by ninjkiran on 2008-02-05
System>Prefferences>Sound

Change from Alsa to OSS~ That might fix your problem.  Otherwise disable onboard sound.

---

### Post by Sciophobia on 2008-02-05
> **ninjkiran said:**
> System>Prefferences>Sound

Change from Alsa to OSS~ That might fix your problem.  Otherwise disable onboard sound.

I selected OSS, but it still only shows the AC'97 mixer.  I'll go back to disabling onboard and see what happens.

Edit so I did, and now theres no devices listed at all in the system menu.  ossinfo and ossxmixer still show it however.

```
Version info: OSS 4.0 (b1013/200802012055) (0x00040003) 
Platform: Linux/i686 2.6.24-5-generic #1 SMP Thu Jan 24 19:45:21 UTC 2008 (adam-desktop)

Number of audio devices:	2
Number of audio engines:	10
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: sbxfi0 Sound Blaster X-Fi (SB046x/067x/076x) interrupts=18332 (18332)
    PCI device 1102:0005, subdevice 1102:0023
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support


Mixer devices
 0: Sound Blaster X-Fi (SB046x/067x/ (Mixer 0 of device object 1)

Audio devices
Sound Blaster X-Fi (SB046x/067x/076x) output  /dev/oss/sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi (SB046x/067x/076x) input  /dev/oss/sbxfi0/pcmin0  (device index 1)

```

---

### Post by fallenfantasyx on 2008-02-05
I wish i had as much success with this driver, i was getting the dreaded "Failed to disable conflicting sound drivers
Reboot and try running soundon again" error, reboot reveals no sound, only time i do get sound on either device is when i run osstest...


Version info: OSS 4.0 (b1013/200802012055) (0x00040003)
Platform: Linux/i686 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 (WindowsSucks)

Number of audio devices: 11
Number of audio engines: 27
Number of mixer devices: 2


Device objects
0: osscore0 OSS core services
1: hdaudio0 Intel HD Audio interrupts=79348 (227359)
HD Audio controller Intel HD Audio
Vendor ID 0x8086284b
Subvendor ID 0x147b1082
Codec 0: ALC888 (0x10ec0888/0x147b0000)
2: sbxfi0 Sound Blaster X-Fi (SB073x) interrupts=226939 (226939)
PCI device 1102:0005, subdevice 1102:0031
3: ossusb0 USB audio core services
4: vmix0 OSS transparent virtual support


Mixer devices
0: High Definition Audio ALC888 (Mixer 0 of device object 1)
1: Sound Blaster X-Fi (SB073x) (Mixer 0 of device object 2)

Audio devices
High Definition Audio front /dev/oss/hdaudio0/pcm0 (device index 0)
High Definition Audio rear /dev/oss/hdaudio0/pcm1 (device index 1)
High Definition Audio center/LFE /dev/oss/hdaudio0/pcm2 (device index 2)
High Definition Audio side /dev/oss/hdaudio0/pcm3 (device index 3)
High Definition Audio pcm4 /dev/oss/hdaudio0/pcm4 (device index 4)
High Definition Audio spdif-out /dev/oss/hdaudio0/spdout0 (device index 5)
High Definition Audio rec1 /dev/oss/hdaudio0/pcmin0 (device index 6)
High Definition Audio rec2 /dev/oss/hdaudio0/pcmin1 (device index 7)
High Definition Audio spdif-in /dev/oss/hdaudio0/spdin0 (device index
Sound Blaster X-Fi (SB073x) output /dev/oss/sbxfi0/pcm0 (device index 9)
Sound Blaster X-Fi (SB073x) input /dev/oss/sbxfi0/pcmin0 (device index 10)

---

### Post by Sciophobia on 2008-02-05
> **fallenfantasyx said:**
> I wish i had as much success with this driver, i was getting the dreaded "Failed to disable conflicting sound drivers
Reboot and try running soundon again" error, reboot reveals no sound, only time i do get sound on either device is when i run osstest...

Thats the same issue I have, try using something like mplayer and settings the audio output to device 2 like it shows in ossinfo.  That should let you play sound from there, but no system sounds.

---

### Post by ninjkiran on 2008-02-06
Just a quick question, did you install the other drivers seperate to ubuntu installation? and if you did I would suggest you remove any packages related to the other sound driver(wether they be proprietary, alsa or old OSS drivers).  even if they came preloaded I would suggest you remove the packages anyway, just write down what you removed just in case, also remove the new x-fi oss drivers and do a clean installation after youve removed everything else.

This should no be detrimental to your system and can always be reinstalled as I said so it is worth a try if you want to use your x-fi.  It is the best solution I can give you with my limited knowledge of linux.

---

### Post by End3r on 2008-02-09
I am having the same issue that Sciophobia described.  Any help would be most appreciated!

---

### Post by Cadmus on 2008-02-09
Wow! Thanks for this find, how are people finding it? I noticed in ryhthmbox sound was a little distorted, but in VLC everything is smooth. I'm using the X-FI Gamer (can't remember exact model, it's the half-height one) on a pretty fresh install of Gusty, my onboard is not avilable sadly as it broke a while back.

Anyone got success in making sound manager see it?

---

### Post by terry_gardener on 2008-02-19
cant get the driver to install. 

ij tried to install it but didn't have the build essential package installed and it failed and said to install build essential so i did and tried installing it again and it keeps giving errors. i tried the howto at: [http://www.ubuntu-unleashed.com/2007/10/get-better-sound-in-ubuntu-with-brand.html](http://www.ubuntu-unleashed.com/2007/10/get-better-sound-in-ubuntu-with-brand.html)

the text from the terminal below: 
terry@terry-desktop:~$ sudo dpkg -i oss-linux_v4.0-1013_i386.deb(Reading database ... 91068 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1013 (using oss-linux_v4.0-1013_i386.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux_v4.0-1013_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux_v4.0-1013_i386.deb

does anyone have any ideas PLEASE 

Thanks

---

### Post by terry_gardener on 2008-02-19
ij have got working, 

i reinstalled ubuntu and then installed all the updates and made sure to install build essential beforte starting the installation and then when i rebooted there was no sound, tried the osstest and there was sound under the x-fi section of it. 

rebooted the pc and disabled onboard sound in bios and now sound works in all apps.

---

### Post by pierre.s.rosen on 2008-02-23
I followed the forum instructions [here]("http://ubuntuforums.org/showpost.php?p=3768914&postcount=60") to install the OSS sound drivers.  I had to reboot the computer twice before oss started with no errors, but I still couldn't hear anything...so I rebooted again and double checked to make sure that my motherboard HD sound was off (it was set to default), and upon reboot, sound worked.

However, when Ubuntu loads I don't hear any sound...I thought I'd at least get some bongos or some sorta start up music...

I was able to watch about half of a YouTube video before my system became sluggish, and then unresponsive.  Had to turn off the computers power to reboot.  I imagine that OSS and Flash don't play so nicely....

Otherwise, sound is working fine.

---

### Post by nicepants on 2008-02-23
i've just installed using instructions from the link from the previous post, and sound is working with my x-fi on xubuntu 7.10 x64. i do have one problem, though: whenever sound starts to play, i get a loud crackle/pop. mplayer gives me this at the start of a video and any time i try to skip around, but just letting it play after the initial crackle results in everything working fine. vlc does the same, though no crackles when i skip around, only when the video starts playing.

if i run it though esd, i don't get any sound crackling, but it does introduce audio lag into videos. also, if i'm already playing a video and open a new one, the new one doesn't skip upon open or seek, and both videos play audio fine.

anyone have any ideas on solving this?

---

### Post by mikebailey on 2008-03-02
i get the same issue as nicepants. from what i have figured out on my own computer is that it doesn't actually link the sounds to the pcm sliders in ossxmix until the music or video starts to play. i was playing around with pulseaudio once, and it made 2 of the pcm sliders in ossxmix to be active with pulseaudio on bootup, and then i didn't have the pop at the beginning of the song or video. its like the soundcard doesn't become active until sound is put through it. because i notice my soundcard makes the same pop over the speakers when it becomes active in the devil windows bootup. whatever i did with pulseaudio was what did it for me. that was the only workaround i found for it. now to reproduce what i did before. i think someone just needs to force a program to use the soundcard on startup so that its always active and ready to go

---

### Post by WoosterB on 2008-04-10
I got the sound in my X-Fi to work using the driver at the start of the post.  However, the sound/video on sites like youtube are out of sync with one another by at least a second.  I'm testing it today to see if my computer videos will do the same.  Anyone else have this issue?

-W

---

### Post by KhaaL on 2008-04-18
There's quite good news for the owners of the X-Fi cards! [See the article at phoronix]("http://www.phoronix.com/scan.php?page=article&item=creative_take_2&num=1").

---

