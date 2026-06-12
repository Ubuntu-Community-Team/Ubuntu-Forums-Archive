---
title: "Hardy 8.04 &amp; OSS4 (Alternative to ALSA)"
date: 2008-05-03
forum: Multimedia Software
---

### Post by Yellow Pasque on 2008-05-03
Now that Ubuntu 8.04 is out and all the old info is archived, I figured it was time for a new thread on OSS4.

Link to the OpenSound System project forum: [http://www.4front-tech.com/forum/index.php](http://www.4front-tech.com/forum/index.php)
I encourage you to register an account there and use their Linux forum if your issue is more pertinent to OSS itself and not installing/using it on Ubuntu. This ensures that users of other Linux distros will have a chance to benefit from or give feedback on your issue, and ensures that we keep non-Ubuntu issues off of these forums, which are already loaded with unresolved issues.

I will be updating this thread with new information and announcements, so remember to subscribe to it.

---

### Post by Yellow Pasque on 2008-05-03
The OSS4 Install Guide has moved to: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by Mr. Sunshine on 2008-05-03
Excuse my ignorance, but what is the advantage of using OSS4 instead of ALSA? I was under the impression that OSS is outdated and ALSA should be used.

Is it for older hardware? Or is the sound quality better than ALSA?

---

### Post by Yellow Pasque on 2008-05-03
> I was under the impression that OSS is outdated and ALSA should be used.
This is a common misconception. Please read Hannu's blog post "OSS is Dead. Long Live OSS!" here: [http://4front-tech.com/hannublog/?p=5](http://4front-tech.com/hannublog/?p=5)

---

### Post by Mr. Sunshine on 2008-05-03
That was enlightning. There are two forks of OSS: a GPL one which is outdated and this one, which is binary only. 

However, that is unimportant.

**What I really want to know is: will OSS4 give better sound with than ALSA?** I have a HD Audio chipset.

---

### Post by Yellow Pasque on 2008-05-03
The blog is about a year old. Since that time, I believe all of OSS is now GPL'd except for some non-Linux stuff (BSD, Solaris & other Unix OS's) and a select few modules whose vendors still have NDA's with 4front.

> What I really want to know is: will OSS4 give better sound with than ALSA?
It did on my sound card (M-Audio Revolution). If your sound works properly, I would not recommend that you switch at this time. But I do think you'll like the upcoming release of OSS 4.1. If you decide to switch, I would recommend using the Mercurial repo version rather than a .deb package because the HD Audio modules have had a lot of work put into them for the new build.

---

### Post by pickboy87 on 2008-05-04
Ok, so I've followed your guide and I'm still having trouble getting sound to work properly. It shows up correctly with ossinfo -v (I have M-Audio Revolution 5.1) and after I installed the package from a failsafe terminal I tried out osstest and it worked for every one of my audio devices (HDA Intel [onboard sound], M-Audio Revolution and my USB audio device), but once I logged in to Ubuntu, it doesn't play audio.

What I have tried is going to the sound options under System -> Preferences -> Sound and changed them all to OSS (I get sound out of both speakers with "test", but the right speaker crackles sometimes [it's only done this in linux with OSS and at medium-high volume]. Every other application I don't get any sound. Any advice?

My guess is it's something similar to Windows where I just need to select M-Audio as my default audio device, but I just can't seem to figure out how.

OS is Hardy Heron 8.04 AMD 64 bit. Any information you need, I'll give to ya!

Thanks for the help,
Nathan.

---

### Post by pickboy87 on 2008-05-04
Double Post...

---

### Post by Yellow Pasque on 2008-05-04
Nathan, are you using your onboard sound for any purpose? If not, it would be best to disable it in the BIOS.

You should also remove the virtual mixer (vmix) because the M-Audio Revolution does mixing with hardware :)

So:
```
sudo soundoff
cd /usr/lib/oss/etc
gksudo gedit installed_drivers
```
(Remove all lines except the M-Audio Revo)
```
sudo soundon
```

---

### Post by pickboy87 on 2008-05-04
Awesome, I'll give it a try once I get home. And yeah, I was thinking the same thing about disabling the onboard sound in the BIOS. I used to use it in windows specifically for the mic, and my M-Audio for music but I really don't have any need for it now.

I really appreciate the help and you taking your time out to help answer my question. I'll edit this post once I try it, and if that still doesn't work, I'll PM you.

Edit: Alright, well I've disabled my onboard sound, and tried what you've said. As far as I can tell, the crackling is gone in the right speaker [I think it was the mixer causing the problem]. Tried osstest again and it gives me sound and it works properly, but I still have some minor issues (I don't think I have login sounds still - haven't rebooted though...). I figured out about Amarok giving me trouble (had been messing around with it and accidently selected some DSP for source [or something...], changed it back and it works again]. I still have trouble with flash audio, but I haven't followed the guide as far as that goes. I'll update this post later if I a) run into more troubles and b) so that I can explain further to people that may have run into similar problems.

Thanks once again for your help, its much appreciated.

Edit 2: Ugh, ran into a whole slew of errors now after reboot. Now I don't get any sound (it says it won't start OSS due to errors). I'm gonna just reformat and install Ubuntu again and start fresh. I've disabled the onboard and am gonna see if ALSA works (but I plan on using OSS again). Windows crapped out on me too for no apparent reason (said it was missing some file ndl something or other) - didn't even mess with Windows and it just decided not to work...God I love linux so much more :-D


This is what I get when I try this:

```
nathan@linux-desktop:~$ sudo soundon
[sudo] password for nathan: 
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue

```

---

### Post by AndyJS on 2008-05-04
> **pickboy87 said:**
> Awesome, I'll give it a try once I get home. And yeah, I was thinking the same thing about disabling the onboard sound in the BIOS. I used to use it in windows specifically for the mic, and my M-Audio for music but I really don't have any need for it now.

I really appreciate the help and you taking your time out to help answer my question. I'll edit this post once I try it, and if that still doesn't work, I'll PM you.

Edit: Alright, well I've disabled my onboard sound, and tried what you've said. As far as I can tell, the crackling is gone in the right speaker [I think it was the mixer causing the problem]. Tried osstest again and it gives me sound and it works properly, but I still have some minor issues (I don't think I have login sounds still - haven't rebooted though...). I figured out about Amarok giving me trouble (had been messing around with it and accidently selected some DSP for source [or something...], changed it back and it works again]. I still have trouble with flash audio, but I haven't followed the guide as far as that goes. I'll update this post later if I a) run into more troubles and b) so that I can explain further to people that may have run into similar problems.

Thanks once again for your help, its much appreciated.

Edit 2: Ugh, ran into a whole slew of errors now after reboot. Now I don't get any sound (it says it won't start OSS due to errors). I'm gonna just reformat and install Ubuntu again and start fresh. I've disabled the onboard and am gonna see if ALSA works (but I plan on using OSS again). Windows crapped out on me too for no apparent reason (said it was missing some file ndl something or other) - didn't even mess with Windows and it just decided not to work...God I love linux so much more :-D


This is what I get when I try this:

```
nathan@linux-desktop:~$ sudo soundon
[sudo] password for nathan: 
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue

```

Hate to say this but it sounds to me like you may have hard disk problems if your Windows install wont boot and your linux install is now complaining about missing files and directories :(

---

### Post by pickboy87 on 2008-05-05
> **AndyJS said:**
> Hate to say this but it sounds to me like you may have hard disk problems if your Windows install wont boot and your linux install is now complaining about missing files and directories :(

I might, but I really don't think so. I researched the missing file a while back (it happened to me and my friend - just once each) and it seems to be a common but uncommon problem. I never really did find an answer for why it happens and no one really knew why either...

As for the missing files in Linux...while, I was dinking around with the sound, but all I did was exactly what Temujin said.


As of right now, I've reinstalled Linux, followed the guide again (wasn't getting sound out of ALSA) and deleted the vmixer off the list. I have yet to reboot, so I'll let you know what happens then shortly. osstest works, and removing the vmixer did help with the crackle. Let's hope no files go missing. Oh, and as far as I can tell, for some reason I'm still not getting sound when I login or logout. I can get sound out of audio devices (still not flash, but then again I haven't messed with it either) and movies.

/fingers crossed it doesn't f--- up again.


Edit: Alright, well I just rebooted and I'm still not getting sound out of the login and logout. I went to go test it under System -> Preferences -> Sound and still got no sound out of it (oh and had to switch all the sound outputs to OSS). I'm not that concerned about it, was just curious why no sound. Just played an mp3 and a movie and did get sound (one in Amarok and one is Totem). Gonna try the flash one in a bit.


Edit 2: Ok, so I've got 2 last problems. One, the sound mixer you suggested by doing ossxmix "works". It shows up correctly, but every time I try to adjust the volume, it shoots it right back to where it was before. So I can't tamper with the volume. The second problem I have is, I'm a little confused still on your flash tutorial. I got to step 2 (my file or directory was not found), but it says to do something to a file...which file and where do I find it?

---

### Post by radamo on 2008-05-05
Please help... Just installed OSS4 and after doing the patch steps on my 64bit Ubuntu I can't load the ossxmix app.  

ossinfo returns the following:
Version info: OSS 4.0 (b1015/200803240317) (0x00040003) 
Platform: Linux/x86_64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 (lintest)

Number of audio devices:	0
Number of audio engines:	0
Number of mixer devices:	0


Device objects
 0: osscore0 OSS core services
 1: ossusb0 USB audio core services
 2: vmix0 OSS transparent virtual mixer


Mixer devices

Audio devices


So not only won't the mixer load it does not see my X-Fi sound card.

How can I fix this?  Thanks for any help.

RA

---

### Post by Yellow Pasque on 2008-05-05
pickboy87, the command to edit the file is:
```
gksudo gedit /usr/lib/oss/lib/flashsupport.c
```
I'm going to add that to the guide. Thanks for the feedback.

radamo, x-fi support is still in the beta phase. My suggestion would be to try the latest build of OSS 4.1 . A guide on that will be coming soon. :)

---

### Post by radamo on 2008-05-06
> **Temüjin said:**
> ...
radamo, x-fi support is still in the beta phase. My suggestion would be to try the latest build of OSS 4.1 . A guide on that will be coming soon. :)

Okay, I understand that x-fi support is beta.  So I have re-enabled my onboard sound which previously worked in both Alsa and OSS. I have removed OSS and reinstalled Alsa... Cannot get on board to work anymore.  No audio devices seem to get recognized.  appreciate the help. 

RA

---

### Post by eturea on 2008-05-06
I have successfully installed OSSv4, but with an annoying problem. Every time sound starts I hear pops and clicks in one speaker, right speaker. 
I use QuodLibet as player and every time is loading a new song it clicks. Only Amarok can play a playlist without clicks, but if I dare to change the playing song it clicks again.
I have an M-Audio Audiophille 2496, installed on Ubuntu 64bit 8.04 (installed on windows partition with wubi). I don't use vmix.
Today I plan to install from source oss-v4.1-build080423-src-gpl.tar.bz2 and if that doesn't work I'm out of ideas. 
Any suggestions are greatly appreciated!
Thank you

---

### Post by Yellow Pasque on 2008-05-06
Prerequisite Packages:
```
sudo apt-get -y install linux-headers-`uname -r` build-essential gawk libtool binutils libgtk2.0-dev linux-sound-base mercurial libesd0 libssl0.9.8 libssl-dev
```
If you want system sounds:
```
sudo apt-get -y install esound esound-clients esound-common libesd0-dev
```
Obtaining and building OSS4.1 beta
```
cd /usr/src
sudo hg clone http://mercurial.opensound.com/ oss-devel
cd ~/
mkdir oss41build
cd oss41build/
sudo sh /usr/src/oss-devel/configure
sudo make
sudo make install
```

---

### Post by radamo on 2008-05-06
> **Temüjin said:**
> radamo,

Thank you for your patience. Below is the procedure I used to install OSS 4.1 from the mercurial repo. If your system complains about ALSA still running, then I recommend doing this procedure from 'recovery mode'.

```
sudo /etc/init.d/alsa-utils stop
sudo apt-get -y remove alsa-oss oss-compat alsa-base libesd-alsa0

sudo apt-get -y install linux-headers-`uname -r` build-essential gawk libtool libgtk2.0-dev libesd0 wget linux-sound-base gcc-multilib libesd0-dev mercurial libssl0.9.8 libssl-dev
cd /usr/src
sudo hg clone http://mercurial.opensound.com/ oss-devel
cd ~/
mkdir oss41build
cd oss41build/
sudo sh /usr/src/oss-devel/configure
sudo make
sudo make install
```

Are you thinking that I need 4.1 just to get my onboard working or is this to get OSS working with my X-fi.  At this point I am ok getting my on board working again... even with Alsa which worked very well... The only reason I went through all this and now have no sound is to try to take advantage of my sound card.

Thanks,
RA

---

### Post by Yellow Pasque on 2008-05-06
> Are you thinking that I need 4.1 just to get my onboard working or is this to get OSS working with my X-fi.
Both.

---

### Post by radamo on 2008-05-06
> **Temüjin said:**
> Both.

radamo@lintest:/usr/src$ sudo hg clone [http://mercurial.opensound.com/](http://mercurial.opensound.com/) oss-devel
sudo: hg: command not found


I get up to the step above...  Is there a typo in the above?  I have never seen hg as a command?  
Thanks,
RA

---

### Post by radamo on 2008-05-06
> **radamo said:**
> radamo@lintest:/usr/src$ sudo hg clone [http://mercurial.opensound.com/](http://mercurial.opensound.com/) oss-devel
sudo: hg: command not found


I get up to the step above...  Is there a typo in the above?  I have never seen hg as a command?  
Thanks,
RA

Nevermind... I needed to install mercurial...now moving further...
Thanks,
RA

---

### Post by radamo on 2008-05-06
> **Temüjin said:**
> radamo,

Thank you for your patience. Below is the procedure I used to install OSS 4.1 from the mercurial repo. If your system complains about ALSA still running, then I recommend doing this procedure from 'recovery mode'.

```
sudo /etc/init.d/alsa-utils stop
sudo apt-get -y remove alsa-oss oss-compat alsa-base libesd-alsa0

sudo apt-get -y install linux-headers-`uname -r` build-essential gawk libtool libgtk2.0-dev libesd0 wget linux-sound-base gcc-multilib libesd0-dev mercurial libssl0.9.8 libssl-dev
cd /usr/src
sudo hg clone http://mercurial.opensound.com/ oss-devel
cd ~/
mkdir oss41build
cd oss41build/
sudo sh /usr/src/oss-devel/configure
sudo make
sudo make install
```

Completed all of the above and got "no mixers in the system"

Tried to run ossxmix -

Get back:  No mixers are availble

Is this better or worse?

ossinfo still returns no audio devices...
Version info: OSS 4.1 (b 080423/200805061338) (0x00040090) 
Platform: Linux/x86_64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 (lintest)

Number of audio devices:	0
Number of audio engines:	0
Number of MIDI devices:		0
Number of mixer devices:	0


Device objects
 0: osscore0 OSS core services
 1: ossusb0 USB audio core services
 2: vmix0 OSS transparent virtual mixer

MIDI devices (/dev/midi*)

Mixer devices

Audio devices

---

### Post by Yellow Pasque on 2008-05-06
Please run:
```
sudo ossdetect -v
```
What output does it give?

---

### Post by radamo on 2008-05-06
> **Temüjin said:**
> Please run:
```
sudo ossdetect -v
```
What output does it give?

Detected Intel High Definition Audio (P35)
Detected Generic USB audio/MIDI device (BETA)
Detected OSS Transparent Virtual Mixing Architecture

Thanks,
RA

---

### Post by Yellow Pasque on 2008-05-06
radamo,
Your HD audio should work now. If it does not, please make a thread on the OSS forum (I saw you made an account there).

---

### Post by radamo on 2008-05-06
> **Temüjin said:**
> radamo,
Your HD audio should work now. If it does not, please make a thread on the OSS forum (I saw you made an account there).

Will do... from the Sound applet I get the following if I press Test:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

---

### Post by terminator14 on 2008-05-06
@Temüjin

I'm a linux noob like I'm sure a lot of us reading you post are and I'd just like to say THANKS A LOT :)... I have been trying to get my X-Fi to work on Linux for probably over a year, waiting for new drivers from creative to come out, and trying stuff people have written about, trying and waiting. Following your guide, I was able to set up my X-Fi on Ubuntu 8.04 in minutes. I can't thank you enough.

BTW, the only thing I don't have working is my media keyboard won't increase/decrease the sound and that sort of thing. You mention that here:

> **Temüjin said:**
> 
**ADDENDUM: Volume Control Patch** The current gstreamer-based volume control in GNOME is incompatible with OSSv4, meaning your mouse wheel and media buttons won't work. To remedy the issue, try Clive Wright's [patch](http://4front-tech.com/forum/viewtopic.php?t=2357&highlight=). I've also built and attached an AMD64 version to this post. Note that this patch was updated on 1/8/08, so if you tried it before then and it didn't work, try again.
Also, if you'd prefer to map commands to your shortcut keys, [here are some scripts to use](http://wiki.archlinux.org/index.php/OSS) (at the bottom of the page).


It seems that [http://www.4front-tech.com](http://www.4front-tech.com) is down right now and I can't get Clive Wright's Patch. Can anyone point out a mirror for this? I would find it myself but I have no idea what the file name of the patch is...

---

### Post by Yellow Pasque on 2008-05-06
> **terminator14 said:**
> Following your guide, I was able to set up my X-Fi on Ubuntu 8.04 in minutes. I can't thank you enough.
Awesome! If you'd like to thank me, please edit your post and remove the huge quote :P (I expect this thread to get rather long as it is)

> It seems that [http://www.4front-tech.com](http://www.4front-tech.com) is down right now and I can't get Clive Wright's Patch.
The forum works fine for me at the time of this post. Just to make sure, I've added the 32-bit version to the original post.

---

### Post by seawright on 2008-05-06
[http://homepage.ntlworld.com/clive_wright/download/gstreamer-ossv4.tar.gz](http://homepage.ntlworld.com/clive_wright/download/gstreamer-ossv4.tar.gz)
contains patch and 32 bit version of libgstossaudio.so

regards,
Clive

---

### Post by terminator14 on 2008-05-06
> **Temüjin said:**
> Awesome! If you'd like to thank me, please edit your post and remove the huge quote :P (I except this thread to get rather long as it is)

Got it. Thanks again for the How To.

> **seawright said:**
> [http://homepage.ntlworld.com/clive_wright/download/gstreamer-ossv4.tar.gz](http://homepage.ntlworld.com/clive_wright/download/gstreamer-ossv4.tar.gz)
contains patch and 32 bit version of libgstossaudio.so

regards,
Clive

Worked like a charm. Thanks

---

### Post by eturea on 2008-05-07
I've changed envy24_nfrags setting: no effect!
I've installed oss-v4.1-build080423-src-gpl: no effect!
I'm lost! :(
For now I'll use Amarok (is the only one who can play a playlist - with one click sound on the first song!)

---

### Post by pickboy87 on 2008-05-07
Alright, I've got another small problem for ya Temujin. So everything is working relativly smoothly in terms of sound...the only other problem I've run into is playing multiple sounds at once. For instance, when I'm browsing and listening to music and run into a flash page, the only way I can listen to the flash is when I completely stop playing my music. Do you have a solution oh wise one? :-D

---

### Post by Yellow Pasque on 2008-05-08
> **pickboy87 said:**
> Alright, I've got another small problem for ya Temujin. So everything is working relativly smoothly in terms of sound...the only other problem I've run into is playing multiple sounds at once. For instance, when I'm browsing and listening to music and run into a flash page, the only way I can listen to the flash is when I completely stop playing my music. Do you have a solution oh wise one? :-D
The solution is to use EsounD because the envy24ht driver doesn't seem to play well with multiple sound streams. I know the hardware is capable of playing/mixing multiple sound streams because I used to do it in Windows (and I was using ASIO to bypass Windows' mixer).

Right now, I'm actually working on the same issue myself (i.e. getting EsounD up and running). I'll let you know if I have success :)

---

### Post by xproject on 2008-05-08
After searching the internet for hours, I feel like I am the only person in the world who is trying to install OSS4 in Kubuntu 8.04 KDE4 remix.



I have followed your instructions, OSS installs fine, ossinfo tells me that my X-Fi card is detected, but osstest does not output anything to the speakers. I think the problem is that I cannot fully remove Alsa -- when I apt-get remove alsa-base, it becomes apparent that KDE4 is dependent on alsa-base. Unless I want to get rid of KDE4, I cannot uninstall alsa.

Any suggestions?

---

### Post by Yellow Pasque on 2008-05-08
> Any suggestions?
Write to the Kubuntu devs and tell them you want an OSS4 spin? Sorry, but I don't like KDE/Kubuntu and my attempt to work with Kubuntu 8.04/KDE 3.5.x didn't go so well: [http://ubuntuforums.org/showthread.php?t=747054](http://ubuntuforums.org/showthread.php?t=747054)

Out of curiosity, do you have the linux-sound-base package installed?

---

### Post by xproject on 2008-05-08
> **Temüjin said:**
> Out of curiosity, do you have the linux-sound-base package installed?

Yes it is -- version 1.0.16-0ubuntu4. And thanks for the quick reply.

---

### Post by dlikhten on 2008-05-10
ossdetect -v
> 
Detected Creative SB X-Fi (EARLY BETA)
Detected Intel High Definition Audio (P35)
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture

ossinfo

> Version info: OSS 4.0 (b1015/200803240256) (0x00040003) 
Platform: Linux/i686 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 (dlikhten-desktop)

Number of audio devices:	12
Number of audio engines:	28
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 Intel HD Audio interrupts=34939 (34940)
    HD Audio controller Intel HD Audio
    Vendor ID    0x8086293e
    Subvendor ID 0x1458a002
     Codec  2: ALC885 (0x10ec0885/0x1458a002)
 2: sbxfi0 Sound Blaster X-Fi (SB073x) interrupts=65075 (65075)
    PCI device 1102:0005, subdevice 1102:0031
 3: ossusb0 USB audio core services
 4: vmix0 OSS transparent virtual mixer


Mixer devices
 0: High Definition Audio ALC885 (Mixer 0 of device object 1)
 1: Sound Blaster X-Fi (SB073x) (Mixer 0 of device object 2)

Audio devices
HD Audio front                    /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio rear                     /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio center/LFE               /dev/oss/hdaudio0/pcm2  (device index 2)
HD Audio side                     /dev/oss/hdaudio0/pcm3  (device index 3)
HD Audio pcm4                     /dev/oss/hdaudio0/pcm4  (device index 4)
HD Audio spdif-out                /dev/oss/hdaudio0/spdout0  (device index 5)
High Definition Audio rec         /dev/oss/hdaudio0/pcmin0  (device index 6)
High Definition Audio rec1        /dev/oss/hdaudio0/pcmin1  (device index 7)
High Definition Audio rec2        /dev/oss/hdaudio0/pcmin2  (device index 8)
High Definition Audio spdif-in    /dev/oss/hdaudio0/spdin0  (device index 9)
Sound Blaster X-Fi (SB073x) output  /dev/oss/sbxfi0/pcm0  (device index 10)
Sound Blaster X-Fi (SB073x) input  /dev/oss/sbxfi0/pcmin0  (device index 11)


Using Ubuntu 8.04 (gnome)


I get no sound. I set up the "sound" configuration (though GUI) to use OSS, I still get absolutely no sound.

Is there any configuration needed to enable everything after installation?

---

### Post by Yellow Pasque on 2008-05-10
dlikhten,
> Link to the OpenSound System project forum: [http://www.4front-tech.com/forum/index.php](http://www.4front-tech.com/forum/index.php)
I encourage you to register an account there and use their Linux forum if your issue is more pertinent to OSS itself and not installing it on Ubuntu. This ensures that users of other Linux distros will have a chance to benefit from or give feedback on your issue, and ensures that we keep non-Ubuntu issues off of these forums, which are already loaded with unresolved issues.


---

### Post by dlikhten on 2008-05-10
Alrighty, I will do that, if I have any luck I'll post here what worked for me.

---

### Post by dlikhten on 2008-05-10
> **dlikhten said:**
> Alrighty, I will do that, if I have any luck I'll post here what worked for me.

Ok here we go:

Get this version of OSS4 -- customized to work with XFI

[oss.tar.bz2]("http://www.fileupyours.com/view/77985/oss.tar.bz2")

Then follow these instructions on how to install it.
[Instructions]("http://www.4front-tech.com/wiki/index.php/Building_OSSv4_from_source#Building_the_OSS_sound_system_from_source")

Retrieved from [THIS POST]("http://www.4front-tech.com/forum/viewtopic.php?t=2621")

Running osstest will ensure that your sound card is working. There is, however, an issue: If you have 2 sound cards (onboard + xfi) you need to have Linux use your xfi instead of the onboard. What I wound up doing is disabling my onboard from BIOS (I don't need it anyways), and Ubuntu used XFI as the main (and only) sound card. You can also blacklist your other sound card.

:guitar:

---

### Post by nezach on 2008-05-10
Temüjin - thanks a lot for the info you provided.

I compiled OSS 4.1 from their repo and my X-Fi works great now.

Thanks again.

Paul

---

### Post by Zorael on 2008-05-10
Okay, so, newbie questions incoming.

I'm a user and not a developer, but even so, I'm terribly weak to the FOSS ideal. And not just because I'm a poor student. Having read the "OSS is dead" blog post and random other google hits from subsequent cursory research, I think more highly of OSS now. So I'd like to take the leap and see if it works for me.

[list=1][*]Will this new-and-improved OSS work with any and all programs that already support the old OSS?
[*]What about mixing? Will any app *ever* nick exclusive access?
[*]Can this be installed alongside ALSA or will I have to remove all traces of it? I'm running pulse now, on my Kubuntu 8.04 x86_64 where it isn't included by default, and getting everything to work was an adventure in itself. If, by any chance, my card won't work with OSS4 (though it's listed in the supported devices page; ICH7 HDA), I'd have to embark on the same adventure to get pulse restored, so I'm naturally treading lightly.
[*]What of compatibility plugins/wrappers toward other sound architectures? If I have an app that *really* only wants to output in ALSA, am I screwed?
[*]Does it feature app-specific volume settings?
[*]To what extent are multiple soundcards supported? I can move sources between sinks in pulse, for instance, in realtime. Anything along those lines?[/list]


Well, the best thing that could happen were if pulse had OSS support, I guess. But as far as I know, it's ALSA-only, right?

---

### Post by Yellow Pasque on 2008-05-10
1. Yes
2. OSS uses its own mixer (vmix) and with simple patches, plays nice with the Gnome/Ubuntu volume control. It's also capable of hardware mixing.
3. If "getting everything to work was an adventure in itself", then don't fix something that's not broken. You even pointed out that your motivation to use OSS4 is far more idealistic than practical.
4. [http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4)
5. See 4
6. PulseAudio is a sound server and it works well with ALSA. The Open Sound System has a different purpose. Read more of Hannu's blog if you want to know the technical differences: [http://4front-tech.com/hannublog/](http://4front-tech.com/hannublog/)

---

### Post by flyinraptr on 2008-05-11
Temüjin -
I was looking at the supported devices - didn't appear to be any TV Tuners - is this the case?   Or is there a workaround?  My primary sound is SB Audigy (chip on mobo) - I had pulled my Xfi card out a long time ago as I could never get it to work properly.  My TV Tuner is a DVICO RT Fusion which uses the Conexant cx23888 chip (cx8811_alsa).  After reading about OSS4 - was thinking about throwing my Xfi card back in the system - would it be possible to route the tv audio through the Xfi using OSS?

Thanks -

---

### Post by Yellow Pasque on 2008-05-11
flyinraptr,
I have no idea, as I am not a developer on the project. Please ask on the OSS forum if you are interested (the OSS Developer subforum)

---

### Post by flyinraptr on 2008-05-11
> **Temüjin said:**
> flyinraptr,
I have no idea, as I am not a developer on the project. Please ask on the OSS forum if you are interested (the OSS Developer subforum)

Sorry - my bad.  I'll check out the OSS forum.  Thanks for the info.

---

### Post by Zorael on 2008-05-11
> **Temüjin said:**
> 3. If "getting everything to work was an adventure in itself", then don't fix something that's not broken. You even pointed out that your motivation to use OSS4 is far more idealistic than practical.
Well, of course. Using Linux to begin with was far more idealistic than practical; with a laptop bundled with XP MCE 2005 as well as a free upgrade to Vista Home Premium *and* paid-for support, I'm supposed to be content and happy with Notepad, Internet Explorer, Outlook Express and Frontpage. Only I'm tired to death of applications created to look pretty to give the idea of solid coding, when they in fact hardly work. Not to mention the embrace-extend-extinguish practise, which I find disgusting. Again, opinion, ideology.

I counter your "don't fix something that's not broken" with what'll ever be as close to a motto as I'll ever have: "just because it works doesn't mean it can't be improved."

That said, I'll likely give it a go.

---

### Post by Yellow Pasque on 2008-05-11
> That said, I'll likely give it a go.
Attaboy :) I admire your pioneering spirit. Keep me posted.

---

### Post by Zorael on 2008-05-11
> **Temüjin said:**
> If you decide to switch, I would recommend using the Mercurial repo version rather than a .deb package because the HD Audio modules have had a lot of work put into them for the new build.
Should I use the downloadable (amd64) .deb or this external repo (to which I can't find a link) if I have an Intel HDA chipset?
```
zorael@sunspire:~$ lshw -C multimedia; aplay -l
WARNING: you should run this program as super-user.
  *-multimedia
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by Yellow Pasque on 2008-05-11
Try the OSS 4.0 .deb method first. If jack sensing and/or ossxmix does not work properly, then we'll work with the OSS 4.1 repo.

---

### Post by benmore on 2008-05-11
I managed to get the sound working without the reboot into failsafe.
It was a clean install with all updates and the sound driver installed.
Just needed to use the 'sudo soundon' line and I could hear the sound initialize.

Thanks for the guide.

---

### Post by Yellow Pasque on 2008-05-11
> **benmore said:**
> I managed to get the sound working without the reboot into failsafe.
It was a clean install with all updates and the sound driver installed.
Just needed to use the 'sudo soundon' line and I could hear the sound initialize.

Thanks for the guide.
Awesome. The install process has gotten easier since I wrote the first guide. I wonder if that reboot is necessary for all users nowadays...

> Thanks for the guide.
No problem. :)

---

### Post by Zorael on 2008-05-11
I get this when I connect my Creative SB MP3+ USB device.
```
Bus 002 Device 002: ID 041e:3010 Creative Technology, Ltd SoundBlaster MP3+
```
```
[  675.151791] usb 2-2: new full speed USB device using uhci_hcd and address 2
[  675.367950] usb 2-2: configuration #1 chosen from 1 choice
[  675.371233] New audioctl device 2/0 - Creative Sound Blaster MP3+
[  675.391867] New audio streaming device 2/1 - Creative Sound Blaster MP3+
[  675.391995] New audio streaming device 2/2 - Creative Sound Blaster MP3+
[  675.458691] snd: Unknown symbol unregister_sound_special
[  675.458790] snd: Unknown symbol register_sound_special_device
[  675.459043] snd: Unknown symbol sound_class
[  675.460461] snd_hwdep: Unknown symbol snd_info_register
[  675.460494] snd_hwdep: Unknown symbol snd_info_create_module_entry
[  675.460525] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.460564] snd_hwdep: Unknown symbol snd_info_free_entry
[  675.460600] snd_hwdep: Unknown symbol snd_unregister_oss_device
[  675.460634] snd_hwdep: Unknown symbol snd_verbose_printk
[  675.460665] snd_hwdep: Unknown symbol snd_register_oss_device
[  675.460697] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[  675.460728] snd_hwdep: Unknown symbol snd_card_file_add
[  675.460765] snd_hwdep: Unknown symbol snd_iprintf
[  675.460796] snd_hwdep: Unknown symbol snd_major
[  675.460836] snd_hwdep: Unknown symbol snd_unregister_device
[  675.460869] snd_hwdep: Unknown symbol snd_device_new
[  675.460908] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[  675.460946] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[  675.460979] snd_hwdep: Unknown symbol snd_lookup_minor_data
[  675.461010] snd_hwdep: Unknown symbol snd_ctl_register_ioctl_compat
[  675.461043] snd_hwdep: Unknown symbol snd_card_file_remove
[  675.461073] snd_hwdep: Unknown symbol snd_register_device_for_dev
[  675.466843] snd_seq_device: Unknown symbol snd_info_register
[  675.466876] snd_seq_device: Unknown symbol snd_info_create_module_entry
[  675.466907] snd_seq_device: Unknown symbol snd_info_free_entry
[  675.466939] snd_seq_device: Unknown symbol snd_seq_root
[  675.466973] snd_seq_device: Unknown symbol snd_verbose_printk
[  675.467007] snd_seq_device: Unknown symbol snd_iprintf
[  675.467049] snd_seq_device: Unknown symbol snd_device_new
[  675.479591] snd: Unknown symbol unregister_sound_special
[  675.479690] snd: Unknown symbol register_sound_special_device
[  675.479980] snd: Unknown symbol sound_class
[  675.481656] snd_seq_device: Unknown symbol snd_info_register
[  675.481688] snd_seq_device: Unknown symbol snd_info_create_module_entry
[  675.481719] snd_seq_device: Unknown symbol snd_info_free_entry
[  675.481752] snd_seq_device: Unknown symbol snd_seq_root
[  675.481807] snd_seq_device: Unknown symbol snd_verbose_printk
[  675.481841] snd_seq_device: Unknown symbol snd_iprintf
[  675.481889] snd_seq_device: Unknown symbol snd_device_new
[  675.484374] snd_rawmidi: Unknown symbol snd_info_register
[  675.484407] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.484459] snd_rawmidi: Unknown symbol snd_seq_device_new
[  675.484495] snd_rawmidi: Unknown symbol snd_info_free_entry
[  675.484531] snd_rawmidi: Unknown symbol snd_unregister_oss_device
[  675.484566] snd_rawmidi: Unknown symbol snd_verbose_printk
[  675.484597] snd_rawmidi: Unknown symbol snd_register_oss_device
[  675.484632] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
[  675.484663] snd_rawmidi: Unknown symbol snd_card_file_add
[  675.484701] snd_rawmidi: Unknown symbol snd_iprintf
[  675.484736] snd_rawmidi: Unknown symbol snd_major
[  675.484782] snd_rawmidi: Unknown symbol snd_oss_info_register
[  675.484813] snd_rawmidi: Unknown symbol snd_unregister_device
[  675.484849] snd_rawmidi: Unknown symbol snd_device_new
[  675.484881] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
[  675.484926] snd_rawmidi: Unknown symbol snd_lookup_oss_minor_data
[  675.484962] snd_rawmidi: Unknown symbol snd_lookup_minor_data
[  675.484992] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl_compat
[  675.485026] snd_rawmidi: Unknown symbol snd_info_create_card_entry
[  675.485060] snd_rawmidi: Unknown symbol snd_card_file_remove
[  675.485093] snd_rawmidi: Unknown symbol snd_register_device_for_dev
[  675.485151] snd_rawmidi: Unknown symbol snd_device_register
[  675.489951] snd_usb_lib: Unknown symbol snd_rawmidi_receive
[  675.490009] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_empty
[  675.490041] snd_usb_lib: Unknown symbol snd_rawmidi_transmit
[  675.490085] snd_usb_lib: Unknown symbol snd_verbose_printk
[  675.490142] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_ack
[  675.490207] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_peek
[  675.490269] snd_usb_lib: Unknown symbol snd_rawmidi_new
[  675.490302] snd_usb_lib: Unknown symbol snd_rawmidi_set_ops
[  675.491480] snd_timer: Unknown symbol snd_info_register
[  675.491512] snd_timer: Unknown symbol snd_info_create_module_entry
[  675.491548] snd_timer: Unknown symbol snd_info_free_entry
[  675.491604] snd_timer: Unknown symbol snd_verbose_printk
[  675.491643] snd_timer: Unknown symbol snd_iprintf
[  675.491687] snd_timer: Unknown symbol snd_ecards_limit
[  675.491722] snd_timer: Unknown symbol snd_oss_info_register
[  675.491754] snd_timer: Unknown symbol snd_unregister_device
[  675.491792] snd_timer: Unknown symbol snd_device_new
[  675.491859] snd_timer: Unknown symbol snd_register_device_for_dev
[  675.503235] snd: Unknown symbol unregister_sound_special
[  675.503335] snd: Unknown symbol register_sound_special_device
[  675.503603] snd: Unknown symbol sound_class
[  675.504332] snd: Unknown symbol unregister_sound_special
[  675.504457] snd: Unknown symbol register_sound_special_device
[  675.504808] snd: Unknown symbol sound_class
[  675.505613] snd: Unknown symbol unregister_sound_special
[  675.505709] snd: Unknown symbol register_sound_special_device
[  675.505987] snd: Unknown symbol sound_class
[  675.506698] snd_hwdep: Unknown symbol snd_info_register
[  675.506731] snd_hwdep: Unknown symbol snd_info_create_module_entry
[  675.506763] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.506794] snd_hwdep: Unknown symbol snd_info_free_entry
[  675.506830] snd_hwdep: Unknown symbol snd_unregister_oss_device
[  675.506864] snd_hwdep: Unknown symbol snd_verbose_printk
[  675.506895] snd_hwdep: Unknown symbol snd_register_oss_device
[  675.506927] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[  675.506959] snd_hwdep: Unknown symbol snd_card_file_add
[  675.506996] snd_hwdep: Unknown symbol snd_iprintf
[  675.507026] snd_hwdep: Unknown symbol snd_major
[  675.507067] snd_hwdep: Unknown symbol snd_unregister_device
[  675.507100] snd_hwdep: Unknown symbol snd_device_new
[  675.507139] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[  675.507177] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[  675.507210] snd_hwdep: Unknown symbol snd_lookup_minor_data
[  675.507241] snd_hwdep: Unknown symbol snd_ctl_register_ioctl_compat
[  675.507274] snd_hwdep: Unknown symbol snd_card_file_remove
[  675.507305] snd_hwdep: Unknown symbol snd_register_device_for_dev
[  675.507558] snd_timer: Unknown symbol snd_info_register
[  675.507592] snd_timer: Unknown symbol snd_info_create_module_entry
[  675.507628] snd_timer: Unknown symbol snd_info_free_entry
[  675.507684] snd_timer: Unknown symbol snd_verbose_printk
[  675.507723] snd_timer: Unknown symbol snd_iprintf
[  675.507787] snd_timer: Unknown symbol snd_ecards_limit
[  675.507823] snd_timer: Unknown symbol snd_oss_info_register
[  675.507854] snd_timer: Unknown symbol snd_unregister_device
[  675.507892] snd_timer: Unknown symbol snd_device_new
[  675.507959] snd_timer: Unknown symbol snd_register_device_for_dev
[  675.508641] snd_pcm: Unknown symbol snd_info_register
[  675.508674] snd_pcm: Unknown symbol snd_info_create_module_entry
[  675.508704] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.508764] snd_pcm: Unknown symbol snd_timer_notify
[  675.508802] snd_pcm: Unknown symbol snd_timer_interrupt
[  675.508833] snd_pcm: Unknown symbol snd_info_free_entry
[  675.508865] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[  675.508904] snd_pcm: Unknown symbol snd_info_get_str
[  675.508975] snd_pcm: Unknown symbol snd_verbose_printk
[  675.509038] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[  675.509068] snd_pcm: Unknown symbol snd_card_file_add
[  675.509129] snd_pcm: Unknown symbol snd_iprintf
[  675.509175] snd_pcm: Unknown symbol snd_major
[  675.509245] snd_pcm: Unknown symbol snd_unregister_device
[  675.509281] snd_pcm: Unknown symbol snd_timer_new
[  675.509312] snd_pcm: Unknown symbol snd_device_new
[  675.509367] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[  675.509419] snd_pcm: Unknown symbol snd_lookup_minor_data
[  675.509450] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[  675.509491] snd_pcm: Unknown symbol snd_info_create_card_entry
[  675.509522] snd_pcm: Unknown symbol snd_power_wait
[  675.509557] snd_pcm: Unknown symbol snd_device_free
[  675.509607] snd_pcm: Unknown symbol snd_card_file_remove
[  675.509638] snd_pcm: Unknown symbol snd_register_device_for_dev
[  675.509705] snd_pcm: Unknown symbol snd_device_register
[  675.509738] snd_pcm: Unknown symbol snd_info_get_line
[  675.614498] snd_usb_audio: Unknown symbol snd_ctl_add
[  675.614573] snd_usb_audio: Unknown symbol snd_pcm_new
[  675.614715] snd_usb_audio: Unknown symbol snd_card_register
[  675.614777] snd_usb_audio: Unknown symbol snd_card_free
[  675.614844] snd_usb_audio: Unknown symbol snd_card_proc_new
[  675.614907] snd_usb_audio: Unknown symbol snd_usb_create_midi_interface
[  675.615023] snd_usb_audio: Unknown symbol snd_pcm_stop
[  675.615123] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_minmax
[  675.615198] snd_usb_audio: Unknown symbol snd_pcm_format_physical_width
[  675.615276] snd_usb_audio: Unknown symbol snd_ctl_find_id
[  675.615339] snd_usb_audio: Unknown symbol snd_verbose_printk
[  675.615407] snd_usb_audio: Unknown symbol snd_ctl_new1
[  675.615491] snd_usb_audio: Unknown symbol snd_component_add
[  675.615556] snd_usb_audio: Unknown symbol snd_pcm_hw_rule_add
[  675.615676] snd_usb_audio: Unknown symbol snd_card_new
[  675.615779] snd_usb_audio: Unknown symbol snd_iprintf
[  675.615840] snd_usb_audio: Unknown symbol snd_ctl_boolean_mono_info
[  675.615903] snd_usb_audio: Unknown symbol snd_pcm_lib_ioctl
[  675.615975] snd_usb_audio: Unknown symbol snd_hwdep_new
[  675.616049] snd_usb_audio: Unknown symbol snd_pcm_new_stream
[  675.616229] snd_usb_audio: Unknown symbol snd_card_free_when_closed
[  675.616298] snd_usb_audio: Unknown symbol snd_ctl_notify
[  675.616445] snd_usb_audio: Unknown symbol snd_pcm_set_ops
[  675.616563] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_list
[  675.616675] snd_usb_audio: Unknown symbol snd_device_new
[  675.616742] snd_usb_audio: Unknown symbol snd_pcm_rate_to_rate_bit
[  675.616876] snd_usb_audio: Unknown symbol snd_pcm_suspend_all
[  675.616941] snd_usb_audio: Unknown symbol snd_card_disconnect
[  675.617242] snd_usb_audio: Unknown symbol snd_pcm_period_elapsed
[  675.617332] snd_usb_audio: Unknown symbol snd_usbmidi_disconnect
[  675.618584] snd_hwdep: Unknown symbol snd_info_register
[  675.618650] snd_hwdep: Unknown symbol snd_info_create_module_entry
[  675.618719] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.618781] snd_hwdep: Unknown symbol snd_info_free_entry
[  675.618854] snd_hwdep: Unknown symbol snd_unregister_oss_device
[  675.618924] snd_hwdep: Unknown symbol snd_verbose_printk
[  675.618987] snd_hwdep: Unknown symbol snd_register_oss_device
[  675.619087] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[  675.619151] snd_hwdep: Unknown symbol snd_card_file_add
[  675.619225] snd_hwdep: Unknown symbol snd_iprintf
[  675.619286] snd_hwdep: Unknown symbol snd_major
[  675.619375] snd_hwdep: Unknown symbol snd_unregister_device
[  675.619442] snd_hwdep: Unknown symbol snd_device_new
[  675.619533] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[  675.619610] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[  675.619677] snd_hwdep: Unknown symbol snd_lookup_minor_data
[  675.619774] snd_hwdep: Unknown symbol snd_ctl_register_ioctl_compat
[  675.619839] snd_hwdep: Unknown symbol snd_card_file_remove
[  675.619901] snd_hwdep: Unknown symbol snd_register_device_for_dev
[  675.657554] ossusb: Endpoint control write error -110
[  675.657567] Failed to set 48000 Hz sampling rate
[  675.657574] osscore: Trigger (input) failed
[  675.660692] snd_seq_device: Unknown symbol snd_info_register
[  675.660760] snd_seq_device: Unknown symbol snd_info_create_module_entry
[  675.660823] snd_seq_device: Unknown symbol snd_info_free_entry
[  675.660890] snd_seq_device: Unknown symbol snd_seq_root
[  675.660958] snd_seq_device: Unknown symbol snd_verbose_printk
[  675.661062] snd_seq_device: Unknown symbol snd_iprintf
[  675.661147] snd_seq_device: Unknown symbol snd_device_new
[  675.661966] snd_seq_device: Unknown symbol snd_info_register
[  675.662037] snd_seq_device: Unknown symbol snd_info_create_module_entry
[  675.662101] snd_seq_device: Unknown symbol snd_info_free_entry
[  675.662167] snd_seq_device: Unknown symbol snd_seq_root
[  675.662235] snd_seq_device: Unknown symbol snd_verbose_printk
[  675.662303] snd_seq_device: Unknown symbol snd_iprintf
[  675.662426] snd_seq_device: Unknown symbol snd_device_new
[  675.674491] snd: Unknown symbol unregister_sound_special
[  675.674682] snd: Unknown symbol register_sound_special_device
[  675.675186] snd: Unknown symbol sound_class
[  675.677619] snd: Unknown symbol unregister_sound_special
[  675.677846] snd: Unknown symbol register_sound_special_device
[  675.678393] snd: Unknown symbol sound_class
[  675.683242] snd_seq_device: Unknown symbol snd_info_register
[  675.683314] snd_seq_device: Unknown symbol snd_info_create_module_entry
[  675.683377] snd_seq_device: Unknown symbol snd_info_free_entry
[  675.683463] snd_seq_device: Unknown symbol snd_seq_root
[  675.683531] snd_seq_device: Unknown symbol snd_verbose_printk
[  675.683599] snd_seq_device: Unknown symbol snd_iprintf
[  675.683724] snd_seq_device: Unknown symbol snd_device_new
[  675.684607] snd_rawmidi: Unknown symbol snd_info_register
[  675.684679] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.684742] snd_rawmidi: Unknown symbol snd_seq_device_new
[  675.684813] snd_rawmidi: Unknown symbol snd_info_free_entry
[  675.684886] snd_rawmidi: Unknown symbol snd_unregister_oss_device
[  675.684956] snd_rawmidi: Unknown symbol snd_verbose_printk
[  675.685061] snd_rawmidi: Unknown symbol snd_register_oss_device
[  675.685131] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
[  675.685192] snd_rawmidi: Unknown symbol snd_card_file_add
[  675.685269] snd_rawmidi: Unknown symbol snd_iprintf
[  675.685345] snd_rawmidi: Unknown symbol snd_major
[  675.685428] snd_rawmidi: Unknown symbol snd_oss_info_register
[  675.685490] snd_rawmidi: Unknown symbol snd_unregister_device
[  675.685564] snd_rawmidi: Unknown symbol snd_device_new
[  675.685629] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
[  675.685756] snd_rawmidi: Unknown symbol snd_lookup_oss_minor_data
[  675.685830] snd_rawmidi: Unknown symbol snd_lookup_minor_data
[  675.685891] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl_compat
[  675.685957] snd_rawmidi: Unknown symbol snd_info_create_card_entry
[  675.686032] snd_rawmidi: Unknown symbol snd_card_file_remove
[  675.686098] snd_rawmidi: Unknown symbol snd_register_device_for_dev
[  675.686166] snd_rawmidi: Unknown symbol snd_device_register
[  675.698088] snd_seq_device: Unknown symbol snd_info_register
[  675.698122] snd_seq_device: Unknown symbol snd_info_create_module_entry
[  675.698154] snd_seq_device: Unknown symbol snd_info_free_entry
[  675.698187] snd_seq_device: Unknown symbol snd_seq_root
[  675.698221] snd_seq_device: Unknown symbol snd_verbose_printk
[  675.698255] snd_seq_device: Unknown symbol snd_iprintf
[  675.698298] snd_seq_device: Unknown symbol snd_device_new
[  675.700783] snd_rawmidi: Unknown symbol snd_info_register
[  675.700816] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.700847] snd_rawmidi: Unknown symbol snd_seq_device_new
[  675.700882] snd_rawmidi: Unknown symbol snd_info_free_entry
[  675.700919] snd_rawmidi: Unknown symbol snd_unregister_oss_device
[  675.700954] snd_rawmidi: Unknown symbol snd_verbose_printk
[  675.700985] snd_rawmidi: Unknown symbol snd_register_oss_device
[  675.701020] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
[  675.701051] snd_rawmidi: Unknown symbol snd_card_file_add
[  675.701090] snd_rawmidi: Unknown symbol snd_iprintf
[  675.701124] snd_rawmidi: Unknown symbol snd_major
[  675.701165] snd_rawmidi: Unknown symbol snd_oss_info_register
[  675.701196] snd_rawmidi: Unknown symbol snd_unregister_device
[  675.701232] snd_rawmidi: Unknown symbol snd_device_new
[  675.701265] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
[  675.701310] snd_rawmidi: Unknown symbol snd_lookup_oss_minor_data
[  675.701346] snd_rawmidi: Unknown symbol snd_lookup_minor_data
[  675.701377] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl_compat
[  675.701410] snd_rawmidi: Unknown symbol snd_info_create_card_entry
[  675.701445] snd_rawmidi: Unknown symbol snd_card_file_remove
[  675.701477] snd_rawmidi: Unknown symbol snd_register_device_for_dev
[  675.701510] snd_rawmidi: Unknown symbol snd_device_register
[  675.706844] snd_usb_lib: Unknown symbol snd_rawmidi_receive
[  675.706902] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_empty
[  675.706933] snd_usb_lib: Unknown symbol snd_rawmidi_transmit
[  675.706999] snd_usb_lib: Unknown symbol snd_verbose_printk
[  675.707056] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_ack
[  675.707122] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_peek
[  675.707184] snd_usb_lib: Unknown symbol snd_rawmidi_new
[  675.707216] snd_usb_lib: Unknown symbol snd_rawmidi_set_ops
[  675.707732] snd_timer: Unknown symbol snd_info_register
[  675.707765] snd_timer: Unknown symbol snd_info_create_module_entry
[  675.707801] snd_timer: Unknown symbol snd_info_free_entry
[  675.707857] snd_timer: Unknown symbol snd_verbose_printk
[  675.707896] snd_timer: Unknown symbol snd_iprintf
[  675.707940] snd_timer: Unknown symbol snd_ecards_limit
[  675.707980] snd_timer: Unknown symbol snd_oss_info_register
[  675.708011] snd_timer: Unknown symbol snd_unregister_device
[  675.708048] snd_timer: Unknown symbol snd_device_new
[  675.708115] snd_timer: Unknown symbol snd_register_device_for_dev
[  675.714023] snd_usb_lib: Unknown symbol snd_rawmidi_receive
[  675.714082] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_empty
[  675.714113] snd_usb_lib: Unknown symbol snd_rawmidi_transmit
[  675.714156] snd_usb_lib: Unknown symbol snd_verbose_printk
[  675.714212] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_ack
[  675.714278] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_peek
[  675.714340] snd_usb_lib: Unknown symbol snd_rawmidi_new
[  675.714371] snd_usb_lib: Unknown symbol snd_rawmidi_set_ops
[  675.714821] snd_timer: Unknown symbol snd_info_register
[  675.714853] snd_timer: Unknown symbol snd_info_create_module_entry
[  675.714888] snd_timer: Unknown symbol snd_info_free_entry
[  675.714944] snd_timer: Unknown symbol snd_verbose_printk
[  675.714982] snd_timer: Unknown symbol snd_iprintf
[  675.715027] snd_timer: Unknown symbol snd_ecards_limit
[  675.715062] snd_timer: Unknown symbol snd_oss_info_register
[  675.715092] snd_timer: Unknown symbol snd_unregister_device
[  675.715129] snd_timer: Unknown symbol snd_device_new
[  675.715197] snd_timer: Unknown symbol snd_register_device_for_dev
[  675.715805] snd: Unknown symbol unregister_sound_special
[  675.715900] snd: Unknown symbol register_sound_special_device
[  675.716158] snd: Unknown symbol sound_class
[  675.723555] snd: Unknown symbol unregister_sound_special
[  675.723676] snd: Unknown symbol register_sound_special_device
[  675.723929] snd: Unknown symbol sound_class
[  675.726513] snd_timer: Unknown symbol snd_info_register
[  675.726546] snd_timer: Unknown symbol snd_info_create_module_entry
[  675.726582] snd_timer: Unknown symbol snd_info_free_entry
[  675.726638] snd_timer: Unknown symbol snd_verbose_printk
[  675.726678] snd_timer: Unknown symbol snd_iprintf
[  675.726722] snd_timer: Unknown symbol snd_ecards_limit
[  675.726757] snd_timer: Unknown symbol snd_oss_info_register
[  675.726789] snd_timer: Unknown symbol snd_unregister_device
[  675.726826] snd_timer: Unknown symbol snd_device_new
[  675.726892] snd_timer: Unknown symbol snd_register_device_for_dev
[  675.727418] snd_pcm: Unknown symbol snd_info_register
[  675.727451] snd_pcm: Unknown symbol snd_info_create_module_entry
[  675.727483] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.727537] snd_pcm: Unknown symbol snd_timer_notify
[  675.727576] snd_pcm: Unknown symbol snd_timer_interrupt
[  675.727607] snd_pcm: Unknown symbol snd_info_free_entry
[  675.727638] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[  675.727677] snd_pcm: Unknown symbol snd_info_get_str
[  675.727748] snd_pcm: Unknown symbol snd_verbose_printk
[  675.727811] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[  675.727841] snd_pcm: Unknown symbol snd_card_file_add
[  675.727879] snd_pcm: Unknown symbol snd_iprintf
[  675.727927] snd_pcm: Unknown symbol snd_major
[  675.727990] snd_pcm: Unknown symbol snd_unregister_device
[  675.728025] snd_pcm: Unknown symbol snd_timer_new
[  675.728056] snd_pcm: Unknown symbol snd_device_new
[  675.728112] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[  675.728161] snd_pcm: Unknown symbol snd_lookup_minor_data
[  675.728192] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[  675.728233] snd_pcm: Unknown symbol snd_info_create_card_entry
[  675.728264] snd_pcm: Unknown symbol snd_power_wait
[  675.728298] snd_pcm: Unknown symbol snd_device_free
[  675.728348] snd_pcm: Unknown symbol snd_card_file_remove
[  675.728380] snd_pcm: Unknown symbol snd_register_device_for_dev
[  675.728456] snd_pcm: Unknown symbol snd_device_register
[  675.728489] snd_pcm: Unknown symbol snd_info_get_line
[  675.729281] snd_usb_audio: Unknown symbol snd_ctl_add
[  675.729315] snd_usb_audio: Unknown symbol snd_pcm_new
[  675.729383] snd_usb_audio: Unknown symbol snd_card_register
[  675.729414] snd_usb_audio: Unknown symbol snd_card_free
[  675.729448] snd_usb_audio: Unknown symbol snd_card_proc_new
[  675.729479] snd_usb_audio: Unknown symbol snd_usb_create_midi_interface
[  675.729537] snd_usb_audio: Unknown symbol snd_pcm_stop
[  675.729568] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_minmax
[  675.729606] snd_usb_audio: Unknown symbol snd_pcm_format_physical_width
[  675.729644] snd_usb_audio: Unknown symbol snd_ctl_find_id
[  675.729675] snd_usb_audio: Unknown symbol snd_verbose_printk
[  675.729706] snd_usb_audio: Unknown symbol snd_ctl_new1
[  675.729740] snd_usb_audio: Unknown symbol snd_component_add
[  675.729772] snd_usb_audio: Unknown symbol snd_pcm_hw_rule_add
[  675.729831] snd_usb_audio: Unknown symbol snd_card_new
[  675.729862] snd_usb_audio: Unknown symbol snd_iprintf
[  675.729894] snd_usb_audio: Unknown symbol snd_ctl_boolean_mono_info
[  675.729925] snd_usb_audio: Unknown symbol snd_pcm_lib_ioctl
[  675.729962] snd_usb_audio: Unknown symbol snd_hwdep_new
[  675.729996] snd_usb_audio: Unknown symbol snd_pcm_new_stream
[  675.730086] snd_usb_audio: Unknown symbol snd_card_free_when_closed
[  675.730120] snd_usb_audio: Unknown symbol snd_ctl_notify
[  675.730176] snd_usb_audio: Unknown symbol snd_pcm_set_ops
[  675.730235] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_list
[  675.730291] snd_usb_audio: Unknown symbol snd_device_new
[  675.730322] snd_usb_audio: Unknown symbol snd_pcm_rate_to_rate_bit
[  675.730389] snd_usb_audio: Unknown symbol snd_pcm_suspend_all
[  675.730422] snd_usb_audio: Unknown symbol snd_card_disconnect
[  675.730555] snd_usb_audio: Unknown symbol snd_pcm_period_elapsed
[  675.730599] snd_usb_audio: Unknown symbol snd_usbmidi_disconnect
[  675.748632] snd_timer: Unknown symbol snd_info_register
[  675.748667] snd_timer: Unknown symbol snd_info_create_module_entry
[  675.748703] snd_timer: Unknown symbol snd_info_free_entry
[  675.748760] snd_timer: Unknown symbol snd_verbose_printk
[  675.748798] snd_timer: Unknown symbol snd_iprintf
[  675.748851] snd_timer: Unknown symbol snd_ecards_limit
[  675.748887] snd_timer: Unknown symbol snd_oss_info_register
[  675.748919] snd_timer: Unknown symbol snd_unregister_device
[  675.748977] snd_timer: Unknown symbol snd_device_new
[  675.749045] snd_timer: Unknown symbol snd_register_device_for_dev
[  675.749716] snd_pcm: Unknown symbol snd_info_register
[  675.749750] snd_pcm: Unknown symbol snd_info_create_module_entry
[  675.749782] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.749837] snd_pcm: Unknown symbol snd_timer_notify
[  675.749876] snd_pcm: Unknown symbol snd_timer_interrupt
[  675.749908] snd_pcm: Unknown symbol snd_info_free_entry
[  675.749943] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[  675.749989] snd_pcm: Unknown symbol snd_info_get_str
[  675.750061] snd_pcm: Unknown symbol snd_verbose_printk
[  675.750124] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[  675.750155] snd_pcm: Unknown symbol snd_card_file_add
[  675.750194] snd_pcm: Unknown symbol snd_iprintf
[  675.750241] snd_pcm: Unknown symbol snd_major
[  675.750325] snd_pcm: Unknown symbol snd_unregister_device
[  675.750361] snd_pcm: Unknown symbol snd_timer_new
[  675.750391] snd_pcm: Unknown symbol snd_device_new
[  675.750446] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[  675.750495] snd_pcm: Unknown symbol snd_lookup_minor_data
[  675.750526] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[  675.750568] snd_pcm: Unknown symbol snd_info_create_card_entry
[  675.750600] snd_pcm: Unknown symbol snd_power_wait
[  675.750639] snd_pcm: Unknown symbol snd_device_free
[  675.750688] snd_pcm: Unknown symbol snd_card_file_remove
[  675.750719] snd_pcm: Unknown symbol snd_register_device_for_dev
[  675.750786] snd_pcm: Unknown symbol snd_device_register
[  675.750819] snd_pcm: Unknown symbol snd_info_get_line
[  675.751939] snd_usb_audio: Unknown symbol snd_ctl_add
[  675.751974] snd_usb_audio: Unknown symbol snd_pcm_new
[  675.752043] snd_usb_audio: Unknown symbol snd_card_register
[  675.752074] snd_usb_audio: Unknown symbol snd_card_free
[  675.752108] snd_usb_audio: Unknown symbol snd_card_proc_new
[  675.752139] snd_usb_audio: Unknown symbol snd_usb_create_midi_interface
[  675.752197] snd_usb_audio: Unknown symbol snd_pcm_stop
[  675.752228] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_minmax
[  675.752266] snd_usb_audio: Unknown symbol snd_pcm_format_physical_width
[  675.752323] snd_usb_audio: Unknown symbol snd_ctl_find_id
[  675.752355] snd_usb_audio: Unknown symbol snd_verbose_printk
[  675.752386] snd_usb_audio: Unknown symbol snd_ctl_new1
[  675.752420] snd_usb_audio: Unknown symbol snd_component_add
[  675.752452] snd_usb_audio: Unknown symbol snd_pcm_hw_rule_add
[  675.752512] snd_usb_audio: Unknown symbol snd_card_new
[  675.752543] snd_usb_audio: Unknown symbol snd_iprintf
[  675.752574] snd_usb_audio: Unknown symbol snd_ctl_boolean_mono_info
[  675.752609] snd_usb_audio: Unknown symbol snd_pcm_lib_ioctl
[  675.752645] snd_usb_audio: Unknown symbol snd_hwdep_new
[  675.752684] snd_usb_audio: Unknown symbol snd_pcm_new_stream
[  675.752775] snd_usb_audio: Unknown symbol snd_card_free_when_closed
[  675.752809] snd_usb_audio: Unknown symbol snd_ctl_notify
[  675.752865] snd_usb_audio: Unknown symbol snd_pcm_set_ops
[  675.752924] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_list
[  675.753003] snd_usb_audio: Unknown symbol snd_device_new
[  675.753035] snd_usb_audio: Unknown symbol snd_pcm_rate_to_rate_bit
[  675.753101] snd_usb_audio: Unknown symbol snd_pcm_suspend_all
[  675.753134] snd_usb_audio: Unknown symbol snd_card_disconnect
[  675.753271] snd_usb_audio: Unknown symbol snd_pcm_period_elapsed
[  675.753316] snd_usb_audio: Unknown symbol snd_usbmidi_disconnect
[  675.761736] snd: Unknown symbol unregister_sound_special
[  675.761833] snd: Unknown symbol register_sound_special_device
[  675.762090] snd: Unknown symbol sound_class
[  675.762769] snd_hwdep: Unknown symbol snd_info_register
[  675.762803] snd_hwdep: Unknown symbol snd_info_create_module_entry
[  675.762834] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.762865] snd_hwdep: Unknown symbol snd_info_free_entry
[  675.762902] snd_hwdep: Unknown symbol snd_unregister_oss_device
[  675.762937] snd_hwdep: Unknown symbol snd_verbose_printk
[  675.762987] snd_hwdep: Unknown symbol snd_register_oss_device
[  675.763019] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[  675.763051] snd_hwdep: Unknown symbol snd_card_file_add
[  675.763089] snd_hwdep: Unknown symbol snd_iprintf
[  675.763119] snd_hwdep: Unknown symbol snd_major
[  675.763160] snd_hwdep: Unknown symbol snd_unregister_device
[  675.763194] snd_hwdep: Unknown symbol snd_device_new
[  675.763233] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[  675.763275] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[  675.763308] snd_hwdep: Unknown symbol snd_lookup_minor_data
[  675.763339] snd_hwdep: Unknown symbol snd_ctl_register_ioctl_compat
[  675.763381] snd_hwdep: Unknown symbol snd_card_file_remove
[  675.763412] snd_hwdep: Unknown symbol snd_register_device_for_dev
[  675.764074] snd_seq_device: Unknown symbol snd_info_register
[  675.764106] snd_seq_device: Unknown symbol snd_info_create_module_entry
[  675.764138] snd_seq_device: Unknown symbol snd_info_free_entry
[  675.764172] snd_seq_device: Unknown symbol snd_seq_root
[  675.764205] snd_seq_device: Unknown symbol snd_verbose_printk
[  675.764239] snd_seq_device: Unknown symbol snd_iprintf
[  675.764301] snd_seq_device: Unknown symbol snd_device_new
[  675.773249] snd: Unknown symbol unregister_sound_special
[  675.773345] snd: Unknown symbol register_sound_special_device
[  675.773598] snd: Unknown symbol sound_class
[  675.774161] snd_seq_device: Unknown symbol snd_info_register
[  675.774193] snd_seq_device: Unknown symbol snd_info_create_module_entry
[  675.774224] snd_seq_device: Unknown symbol snd_info_free_entry
[  675.774257] snd_seq_device: Unknown symbol snd_seq_root
[  675.774291] snd_seq_device: Unknown symbol snd_verbose_printk
[  675.774325] snd_seq_device: Unknown symbol snd_iprintf
[  675.774369] snd_seq_device: Unknown symbol snd_device_new
[  675.774767] snd_rawmidi: Unknown symbol snd_info_register
[  675.774800] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.774832] snd_rawmidi: Unknown symbol snd_seq_device_new
[  675.774868] snd_rawmidi: Unknown symbol snd_info_free_entry
[  675.774906] snd_rawmidi: Unknown symbol snd_unregister_oss_device
[  675.774942] snd_rawmidi: Unknown symbol snd_verbose_printk
[  675.774973] snd_rawmidi: Unknown symbol snd_register_oss_device
[  675.775008] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
[  675.775040] snd_rawmidi: Unknown symbol snd_card_file_add
[  675.775079] snd_rawmidi: Unknown symbol snd_iprintf
[  675.775113] snd_rawmidi: Unknown symbol snd_major
[  675.775154] snd_rawmidi: Unknown symbol snd_oss_info_register
[  675.775185] snd_rawmidi: Unknown symbol snd_unregister_device
[  675.775222] snd_rawmidi: Unknown symbol snd_device_new
[  675.775254] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
[  675.775300] snd_rawmidi: Unknown symbol snd_lookup_oss_minor_data
[  675.775336] snd_rawmidi: Unknown symbol snd_lookup_minor_data
[  675.775367] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl_compat
[  675.775400] snd_rawmidi: Unknown symbol snd_info_create_card_entry
[  675.775435] snd_rawmidi: Unknown symbol snd_card_file_remove
[  675.775467] snd_rawmidi: Unknown symbol snd_register_device_for_dev
[  675.775501] snd_rawmidi: Unknown symbol snd_device_register
[  675.776275] snd_usb_lib: Unknown symbol snd_rawmidi_receive
[  675.776331] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_empty
[  675.776372] snd_usb_lib: Unknown symbol snd_rawmidi_transmit
[  675.776415] snd_usb_lib: Unknown symbol snd_verbose_printk
[  675.776471] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_ack
[  675.776537] snd_usb_lib: Unknown symbol snd_rawmidi_transmit_peek
[  675.776598] snd_usb_lib: Unknown symbol snd_rawmidi_new
[  675.776631] snd_usb_lib: Unknown symbol snd_rawmidi_set_ops
[  675.777177] snd_timer: Unknown symbol snd_info_register
[  675.777210] snd_timer: Unknown symbol snd_info_create_module_entry
[  675.777246] snd_timer: Unknown symbol snd_info_free_entry
[  675.777302] snd_timer: Unknown symbol snd_verbose_printk
[  675.777340] snd_timer: Unknown symbol snd_iprintf
[  675.777384] snd_timer: Unknown symbol snd_ecards_limit
[  675.777419] snd_timer: Unknown symbol snd_oss_info_register
[  675.777450] snd_timer: Unknown symbol snd_unregister_device
[  675.777487] snd_timer: Unknown symbol snd_device_new
[  675.777553] snd_timer: Unknown symbol snd_register_device_for_dev
[  675.784616] snd: Unknown symbol unregister_sound_special
[  675.784712] snd: Unknown symbol register_sound_special_device
[  675.784988] snd: Unknown symbol sound_class
[  675.790196] snd_timer: Unknown symbol snd_info_register
[  675.790229] snd_timer: Unknown symbol snd_info_create_module_entry
[  675.790265] snd_timer: Unknown symbol snd_info_free_entry
[  675.790321] snd_timer: Unknown symbol snd_verbose_printk
[  675.790360] snd_timer: Unknown symbol snd_iprintf
[  675.790404] snd_timer: Unknown symbol snd_ecards_limit
[  675.790439] snd_timer: Unknown symbol snd_oss_info_register
[  675.790471] snd_timer: Unknown symbol snd_unregister_device
[  675.790508] snd_timer: Unknown symbol snd_device_new
[  675.790575] snd_timer: Unknown symbol snd_register_device_for_dev
[  675.791101] snd_pcm: Unknown symbol snd_info_register
[  675.791133] snd_pcm: Unknown symbol snd_info_create_module_entry
[  675.791165] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
[  675.791220] snd_pcm: Unknown symbol snd_timer_notify
[  675.791259] snd_pcm: Unknown symbol snd_timer_interrupt
[  675.791290] snd_pcm: Unknown symbol snd_info_free_entry
[  675.791321] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[  675.791360] snd_pcm: Unknown symbol snd_info_get_str
[  675.791432] snd_pcm: Unknown symbol snd_verbose_printk
[  675.791495] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[  675.791527] snd_pcm: Unknown symbol snd_card_file_add
[  675.791565] snd_pcm: Unknown symbol snd_iprintf
[  675.791612] snd_pcm: Unknown symbol snd_major
[  675.791676] snd_pcm: Unknown symbol snd_unregister_device
[  675.791711] snd_pcm: Unknown symbol snd_timer_new
[  675.791743] snd_pcm: Unknown symbol snd_device_new
[  675.791798] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[  675.791846] snd_pcm: Unknown symbol snd_lookup_minor_data
[  675.791878] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[  675.791920] snd_pcm: Unknown symbol snd_info_create_card_entry
[  675.791952] snd_pcm: Unknown symbol snd_power_wait
[  675.791987] snd_pcm: Unknown symbol snd_device_free
[  675.792037] snd_pcm: Unknown symbol snd_card_file_remove
[  675.792068] snd_pcm: Unknown symbol snd_register_device_for_dev
[  675.792136] snd_pcm: Unknown symbol snd_device_register
[  675.792169] snd_pcm: Unknown symbol snd_info_get_line
[  675.792953] snd_usb_audio: Unknown symbol snd_ctl_add
[  675.792988] snd_usb_audio: Unknown symbol snd_pcm_new
[  675.793056] snd_usb_audio: Unknown symbol snd_card_register
[  675.793088] snd_usb_audio: Unknown symbol snd_card_free
[  675.793121] snd_usb_audio: Unknown symbol snd_card_proc_new
[  675.793153] snd_usb_audio: Unknown symbol snd_usb_create_midi_interface
[  675.793211] snd_usb_audio: Unknown symbol snd_pcm_stop
[  675.793242] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_minmax
[  675.793280] snd_usb_audio: Unknown symbol snd_pcm_format_physical_width
[  675.793319] snd_usb_audio: Unknown symbol snd_ctl_find_id
[  675.793351] snd_usb_audio: Unknown symbol snd_verbose_printk
[  675.793382] snd_usb_audio: Unknown symbol snd_ctl_new1
[  675.793415] snd_usb_audio: Unknown symbol snd_component_add
[  675.793448] snd_usb_audio: Unknown symbol snd_pcm_hw_rule_add
[  675.793508] snd_usb_audio: Unknown symbol snd_card_new
[  675.793539] snd_usb_audio: Unknown symbol snd_iprintf
[  675.793570] snd_usb_audio: Unknown symbol snd_ctl_boolean_mono_info
[  675.793601] snd_usb_audio: Unknown symbol snd_pcm_lib_ioctl
[  675.793637] snd_usb_audio: Unknown symbol snd_hwdep_new
[  675.793670] snd_usb_audio: Unknown symbol snd_pcm_new_stream
[  675.793760] snd_usb_audio: Unknown symbol snd_card_free_when_closed
[  675.793795] snd_usb_audio: Unknown symbol snd_ctl_notify
[  675.793852] snd_usb_audio: Unknown symbol snd_pcm_set_ops
[  675.793911] snd_usb_audio: Unknown symbol snd_pcm_hw_constraint_list
[  675.793967] snd_usb_audio: Unknown symbol snd_device_new
[  675.793998] snd_usb_audio: Unknown symbol snd_pcm_rate_to_rate_bit
[  675.794065] snd_usb_audio: Unknown symbol snd_pcm_suspend_all
[  675.794098] snd_usb_audio: Unknown symbol snd_card_disconnect
[  675.794231] snd_usb_audio: Unknown symbol snd_pcm_period_elapsed
[  675.794275] snd_usb_audio: Unknown symbol snd_usbmidi_disconnect
[  675.908428] ossusb: Endpoint control write error -110
[  675.908438] Failed to set 48000 Hz sampling rate
[  675.908442] osscore: Trigger failed
```
...which, uh, doesn't seem promising.

How can I try to output a test sound to that device? Better yet, is there an easy way to change which device an application outputs to? Amarok (xine), for instance, has three options; auto, /dev/dsp and /dev/sound/dsp, which makes me suspect I need to look elsewhere.

And while I'm asking stupid questions, you mentioned and linked towards a Gnome volume mixer patch; is there a similar one for KDE's kmix? I'd use pulse's but it doesn't seem to want to play nice with OSS. The volume up/down keys also call kmix.

edit: It works with my integrated sound, forgot to mention that.

---

### Post by Yellow Pasque on 2008-05-11
Ok, we'll either have to uninstall ALSA or blacklist the modules, because they're interfering. Please run:
```
lsmod | grep snd
```

> you mentioned and linked towards a Gnome volume mixer patch; is there a similar one for KDE's kmix?
I tried to build the kde-multimedia package from source, but it didn't turn out so well. See: [http://ubuntuforums.org/showthread.php?t=747054](http://ubuntuforums.org/showthread.php?t=747054)

> I'd use pulse's but it doesn't seem to want to play nice with OSS
The OSS and PulseAudio developers are trying to collaborate right now. [http://4front-tech.com/forum/viewtopic.php?t=2507&highlight=pulseaudio](http://4front-tech.com/forum/viewtopic.php?t=2507&highlight=pulseaudio)

---

### Post by Zorael on 2008-05-11
```
zorael@sunspire:~$ lsmod | grep snd
zorael@sunspire:~$
```

I discovered ossinfo and osstest *n*, and as such verified that the USB device works.
```
zorael@sunspire:~$ ossinfo
Version info: OSS 4.0 (b1015/200803240317) (0x00040003)
Platform: Linux/x86_64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 (sunspire)

Number of audio devices:        12
Number of audio engines:        28
Number of mixer devices:        2


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 Intel HD Audio interrupts=1109 (1110)
    HD Audio controller Intel HD Audio
    Vendor ID    0x808627d8
    Subvendor ID 0x1025006c
     Codec  0: ALC883 (0x10ec0883/0x1025162d)
     Codec  1: Conexant2bfa (0x14f12bfa)
 2: ossusb0 USB audio core services
 3: usb041e3010-0 Creative Sound Blaster MP3+
 4: usb041e3010-1 Creative Sound Blaster MP3+
 5: usb041e3010-2 Creative Sound Blaster MP3+
 6: vmix0 OSS transparent virtual mixer


Mixer devices
 0: High Definition Audio ALC883 (Mixer 0 of device object 1)
 1: Creative Sound Blaster MP3+ (Mixer 0 of device object 3)

Audio devices
HD Audio front                    /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio rear                     /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio center/LFE               /dev/oss/hdaudio0/pcm2  (device index 2)
HD Audio side                     /dev/oss/hdaudio0/pcm3  (device index 3)
HD Audio pcm4                     /dev/oss/hdaudio0/pcm4  (device index 4)
HD Audio modem-out                /dev/oss/hdaudio0/pcm5  (device index 5)
HD Audio spdif-out                /dev/oss/hdaudio0/spdout0  (device index 6)
High Definition Audio rec1        /dev/oss/hdaudio0/pcmin0  (device index 7)
High Definition Audio rec2        /dev/oss/hdaudio0/pcmin1  (device index 8)
High Definition Audio modem-in    /dev/oss/hdaudio0/pcmin2  (device index 9)
**Creative Sound Blaster MP3+ play  /dev/oss/usb041e3010-1/pcm0  (device index 10)**
Creative Sound Blaster MP3+ rec   /dev/oss/usb041e3010-2/pcmin0  (device index 11)

zorael@sunspire:~$ osstest **10**
Sound subsystem and version: OSS 4.0 (b1015/200803240317) (0x00040003)
Platform: Linux/x86_64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/usb041e3010-1/pcm0 (audio engine 10): Creative Sound Blaster MP3+ play
- Performing audio playback test...
  <left> OK <right> OK <stereo> OK <measured srate 47958.00 Hz (-0.09%)>

*** All tests completed OK ***
```
It doesn't seem to support hotplugging though; I have to do soundoff and soundon again to get OSS to load its drivers.
```
zorael@sunspire:~$ ls /dev/oss
hdaudio0  usb041e3010-0  usb041e3010-1  usb041e3010-2

*<disconnection and reconnection of the device>*

zorael@sunspire:~$ ossinfo
Version info: OSS 4.0 (b1015/200803240317) (0x00040003)
Platform: Linux/x86_64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 (sunspire)

Number of audio devices:        14
Number of audio engines:        38
Number of mixer devices:        3


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 Intel HD Audio interrupts=1109 (1110)
    HD Audio controller Intel HD Audio
    Vendor ID    0x808627d8
    Subvendor ID 0x1025006c
     Codec  0: ALC883 (0x10ec0883/0x1025162d)
     Codec  1: Conexant2bfa (0x14f12bfa)
 2: ossusb0 USB audio core services
 3: usb041e3010-0 Creative Sound Blaster MP3+
 4: usb041e3010-1 Creative Sound Blaster MP3+
 5: usb041e3010-2 Creative Sound Blaster MP3+
 6: vmix0 OSS transparent virtual mixer
 7: usb041e3010-3 Creative Sound Blaster MP3+
 8: usb041e3010-4 Creative Sound Blaster MP3+
 9: usb041e3010-5 Creative Sound Blaster MP3+


Mixer devices
 0: High Definition Audio ALC883 (Mixer 0 of device object 1)
 1: (Creative Sound Blaster MP3+ )(Mixer 0 of device object 3)
 2: Creative Sound Blaster MP3+ (Mixer 0 of device object 7)

Audio devices
HD Audio front                    /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio rear                     /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio center/LFE               /dev/oss/hdaudio0/pcm2  (device index 2)
HD Audio side                     /dev/oss/hdaudio0/pcm3  (device index 3)
HD Audio pcm4                     /dev/oss/hdaudio0/pcm4  (device index 4)
HD Audio modem-out                /dev/oss/hdaudio0/pcm5  (device index 5)
HD Audio spdif-out                /dev/oss/hdaudio0/spdout0  (device index 6)
High Definition Audio rec1        /dev/oss/hdaudio0/pcmin0  (device index 7)
High Definition Audio rec2        /dev/oss/hdaudio0/pcmin1  (device index 8)
High Definition Audio modem-in    /dev/oss/hdaudio0/pcmin2  (device index 9)
(Creative Sound Blaster MP3+ play  /dev/oss/usb041e3010-1/pcm0 ) (device index 10)
(Creative Sound Blaster MP3+ rec   /dev/oss/usb041e3010-2/pcmin0 ) (device index 11)
**Creative Sound Blaster MP3+ play  /dev/oss/usb041e3010-4/pcm0  (device index 12)**
Creative Sound Blaster MP3+ rec   /dev/oss/usb041e3010-5/pcmin0  (device index 13)

zorael@sunspire:~$ osstest **12**
Sound subsystem and version: OSS 4.0 (b1015/200803240317) (0x00040003)
Platform: Linux/x86_64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/usb041e3010-4/pcm0 (audio engine 28): Creative Sound Blaster MP3+ play
- Performing audio playback test... **/dev/oss/usb041e3010-4/pcm0**: No such file or directory
The device file is missing from /dev.
Perhaps you have not installed and started Open Sound System yet
Can't open the device

*** Some errors were detected during the tests ***

zorael@sunspire:~$ ls /dev/oss
hdaudio0  usb041e3010-0  usb041e3010-1  usb041e3010-2

zorael@sunspire:~$ osstest **10**
Sound subsystem and version: OSS 4.0 (b1015/200803240317) (0x00040003)
Platform: Linux/x86_64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/usb041e3010-1/pcm0 (audio engine 10): Creative Sound Blaster MP3+ play
- Device not present - Skipping

*** All tests completed OK ***
```

---

### Post by Zorael on 2008-05-11
[FONT="Courier New"]sudo ossdetect -d[/FONT] rediscovers the usb device, though requires sudo, which is unfortunate. [FONT="Courier New"]ossxmix[/FONT] is broken since it was first disconnected.
```
zorael@sunspire:~$ ossxmix
SNDCTL_MIX_NREXT: No such device or address
```

Think an upgrade to that 4.1 version would fix this, or should I just take it to the OSS forums?

---

### Post by Yellow Pasque on 2008-05-11
You have an interesting hardware setup, so I think we should take it the OSS4 forums and work with the experts and developers there, even if we try and install OSS 4.1.

---

### Post by nezach on 2008-05-11
In order to use OSS with games like Sauerbraten you need to install package:

libsdl1.2debian-oss and remove libsdl1.2debian-alsa.

---

### Post by flyinraptr on 2008-05-11
Problems trying to install -

Initially received error messages towards the end of the install - complaining about cx88_alsa still in use.  I rebooted and added it to /etc/modprobe.d/blacklist.  Rebooted back into failsafe terminal and tried running the install again - it fails with ...
cd: 3 can't cd to /usr/lib/oss/build
sh can't open install.sh
cat: /usr/lib/oss/version.dat:  no such file or directory

It appears at this point I have a half-baked install.  Tried uninstalling using apt-get and Synaptic - get a message "error processing".

How can I remove it to attempt a re-install?

Thanks -

---

### Post by Yellow Pasque on 2008-05-11
> **flyinraptr said:**
> Problems trying to install -

Initially received error messages towards the end of the install - complaining about cx88_alsa still in use.  I rebooted and added it to /etc/modprobe.d/blacklist.  Rebooted back into failsafe terminal and tried running the install again - it fails with ...
cd: 3 can't cd to /usr/lib/oss/build
sh can't open install.sh
cat: /usr/lib/oss/version.dat:  no such file or directory

It appears at this point I have a half-baked install.  Tried uninstalling using apt-get and Synaptic - get a message "error processing".

How can I remove it to attempt a re-install?

Thanks -
As seawright linked to on the OSS forum:
[http://www.4front-tech.com/forum/viewtopic.php?t=2054](http://www.4front-tech.com/forum/viewtopic.php?t=2054)

---

### Post by flyinraptr on 2008-05-11
> **Temüjin said:**
> As seawright linked to on the OSS forum:
[http://www.4front-tech.com/forum/viewtopic.php?t=2054](http://www.4front-tech.com/forum/viewtopic.php?t=2054)

Thanks -

---

### Post by Keldek on 2008-05-12
> **Temüjin said:**
> radamo,

Thank you for your patience. Below is the procedure I used to install OSS 4.1 from the mercurial repo. If your system complains about ALSA still running, then I recommend doing this procedure from 'recovery mode'.

```
sudo /etc/init.d/alsa-utils stop
sudo apt-get -y remove alsa-oss oss-compat alsa-base libesd-alsa0

sudo apt-get -y install linux-headers-`uname -r` build-essential gawk libtool libgtk2.0-dev libesd0 esound esound-common linux-sound-base gcc-multilib libesd0-dev mercurial libssl0.9.8 libssl-dev
cd /usr/src
sudo hg clone http://mercurial.opensound.com/ oss-devel
cd ~/
mkdir oss41build
cd oss41build/
sudo sh /usr/src/oss-devel/configure
sudo make
sudo make install
```

I got to this part:
```
sudo apt-get -y remove alsa-oss oss-compat alsa-base libesd-alsa0
```

and this happened:

```
keldek@System-X:~$ sudo /etc/init.d/alsa-utils stop
 * Shutting down ALSA...                                                                                                                               [ OK ] 
keldek@System-X:~$ sudo apt-get -y remove alsa-oss oss-compat alsa-base libesd-alsa0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package alsa-oss is not installed, so not removed
Package oss-compat is not installed, so not removed
Package alsa-base is not installed, so not removed
The following packages were automatically installed and are no longer required:
  sndfile-programs libavahi-qt3-1 libpano12-bin libwxbase2.6-0 libsigc++-1.2-5c2 libwxbase2.8-0 rosegarden-data libxine1-x libmodplug0c2 libxcb-xv0
  libmp4v2-0 libtunepimp5 liblualib50 libiso9660-5 libcommons-cli-java libxine1-plugins libdvbpsi4 libxosd2 ruby1.8 libvlc0 libgdl-1-common hugin-data ruby
  vlc-nox libboost-thread1.34.1 libmatroska0 libxine1-console libswt3.2-gtk-java libgda3-common libpano12-0 libifp4 flac libdvdnav4 libgnome-vfsmm-2.6-1c2a
  libxine1-misc-plugins libxvmc1 libgda3-3 libcommons-lang-java kdelibs-data liblua50 libruby1.8 python-xlib libxcb-shape0 libxcb-shm0 libvcdinfo0 libebml0
  libswt3.2-gtk-jni libnjb5 libofa0 autopano-sift libgdiplus vlc-plugin-pulse libseda-java libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  agave alacarte amarok amarok-xine audacious-plugins-extra audacity bittornado-gui bluefish brasero bug-buddy compiz compiz-gnome contact-lookup-applet
  creox deskbar-applet ekiga eog evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal f-spot fast-user-switch-applet
  file-roller firefox-2-gnome-support freqtweak gcdmaster gconf-editor gedit gimp-gnomevfs gnome-applets gnome-control-center gnome-games gnome-media
  gnome-netstatus-applet gnome-orca gnome-panel gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-session gnome-settings-daemon gnome-specimen
  gnome-spell gnome-terminal gnome-user-guide gnome-utils gnome-volume-manager gtkhtml3.14 hugin hugin-bin hugin-tools istanbul kdebase-bin kdebase-bin-kde3
  kdelibs4c2a khelpcenter libarts1c2a libbonoboui2-0 libdeskbar-tracker libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserverui1.2-8 libeel2-2 libesd-alsa0 libexchange-storage1.2-3 libgail-gnome-module libgdl-1-0 libgdl-gnome-1-0 libgnome-desktop-2
  libgnome-window-settings1 libgnome2-0 libgnome2-perl libgnome2.0-cil libgnomemm-2.6-1c2 libgnomeui-0 libgnomeuimm-2.6-1c2a libgtkhtml3.14-19
  libgtkhtml3.16-cil liblpint-bonobo0 libpanel-applet2-0 libwxgtk2.6-0 libwxgtk2.8-0 mousetweaks nautilus nautilus-actions nautilus-cd-burner
  nautilus-image-converter nautilus-sendto nautilus-share network-manager-gnome python-gnome2 python-gnome2-desktop python-gnome2-extras python-pyatspi
  python-wxgtk2.6 python-wxversion rhythmbox rosegarden seahorse sooperlooper sound-juicer system-config-printer-gnome timidity tomboy totem totem-gstreamer
  totem-mozilla totem-plugins tracker-search-tool tsclient ubuntu-docs ubuntustudio-audio ubuntustudio-graphics update-notifier vino vlc
  xulrunner-1.9-gnome-support yelp
0 upgraded, 0 newly installed, 123 to remove and 0 not upgraded.
After this operation, 508MB disk space will be freed.
(Reading database ... 155777 files and directories currently installed.)
Removing ubuntustudio-graphics ...
Removing agave ...
Removing alacarte ...
Removing ubuntustudio-audio ...
@audio          -       rtprio          99

Removing audacious-plugins-extra ...
Removing audacity ...
Removing bittornado-gui ...
Removing bluefish ...
Removing brasero ...
Removing bug-buddy ...
Removing compiz ...
Removing compiz-gnome ...
Removing contact-lookup-applet ...
Removing creox ...
Removing libdeskbar-tracker ...
Removing deskbar-applet ...
Removing ekiga ...
Removing eog ...
Removing evince ...
Removing evolution-plugins ...
Removing evolution-exchange ...
Removing evolution ...
Removing evolution-data-server ...
Removing evolution-webcal ...
Removing f-spot ...
Removing fast-user-switch-applet ...
Removing file-roller ...
Removing firefox-2-gnome-support ...
Removing freqtweak ...
Removing gcdmaster ...
Removing gconf-editor ...
Removing gedit ...
Removing gimp-gnomevfs ...
Removing gnome-applets ...
Removing nautilus-image-converter ...
Removing nautilus-share ...
Removing nautilus-cd-burner ...
Removing nautilus-sendto ...
Removing nautilus ...
Removing gnome-panel ...
Removing gnome-terminal ...
Removing gnome-control-center ...
Removing gnome-games ...
Removing gnome-media ...
Removing gnome-netstatus-applet ...
Removing gnome-orca ...
Removing gnome-pilot-conduits ...
Removing gnome-pilot ...
Removing gnome-session ...
Removing gnome-power-manager ...
Removing gnome-settings-daemon ...
Removing gnome-specimen ...
Removing gnome-spell ...
Removing ubuntu-docs ...
Removing gnome-user-guide ...
Removing gnome-utils ...
Removing gnome-volume-manager ...
Removing gtkhtml3.14 ...
Removing hugin ...
Removing hugin-bin ...
Removing hugin-tools ...
Removing istanbul ...
Removing rosegarden ...
Removing kdebase-bin ...
Removing kdebase-bin-kde3 ...
Removing khelpcenter ...
Removing libgnome-window-settings1 ...
Removing tsclient ...
Removing tomboy ...
Removing seahorse ...
Removing python-gnome2-extras ...
Removing python-gnome2-desktop ...
Removing mousetweaks ...
Removing libgnome2.0-cil ...
Removing libgail-gnome-module ...
Removing libpanel-applet2-0 ...
Removing nautilus-actions ...
Removing update-notifier ...
Removing totem ...
Removing totem-plugins ...
Removing totem-mozilla ...
Removing totem-gstreamer ...
Removing sound-juicer ...
Removing rhythmbox ...
Removing system-config-printer-gnome ...
Removing python-pyatspi ...
Removing python-gnome2 ...
Removing network-manager-gnome ...
Removing liblpint-bonobo0 ...
Removing libgtkhtml3.16-cil ...
Removing libgtkhtml3.14-19 ...
Removing libgnomeuimm-2.6-1c2a ...
Removing tracker-search-tool ...
Removing libeel2-2 ...
Removing libgnome-desktop-2 ...
Removing yelp ...
Removing vino ...
Removing libgnome2-perl ...
Removing libgdl-gnome-1-0 ...
Removing libgdl-1-0 ...
Removing libgnomeui-0 ...
Removing libbonoboui2-0 ...
Removing libedataserverui1.2-8 ...
Removing libedata-book1.2-2 ...
Removing libebook1.2-9 ...
Removing libedata-cal1.2-6 ...
Removing libecal1.2-7 ...
Removing timidity ...
 * Stopping TiMidity++ ALSA midi emulation...                                                                                                          [ OK ] 
Removing libwxgtk2.8-0 ...
Removing vlc ...
Removing sooperlooper ...
Removing xulrunner-1.9-gnome-support ...
Removing libexchange-storage1.2-3 ...
Removing libgnomemm-2.6-1c2 ...
Removing libgnome2-0 ...
Removing python-wxversion ...
Removing amarok ...
Removing amarok-xine ...
Removing kdelibs4c2a ...
Removing libarts1c2a ...
Removing python-wxgtk2.6 ...
Removing libwxgtk2.6-0 ...
Removing libesd-alsa0 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
keldek@System-X:~$ 

```

SIGH :icon_frown:

---

### Post by Keldek on 2008-05-12
I've gotten almost everything reinstalled from the list above, except now I run into this problem:

```
keldek@System-X:~$ sudo apt-get install ubuntustudio-audio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntustudio-audio is already the newest version.
The following packages were automatically installed and are no longer required:
  libcommons-cli-java libswt3.2-gtk-java libcommons-lang-java
  libswt3.2-gtk-jni libseda-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                            [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg: error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 timidity
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)
keldek@System-X:~$ 

```

---

### Post by fuzzyworbles on 2008-05-12
Wait a second.. removing the alsa packages you mention here causes me to remove ubuntu-desktop. That doesn't seem right. I'm sure glad i didn't include the -y switch.

I recall installing oss4 in gutsy without removing anything. instead, i added alsa modules to the blacklist. maybe i should relocate that howto.

[edit] .. alright, since nobody else had complained about the ubuntu-desktop removal (and 'cause i realize that it's just a metapackage), i went ahead and followed through with your instructions.

now, gdm doesn't play fancy sounds when logging in, and more importantly, audacious doesn't work (yes, i've changed the settings, and it shows up under a pcm channel in ossxmix). zsnes doesn't work either when set to use oss. all of these used to work with oss4 under gutsy (actually, i used xmms under gutsy, not audacious -- regardless, it worked w/ oss4). what's up with this? at least totem works though, and so does flash under firefox. suggestions?

[edit] .. alright, i found that i can get gdm to (kind of) work if i change the audio player in gdm.conf to /usr/bin/ossplay, but it only does the bongo drums (login ready), but not the jungly noises after successfully logging in. i couldn't find anything on audacious except recompleing the output plugins from source with oss4=on configure parameters (which are off by default for some reason). so, i complied xmms that can actually use oss4 and uses less cpu than audacious. the streaming sucks though.

zsnes still doesn't have audio.

---

### Post by nezach on 2008-05-12
> **Keldek said:**
> I got to this part:
```
sudo apt-get -y remove alsa-oss oss-compat alsa-base libesd-alsa0
```

and this happened:

```
keldek@System-X:~$ sudo /etc/init.d/alsa-utils stop
 * Shutting down ALSA...                                                                                                                               [ OK ] 
keldek@System-X:~$ sudo apt-get -y remove alsa-oss oss-compat alsa-base libesd-alsa0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package alsa-oss is not installed, so not removed
Package oss-compat is not installed, so not removed
Package alsa-base is not installed, so not removed
The following packages were automatically installed and are no longer required:
  sndfile-programs libavahi-qt3-1 libpano12-bin libwxbase2.6-0 libsigc++-1.2-5c2 libwxbase2.8-0 rosegarden-data libxine1-x libmodplug0c2 libxcb-xv0
  libmp4v2-0 libtunepimp5 liblualib50 libiso9660-5 libcommons-cli-java libxine1-plugins libdvbpsi4 libxosd2 ruby1.8 libvlc0 libgdl-1-common hugin-data ruby
  vlc-nox libboost-thread1.34.1 libmatroska0 libxine1-console libswt3.2-gtk-java libgda3-common libpano12-0 libifp4 flac libdvdnav4 libgnome-vfsmm-2.6-1c2a
  libxine1-misc-plugins libxvmc1 libgda3-3 libcommons-lang-java kdelibs-data liblua50 libruby1.8 python-xlib libxcb-shape0 libxcb-shm0 libvcdinfo0 libebml0
  libswt3.2-gtk-jni libnjb5 libofa0 autopano-sift libgdiplus vlc-plugin-pulse libseda-java libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  agave alacarte amarok amarok-xine audacious-plugins-extra audacity bittornado-gui bluefish brasero bug-buddy compiz compiz-gnome contact-lookup-applet
  creox deskbar-applet ekiga eog evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal f-spot fast-user-switch-applet
  file-roller firefox-2-gnome-support freqtweak gcdmaster gconf-editor gedit gimp-gnomevfs gnome-applets gnome-control-center gnome-games gnome-media
  gnome-netstatus-applet gnome-orca gnome-panel gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-session gnome-settings-daemon gnome-specimen
  gnome-spell gnome-terminal gnome-user-guide gnome-utils gnome-volume-manager gtkhtml3.14 hugin hugin-bin hugin-tools istanbul kdebase-bin kdebase-bin-kde3
  kdelibs4c2a khelpcenter libarts1c2a libbonoboui2-0 libdeskbar-tracker libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserverui1.2-8 libeel2-2 libesd-alsa0 libexchange-storage1.2-3 libgail-gnome-module libgdl-1-0 libgdl-gnome-1-0 libgnome-desktop-2
  libgnome-window-settings1 libgnome2-0 libgnome2-perl libgnome2.0-cil libgnomemm-2.6-1c2 libgnomeui-0 libgnomeuimm-2.6-1c2a libgtkhtml3.14-19
  libgtkhtml3.16-cil liblpint-bonobo0 libpanel-applet2-0 libwxgtk2.6-0 libwxgtk2.8-0 mousetweaks nautilus nautilus-actions nautilus-cd-burner
  nautilus-image-converter nautilus-sendto nautilus-share network-manager-gnome python-gnome2 python-gnome2-desktop python-gnome2-extras python-pyatspi
  python-wxgtk2.6 python-wxversion rhythmbox rosegarden seahorse sooperlooper sound-juicer system-config-printer-gnome timidity tomboy totem totem-gstreamer
  totem-mozilla totem-plugins tracker-search-tool tsclient ubuntu-docs ubuntustudio-audio ubuntustudio-graphics update-notifier vino vlc
  xulrunner-1.9-gnome-support yelp
0 upgraded, 0 newly installed, 123 to remove and 0 not upgraded.
After this operation, 508MB disk space will be freed.
(Reading database ... 155777 files and directories currently installed.)
Removing ubuntustudio-graphics ...
Removing agave ...
Removing alacarte ...
Removing ubuntustudio-audio ...
@audio          -       rtprio          99

Removing audacious-plugins-extra ...
Removing audacity ...
Removing bittornado-gui ...
Removing bluefish ...
Removing brasero ...
Removing bug-buddy ...
Removing compiz ...
Removing compiz-gnome ...
Removing contact-lookup-applet ...
Removing creox ...
Removing libdeskbar-tracker ...
Removing deskbar-applet ...
Removing ekiga ...
Removing eog ...
Removing evince ...
Removing evolution-plugins ...
Removing evolution-exchange ...
Removing evolution ...
Removing evolution-data-server ...
Removing evolution-webcal ...
Removing f-spot ...
Removing fast-user-switch-applet ...
Removing file-roller ...
Removing firefox-2-gnome-support ...
Removing freqtweak ...
Removing gcdmaster ...
Removing gconf-editor ...
Removing gedit ...
Removing gimp-gnomevfs ...
Removing gnome-applets ...
Removing nautilus-image-converter ...
Removing nautilus-share ...
Removing nautilus-cd-burner ...
Removing nautilus-sendto ...
Removing nautilus ...
Removing gnome-panel ...
Removing gnome-terminal ...
Removing gnome-control-center ...
Removing gnome-games ...
Removing gnome-media ...
Removing gnome-netstatus-applet ...
Removing gnome-orca ...
Removing gnome-pilot-conduits ...
Removing gnome-pilot ...
Removing gnome-session ...
Removing gnome-power-manager ...
Removing gnome-settings-daemon ...
Removing gnome-specimen ...
Removing gnome-spell ...
Removing ubuntu-docs ...
Removing gnome-user-guide ...
Removing gnome-utils ...
Removing gnome-volume-manager ...
Removing gtkhtml3.14 ...
Removing hugin ...
Removing hugin-bin ...
Removing hugin-tools ...
Removing istanbul ...
Removing rosegarden ...
Removing kdebase-bin ...
Removing kdebase-bin-kde3 ...
Removing khelpcenter ...
Removing libgnome-window-settings1 ...
Removing tsclient ...
Removing tomboy ...
Removing seahorse ...
Removing python-gnome2-extras ...
Removing python-gnome2-desktop ...
Removing mousetweaks ...
Removing libgnome2.0-cil ...
Removing libgail-gnome-module ...
Removing libpanel-applet2-0 ...
Removing nautilus-actions ...
Removing update-notifier ...
Removing totem ...
Removing totem-plugins ...
Removing totem-mozilla ...
Removing totem-gstreamer ...
Removing sound-juicer ...
Removing rhythmbox ...
Removing system-config-printer-gnome ...
Removing python-pyatspi ...
Removing python-gnome2 ...
Removing network-manager-gnome ...
Removing liblpint-bonobo0 ...
Removing libgtkhtml3.16-cil ...
Removing libgtkhtml3.14-19 ...
Removing libgnomeuimm-2.6-1c2a ...
Removing tracker-search-tool ...
Removing libeel2-2 ...
Removing libgnome-desktop-2 ...
Removing yelp ...
Removing vino ...
Removing libgnome2-perl ...
Removing libgdl-gnome-1-0 ...
Removing libgdl-1-0 ...
Removing libgnomeui-0 ...
Removing libbonoboui2-0 ...
Removing libedataserverui1.2-8 ...
Removing libedata-book1.2-2 ...
Removing libebook1.2-9 ...
Removing libedata-cal1.2-6 ...
Removing libecal1.2-7 ...
Removing timidity ...
 * Stopping TiMidity++ ALSA midi emulation...                                                                                                          [ OK ] 
Removing libwxgtk2.8-0 ...
Removing vlc ...
Removing sooperlooper ...
Removing xulrunner-1.9-gnome-support ...
Removing libexchange-storage1.2-3 ...
Removing libgnomemm-2.6-1c2 ...
Removing libgnome2-0 ...
Removing python-wxversion ...
Removing amarok ...
Removing amarok-xine ...
Removing kdelibs4c2a ...
Removing libarts1c2a ...
Removing python-wxgtk2.6 ...
Removing libwxgtk2.6-0 ...
Removing libesd-alsa0 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
keldek@System-X:~$ 

```

SIGH :icon_frown:

Did you do it from the recovery mode? Try installing libesd0 and libesd0-dev before removing libesd-alsa0. That way you will not break that many dependencies.

---

### Post by fuzzyworbles on 2008-05-13
you know, it's not really worth the upgrade for my ibm t30 with a basic boring ol' intel integrated sound card... slightly better sound quality at the cost of no system sounds and no support out-of-the-box with a variety of other packages. the most irritating was probably having to make sure nothing was occupying oss before going on standby... thanks anyway. I'm currently trying to get everything back to using alsa. lets see if that's as problematic as getting them to use oss4...

.. yup, I guess it is. can anybody point my in the right direction to get totem to stop saying that the device is occupied? i've removed oss4, reinstalled alsa, and reverted back from the gstreamer patch. gstreamer-properties tests well when set to alsa, and system sounds are back, but it's just totem that doesn't want to cooperate. help? anybody?

---

### Post by sync_85 on 2008-05-14
thank you very much.finally i can hear sound on my speaker.

---

### Post by Zorael on 2008-05-14
[http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)

I'm going to try compiling OSS 4.1 later and see if it works better, but so far my main gripes (with the prepackaged 4.0 version) are, in no particular order:

[list][*]Doesn't work with Pulse. OSS4 isn't completely backwards compatible and Pulse calls some old-and-removed functions, and neither side places priority on fixing. I've the greatest respect for both dev teams for their work, just wish they'd play nice with eachother
[*]ossxmix.
[list][*]Confusage Incarnate™, rampant bars with no labeling, but I could likely use pulse's mixer if that worked
[*]Seemingly no way of transfering sources between sinks, if I'm allowed to use pulse's terminology. I don't see why? (Or am I missing it? Perhaps I could use pulse's mixer for this, as well[/list]
[*]Doesn't seem to support hotplugging of (usb) devices (see earlier posts in this thread), unplugging once breaks possibility of reconnecting without reloading OSS
[*]KDE's kmix doesn't work at all, which by extension means my multimedia keys for volume up/down don't work. Not OSS's fault, just wish kmix was more flexible. Likely to improve in KDE4 with Phonon, but 4.0.4 is more like 4.0.0rc4. If anyone coding-proficient reads this, WTB kmix (and kmilo) patch :<
[*]When doing [FONT="Courier New"]soundon[/FONT] (which it does in the boot process), sound card is for a few seconds enabled with 100% volume and output from microphone not muted, which makes my ears bleed.[/list]

---

### Post by Shadowmeph on 2008-05-14
I read a few at the 4front tech site and couldn't really find anything . anyway I bought a Xonar dx sound card and installed it on my Ubuntu hardy64bit using the instructions on this forum but my card doesn't work here is as much info as I know how to give
ossmix
Code:
Selected mixer 0/CMedia CMI8788
Known controls are:
pcm <both>[:<rightvol>] (currently 100:100)
rear <both>[:<rightvol>] (currently 100:100)
center <both>[:<rightvol>] (currently 40:40)
side <both>[:<rightvol>] (currently 75:75)
ext.monitor.multichannel ON|OFF (currently OFF)
ext.monitor.frontpanel ON|OFF (currently ON)
ext.monitor.spdif ON|OFF (currently OFF)
ext.routing.speaker-spread ON|OFF (currently OFF)
ext.routing.spdif-loopback ON|OFF (currently OFF)
spdif-out.enable ON|OFF (currently OFF)
spdif-out.adc/dac ON|OFF (currently OFF)
spdif-out.pro <Consumer> (currently Consumer)
spdif-out.audio <Audio> (currently Audio)
spdif-out.copy ON|OFF (currently OFF)
spdif-out.pre-emph ON|OFF (currently OFF)
spdif-out.rate <44> (currently 48KHz)
spdif-out.vbit ON|OFF (currently OFF)

ossinfo
Code:
Version info: OSS 4.0 (b1015/200803240317) (0x00040003)
Platform: Linux/x86_64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 (dallas-desktop)
Number of audio devices:   2
Number of audio engines:   11
Number of mixer devices:   2
Device objects
 0: osscore0 OSS core services
 1: cmi87880 CMedia CMI8788 interrupts=7 (9)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual mixer
Mixer devices
 0: CMedia CMI8788 (Mixer 0 of device object 1)
 1: AC97 Input Mixer (CMI9780) (Mixer 1 of device object 1)
Audio devices
CMedia CMI8788 (MultiChannel)     /dev/oss/cmi87880/pcm0  (device index 0)
CMedia CMI8788 (SPDIF)            /dev/oss/cmi87880/pcm1  (device index 1)

under the sound settings in preference it doesn't show any oss at all
I did the osstest I get no sound but this is the output
osstest
Code:
Sound subsystem and version: OSS 4.0 (b1015/200803240317) (0x00040003)
Platform: Linux/x86_64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008
*** Scanning sound adapter #-1 ***
/dev/oss/cmi87880/pcm0 (audio engine 0): CMedia CMI8788 (MultiChannel)
- Performing audio playback test...
  <left> OK <right> OK <stereo> OK <measured>
/dev/oss/cmi87880/pcm1 (audio engine 2): CMedia CMI8788 (SPDIF)
- Performing audio playback test...
  <left> OK <right> OK <stereo> OK <measured>

*** All tests completed OK ***

I went to the 4front-tech to try and get some help for my Xonar dx card and apparently the oss doesn't support my card but I was given a link to the oss-development site in which a person (Mario Goebbels) has made a patch for this but I am not sure of how to apply the patch , you see it is a bat file and being pretty new to Linux I am not sure how to apply the patch. I asked this on the 4front-tech site and they said I have to build my own, now I don't have any problem doing this but the instructions at [http://4front-tech.com/wiki/index.php/Building_OSSv4_from_source]("http://4front-tech.com/wiki/index.php/Building_OSSv4_from_source") are confusing to me because it doesn't show how I am to install the bat file at all also when I tried to follow the instructions I get lost. any help would be appreciated. and if I cannot get my card to work I could always go back to my onboard sound card but as of now that doesn't work either :(

---

### Post by Shadowmeph on 2008-05-14
I downloaded the /testing/gpl ([ ] oss-v4.1-build080509..>) instructions and file and in the instructions it says to

> cd /usr/src
which I did then it says
Quote:
restore the files in the tarball by executing the following command:
bunzip2 -c /tmp/oss-v4.1-build080509-src-gpl.tar.bz2 | tar xvf -
but when I do this I get

> oss-v4.1-build080509-src-gpl/RELNOTES.txt
tar: oss-v4.1-build080509-src-gpl/RELNOTES.txt: Cannot open: No such file or directory
tar: Error exit delayed from previous errors

I just copy and pasted the last part because it pretty much says the same thing through out " no such directory"
and I do have the file in the tmp directory so I am not sure why it is doing that

---

### Post by Yellow Pasque on 2008-05-14
Edit: Ok, Hannu has fixed the Mercurial repo. :)

---

### Post by fuzzyworbles on 2008-05-15
Can somebody PLEASE show me how to correctly restore alsa as it was before I installed OSS4? So far I've uninstalled it, and reinstalled everything that this how to instructed me to remove. This has left me with sound only when the application can use ESD, but direct alsa use still fails (it says that it's busy even when nothing is using it). Also, totem doesn't have audio even though it tests fine under gstreamer-properties. Finally, I can't use audacious because it emits a loud white noise when using ESD (and as I mentioned, ALSA is broken). What really confuses me is that ESD is just a mixing layer on ALSA, right? So... what's the deal? :confused:

Any help would be GREATLY appreciated!

.. ah ha! i guess installing oss4 mucks with kernel (i guess -- really i don't know) but reinstalling the kernel and ubuntu module package did the trick.

---

### Post by sheldoon on 2008-05-15
Greetings all, an xubuntu newb here.  Just got the OSS package to install, osstest works fine, gives no errors but I still have no sound.  Running the SB-XFi Fatal1ty, using the digital coax output through the 5.25 extension bay.  Anybody know how to enable that beast, or is that part of the beta support that's not been worked on yet?

---

### Post by PRGUY85 on 2008-05-16
I am trying to reinstall everything since I am having problems now with OSS.

Tried removing the oss-linux package through Synaptic and got the following:

E: oss-linux: subprocess pre-removal script returned error exit status 2

---

### Post by Yellow Pasque on 2008-05-16
PRGUY85:
[http://www.4front-tech.com/forum/viewtopic.php?t=2054](http://www.4front-tech.com/forum/viewtopic.php?t=2054)

---

### Post by spotteddog on 2008-05-16
What would be the _normal_ time-frame for this whole Creative X-fi problems thing to be fixed?  
I've been trying Ubuntu for 4 weeks and have been waiting for (X-fi) sound, before making a complete migration from Vista to Ubuntu Hardy.
Apparently the OOS4 fix is so buggy it shouldn't be attempted by a newb (me). I could downgrade my sound card, but I don't want too. 
How long do these things take. The X-Fi has been out for years.

(Not complaining. Just asking a question)

---

### Post by Yellow Pasque on 2008-05-16
spotteddog: I haven't heard any timeframe. As soon as an update is available for the X-fi or another OSS 4.0 build is released, I will post in this thread. You might want to subscribe to the X-fi thread: [http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

---

### Post by youpo on 2008-05-16
> **Temüjin said:**
> [SIZE="4"]Installing OSS 4.0 From a .deb package[/SIZE]

Check to see if your device is supported by OSS...


Thanks!

---

### Post by PRGUY85 on 2008-05-18
> **Temüjin said:**
> PRGUY85:
[http://www.4front-tech.com/forum/viewtopic.php?t=2054](http://www.4front-tech.com/forum/viewtopic.php?t=2054)

Worked.

---

### Post by ninocass on 2008-05-18
Hey, thanks for the guide.

When i have music/video playering and the oss mixer is up i can see the volume levels increase and decrease on the graphics equaliser thingy however i cant hear any sound :S

ossinfo give me:

```

Version info: OSS 4.0 (b1015/200803240256) (0x00040003) 
Platform: Linux/i686 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 (nino-xps-linux)

Number of audio devices:	8
Number of audio engines:	16
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 Intel HD Audio interrupts=262207 (262207)
    HD Audio controller Intel HD Audio
    Vendor ID    0x8086284b
    Subvendor ID 0x10280209
     Codec  0: STAC9228X (0x83847616/0x10280209)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual mixer


Mixer devices
 0: High Definition Audio STAC9228X (Mixer 0 of device object 1)

Audio devices
HD Audio front                    /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio center/LFE               /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio rear                     /dev/oss/hdaudio0/pcm2  (device index 2)
HD Audio side                     /dev/oss/hdaudio0/pcm3  (device index 3)
HD Audio spdif-out                /dev/oss/hdaudio0/spdout0  (device index 4)
High Definition Audio rec1        /dev/oss/hdaudio0/pcmin0  (device index 5)
High Definition Audio rec2        /dev/oss/hdaudio0/pcmin1  (device index 6)
High Definition Audio rec3        /dev/oss/hdaudio0/pcmin2  (device index 7)

```

---

### Post by pai60 on 2008-05-19
Hi, everyone. I just follow Temujin guide and ...magically sound and music everywhere from my x-fi! Thanks, man, really great job.

---

### Post by ninocass on 2008-05-19
trying to remove ossv4 as i cant seem to ge tit working but i cant get alsa back on, i keep getting an error saying that there is no Gstramer or audio device :S

thanks

---

### Post by spotteddog on 2008-05-19
I followed Temujin's instructions to uninstall ALSA and install OSS. 
Everything seemed to install OK. I have the new mixer icon installed and everything seemed to be where it was supposed to be. I had the OSS option in my "Sound" menu, etc. I tried to apply the "patch", which failed. And then.....
After I rebooted, I had nothing: No OSS option in the "sounds" menu, No ALSA is installed. 
I tried to start over again, but got the error "no ALSA install", then the install OSS fails. 
I tried the "recovering from failed .deb install", but that also just returns errors.
So now I have no sound of any kind installed. 

(And it all seemed to be going so well!  :()

Where did I go wrong? What next?

Thanks

---

### Post by PRGUY85 on 2008-05-19
Hey, I installed Mythtv.  How can I add sound there?

SOLVED

---

### Post by Yellow Pasque on 2008-05-20
For those using Kubuntu: I installed Kubuntu 8.04 on my stepdad's computer (SB Audigy) and had to install OSS4 since ALSA didn't work (surprise..). I'm not quite sure how I managed it, but after running the command below and rebooting, OSS4 was working with kmix. kmix didn't have all of the options ossxmix did, but it did have master volume, so I assume it would work if one had it setup to use multimedia keys or the scrollwheel to control volume.

```
sudo dpkg-reconfigure linux-sound-base
```

---

### Post by Rhapsody on 2008-05-20
> **Temüjin said:**
> For those using Kubuntu: I installed Kubuntu 8.04 on my stepdad's computer (SB Audigy) and had to install OSS4 since ALSA didn't work (surprise..). I'm not quite sure how I managed it, but after running the command below and rebooting, OSS4 was working with kmix. kmix didn't have all of the options ossxmix did, but it did have master volume, so I assume it would work if one had it setup to use multimedia keys or the scrollwheel to control volume.
I was wondering about this myself. It seemed this topic had the age-old 'KDE Problem' where a problem was mentioned that probably existed in KDE, but the only solution given is for GNOME and I end up not knowing if I even have a problem, nor how to fix it if I do.

So I've got a Sound Blaster X-Fi XtremeGamer on Kubuntu 8.04, and it looks like I'll need OSSv4 to make it work. Will it work with KMix, and if not, how the hell do I use ossxmix with KDE?

---

### Post by PRGUY85 on 2008-05-21
Hey, is Skype OSS version a bit sluggish on your PCs?

---

### Post by spotteddog on 2008-05-22
I ended up reinstalling Hardy and I re-tried Temujin's OSS instructions for getting sound from my X-Fi. This time it worked and I have sound. Sounds great. Thanks Temujin.

But, I don't have any system sounds, though. How do I get my system sounds to work with OSS 4?

Anything else I need to do with my OSS and X-Fi? I have only tried to play CD's and they work fine. Haven't really had time to try anything else yet.

Thanks,

Spot

---

### Post by Yellow Pasque on 2008-05-22
> **spotteddog said:**
> But, I don't have any system sounds, though. How do I get my system sounds to work with OSS 4?

For GNOME, you have to get ESD running and set the System -> Preferences -> Sound to use it. I'm not sure exactly how to to install it and have it start automatically. I do know you'll need to fire up Synaptic and make sure libesd0 is installed (which should remove libesd-alsa0).

To be honest, I haven't spent a whole lot of time on it because I don't want system sounds playing over my music anyway. I prefer to keep my build lightweight and running ESD and all sound through it just doesn't appeal to me.

Note to Kubuntu/KDE users: You'll need to get aRts up and running (do a search in Synaptic) and set System -> Prefences -> Sounds to use it.

> Anything else I need to do with my OSS and X-Fi?
Tell Ubuntu to force OSS output. The following command will bring up an information message. Hit [Enter] to say OK and use the down-arrow to select 'OSS' on the next menu. Press the Tab key and [Enter] to say OK, and you'll be back at the terminal.
```
sudo dpkg-reconfigure linux-sound-base
```

---

### Post by spotteddog on 2008-05-22
Thanks Temüjin. You have been so helpful. Greatly appreciated. :popcorn:

---

### Post by Yellow Pasque on 2008-05-22
> **spotteddog said:**
> Thanks Temüjin. You have been so helpful. Greatly appreciated.
Np. If you have any more issues, check what /dev/dsp is pointing at, i.e.:
```
cd /dev
ls -la | grep dsp
```
A full reinstall of Hardy shouldn't be necessary.

---

### Post by OpposingForce on 2008-05-22
Thanks for this guide, it helped me get my Xfi working.  Will ALSA be supporting the XFI cards?  And can I have alsa and oss4 installed at the same time

---

### Post by Yellow Pasque on 2008-05-22
You can have alsa and OSS4 installed at the same time, but I would not recommend it.

To keep ALSA, but prevent it from running use the following command and restart the system:
```
sudo cat /lib/linux-sound-base/noALSA.modprobe.conf >> /etc/modprobe.d/blacklist
```

To undo the ALSA blacklist, delete all the "blacklist snd-" lines on the end of the file.
```
gksudo gedit /etc/modprobe.d/blacklist/
```
(There's probably a slick command to do this, but I can't think of one off the top of my head.)

As for preventing oss4 from loading at startup, I believe the following command will work:
```
cd /etc/init.d/; sudo gzip oss
```
And when you're ready for OSS4 again:
```
cd /etc/init.d/; sudo gunzip oss
```

If OSS still manages to load, a good ol' sudo soundoff will unload it and then you should be able to sudo modprobe the intended ALSA modules.

---

### Post by OpposingForce on 2008-05-22
Thanks, sounds like a lot of trouble though, but I'll keep that in mind.  I guess I'll just have to wait until ALSA supports the XFi cards before I start using ALSA again.

---

### Post by adramalech on 2008-05-23
i was wondering why the ossxmix seems to return this...i get the popup ui and everything but this is the picture...

[IMG]http://i272.photobucket.com/albums/jj179/adramalech707/Screenshot.png[/IMG]

---

### Post by StratusX on 2008-05-26
Okay so I followed the guide hoping that with this version of OSS i could use my X-Fi in linux finally.

So I followed all the steps and everything was good till it got to

"Starting Open Sound System"

After about 5 seconds my computer completely froze. So I did a hard reboot and tried "sudo soundon" and got:

Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.

So I did that and after running sudo soundon my computer crashed again.

So I can install it just fine, just starting it crashes my computer =[

Any thoughts on what's wrong?

Thanks,
Ian

---

### Post by OpposingForce on 2008-05-26
STratusX, maybe try reinstalling OSS4

OSS4 works with my card, but Totem does not work.  I get an error "Invalid Argument- could not connect stream" when I try to load a video.  Some fixes that I googled said going into preferences->sound and changing it to ALSA would work.  But obviously since I removed ALSA that's not going to be an option.  And whenever I go into the preferences->sound menu and hit test, I always get an error something like 'invalid argument' on any sound option that I attempt to "test".  However, VLC works perfectly, with sound, right out of the box.  I didn't need to tweak anything.  Does it use OSS by default or something?  My bug is not totally imperative that I resolve it, as an alternative media player (VLC) is avaibile and works fine, but I'd like to get to the bottom of this and maybe even help others solve this issue.

edit- I just got the new linux kernel update which ubuntu just alerted me to this morning.  I started the new kernel and it said something about relinking modules.  It said "oss started OK" and sound still works the same.  This happens every time the kernel updates?

---

### Post by Yellow Pasque on 2008-05-26
OpposingForce:
```
sudo dpkg-reconfigure linux-sound-base
``` Select OSS. Also make sure you go to System -> Preferences -> Sound and set the options appropriately.

If that doesn't work, make sure you have all the necessary plugins for totem/gstreamer (Do a search in synaptic)

---

### Post by OpposingForce on 2008-05-26
> **Temüjin said:**
> OpposingForce:
```
sudo dpkg-reconfigure linux-sound-base
``` Select OSS. Also make sure you go to System -> Preferences -> Sound and set the options appropriately.

If that doesn't work, make sure you have all the necessary plugins for totem/gstreamer (Do a search in synaptic)

Thanks, but I'm unsure of what to search for.  There is still no option in the system->pref->sound menu for OSS.

---

### Post by Yellow Pasque on 2008-05-26
```
sudo apt-get install totem-gstreamer
```

---

### Post by OpposingForce on 2008-05-26
> **Temüjin said:**
> ```
sudo apt-get install totem-gstreamer
```

Thanks for the quick reply, but I got this

```
cory@cory-desktop:~$ sudo apt-get install totem-gstreamer
[sudo] password for cory: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
totem-gstreamer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.

```

and I ran

```
sudo dpkg-reconfigure linux-sound-base
```

And selected OSS, but oss still does not appear as an option in the GNOME sound menu.

---

### Post by ebike on 2008-05-26
Hi Guys,

I have just tried this install for the Creative X-fi Xmod USB card.

I installed the .deb package and that went fine, blacklisted all the alsa stuff as elsewhere in this thread, rebooted.

The OSS installation worked for my internal sound card and osstest plays on that device, however it doesn't work on the USB X-Fi card.

Has anyone else tried with this card, or is it just not supported. I know alsa doesn't support it in 8.04, yet it worked with alsa on 7.10.

dmesg gives:
> [  172.596215] New audioctl device 1/0 - USB sound device
[  172.608061] USB mixer unit read error -71
[  172.609156] USB mixer unit read error -71
[  172.612185] USB mixer unit read error -71
[  172.615243] New audio streaming device 1/1 - USB sound device
[  172.615335] New audio streaming device 1/2 - USB sound device
[  172.616051] ossusb: oss usbaudio: Failed to set interface mode, error -71 - ignored
[  172.617038] ossusb: oss usbaudio: Failed to set interface mode, error -71 - ignored
[  172.618025] ossusb: Endpoint control write error -71
[  172.618031] Failed to set 44100 Hz sampling rate
[  172.618035] osscore: Trigger (input) failed
[  172.619031] ossusb: Endpoint control write error -71
[  172.619037] Failed to set 44100 Hz sampling rate
[  172.619040] osscore: Trigger failed
[  172.668021] usb 3-1: USB disconnect, address 98
[  173.898977] usb 3-1: new full speed USB device using uhci_hcd and address 99
[  174.065989] usb 3-1: configuration #1 chosen from 1 choice
[  174.070874] usb 3-1: can't set config #1, error -84
[  174.070924] usb 3-1: USB disconnect, address 99
[  175.385756] usb 3-1: new full speed USB device using uhci_hcd and address 100
[  175.551778] usb 3-1: configuration #1 chosen from 1 choice
[  175.557656] usb 3-1: can't set config #1, error -84
[  175.557706] usb 3-1: USB disconnect, address 100
[  176.872550] usb 3-1: new full speed USB device using uhci_hcd and address 101
[  177.038551] usb 3-1: configuration #1 chosen from 1 choice
[  177.045303] usb 3-1: can't set config #1, error -84
[  177.045353] usb 3-1: USB disconnect, address 101


ossinfo is:
> Version info: OSS 4.0 (b1015/200803240256) (0x00040003) 
Platform: Linux/i686 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 (Family)

Number of audio devices:	3
Number of audio engines:	20
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: via82330 VIA VT8235
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual mixer
 4: usb041e30d0-0 USB sound device
 5: usb041e30d0-1 USB sound device
 6: usb041e30d0-2 USB sound device


Mixer devices
 0: VIA823x AC97 Mixer (CMI9739) (Mixer 0 of device object 1)
 1: (USB sound device )(Mixer 0 of device object 4)

Audio devices
VIA VT8235                        /dev/oss/via82330/pcm0  (device index 0)
(USB sound device play             /dev/oss/usb041e30d0-1/pcm0 ) (device index 1)
(USB sound device rec              /dev/oss/usb041e30d0-2/pcmin0 ) (device index 2)


lsmod shows the relevant modules:
> Module                  Size  Used by
vmix                   14132  0 
ossusb                 56072  0 
via8233                13296  0 
osscore               565044  3 vmix,ossusb,via8233
ipv6                  267780  8 
binfmt_misc            12808  1 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
video                  19856  0 
output                  4736  1 video
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
nfs                   262540  1 
lockd                  67720  2 nfs
nfs_acl                 4608  1 nfs
sunrpc                185884  9 nfs,lockd,nfs_acl
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
xfs                   571416  1 
ac                      6916  0 
lp                     12324  0 
usb_storage            73664  0 
usbhid                 31872  0 
libusual               19108  1 usb_storage
hid                    38784  1 usbhid
usblp                  15872  0 
nvidia               7825536  34 
evdev                  13056  4 
i2c_viapro              9876  0 
i2c_core               24832  2 nvidia,i2c_viapro
button                  9232  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
via_ircc               27796  0 
analog                 13600  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
irda                  203068  1 via_ircc
gameport               16008  1 analog
pcspkr                  4224  0 
via_agp                11136  1 
crc_ccitt               3072  1 irda
agpgart                34760  2 nvidia,via_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  4 
pata_acpi               8320  0 
ata_generic             8324  0 
floppy                 59588  0 
pata_via               13316  3 
via_rhine              26632  0 
mii                     6400  1 via_rhine
libata                159344  3 pata_acpi,ata_generic,pata_via
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  8 ossusb,usb_storage,usbhid,libusual,usblp,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

But, doesn't look like ossusb sees the device.
Any suggestions anyone?

Thanks.

---

### Post by OpposingForce on 2008-05-27
**Update** 

solved the problem with system sounds not working on my  X-fi.  I had to install esound by doing

sudo apt-get install esound libesd0

and &#65279;

sudo apt-get install esound-clients

Then I logged out, and back in to restart gnome, and heard the ubuntu theme music.  It still doesnt show OSS or esound in the gnome sound program, but at least it works.  Hope this helps others

---

### Post by Yellow Pasque on 2008-05-27
ebike, I don't know if your USB X-fi card is supported. I suggest making a thread on the OpenSound forums.
Other suggestions would include disabling your onboard audio in the BIOS if you're not using it (run soundoff, ossdetect -v, and soundon on the next boot if you do that) and configuring your audio program to resample to 48KHz (Creative/E-MU chips usually resample to 48KHz in hardware, but it appears the 44.1 KHz format is choking it.)
If you don't see a resampling setting in your media player, try installing Audacious (available in Synaptic/Ubuntu repo) for test purposes. It has a resampling option.

---

### Post by Yellow Pasque on 2008-05-27
[SIZE="4"]**Purging a Failed OSS4 .deb Install, the Ubuntu Way**[/SIZE]
(Based on [http://www.4front-tech.com/forum/viewtopic.php?t=2054](http://www.4front-tech.com/forum/viewtopic.php?t=2054), thanks to Dev Mazumdar)

```
cd /var/lib/dpkg/info
sudo rm oss-linux*
```

Now run the following command and press Ctrl+F or click on the Find icon. Enter oss-linux and it should bring you to a block of text that looks similar to the quote below. Remove that block, save, and quit.

```
gksudo gedit /var/lib/dpkg/status
```

> Package: oss-linux
Status: install ok installed
Priority: extra
Section: alien
Installed-Size: 8440
Maintainer: root <root@dev-desktop>
Architecture: amd64
Version: v4.0rc9-999
Depends: libatk1.0-0 (>= 1.12.1), libc6 (>= 2.4-1), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.3.0), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.10.3), libpango1.0-0 (>= 1.14.5), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1
Conffiles:
/etc/oss.conf 055432d38aaf37fc6de3dba4a95accc3
Description: Open Sound System sound drivers for Linux
Open Sound System for Linux (OSS/Linux) is a commercial quality sound driver
distributed by 4Front Technologies ([http://www.opensound.com](http://www.opensound.com)). OSS provides
support for practically all sound cards on the market including PnP and
many PCI ones. Installation and configuration is higly automated and easy to
perform. To obtain technical support and additional features, you will need to
order a license key from [http://www.opensound.com/order.html](http://www.opensound.com/order.html)
.
(Converted from a rpm package by alien version 8.64.)

---

### Post by spotteddog on 2008-05-27
> **OpposingForce said:**
> **Update** 

solved the problem with sound systems not working on my  X-fi.  I had to install esound by doing

sudo apt-get install esound libesd0

and &#65279;

sudo apt-get install esound-clients

Then I logged out, and back in to restart gnome, and heard the ubuntu theme music.  It still doesnt show OSS or esound in the gnome sound program, but at least it works.  Hope this helps others
Thanks OpposingForce. It works for me too. (X-Fi, OSS4 and Hardy).

---

### Post by ebike on 2008-05-27
> **Temüjin said:**
> ebike, I don't know if your USB X-fi card is supported. I suggest making a thread on the OpenSound forums.
Other suggestions would include disabling your onboard audio in the BIOS if you're not using it (run soundoff, ossdetect -v, and soundon on the next boot if you do that) and configuring your audio program to resample to 48KHz (Creative/E-MU chips usually resample to 48KHz in hardware, but it appears the 44.1 KHz format is choking it.)
If you don't see a resampling setting in your media player, try installing Audacious (available in Synaptic/Ubuntu repo) for test purposes. It has a resampling option.

Thanks for the advice, I will join that forum. I don't know about your logic on the 48k sampling rate. I get that error on the 44.1khz when the module is loaded (i.e when I plig the card into the USB), there are no programs trying to send data to the card at the time, I have disabled everything. The card hasn't really been recognized yet .....

---

### Post by StratusX on 2008-05-27
> **OpposingForce said:**
> STratusX, maybe try reinstalling OSS4

I've tried that. installing it isn't the problem. But trying to start it causes my system to crash.

---

### Post by Yellow Pasque on 2008-05-28
I've updated the guide. Please let me know if you have problems with the installation. If you get the package installed, but still don't hear sound, please post here: [http://4front-tech.com/forum/index.php](http://4front-tech.com/forum/index.php)

---

### Post by jasontu on 2008-05-28
[http://ubuntuforums.org/showthread.php?t=809881&highlight=usb+microphone](http://ubuntuforums.org/showthread.php?t=809881&highlight=usb+microphone)

Would it be possible that this OSS4 would help me fix my problem getting a USB microphone to work? (issue linked to above)

As it is the USB Audio Device is detected by system, it seems to even detect that there is a microphone on it.  It plays sound to the headphones just fine, but it refuses to pick up sound from the microphone.  I'm not at the machine now but I'm pretty sure that it is managed by ALSA at the moment.  The USB mic is Gigaware, RadioShack's generic brand.

Thanks.

---

### Post by d58e7 on 2008-05-28
I'm not sure how to resolve this but I get this 

```
(Reading database ... 123921 files and directories currently installed.)
Unpacking oss-linux (from oss-linux_v4.0-1015_amd64.deb) ...
Setting up oss-linux (v4.0-1015) ...
Building OSS Modules for Linux-unknown 2.6.24-12-generic

OSS build environment set up for REGPARM kernels


Warning: Cannot locate the Linux kernel development package for
         Linux kernel version  2.6.24-12-generic
         Please install the kernel development package if linking the
         OSS modules fails.

The kernel development package may be called kernel-devel, kernel-smp-devel,
kernel-sources, kernel-headers or something like that. Please refer
to the documentation of your Linux distribution if there are any
difficulties in installing the kernel/driver development environment.

For your Linux distribution the right kernel source package
might be kernel-source.

Under Ubuntu you may need to prepare the kernel environment
after downloading the kernel sources using

  sudo apt-get install linux-headers-2.6.24-12-generic
  cd /usr/src/linux-headers-2.6.24-12-generic/
  sudo make prepare
  sudo make prepare scripts

Building module osscore
Failed to compile OSS
make -C /lib/modules/2.6.24-12-generic/build M=/usr/lib/oss/build modules
make: *** /lib/modules/2.6.24-12-generic/build: No such file or directory.  Stop.
make: *** [default] Error 2
Starting Open Sound System
Relinking OSS kernel modules for "2.6.24-12-generic SMP mod_unload "
This may take few moments - please stand by...

OSS build environment set up for REGPARM kernels


Warning: Cannot locate the Linux kernel development package for
         Linux kernel version  2.6.24-12-generic
         Please install the kernel development package if linking the
         OSS modules fails.

The kernel development package may be called kernel-devel, kernel-smp-devel,
kernel-sources, kernel-headers or something like that. Please refer
to the documentation of your Linux distribution if there are any
difficulties in installing the kernel/driver development environment.

For your Linux distribution the right kernel source package
might be kernel-source.

Under Ubuntu you may need to prepare the kernel environment
after downloading the kernel sources using

  sudo apt-get install linux-headers-2.6.24-12-generic
  cd /usr/src/linux-headers-2.6.24-12-generic/
  sudo make prepare
  sudo make prepare scripts

Building module osscore
Failed to compile OSS
make -C /lib/modules/2.6.24-12-generic/build M=/usr/lib/oss/build modules
make: *** /lib/modules/2.6.24-12-generic/build: No such file or directory.  Stop.
make: *** [default] Error 2

Relinking the OSS kernel modules failed

```

I have tried   sudo apt-get install linux-headers-2.6.24-12-generic but I get the following.```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.24-12-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-12-generic has no installation candidate

```

---

### Post by Yellow Pasque on 2008-05-28
The latest ubuntu amd64 kernel is 2.6.24-17. You can retrieve it and the headers with
```
sudo apt-get install linux-generic linux-headers-2.6.24-17-generic
```

---

### Post by d58e7 on 2008-05-28
Tried that and it didn't do anything I got this

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic is already the newest version.
linux-headers-2.6.24-17-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Yellow Pasque on 2008-05-29
Are you booting off of that kernel? Post your /boot/grub/menu.lst

---

### Post by Deverell on 2008-05-29
Hello,

I'm having trouble with instruction number six. This is what I'm getting.

```
sean@sean-desktop:~/Desktop$ sudo dpkg -i oss-linux_v4.0-1015_amd64.deb
[sudo] password for sean: 
(Reading database ... 109150 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1015 (using oss-linux_v4.0-1015_amd64.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux_v4.0-1015_amd64.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.24-16-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux_v4.0-1015_amd64.deb

```

Any help or advice would be much appreciated. 
Thanks,
Dev

I'm running Hardy Heron 64 as I have an AMD 64 processor.

---

### Post by bm13084 on 2008-05-29
this didn't work from the blacklisting step on... i would like to either go back, or figure out why this didnt work.  either or....

---

### Post by goofeyfoot on 2008-05-29
Thanks for the guide gents.

Unfortunately I couldn't get it to work.

Here is the chronology.

First I had ALSA and no sound on a Creative X-Fi Card.

Then I did the OSS guide thing and I got some sound but not very good.  Some crackling in games.

So then I saw a post about the Creative Beta driver and I tried to install that and got about halfway and a bunch of errors.

Then I said "to heck with all this" and tried to go back to OSS (ie the only thing that ever came close to working, again using the guide.  

This time when I got to the part about putting in the OSS package thing I got a bunch of errors that looks to my layman's eye as being a conflicting driver.  Here is a quote of the error:

Detected Creative SB X-Fi (EARLY BETA)
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture
-----------------------------

Starting Open Sound System
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
Failed to disable conflicting sound drivers
Reboot and try running soundon again

Also check that you have not compiled sound support statically
into the kernel.

michael@michael-desktop:~$ sudo soundon
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
Failed to disable conflicting sound drivers
Reboot and try running soundon again

Also check that you have not compiled sound support statically
into the kernel.
michael@michael-desktop:~$ 

Yeah right, like I even have a clue what all that means.

So gents, how do I get past this?  I can't seem to uninstall the darn Creative Beta driver, at least not in the thin explanation they give you as to how to do that.

Any ideas would be greatly appreciated.  Any sound is better than silence.

Thanks.

Michael

---

### Post by Yellow Pasque on 2008-05-29
Sorry folks, I had a few typos on the blacklisting command. /etc/modprobe.d/ turned out to be etc/modrpobe.d

Try it again and thanks for the help/feedback.

---

### Post by goofeyfoot on 2008-05-29
Does anyone have an answer to my post which is number 117?

Thanks.

Michael

---

### Post by Yellow Pasque on 2008-05-29
> **goofeyfoot said:**
> Does anyone have an answer to my post which is number 117?

Thanks.

Michael
Yes, read post 118

---

### Post by maxfiles on 2008-05-30
put your updates in the original post as to solve problems.

and now I want to revert.

---

### Post by Deverell on 2008-05-30
Ok I replaced the spelling mistake on the blacklist command and I get this.

```
sean@sean-desktop:~$ sudo cat /lib/linux-sound-base/noALSAmodprobe.conf >> /etc/modrpobe.d/blacklist
bash: /etc/modrpobe.d/blacklist: No such file or directory

```

I know I'm a pain. I'm sorry, again to emphasize I'm new to Linux.

---

### Post by qwertM3 on 2008-05-30
This command has failed (twice) on me as well:
1. if I remember correctly it should be "noALSA.modprobe.conf"
2. I was not able to append to "/etc/modrpobe.d/blacklist". I just copied content of "noALSA.modprobe.conf" and added to the end of "etc/modrpobe.d/blacklist".

Check with "cat /etc/modrpobe.d/blacklist" afterwards.

br, qwertM3.

---

### Post by Yellow Pasque on 2008-05-30
> put your updates in the original post as to solve problems.
I updated the guide yesterday and fixed the command. (You're welcome)

---

### Post by goofeyfoot on 2008-05-30
Temujjin:

I tried that right off, but it didn't do anything.  I used it with your "blacklist" code.

Here's what came back to me:

michael@michael-desktop:~$ sudo cat /lib/linux-sound-base/noALSAmodprobe.conf >> /etc/mobprobe.d/blacklist
bash: /etc/mobprobe.d/blacklist: No such file or directory
michael@michael-desktop:~$ 


Thanks.

Michael

---

### Post by Yellow Pasque on 2008-05-30
I suck at typing.
mobprobe.d ---> modprobe.d
Fixed. Sorry.

---

### Post by aashay on 2008-05-30
OSS has been working great on my laptop. Does things ALSA cannot. The only problem is suspend. After I suspend and resume, everything audio related (vids, flash vids, songs etc)starts to lag and eventually stops after 3-4 secs. I need to manually soundoff and soundon (after closing any process that is using OSS, including Firefox, which can be a drag) to make things normal again. Is there a better way to do this?
Edit: Same thing with resuming from hibernate
Heres what dmesg fills in with whenever I play for example a video (keeps repeating)
```
[  182.617260] osscore: Output timed out on audio engine 11/'HD Audio speaker (VMIX0)' (count=0)
[  182.757222] osscore: Output timed out (sync) on audio engine 11
```
Heres what I get when I soundoff (also keeps repeating till the thing is done)
```
SNDCTL_MIX_READ: Input/output error
SNDCTL_MIX_READ: Input/output error
```

---

### Post by goofeyfoot on 2008-05-30
I know it sounds stupid but I cannot get this blacklist thing to work.

Here is what I get.

 sudo cat /lib/linux-sound-base/noALSAmodprobe.conf >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
michael@michael-desktop:~$ 

And here is an error I get with another command.

michael@michael-desktop:~$ sudo dpkg -i oss-linux_v4.0-1015_i386.deb
[sudo] password for michael:
(Reading database ... 129033 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1015 (using oss-linux_v4.0-1015_i386.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux_v4.0-1015_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux_v4.0-1015_i386.deb
michael@michael-desktop:~$ 



Will someone please look at this and tell me what is wrong?

Thanks.

Michael

---

### Post by goofeyfoot on 2008-05-30
And to make things worse I did the "recover from failed OSS installation thing and tried it again.

Here are the errors I got this time.

Can someone please look at this and let me know how I can clean up this horror show?

Thanks.

Michael

michael@michael-desktop:~$ sudo dpkg -i oss-linux_v4.0-1015_i386.deb
Selecting previously deselected package oss-linux.
(Reading database ... 128757 files and directories currently installed.)
Unpacking oss-linux (from oss-linux_v4.0-1015_i386.deb) ...
Setting up oss-linux (v4.0-1015) ...
Building OSS Modules for Linux-unknown 2.6.22-14-generic

OSS build environment set up for REGPARM kernels

Building module osscore
Building module ali5455
Building module allegro
Building module als300
Building module als4000
Building module apci97
Building module atiaudio
Building module audigyls
Building module audioloop
Building module audiopci
Building module cmi8788
Building module cmpci
Building module cs4280
Building module cs4281
Building module digi32
Building module digi96
Building module emu10k1x
Building module envy24
Building module envy24ht
Building module fm801
Building module geode
Building module hdaudio
Building module hdsp
Building module ich
Building module imux
Building module lynxone
Building module lynxtwo
Building module maestro
Building module neomagic
Building module ossusb
Building module riptide
Building module s3vibes
Building module sblive
Building module sbxfi
Building module softoss
Building module solo
Building module sonorus
Building module trident
Building module via8233
Building module via97
Building module vmix
Building module vortex
Building module ymf7xx
depmod -a
-----------------------------
Detected Creative SB X-Fi (EARLY BETA)
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture
-----------------------------

Starting Open Sound System
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_pcm is in use by ctalsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
Failed to disable conflicting sound drivers
Reboot and try running soundon again

Also check that you have not compiled sound support statically
into the kernel.

michael@michael-desktop:~$

---

### Post by Yellow Pasque on 2008-05-31
For those using the latest code via Mercurial: Is anyone else having problems with ossxmix not displaying the rate lock checkbox or the rate menu? Try starting ossxmix via the terminal (no root permissions needed):
```
ossxmix
```
I'm getting the following output:
```
dan@harvest:/dev$ ossxmix
Control 14/rate: Parent(2)==NULL

(ossxmix:20565): Gtk-CRITICAL **: gtk_box_pack_start: assertion `GTK_IS_BOX (box)' failed
Control 15/sync: Parent(2)==NULL

(ossxmix:20565): Gtk-CRITICAL **: gtk_box_pack_start: assertion `GTK_IS_BOX (box)' failed
Control 16/src: Parent(2)==NULL

(ossxmix:20565): Gtk-CRITICAL **: gtk_box_pack_start: assertion `GTK_IS_BOX (box)' failed
Control 17/ratelock: Parent(2)==NULL

(ossxmix:20565): Gtk-CRITICAL **: gtk_box_pack_start: assertion `GTK_IS_BOX (box)' failed
Control 18/actrate: Parent(2)==NULL

(ossxmix:20565): Gtk-CRITICAL **: gtk_box_pack_start: assertion `GTK_IS_BOX (box)' failed

```
And the options don't appear in ossxmix (screenshot):

---

### Post by dawynn on 2008-06-03
A few notes:

Zsnes in Hardy.  zsnes -ad 'oss' does not work.  Oh, zsnes still runs, but without sound.  zsnes -ad 'esd' is no better.  However, the following command worked for me:
zsnes -ad 'sdl'
The sound seemed slightly sluggish, but it did work.

*Edit: Above comment refers to zsnes from Ubuntu repositories.  I assume that zsnes downloaded from the official website and recompiled from source does not have restrictions that block out support for oss and esd.*

Other problems.  If you can't get the blacklist command to work, do what I did: look at the intent of the command and do it yourself.  Look in /lib/linux-sound-base/.  (Not at my Linux box right now, so I'm going off of memory)  The filename is not noALSAmodprobe.conf, but that's close enough.  Do an 'ls' command to see the real filename.  Open up that file, copy everything in there.  Now, open up /etc/modprobe.d/blacklist in sudo mode and paste everything at the end.  Suggestion: Add a comment prior to pasting so, if you want to back out your changes, you can.

Finally -- I tried OSS.  I really did.  To me, sounds sounded crisper than with ALSA.  I was ready to keep using OSS.  Then things started fighting me.  pSX (Playstation emulator) must have ALSA in order to run.  Now, there are adaptors so that oss-only programs can be run through ALSA, but the opposite does not exist yet.  One is in development, but may be scratched.  And since OSS had been marked deprecated for so long, there are several programs that really believed it to be dead and gone.  Meaning: no support for these programs under an OSS-only system.  Not good.

Then Audacity went flaky.  It kept working even after a few restarts, then finally started failing.  Turns out OSS does not always restore everything correctly after a restart.  The user must continue to check after each restart that OSS actually started.  Well, that kinda sucks.

That's when I found this.  Use your best judgement:
[http://cinnamonpirate.com/blog/480/](http://cinnamonpirate.com/blog/480/)

End result: If ALSA works with your card, you're best off sticking with ALSA as long as you're using Ubuntu.  If need be, switch to the ubuntu-studio kernel for lower latency.  But OSS still is not the best solution for general use.

In order to change back to ALSA -- undo what you did.  Reinstall ubuntu-desktop.  Strip off every package that supports oss and esound/esd.  Switch to ALSA or Pulseaudio modules to replace these.  (Keep alsa-oss and oss-compat)  (esd would not be so bad since it can work with ALSA.  If using Kubuntu -- arts is acceptable.  But -- as noted in the blog I listed -- esd and arts only support gnome and KDE respectively.  ALSA / pulseaudio supports the whole system)  dpkg-reconfigure your Linux sound again (see the original guide) only this time -- choose ALSA, and manually change any system or program-specific settings back to ALSA or Pulseaudio (or ARTS / esd if you wish).  May have to reboot after reinstalling ALSA, but make sure to strip oss-linux package off of your system.

Cheers!

---

### Post by sleepydada on 2008-06-04
I want help!!!


I am Chinese not very good at English..

I have no sound in Ubuntu 8.04 on Asus z99.

It uses nVidia Corporation MCP67 High Definition Audio (rev a1) 
ALC660-VD..

I want to clean ALSA  completely.

AND use OSS4.

so what I should do...

---

### Post by sleepydada on 2008-06-04
sleep@sleep-laptop:~/&#26700;&#38754;$ sudo dpkg -i oss-linux_v4.0-1015_amd64.deb
&#36873;&#20013;&#20102;&#26366;&#34987;&#21462;&#28040;&#36873;&#25321;&#30340;&#36719;&#20214;&#21253; oss-linux&#12290;
(&#27491;&#22312;&#35835;&#21462;&#25968;&#25454;&#24211; ... &#31995;&#32479;&#24403;&#21069;&#24635;&#20849;&#23433;&#35013;&#26377; 122674 &#20010;&#25991;&#20214;&#21644;&#30446;&#24405;&#12290;)
&#27491;&#22312;&#35299;&#21387;&#32553; oss-linux (&#20174; oss-linux_v4.0-1015_amd64.deb) ...
&#27491;&#22312;&#35774;&#32622; oss-linux (v4.0-1015) ...
Building OSS Modules for Linux-unknown 2.6.24-17-generic

OSS build environment set up for REGPARM kernels

Building module osscore
Building module ali5455
Building module allegro
Building module als300
Building module als4000
Building module apci97
Building module atiaudio
Building module audigyls
Building module audioloop
Building module audiopci
Building module cmi8788
Building module cmpci
Building module cs4280
Building module cs4281
Building module digi32
Building module digi96
Building module emu10k1x
Building module envy24
Building module envy24ht
Building module fm801
Building module geode
Building module hdaudio
Building module hdsp
Building module ich
Building module imux
Building module lynxone
Building module lynxtwo
Building module maestro
Building module neomagic
Building module ossusb
Building module riptide
Building module s3vibes
Building module sblive
Building module sbxfi
Building module softoss
Building module solo
Building module sonorus
Building module trident
Building module via8233
Building module via97
Building module vmix
Building module vortex
Building module ymf7xx
depmod -a
-----------------------------
Detected Nvidia High Definition Audio (MCP67)
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture
-----------------------------

Starting Open Sound System
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
Failed to disable conflicting sound drivers
Reboot and try running soundon again

Also check that you have not compiled sound support statically
into the kernel.

---

### Post by sleepydada on 2008-06-04
I used the blacklist,but maybe it is not work...

how can I rmmod snd?

> sleep@sleep-laptop:~/oss41build$ lsmod
Module                  Size  Used by
ipv6                  311720  10 
af_packet              27272  2 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
powernow_k8            16608  1 
cpufreq_powersave       3200  0 
cpufreq_userspace       6180  0 
cpufreq_stats           8416  0 
cpufreq_conservative    10632  0 
cpufreq_ondemand       11152  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
container               6656  0 
dock                   12960  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
ath_pci               107824  0 
nvidia               8858052  36 
wlan                  227104  1 ath_pci
i2c_core               28544  1 nvidia
ath_hal               219888  1 ath_pci
evdev                  14976  7 
video                  23444  0 
output                  5632  1 video
battery                16776  0 
ac                      8328  0 
serio_raw               9092  0 
sdhci                  21508  0 
ricoh_mmc               5120  0 
psmouse                46236  0 
mmc_core               59272  1 sdhci
asus_laptop            22492  0 
snd_hda_intel         440408  1 
led_class               7176  1 asus_laptop
button                 10912  0 
snd_pcm                92168  1 snd_hda_intel
snd_timer              27912  1 snd_pcm
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd                    70856  6 snd_hda_intel,snd_pcm,snd_timer,snd_hwdep
soundcore              10400  1 snd
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
k8temp                  7680  0 
pcspkr                  4992  0 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
loop                   21508  2 
sd_mod                 33280  2 
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
ahci                   33028  1 
usbhid                 35168  0 
hid                    44992  1 usbhid
ata_generic             9988  0 
pata_amd               16772  0 
ohci1394               36532  0 
forcedeth              55564  0 
ieee1394              106968  2 sbp2,ohci1394
pata_acpi               9856  0 
libata                176304  4 ahci,ata_generic,pata_amd,pata_acpi
scsi_mod              178488  5 sbp2,sd_mod,sg,sr_mod,libata
ehci_hcd               41996  0 
ohci_hcd               27524  0 
usbcore               169904  4 usbhid,ehci_hcd,ohci_hcd
thermal                19744  0 
processor              41448  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  5 


---

### Post by sleepydada on 2008-06-04
Thank you very much !!!!!!

Finally, I heard sound....

I found the problem is in the file "/lib/linux-sound-base/noALSA.modprobe.conf"

```

...
blacklist snd-gus-lib
blacklist snd-gusmax
blacklist snd-gus-synth
blacklist snd-harmony
blacklist snd-hdaintel------should be change-->blacklist snd-hda-intel
blacklist snd-hdsp
blacklist snd-hdspm
blacklist snd-hwdep
blacklist snd-i2c
...

```


thank you..

---

### Post by Yellow Pasque on 2008-06-04
Yes, they keep changing the module names. My apologies, but I've been very busy over the past few days:
```
blacklist snd_hda_intel 
blacklist snd_mixer_oss 
blacklist snd_pcm
blacklist snd_timer
blacklist snd_page_alloc
blacklist snd_hwdep
blacklist snd
blacklist soundcore
```

---

### Post by Draylorre on 2008-06-04
Main reason I went to OSS is because I was sittin' there, playing music, adjusted the sound via the audio panel and the ALSA drivers just crapped out. Dunno how or why, but whatever. 

Also, one major problem for the original poster before I begin

```
sudo chmod 774 /etc/modprobe.d/blacklist
sudo cat /lib/linux-sound-base/noALSAmodprobe.conf >> /etc/modprobe.d/blacklist
```

Change that to ```
"noALSA.modprobe.conf"[/QUOTE] instead of [QUOTE]"noALSAmodprobe.conf"
```

I'm using an ASUS Xonar D2. Installed everything, had to log off and log back on because soundon didn't initialize when I did the package, but sound is now on when I boot up. First problem: No sound.

ossdetect -v
```
Detected CMedia CMI8788
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture
```


ossinfo
```
Version info: OSS 4.0 (b1015/200803240256) (0x00040003) 
Platform: Linux/i686 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 (SHELL)

Number of audio devices:	3
Number of audio engines:	12
Number of mixer devices:	3


Device objects
 0: osscore0 OSS core services
 1: cmi87880 CMedia CMI8788 interrupts=1031607 (1031609)
 2: ossusb0 USB audio core services
 3: usb05560001-0 USB sound device
 4: usb05560001-1 USB sound device
 5: vmix0 OSS transparent virtual mixer


Mixer devices
 0: CMedia CMI8788 (Mixer 0 of device object 1)
 1: AC97 Input Mixer (CMI9780) (Mixer 1 of device object 1)
 2: USB sound device (Mixer 0 of device object 3)

Audio devices
CMedia CMI8788 (MultiChannel)     /dev/oss/cmi87880/pcm0  (device index 0)
CMedia CMI8788 (SPDIF)            /dev/oss/cmi87880/pcm1  (device index 1)
USB sound device rec              /dev/oss/usb05560001-1/pcmin0  (device index 2)
```

Please ignore this post and see my newest post later in this thread.

---

### Post by pkeno666 on 2008-06-05
> **Temüjin said:**
> [SIZE="4"]Installing OSS 4.0 From a .deb package[/SIZE]

Check to see if your device is supported by OSS:
The official and outdated list can be found at [http://manuals.opensound.com/devlists/Linux.html](http://manuals.opensound.com/devlists/Linux.html)
(Ignore the old references to retail drivers; it's all free now)
I've also attached the device list from the latest build (4.0-1015) so double-check that if you don't see your card on the site's list.

Go here:[http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)
Get the Linux 2.6 DEB package for your architecture (use x86 unless you have the amd64 Ubuntu) and save it to your home folder (i.e. the ~/ directory)

0. Get necessary packages
```
sudo apt-get install gcc gcc-4.2 gcc-4.2-base make build-essential binutils linux-headers-`uname -r` libssl-dev libssl0.9.8 
```
1. If you want the ability to hear system sounds, install ESD (Enlightened Sound Daemon) with the commands below. Note that this will remove libesd-alsa0 if installed. Remember to reinstall that package if you ever switch back to ALSA for some reason.
```
sudo apt-get install esound esound-clients esound-common libesd0 libesd0-dev gstreamer0.10-esd
```
2. Blacklist ALSA modules
```
sudo chmod 774 /etc/modprobe.d/blacklist
sudo cat /lib/linux-sound-base/noALSAmodprobe.conf >> /etc/modprobe.d/blacklist
```
3. Configure linux-sound-base package (sudo apt-get install linux-sound-base if it is not already)
```
sudo dpkg-reconfigure linux-sound-base
```
Press [Enter] to say OK and use the down-arrow to select 'OSS' on the next menu. Press the Tab key and [Enter] to say OK, and you'll be back at the terminal.
4. Restart the system
5. (Optional) Remove ALSA. This may cause the package manager to ask to remove a lot of critical packages, depending on whether you've done a clean install or upgraded from a previous Ubuntu release. If so, press 'N' and go to step 6. I am not sure about the ubuntu-desktop package. I have removed it and haven't had any issues, even when I upgraded from Gutsy 7.10. If  you are unsure about removing that package or any others, skip this step:
```
sudo apt-get remove alsa-base alsa-oss oss-compat
```
6. Navigate to where you have the deb file saved (e.g. if it's your home dir, cd ~/ ). Note the name of the file will be oss-linux_v4.0-1015_amd64.deb if you downloaded that version
```
sudo dpkg -i oss-linux_v4.0-1015_i386.deb
sudo soundon
```
7. Add a new custom application launcher to the panel that runs the command: ossxmix - That's oss**x**mix, not ossmix, Name the launcher whatever you want and pick an icon. I named mine "Mixer" and chose /usr/share/icons/gnome/32x32/status/stock_volume-med.png as my icon.
8. You'll have to tell applications to use the OSS output plugin instead of ALSA. Some applications (like Audacious) have user-friendly controls for this. Others require command line input or configuring a text file. See: [http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4)

If you're still not getting sound, see what the ossdetect -v and ossinfo commands give you.

**ADDENDUM: Volume Control Patch** The current gstreamer-based volume control in GNOME is incompatible with OSSv4, meaning your mouse wheel and media buttons won't work. To remedy the issue, try Clive Wright's [patch](http://4front-tech.com/forum/viewtopic.php?t=2357&highlight=). I've also built and attached an AMD64 version to this post. 
Also, if you'd prefer to map commands to your shortcut keys, [here are some scripts to use](http://wiki.archlinux.org/index.php/OSS) (at the bottom of the page).

**ADDENDUM2: Sound in Flash**
1. Run:
```
file /usr/lib/libflashsupport.so
```
If this returns info on the file, skip ahead to step 4. If the file isn't found...
2. Save the attached libflashsupport.so.gz to your Desktop
3. ```
cd ~/Desktop; gunzip libflashsupport.so.gz; sudo mv libflashsupport.so /usr/lib
```
4. create symbolic links to /usr/lib/firefox/plugins & /usr/lib/mozilla/plugins:
```
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins; sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
```

**ADDENDUM3: Recovering From a Failed .deb Install**
[http://ubuntuforums.org/showpost.php?p=5055305&postcount=105](http://ubuntuforums.org/showpost.php?p=5055305&postcount=105)

Thanks for the info. My Sound Blaster XFI is now working :guitar::guitar:

---

### Post by endor43 on 2008-06-05
ive done everything, changed the noALSA.modprobe.conf
and all the new module names, followed directions step by step, but it is not working, when it comes time to sudo dpkg -i oss-linux_v4.0-1015_i386.deb, it gives me an error and then erases everything in my /usr/lib/oss folder, which explains why it cant find the stuff its looking for but why does it do that in the first place? (i made a copy of the oss folder before it was deleted because ive formated like twice to get this thing to work, so i can paste it back if i need) the oss4 isnt working and i dont know why, ive tried all i know, i have a creative sb x-fi xtremegamer and as of now because of that error its not working

please help

error:

```
thomas@thomas-computer:~/Desktop$ sudo dpkg -i oss-linux_v4.0-1015_i386.deb
(Reading database ... 116855 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1015 (using oss-linux_v4.0-1015_i386.deb) ...
OSS not loaded.
Unpacking replacement oss-linux ...
Setting up oss-linux (v4.0-1015) ...
Building OSS Modules for Linux-unknown 2.6.24-18-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

---

### Post by Draylorre on 2008-06-05
So, I have an ASUS Xonar D2, and after trolling the other forums, I found that the Xonar isn't fully compatible with OSS. I found a thread where someone was able to get it working, however, after following the patching instructions and rebuilding the code several times (I was up until 5 AM doing this, although it was tons of fun for me :) ) I still couldn't get this to work.

If you have an ASUS Xonar D2, please check this thread located here. 

[http://www.4front-tech.com/forum/viewtopic.php?t=2666&postdays=0&postorder=asc&highlight=cmi8788&start=0](http://www.4front-tech.com/forum/viewtopic.php?t=2666&postdays=0&postorder=asc&highlight=cmi8788&start=0)

You may be able to get it work, but I'd recommend sticking with ALSA if you can wait for full OSS compatibility. :)


BTW, great thread and instructions. I found it pretty easy to follow despite the few spelling and typing errors. I'll definitely be looking to try OSS out again later in time, if not for the sole purpose of curiosity and breaking my Linux install. :twisted:

---

### Post by endor43 on 2008-06-05
> **endor43 said:**
> ive done everything, changed the noALSA.modprobe.conf
and all the new module names, followed directions step by step, but it is not working, when it comes time to sudo dpkg -i oss-linux_v4.0-1015_i386.deb, it gives me an error and then erases everything in my /usr/lib/oss folder, which explains why it cant find the stuff its looking for but why does it do that in the first place? (i made a copy of the oss folder before it was deleted because ive formated like twice to get this thing to work, so i can paste it back if i need) the oss4 isnt working and i dont know why, ive tried all i know, i have a creative sb x-fi xtremegamer and as of now because of that error its not working

please help

error:

```
thomas@thomas-computer:~/Desktop$ sudo dpkg -i oss-linux_v4.0-1015_i386.deb
(Reading database ... 116855 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1015 (using oss-linux_v4.0-1015_i386.deb) ...
OSS not loaded.
Unpacking replacement oss-linux ...
Setting up oss-linux (v4.0-1015) ...
Building OSS Modules for Linux-unknown 2.6.24-18-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

i dont have an ASUS Xonar D2 and switching to ALSA for my x-fi makes my computer crash on boot to ubuntu, i know this works because pkeno666 got it to work, i really need help, this is all thats keeping me from using ubuntu and why im still stuck on windows.

---

### Post by OpposingForce on 2008-06-06
What exactly does black listing the ALSA modules do?  It wouldn't let me do it anyway, said permission denied, and yes I used the chmod command that was posted on the guide.  Anyway I continued without it and it still works.  However the gstreamer patch you attached doesn't seem to have done anything though.  Gnome sound applet still says

"No volume control GStreamer plugins and/or devices found."

which was the same as before I installed the patch.

---

### Post by endor43 on 2008-06-06
> **OpposingForce said:**
> What exactly does black listing the ALSA modules do?  It wouldn't let me do it anyway, said permission denied, and yes I used the chmod command that was posted on the guide.  Anyway I continued without it and it still works.  However the gstreamer patch you attached doesn't seem to have done anything though.  Gnome sound applet still says

"No volume control GStreamer plugins and/or devices found."

which was the same as before I installed the patch.

you need to cd to the directory where this is ( i think /lib/linux-sound-base) and then
 
chmod a+rwx noALSA.modprobe.conf

to get the permission and make sure the blacklist says noALSA.modprobe.conf with a dot before modprobe.

---

### Post by Yellow Pasque on 2008-06-06
ALSA has released 1.0.17-rc1 today with no update to the X-fi drivers. I'm sure there are numerous updates to the hda-intel driver.
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24) for scripts to install the latest ALSA driver

---

### Post by OpposingForce on 2008-06-06
Guys not sure what's up, but I just did a clean install of Ubuntu because I just got a new 750 gb hard drive and replaced the old small one.  I installed all my stuff again and followed this tutorial and everything is working perfectly.  And OSS appears in the gnome sound applet.  Exaile plays sound, totem doesn't crash on startup.  Chocolate doom (a linux port of doom) plays midi without having to install timidity). I don't know what happened.  but it works.

---

### Post by rv65 on 2008-06-07
So far I got the OSS4 driver to work. My big problem is the G-streamer integration. I use the AMD64 version on this Core2 Quad machine.  

```
michael@michael-desktop:~/Desktop/stuff$ sudo gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
gzip: /usr/lib/gstreamer-0.10/libgstossaudio.so: No such file or directory
michael@michael-desktop:~/Desktop/stuff$ mv libgstossaudio.so /usr/lib/gstreamer-0.10/
mv: cannot stat `libgstossaudio.so': No such file or directory

```

I basically get this when I try to install it. Any responses that help fix this problem would be great.

---

### Post by goofeyfoot on 2008-06-07
> **goofeyfoot said:**
> I know it sounds stupid but I cannot get this blacklist thing to work.

Here is what I get.

 sudo cat /lib/linux-sound-base/noALSAmodprobe.conf >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
michael@michael-desktop:~$ 

And here is an error I get with another command.

michael@michael-desktop:~$ sudo dpkg -i oss-linux_v4.0-1015_i386.deb
[sudo] password for michael:
(Reading database ... 129033 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1015 (using oss-linux_v4.0-1015_i386.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux_v4.0-1015_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux_v4.0-1015_i386.deb
michael@michael-desktop:~$ 



Will someone please look at this and tell me what is wrong?

Thanks.

Michael

Does anyone have a solution for my problem which I posted last week?

I guess I am again going to have to blow out the whole system just for this one stupid problem.

Is there a way to clean up an install without starting all over again?  Seems like kind of a waste just for sound.

Thanks.

Michael

---

### Post by Rhapsody on 2008-06-07
Well, I've just followed the instructions now to the best of my ability, and it hasn't worked. No sound whatsoever.

OSS definitely seems to be installed. sudo soundon results in "OSS is already loaded.", my sound system in the KDE System Settings is "Open Sound System", Amarok is also set to "oss", ALSA has been removed, ossxmix seems to be properly configured, but nothing produces any sound.

Not that I didn't expect this. It's now been over 18 months since I've had a fully working sound system, and I'm slowly starting to think that I will never have one ever again. Linux developers apparently hate sound of all kinds.

---

### Post by endor43 on 2008-06-07
> **goofeyfoot said:**
> Does anyone have a solution for my problem which I posted last week?

I guess I am again going to have to blow out the whole system just for this one stupid problem.

Is there a way to clean up an install without starting all over again?  Seems like kind of a waste just for sound.

Thanks.

Michael

hey, im having the same problem as your second one and i really would like to know how to fix it too, i posted the solution to your permission denied problem on POST 143, but i really would like oss to work so if anyone could help me and michael out that'd be great.

thanks

---

### Post by Cubby on 2008-06-09
> **Temüjin said:**
> [SIZE="4"]

0. Get necessary packages
```
sudo apt-get install gcc gcc-4.2 gcc-4.2-base make build-essential binutils linux-headers-`uname -r` libssl-dev libssl0.9.8 
```


Thanks for the great guide! It  helped me get my CMI 8788 chipset 'Oxygen' card to output sound in LINUX Mint KDE Daryna.

I'm newbie at this sort of thing, so bear with me about my ignorance.  
When one is doing the step 0. getting necessary packages, the one where you 'apt-get linux-headers- `uname -r`' has me stumped.  Am I replacing my current kernel by doing this.  
Today I reinstalled Mint KDE Daryna and synaptic shows the following in the list:
linux-generic not installed
linux-headers-2.5.22.14 upgradeable
linux-headers-2.5.22.14-386 not installed
linux-headers-2.5.22.14-generic upgradeable
linux-headers-386 not installed

so,  I don't need to do apt-get linux-header (my version) as it's already installed, correct? Or do I need to install one of those in the above list that's not installed?  

I only say this, as when I successfully installed OSS4 for my previous Mint KDE installation, when I did this command I had this output:

cat /usr/src/linux-headers-2.6.22-14-generic/include/linux/utsrelease.h 
 #define UTS_RELEASE "2.6.22.9"
  
that should have read:

cat /usr/src/linux-headers-2.6.22-14-generic/include/linux/utsrelease.h
#define UTS_RELEASE "2.6.22-14-generic"

eventually seawright's help showed how reinstall the header files.  I'm not sure how my headers became corrupt.  In my previous installation I did do a major recommended software package updates a few days before attempting to install oss4.  
I'm just not sure if I have to do apt-get linux-headers as the one I need is already installed.  I did it the last time and not sure if I needed to and if it caused any corrupt headers.

Right now, with my reinstallation of Linux Mint KDE, when I do the cat command, I get the correct output:
cat /usr/src/linux-headers-2.6.22-14-generic/include/linux/utsrelease.h
#define UTS_RELEASE "2.6.22-14-generic"

Thanks to anyone with an answer!

---

### Post by Yellow Pasque on 2008-06-09
I have revised the guide (specifically, the blacklisting procedure). Enjoy :popcorn:

---

### Post by OpposingForce on 2008-06-09
Hey again just installed Swfdec flash player (I can't use the adobe flash player because it crashes too much, like half of all flash content the page loads crashes the browser randomly).  The video plays but I don't get sound.  I ran firefox through the terminal and noticed it was trying to load ALSA for some reason instead of OSS, even though OSS is selected in the gnome sound menu for everything.  Here's the console output

```
cory@cory-desktop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Unsupported movie property allowscriptaccess with value "always"
Unsupported movie property wmode with value "transparent"
unhandled event 19
Loading stream: http://www.youtube.com/swf/watch.swf?video_id=rOFGvaXeaJc&t=OEgsToPDskJjemsfxW6EPwY2kTZ8tVGI&l=211&hl=en
Unsupported movie property style with value ""
Unsupported movie property id with value "movie_player"
Unsupported movie property name with value "movie_player"
Unsupported movie property quality with value "high"
Unsupported movie property allowfullscreen with value "true"
Unsupported movie property allowscriptaccess with value "always"
unhandled event 19
Unsupported movie property style with value ""
Unsupported movie property id with value "checker"
Unsupported movie property name with value "checker"
Unsupported movie property quality with value "high"
Loading stream: http://s.ytimg.com/yt/swf/watch-vfl42309.swf
Loading stream: http://www.youtube.com/version-check.swf
Loading stream: http://ash-v259.ash.youtube.com/get_video?video_id=vwSiDUKJd0o&signature=A06A13D9ED0E85470C4D9A8C5AB31F12BECB7C2D.1A9B08FE99B11185ED778CE42E8F74EB298CED9D&ip=98.15.197.13&ipbits=16&expire=1213077945&key=yt1&sver=2
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
Failed to open sound device: No such file or directory
Loading stream: http://video-stats.video.google.com/s?ns=yt&plid=AARPRLASvOn4JWjFAAAAoAAQAAA&sourceid=y&sdetail=p%3A%2Fuser%2FLaddil&vid=R7jWVWcfHWbcWp5H09AH1AtoFPDkCtUaR&docid=vwSiDUKJd0o&el=detailpage&bc=134756&rt=1.6&st=0.133&fv=WIN%209%2C0%2C100%2C0&et=0.133&len=168.438

```

I googled all over the place and can't figure out how to setup swfdec with OSS, or OSS4.  Alsa is also blacklisted like in the tutorial.  If anyone can help thanks

---

### Post by anthony2010 on 2008-06-09
Hi.
Im so new to this I just copy and paste anything in desperation to get my sound back! 

Mine is an nvidia on board sound card. Since an update about 3 weeks ago all my sound has gone. I tried everything above and converted to this alternative format. Unfortunately the only difference is where before I had no sound, I now get a message telling me I have no sound!!!(and still no sound)

I love the learning curve but Im truly stuck on this one. Any ideas?

Ant.

---

### Post by Cubby on 2008-06-10
> **Cubby said:**
>   
When one is doing the step 0. getting necessary packages, the one where you 'apt-get linux-headers- `uname -r`' has me stumped.  Am I replacing my current kernel by doing this?  
Today I reinstalled Mint KDE Daryna and synaptic shows the following in the list:
linux-generic not installed
linux-headers-2.5.22.14 upgradeable
linux-headers-2.5.22.14-386 not installed
linux-headers-2.5.22.14-generic upgradeable
linux-headers-386 not installed

so,  I don't need to do apt-get linux-header (my version) as it's already installed, correct? Or do I need to install one of those in the above list that's not installed?  


Still curious.  I could go ahead and do the command, because I'm newbie at this.  I'm just assuming the package is already installed because of what synaptic has in list (4th entry) as already installed.   Just trying to avoid any corruption of kernel header.  I don't know what I did in previous installation that corrupted my header.  Trying to understand just what doing a apt-get install linux-header (uname -r) entails.  Sounds major.

Thanks again for listing to me nag once more.

Lisa

---

### Post by janfsd on 2008-06-10
Cubby, that command should install the headers of the kernel currently being used. You can try just uname -r and you will get the version of kernel. If you have the headers already installed, nothing will happen. You can have several versions without problems. Btw, I think is better to install linux-headers-generic, with that when a new kernel goes out, newer headers will be installed.


Temüjin what about making some ppa repos of oss4? It would easier for a lot of people, and maybe someday it will be included in Ubuntu. That for sure will increase the interest in oss4, since there isn't plans to push it into the kernel.

---

### Post by Cubby on 2008-06-10
> **anthony2010 said:**
> 
Since an update about 3 weeks ago all my sound has gone. 


Hi Anthony, 

I can't help you with this, but I asked at the OSS4 forum about the issue of "recommended software updates" via one's software manager - which ones should one avoid after installing OSS?  I would assume ALSA, of course.  The general answer was none to worry about.
Many folks lose sound after doing major updates even when using ALSA.  Doing some of the following commands could help with their output given here.
If you still have ALSA installed, then maybe this guide will help, as some of the commands are specific to ALSA:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Here are some oss terminal commands I've been using a lot lately.  The blind leading the blind "wink".  You might check with the OSS4 forum, 4Front Technologies.
in terminal:
ossmix
and
ossinfo
and 
ossinfo -v3

---

### Post by janfsd on 2008-06-10
Yes, I lose sound too for instance when upgrading the kernel, it seems that the alsa modules are loaded again, and oss can't load. Easy fix in my case:
```
sudo rmmod saa7134-alsa
```
I suppose I could blacklist that module...

> **anthony2010 said:**
> Hi.
Im so new to this I just copy and paste anything in desperation to get my sound back! 

Mine is an nvidia on board sound card. Since an update about 3 weeks ago all my sound has gone. I tried everything above and converted to this alternative format. Unfortunately the only difference is where before I had no sound, I now get a message telling me I have no sound!!!(and still no sound)

I love the learning curve but Im truly stuck on this one. Any ideas?

Ant.
Try in terminal
```
sudo soundon
```
And paste the output here.

---

### Post by janfsd on 2008-06-10
> **OpposingForce said:**
> Hey again just installed Swfdec flash player (I can't use the adobe flash player because it crashes too much, like half of all flash content the page loads crashes the browser randomly).  The video plays but I don't get sound.  I ran firefox through the terminal and noticed it was trying to load ALSA for some reason instead of OSS, even though OSS is selected in the gnome sound menu for everything.  Here's the console output

```
cory@cory-desktop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Unsupported movie property allowscriptaccess with value "always"
Unsupported movie property wmode with value "transparent"
unhandled event 19
Loading stream: http://www.youtube.com/swf/watch.swf?video_id=rOFGvaXeaJc&t=OEgsToPDskJjemsfxW6EPwY2kTZ8tVGI&l=211&hl=en
Unsupported movie property style with value ""
Unsupported movie property id with value "movie_player"
Unsupported movie property name with value "movie_player"
Unsupported movie property quality with value "high"
Unsupported movie property allowfullscreen with value "true"
Unsupported movie property allowscriptaccess with value "always"
unhandled event 19
Unsupported movie property style with value ""
Unsupported movie property id with value "checker"
Unsupported movie property name with value "checker"
Unsupported movie property quality with value "high"
Loading stream: http://s.ytimg.com/yt/swf/watch-vfl42309.swf
Loading stream: http://www.youtube.com/version-check.swf
Loading stream: http://ash-v259.ash.youtube.com/get_video?video_id=vwSiDUKJd0o&signature=A06A13D9ED0E85470C4D9A8C5AB31F12BECB7C2D.1A9B08FE99B11185ED778CE42E8F74EB298CED9D&ip=98.15.197.13&ipbits=16&expire=1213077945&key=yt1&sver=2
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
Failed to open sound device: No such file or directory
Loading stream: http://video-stats.video.google.com/s?ns=yt&plid=AARPRLASvOn4JWjFAAAAoAAQAAA&sourceid=y&sdetail=p%3A%2Fuser%2FLaddil&vid=R7jWVWcfHWbcWp5H09AH1AtoFPDkCtUaR&docid=vwSiDUKJd0o&el=detailpage&bc=134756&rt=1.6&st=0.133&fv=WIN%209%2C0%2C100%2C0&et=0.133&len=168.438

```

I googled all over the place and can't figure out how to setup swfdec with OSS, or OSS4.  Alsa is also blacklisted like in the tutorial.  If anyone can help thanks

I don't know about swfdec, but you could try flash 10 beta. It doesn't crash for me.  
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

Also, there is some kind of patch for libflashsupport for flash 9, I remember seeing something like that in launchpad...

Or you could try gnash.

---

### Post by Cubby on 2008-06-10
Thank you, janfsd!

I went ahead with installation, and the only step I skipped this second time was the one where you remove alsa-base.  Since it's a new install of LINUX Mint KDE, it didn't have the other alsa stuff installed. The reason I skipped this is it said it needed to remove ubuntu minimal, so I decided to avoid it.  
I did 
osstest
in terminal and boy, sounds great with my cmi8788 card.  

I know this how to guide is written mainly for those that have gnome desktop.  What I notice is that in both installs,  I no longer had the kmix icon in the kicker panel.  And, when I went to KDE>All Applications>System Settings>Sound & Multimedia> when I click on Sound System it wouldn't bring up it that menu.

cesium at oss4 forum said to do in terminal:
kcmshell arts
and this brought up this missing menu via terminal.   Now I just have to figure out how to get this broken path fixed, otherwise I can use terminal command to bring it up, no problem.  In Sound System, sound was set to open sound system.

This was readout in xsessions
```
startkde: Starting up...
startkde: kpersonalizer not found! Please install to properly configure your user.
kbuildsycoca running...
Reusing existing ksycoca
Could not open library kmixctrl.la: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
kmixctrl: relocation error: /usr/lib/libkdeinit_kmixctrl.so: symbol snd_mixer_free, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
Could not open library kmix.la: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

Xsession: X session started for fonk76wink3l at Tue Jun 10 11:59:28 CDT 2008
startkde: Starting up...
startkde: kpersonalizer not found! Please install to properly configure your user.
kbuildsycoca running...
Reusing existing ksycoca
Could not open library kmixctrl.la: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
kmixctrl: relocation error: /usr/lib/libkdeinit_kmixctrl.so: symbol snd_mixer_free, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
Could not open library kmix.la: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf


********************   WARNING   *******************************
Warning! kmix uses ALSA emulation instead of the native OSS API
****************************************************************

kmix: relocation error: /usr/lib/libkdeinit_kmix.so: symbol snd_mixer_free, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
DCOP aborting (delayed) call from 'anonymous-5574' to 'kmix'
ERROR: Communication problem with kmix, it probably crashed.
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libjavaplugin.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libjavaplugin.so: undefined symbol: NP_GetMIMEDescription
Ignored duplicate item: KWiFiManager
Ignored duplicate item: Dictionary
Ignored duplicate item: KArm
Ignored duplicate item: Windows Wireless Drivers
Ignored duplicate item: mintInstall
Ignored duplicate item: mintAssistant
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: NP_GetMIMEDescription
kdecore (KProcess): WARNING: _attachPty() 13
Could not open library '/usr/lib/kde3/knotify.la'.
/usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
kbuildsycoca running...
Reusing existing ksycoca
Could not open library '/usr/lib/kde3/knotify.la'.
/usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
--11:59:47--  http://www.linuxmint.com/repository/rules
           => `rules'
Resolving www.linuxmint.com... failed: Name or service not known.
kbuildsycoca running...
Reusing existing ksycoca
kmenuedit: WARNING: Could not read /home/fonk76wink3l/.config/menus/applications-kmenuedit.menu
kbuildsycoca running...
Reusing existing ksycoca
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x260047f
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
Could not open library '/usr/lib/kde3/knotify.la'.
/usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
kwin: X_SetInputFocus(0x2600065): BadMatch (invalid parameter attributes)
kdecore (KProcess): WARNING: _attachPty() 11
Could not open library '/usr/lib/kde3/knotify.la'.
/usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
Opener: received SetSecret
Opener: received OpenLock

Opener: received OpenDevice
Opener: received ExecPPPDaemon
Kernel supports ppp alright.
In parent: pppd pid 5672
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Opener: received OpenResolv
Opener: received RemoveSecret
Opener: received RemoveSecret
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00065
konsole: WARNING: Unable to use /usr/share/apps/konsole/sumc.desktop
konsole: WARNING: Unable to use /usr/share/apps/konsole/mc.desktop
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00065
Could not open library '/usr/lib/kde3/knotify.la'.
/usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2600065
Launched ok, pid = 5975
konqueror: WARNING: Profile Loading Error: No orientation specified in Container0
Launched ok, pid = 5982
konqueror: WARNING: Profile Loading Error: No orientation specified in Container0
Invalid entry (missing '=') at /etc/kde/share/apps/konqueror/servicemenus/konsolehere.desktop:80
```

I was able to bring back the kmix icon in kicker (which, by the way shows the correct mixer:cmedia cmi8788 ) by pre-loading the old lib as user according to this fellows suggestion for kmix:
[http://ubuntuforums.org/archive/index.php/t-575521.html](http://ubuntuforums.org/archive/index.php/t-575521.html)
edited to add that this needs to be done again upon restarting computer, unless there's a way to force it.  I don't need kmix as I can use ossxmix.

---

### Post by endor43 on 2008-06-10
> **Temüjin said:**
> [SIZE="4"]Installing OSS 4.0 From a .deb package[/SIZE]


"4. Restart the system"


is this restart the computer or restart oss and if it is restart oss how should i do that?

thanks

---

### Post by Cubby on 2008-06-10
endore43, it's restart your computer for that step in the procedure.

To restart OSS, you do as root in terminal:
soundoff

then as root in terminal:

soundon

but, for that installation step you restart your computer.

---

### Post by janfsd on 2008-06-10
> **Cubby said:**
> Thank you, janfsd!

I went ahead with installation, and the only step I skipped this second time was the one where you remove alsa-base.  Since it's a new install of LINUX Mint KDE, it didn't have the other alsa stuff installed. The reason I skipped this is it said it needed to remove ubuntu minimal, so I decided to avoid it.  
I did 
osstest
in terminal and boy, sounds great with my cmi8788 card.  

I know this how to guide is written mainly for those that have gnome desktop.  What I notice is that in both installs,  I no longer had the kmix icon in the kicker panel.  And, when I went to KDE>All Applications>System Settings>Sound & Multimedia> when I click on Sound System it wouldn't bring up it that menu.

cesium at oss4 forum said to do in terminal:
kcmshell arts
and this brought up this missing menu via terminal.   Now I just have to figure out how to get this broken path fixed, otherwise I can use terminal command to bring it up, no problem.  In Sound System, sound was set to open sound system.

This was readout in xsessions
```
startkde: Starting up...
startkde: kpersonalizer not found! Please install to properly configure your user.
kbuildsycoca running...
Reusing existing ksycoca
Could not open library kmixctrl.la: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
kmixctrl: relocation error: /usr/lib/libkdeinit_kmixctrl.so: symbol snd_mixer_free, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
Could not open library kmix.la: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

Xsession: X session started for fonk76wink3l at Tue Jun 10 11:59:28 CDT 2008
startkde: Starting up...
startkde: kpersonalizer not found! Please install to properly configure your user.
kbuildsycoca running...
Reusing existing ksycoca
Could not open library kmixctrl.la: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
kmixctrl: relocation error: /usr/lib/libkdeinit_kmixctrl.so: symbol snd_mixer_free, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
Could not open library kmix.la: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf


********************   WARNING   *******************************
Warning! kmix uses ALSA emulation instead of the native OSS API
****************************************************************

kmix: relocation error: /usr/lib/libkdeinit_kmix.so: symbol snd_mixer_free, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
DCOP aborting (delayed) call from 'anonymous-5574' to 'kmix'
ERROR: Communication problem with kmix, it probably crashed.
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libjavaplugin.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libjavaplugin.so: undefined symbol: NP_GetMIMEDescription
Ignored duplicate item: KWiFiManager
Ignored duplicate item: Dictionary
Ignored duplicate item: KArm
Ignored duplicate item: Windows Wireless Drivers
Ignored duplicate item: mintInstall
Ignored duplicate item: mintAssistant
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: NP_GetMIMEDescription
kdecore (KProcess): WARNING: _attachPty() 13
Could not open library '/usr/lib/kde3/knotify.la'.
/usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
kbuildsycoca running...
Reusing existing ksycoca
Could not open library '/usr/lib/kde3/knotify.la'.
/usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
--11:59:47--  http://www.linuxmint.com/repository/rules
           => `rules'
Resolving www.linuxmint.com... failed: Name or service not known.
kbuildsycoca running...
Reusing existing ksycoca
kmenuedit: WARNING: Could not read /home/fonk76wink3l/.config/menus/applications-kmenuedit.menu
kbuildsycoca running...
Reusing existing ksycoca
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x260047f
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
Could not open library '/usr/lib/kde3/knotify.la'.
/usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
kwin: X_SetInputFocus(0x2600065): BadMatch (invalid parameter attributes)
kdecore (KProcess): WARNING: _attachPty() 11
Could not open library '/usr/lib/kde3/knotify.la'.
/usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
Opener: received SetSecret
Opener: received OpenLock

Opener: received OpenDevice
Opener: received ExecPPPDaemon
Kernel supports ppp alright.
In parent: pppd pid 5672
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Opener: received OpenResolv
Opener: received RemoveSecret
Opener: received RemoveSecret
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00065
konsole: WARNING: Unable to use /usr/share/apps/konsole/sumc.desktop
konsole: WARNING: Unable to use /usr/share/apps/konsole/mc.desktop
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00065
Could not open library '/usr/lib/kde3/knotify.la'.
/usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2a00065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2600065
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2600065
Launched ok, pid = 5975
konqueror: WARNING: Profile Loading Error: No orientation specified in Container0
Launched ok, pid = 5982
konqueror: WARNING: Profile Loading Error: No orientation specified in Container0
Invalid entry (missing '=') at /etc/kde/share/apps/konqueror/servicemenus/konsolehere.desktop:80
```

I was able to bring back the kmix icon in kicker (which, by the way shows the correct mixer:cmedia cmi8788 ) by pre-loading the old lib as user according to this fellows suggestion for kmix:
[http://ubuntuforums.org/archive/index.php/t-575521.html](http://ubuntuforums.org/archive/index.php/t-575521.html)
edited to add that this needs to be done again upon restarting computer, unless there's a way to force it.  I don't need kmix as I can use ossxmix.

Try first point here:
[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)

About removing ubuntu-minimal, it shouldn't cause any problems since it is a meta-package. So no need to worry about that.
In Hardy removing alsa-base doesn't remove ubuntu-minimal. But I think that in previous versions it removed that package. I think if it matters for you that kmix works you can try that last.

---

### Post by Killaspike on 2008-06-10
I just downloaded Ubuntu today so I have no clue what im doing, first time using linux.

I got everything working and it works in the oss test.

But I cant get it working with the gnome interface. It wont recognize it when I go to sounds in system->preferences->sounds it wont show an option for oss. 

I dont think I am installing the patch right or I dont know how...

Ive got the file "gstreamer-ossv4-amd64.tar.gz" but I dont know what to do with it or how to install it.

---

### Post by janfsd on 2008-06-10
> **Killaspike said:**
> I just downloaded Ubuntu today so I have no clue what im doing, first time using linux.

I got everything working and it works in the oss test.

But I cant get it working with the gnome interface. It wont recognize it when I go to sounds in system->preferences->sounds it wont show an option for oss. 

I dont think I am installing the patch right or I dont know how...

Ive got the file "gstreamer-ossv4-amd64.tar.gz" but I dont know what to do with it or how to install it.

Do you mean that the sound applet doesn't work?
To use that file, unpack it somewhere and inside that folder, open a terminal and type:
```
sudo gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
sudo mv libgstossaudio.so /usr/lib/gstreamer-0.10/
```

---

### Post by Killaspike on 2008-06-10
> **janfsd said:**
> Do you mean that the sound applet doesn't work?

I dont know, whats the sound applet? :confused:

First time ever using Linux all these stuff is new to me.

---

### Post by janfsd on 2008-06-10
But then, is there any problem? if osstest works and you hear sound, and if playing a songs works without problem, I think you shouldn't neet to worry about that it doesn't show in the menu.

The sound applet, is something like a volume control that is in your panel.

---

### Post by endor43 on 2008-06-10
ok! everything works up to this point followed all the directions in the tutorial for the fifth time and it installed no errors, soundon gives me no errors either. after i did that ossdetect and ossinfo detected my mixing/mixer devices (most importantly creative sb x-fi) but the volume control panel and sound menu in preferences did not, so i installed the patch for volume control and now it recognizes High Definition Audio STA9227X (oss mixer) which i thought would be good but when enabled it still plays no sound so then i gathered that the device that i was using had to be the creative sb x-fi not generic oss mixer and ossdetect/info detects it as

> thomas@thomas-computer:~$ sudo ossinfo
Version info: OSS 4.0 (b1015/200803240256) (0x00040003) 
Platform: Linux/i686 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 (thomas-computer)

Number of audio devices:	10
Number of audio engines:	26
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 nVidia HD Audio interrupts=345744 (347755)
    HD Audio controller nVidia HD Audio
    Vendor ID    0x10de0371
    Subvendor ID 0x102801e1
     Codec  0: STAC9227X (0x83847618/0x102801e1)
 2: sbxfi0 Sound Blaster X-Fi (UAA)
    PCI device 1102:0005, subdevice 1102:6002
 3: ossusb0 USB audio core services
 4: vmix0 OSS transparent virtual mixer


Mixer devices
 0: High Definition Audio STAC9227X (Mixer 0 of device object 1)
 1: Sound Blaster X-Fi (UAA) (Mixer 0 of device object 2)

Audio devices
HD Audio front                    /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio center/LFE               /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio rear                     /dev/oss/hdaudio0/pcm2  (device index 2)
HD Audio side                     /dev/oss/hdaudio0/pcm3  (device index 3)
HD Audio spdif-out                /dev/oss/hdaudio0/spdout0  (device index 4)
High Definition Audio rec1        /dev/oss/hdaudio0/pcmin0  (device index 5)
High Definition Audio rec2        /dev/oss/hdaudio0/pcmin1  (device index 6)
High Definition Audio rec3        /dev/oss/hdaudio0/pcmin2  (device index 7)
Sound Blaster X-Fi (UAA) output   /dev/oss/sbxfi0/pcm0  (device index 8)
Sound Blaster X-Fi (UAA) input    /dev/oss/sbxfi0/pcmin0  (device index 9)


but when i run osstest it gives me this at the bottom and no sound plays during any of this test(i dont know if that s normal or not, but look at error at bottom please)
> thomas@thomas-computer:~$ sudo osstest
Sound subsystem and version: OSS 4.0 (b1015/200803240256) (0x00040003)
Platform: Linux/i686 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/hdaudio0/pcm0 (audio engine 0): HD Audio front
Note! Device is in use (by PID 0/VMIX) but will try anyway
- Performing audio playback test... 
  <left> OK <right>  
OK <stereo> OK <measured srate 48010.00 Hz (0.02%)> 
/dev/oss/hdaudio0/pcm1 (audio engine 1): HD Audio center/LFE
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 48000.00 Hz (0.00%)> 
/dev/oss/hdaudio0/pcm2 (audio engine 2): HD Audio rear
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 48002.00 Hz (0.00%)> 
/dev/oss/hdaudio0/pcm3 (audio engine 3): HD Audio side
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 48002.00 Hz (0.00%)> 
/dev/oss/hdaudio0/spdout0 (audio engine 4): HD Audio spdif-out
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 48000.00 Hz (0.00%)> 
/dev/oss/hdaudio0/pcmin0 (audio engine 5): High Definition Audio rec1
- Skipping input only device
/dev/oss/hdaudio0/pcmin1 (audio engine 6): High Definition Audio rec2
- Skipping input only device
/dev/oss/hdaudio0/pcmin2 (audio engine 7): High Definition Audio rec3
- Skipping input only device

*** Scanning sound adapter #1 ***
/dev/oss/sbxfi0/pcm0 (audio engine 8): Sound Blaster X-Fi (UAA) output
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/sbxfi0/pcmin0 (audio engine 9): Sound Blaster X-Fi (UAA) input
- Skipping input only device

*** Some errors were detected during the tests ***


sorry im not good at linux, i really need help

thank you


ps smilies are an 8 and then a ) "8 )" without the space in between, im not sure how to change that

---

### Post by Killaspike on 2008-06-10
> **janfsd said:**
> But then, is there any problem? if osstest works and you hear sound, and if playing a songs works without problem, I think you shouldn't neet to worry about that it doesn't show in the menu.

The sound applet, is something like a volume control that is in your panel.

The volume control doesnt work it shows it as muted. 

And I cant hear any sound from any source except the osstest.

On the system->prefrences->sound page it doesnt show oss as an option. 

Im thinking its because I didnt install "gstreamer-ossv4-amd64.tar.gz", because I dont know how to install it manually.

---

### Post by janfsd on 2008-06-10
To use that file, unpack it somewhere for instance in the Desktop, just open it and extract it and in path you select Desktop. Open the terminal (aapplications, accesories, terminal)
```
cd ~/Desktop/gstreamer-ossv4
sudo gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
sudo mv libgstossaudio.so /usr/lib/gstreamer-0.10/
```
If sound works in osstest, then in other applications it should work, what's the output of ossinfo?
Try too to shutdown pulseaudio, open system monitor (system, administration) and look for something like pulseaudio, right click and kill it.

---

### Post by Killaspike on 2008-06-10
ryan@ryan-desktop:~$ cd ~/Desktop/gstreamer-ossv4
ryan@ryan-desktop:~/Desktop/gstreamer-ossv4$ sudo gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
gzip: /usr/lib/gstreamer-0.10/libgstossaudio.so: No such file or directory
ryan@ryan-desktop:~/Desktop/gstreamer-ossv4$ 



thats what I get

---

### Post by janfsd on 2008-06-10
> **Killaspike said:**
> ryan@ryan-desktop:~$ cd ~/Desktop/gstreamer-ossv4
ryan@ryan-desktop:~/Desktop/gstreamer-ossv4$ sudo gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
gzip: /usr/lib/gstreamer-0.10/libgstossaudio.so: No such file or directory
ryan@ryan-desktop:~/Desktop/gstreamer-ossv4$ 



thats what I get
Install: gstreamer0.10-plugins-good
after proceed as I told you.
I forgot to add once you do all type at the end:
```
sudo ldconfig
``` and logout and login.

---

### Post by Killaspike on 2008-06-10
[[IMG]http://img413.imageshack.us/img413/4083/screenshotow4.png[/IMG]](http://imageshack.us)
[[IMG]http://img413.imageshack.us/img413/4083/screenshotow4.b85796bbb0.jpg[/IMG]](http://g.imageshack.us/g.php?h=413&i=screenshotow4.png)

---

### Post by janfsd on 2008-06-10
> **endor43 said:**
> ok! everything works up to this point followed all the directions in the tutorial for the fifth time and it installed no errors, soundon gives me no errors either. after i did that ossdetect and ossinfo detected my mixing/mixer devices (most importantly creative sb x-fi) but the volume control panel and sound menu in preferences did not, so i installed the patch for volume control and now it recognizes High Definition Audio STA9227X (oss mixer) which i thought would be good but when enabled it still plays no sound so then i gathered that the device that i was using had to be the creative sb x-fi not generic oss mixer and ossdetect/info detects it as



but when i run osstest it gives me this at the bottom and no sound plays during any of this test(i dont know if that s normal or not, but look at error at bottom please)


sorry im not good at linux, i really need help

thank you


ps smilies are an 8 and then a ) "8 )" without the space in between, im not sure how to change that

It seems that you have 2 cards available, have you tried to disable one of them in the BIOS?
Maybe this is related:
[http://www.4front-tech.com/forum/viewtopic.php?t=2666&start=30&sid=1e82908659faf6524463da156d9a7d74](http://www.4front-tech.com/forum/viewtopic.php?t=2666&start=30&sid=1e82908659faf6524463da156d9a7d74)
[http://4front-tech.com/forum/viewtopic.php?p=9126&sid=9ec610bef6f9031df8f4c68b3ed1d466](http://4front-tech.com/forum/viewtopic.php?p=9126&sid=9ec610bef6f9031df8f4c68b3ed1d466)
Try this too (2nd point): [http://www.opensound.com/wiki/index.php/Tips_And_Tricks#Changing_the_default_sound_output_used_for_.2Fdev.2Fdsp](http://www.opensound.com/wiki/index.php/Tips_And_Tricks#Changing_the_default_sound_output_used_for_.2Fdev.2Fdsp)


**Killaspike** are you sure that you have installed this: gstreamer0.10-plugins-good ?

---

### Post by Killaspike on 2008-06-10
yes it is installed

still cant install gstreamer-ossv4-amd64.tar.gz though

---

### Post by janfsd on 2008-06-10
Could you try: locate libgstossaudio.so 
Or: ls -l /usr/lib/gstre*
And try to reinstall gstreamer0.10-plugins-good

---

### Post by Killaspike on 2008-06-10
> **janfsd said:**
> Could you try: locate libgstossaudio.so 
Or: ls -l /usr/lib/gstre*
And try to reinstall gstreamer0.10-plugins-good

the first command line works the second doesnt

---

### Post by janfsd on 2008-06-10
Does it show something?

---

### Post by Yellow Pasque on 2008-06-10
endor43, if you're not using your onboard audio, disable it in the BIOS, then:
```
sudo soundoff
sudo ossdetect -v
sudo soundon
```

Cubby, thanks for the help with kmix. I do not currently have a working Kubuntu install (I despise KDE), but I may try it again at some point in the future. If I understand this correctly, you're entering this command into the terminal every time you start your computer?
```
LD_PRELOAD=/usr/lib/libasound.so.2.0.0 kmix
```

---

### Post by endor43 on 2008-06-10
> **Temüjin said:**
> endor43, if you're not using your onboard audio, disable it in the BIOS, then:
```
sudo soundoff
sudo ossdetect -v
sudo soundon
```

 
i get this in terminal

> thomas@thomas-computer:~$ sudo soundoff

Some applications are still using OSS - cannot unload

7056 /usr/lib/gnome-applets/mixer_applet2--oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory--oaf-ior-fd=22

Please stop these applications and run soundoff again


---

### Post by Yellow Pasque on 2008-06-10
endor43, log out. You can either log into a failsafe terminal session through the GNOME desktop manager/login screen or press Ctrl+Alt+F1 to drop to a text terminal. Run the commands again.

---

### Post by endor43 on 2008-06-10
ok i found the device that was preventing me from running soundon and i did what you said, Sound Blaster X-Fi (UAA) (oss mixer) is now the sound device, but it still plays no sound. after running osstest it gives me this message again.
> thomas@thomas-computer:~$ sudo osstest
Sound subsystem and version: OSS 4.0 (b1015/200803240256) (0x00040003)
Platform: Linux/i686 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/sbxfi0/pcm0 (audio engine 0): Sound Blaster X-Fi (UAA) output
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/sbxfi0/pcmin0 (audio engine 1): Sound Blaster X-Fi (UAA) input
- Skipping input only device

*** Some errors were detected during the tests ***


please help
thanks

---

### Post by Yellow Pasque on 2008-06-10
endor43, at this point, I can only direct you to the OpenSound forums. [http://www.4front-tech.com/forum/index.php](http://www.4front-tech.com/forum/index.php)

If you've recently purchased your X-fi, and are still able to return it, I suggest doing so and buying a Linux-friendly sound card based on the C-Media 8788 chipset. Envy24(HT) cards are good as well, but I do not like to support VIA because of their poor cooperation with open-source efforts.

---

### Post by endor43 on 2008-06-10
> **Temüjin said:**
> endor43, at this point, I can only direct you to the OpenSound forums. [http://www.4front-tech.com/forum/index.php](http://www.4front-tech.com/forum/index.php)

If you've recently purchased your X-fi, and are still able to return it, I suggest doing so and buying a Linux-friendly sound card based on the C-Media 8788 chipset. Envy24(HT) cards are good as well, but I do not like to support VIA because of their poor cooperation with open-source efforts.

how is it that other Creative sb x-fi xtreme gamer owners have got it to work?

---

### Post by endor43 on 2008-06-10
> **MobiusNZ said:**
> I'm in the same boat. I have to keep my onboard sound enabled in the bios and disabled in windows, and a cable going from the onboard sound to my speaker's aux in to get sound in linux. :(

i found this here

[http://ubuntuforums.org/showthread.php?t=665215](http://ubuntuforums.org/showthread.php?t=665215)

is this a viable soulution?, if so
how might i go about doing this?

thank you once again

---

### Post by janfsd on 2008-06-10
Good reading from Hannu, one of the devolpers of OSS4
[http://4front-tech.com/hannublog/?p=11](http://4front-tech.com/hannublog/?p=11)
I just noticed that after a long period of not posting anything, he has already write 3 times in May...

---

### Post by Yellow Pasque on 2008-06-10
> how is it that other Creative sb x-fi xtreme gamer owners have got it to work?
I'm not sure of the differences between X-fi's. Creative released a set of specifications to the developers (OSS and ALSA), and I assume they're still under an NDA (NonDisclosure Agreement).
The bottom line is that Creative does not support their hardware in the open-source community, and it is not a priority of the OSS developers to work on the drivers unless Creative starts funding such an endevour (don't hold your breath).

---

### Post by Cubby on 2008-06-10
> **Temüjin said:**
>  If I understand this correctly, you're entering this command into the terminal every time you start your computer?
```
LD_PRELOAD=/usr/lib/libasound.so.2.0.0 kmix
```

Yes, that is the command, given as user.  Can't give command as root.  Shows you how little I know about LINUX. But, I'm learning.

So far, it's working great, except for the broken path to kcmshell arts, but I can easily enter that command into terminal to bring up sound system module. In case it is if importance, I noticed that I could upgrade kcontrol. So, I did.  It installed snort-rules-default, and upgraded kdm, konqueror, kdesktop, kdebase, kdebase-kio-plugins,
kfind, kcontrol.  After it finished, I clicked on sound system under sound & multimedia, and  lo-and-behold, it brough up sound system.  Then, when I restarted computer, it was back to the way it was where when I click on 'sound system', it would not bring up the 'configure KDE control module'.  So, it's something in x11 I suspect.  I can still bring it up using terminal command, so no problem.  Just curious and will look into this more as I like to try and solve things.

endor43, I had that message too "Some applications are still using OSS - cannot unload" when I had amarok player quick launch in kicker panel.  I right clicked on amarok icon and selected quit, then tried again with soundoff.
Maybe you have a player in your quick launch panel?

---

### Post by anthony2010 on 2008-06-10
Hiya .

I typed:
'sudo soundon' in the terminal. It simply asked for my password and came back with 'command not found'

I think that also happenned when I tried the alternative to Alsa ( oss was it?) I followed the instructions to the letter.

Im not sure if this will provide a clue but I also notice that the system doesnt see the souncard. ( I dont know how I know that. Just stumbled upon it at some point!)

---

### Post by anthony2010 on 2008-06-10
Cubby.

Thanks to you too for taking the trouble to look into this. I am most grateful. I feel sure that this will be resolved in the forums due to the teamwork of people like yourself.

Thanks again.

Ant.

---

### Post by janfsd on 2008-06-10
> **anthony2010 said:**
> 
Hiya .

I typed:
'sudo soundon' in the terminal. It simply asked for my password and came back with 'command not found'

I think that also happenned when I tried the alternative to Alsa ( oss was it?) I followed the instructions to the letter.

Im not sure if this will provide a clue but I also notice that the system doesnt see the souncard. ( I dont know how I know that. Just stumbled upon it at some point!)

What is the output of ossinfo? is osstest working?

---

### Post by Yellow Pasque on 2008-06-10
Anthony, what kind of sound card do you have? Perhaps it is not seated correctly in the PCI slot or there is something wrong with the slot. Also, make sure the card/slot is not disabled in the BIOS.

Please make sure your sound card is inserted correctly and run:
```
sudo update-pciids
sudo lspci | grep dio
```

---

### Post by Killaspike on 2008-06-10
> **janfsd said:**
> Install: gstreamer0.10-plugins-good
after proceed as I told you.
I forgot to add once you do all type at the end:
```
sudo ldconfig
``` and logout and login.

I tried this and reinstalled gstreamer0.10-plugins-good and it still gives me the "No such file or directory" prompt

I dont know what to do

It wont let me install "gstreamer-ossv4-amd64.tar.gz"

---

### Post by Cubby on 2008-06-11
> **Killaspike said:**
> 

Im thinking its because I didnt install "gstreamer-ossv4-amd64.tar.gz", because I dont know how to install it manually.

I had to learn this over and over, too.  

Since you are new to LINUX, you have to first point the terminal to where you have gstreamer-ossv4-amd64.tar.gz.  Where is it located in your home folder. Is it on the desktop, or simply in your Home folder?

In KDE Mint, I have a folder in my home folder called Downloads, and that is where I save downloaded software or packages to be installed manually.

So, what I do in terminal to first point to the location of the file I want to install, as user I do the following command:
cd /home/(your user name entered here without parenthesis)/Downloads (exact name of file pasted here)

So, if I wanted to direct the terminal to a file called gstreamer-ossv4-amd64.tar.gz that I had saved in downloads folder, and my user name was john, I would do the following command:
cd /home/john/Downloads gstreamer-ossv4-amd64.tar.gz  

I make sure that 'downloads' starts with a captital D, as that is how it is spelled in my home folder.  You have to make sure the syntax is spot on and correct, or you'll get a 'file or directory not found' message.  

If you do the above correctly, it will output with my example in terminal if you store your downloads in a file named Downloads:
 
john:~/Downloads$ 

and then you can do the commands to unpack the tar file.  Or, a more familiar way if you are coming from Windows, no terminal commands needed, go to the file, right click on it, and choose to unzip here or 'extract here'.  The folder that is produced is the one you will be installing.  When it comes to installing via the terminal, you will still need to do change the directory as above to point the terminal to the file you are trying to install.  If you did 'extract here' then you can open the file and read the "install" which will explain how to install it, whether you have to do ./configure, or make, and make install.  

If I did a 'extract here' then the next thing to do would be open up terminal and as example:
cd /home/john/Downloads gstreamer-ossv4-amd64 (notice that it doesn't have the ending .tar.gz as you have unpacked it, like a winrar file.
Then enter
you'll then see the terminal is where the file is and you start the install commands, of whatever they are according to the "install" read-me file.

I hope this helps.  It's late, and I'm tired, but tomorrow is another day for OSS and these new fangled high-end audio card.  Hurray for OSS!

---

### Post by ressac on 2008-06-11
hello everybody, driver OSS works and its great :))) i'am happy

but some app. like LAST.FM , xmms dont work, can anybody help me ?

---

### Post by jalada on 2008-06-11
Just wanted to say that I switched from PulseAudio to ALSA, and then finally to OSSv4, in order to get MPD to work properly (with PulseAudio it skipped, with ALSA it caused large CPU usage that couldn't be fixed with the suggestions on the MPD Wiki). And it works brilliantly. Not only that, but Lord of the Rings Online under WINE also now has sound, Flash has sound, and Skype now works (using the details outlined on the [OSSv4 Wiki]("http://4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4") and a bit of tweaking in the settings). Everything just works with OSSv4 - and I put that partly down to most things having SOME sort of legacy support for it.

But yeah, for those just starting to use OSSv4, [this wiki article]("http://4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4") has lots of guides on getting applications to work. Very useful (just follow the instructions for Debian where applicable).

---

### Post by Yellow Pasque on 2008-06-11
ressac, I assume you followed the steps about configuring linux-sound-base and setting System -> Preferences -> Sound to OSS, so let's check the basics. Please post output of:
```
ossinfo
cd /dev; ls -la | grep dsp
```

---

### Post by ressac on 2008-06-11
```
root@amigo:/home/ressac# ossinfo
Version info: OSS 4.0 (b1015/200803240256) (0x00040003) 
Platform: Linux/i686 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 (amigo)

Number of audio devices:	2
Number of audio engines:	10
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: sbxfi0 Sound Blaster X-Fi (SB046x/067x/076x) interrupts=908063 (908063)
    PCI device 1102:0005, subdevice 1102:0021
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual mixer


Mixer devices
 0: Sound Blaster X-Fi (SB046x/067x/s (Mixer 0 of device object 1)

Audio devices
Sound Blaster X-Fi (SB046x/067x/076x) output  /dev/oss/sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi (SB046x/067x/076x) input  /dev/oss/sbxfi0/pcmin0  (device index 1)
root@amigo:/home/ressac# cd /dev; ls -la | grep dsp
lrwxrwxrwx   1 root   root          20 2008-06-11 17:17 dsp -> /dev/oss/sbxfi0/pcm0
lrwxrwxrwx   1 root   root          20 2008-06-11 17:17 dsp0 -> /dev/oss/sbxfi0/pcm0
lrwxrwxrwx   1 root   root          22 2008-06-11 17:17 dsp1 -> /dev/oss/sbxfi0/pcmin0
lrwxrwxrwx   1 root   root           8 2008-06-11 17:17 dsp_in -> /dev/dsp
lrwxrwxrwx   1 root   root          20 2008-06-11 17:17 dsp_mmap -> /dev/oss/sbxfi0/pcm0
lrwxrwxrwx   1 root   root          20 2008-06-11 17:17 dsp_out -> /dev/oss/sbxfi0/pcm0

```

---

### Post by ressac on 2008-06-11
xmms work fine, but LAST.FM not - it's use a ALSA :( how make it work with OSS?

---

### Post by janfsd on 2008-06-11
Ask the Last.fm developers to support OSS4. Are you sure Last.FM client doesn't have an option for changing sound output? Anyway you could use other music clients, AFAIK Exaile and Banshee (and probably others) support Last.FM

I just tested it, it doesn't work...
```
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
```

It seems that you can't use OSS with Last.fm

[http://www.last.fm/forum/34905/_/420873](http://www.last.fm/forum/34905/_/420873)
[http://www.last.fm/forum/21714/_/62786/1](http://www.last.fm/forum/21714/_/62786/1)

It seems that older versions supported oss.

After looking around a bit:
[http://www.last.fm/forum/34905/_/138262](http://www.last.fm/forum/34905/_/138262)
It seems by compiling manually you could enable OSS4

```
1. svn co svn://svn.audioscrobbler.net/LastFM_client/trunk/
2. cd trunk
3. Be sure to run qt4 instead of qt3:
qt-config qt4
4. change from line 225(?) in src/output/RtAudio/rtaudioplayback.cpp

api = RtAudio::LINUX_ALSA;
to
api = RtAudio::LINUX_OSS;

5. Run qmake. Change the paths to suit your system, mine are as follows: qmake QTDIR=/opt/qt4 QMAKE_UIC=/opt/qt4/bin/uic QMAKE_MOC=/opt/qt4/bin/moc CONFIG+=release
6. make
7. cd bin
8. ./lastfm.sh

```

Since the instructions are old, they don't apply anymore for newer version, I am trying to build it. If I succeed I will post it here.

Hmm... after trying to hack the sources, and compiling several times, I failed to make it work with OSS4 :(

---

### Post by ressac on 2008-06-11
i have try everything, not work!!

so just it's three ways:

1) use old version of last.fm , yes it work but it's SO OLD so i dont want to use :)
2) use amorok or something like this. (THIS WHAT i'am doing)
3) waiting for new versions :)

---

### Post by janfsd on 2008-06-11
**ressac** I think the best option is to write in Last.fm forums: [http://www.last.fm/forum/](http://www.last.fm/forum/) 
Maybe some developer can fix this to work with OSS4.

---

### Post by ressac on 2008-06-11
already do it :)
but i'dont think they fix it, becouse this problem from a long time

sorry for my english :)

---

### Post by OpposingForce on 2008-06-12
> **janfsd said:**
> I don't know about swfdec, but you could try flash 10 beta. It doesn't crash for me.  
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

Also, there is some kind of patch for libflashsupport for flash 9, I remember seeing something like that in launchpad...

Or you could try gnash.

Thanks, I installed it and it works.  I tried gnash also but it doesn't even load the video, no sound either.  I hate to support this closed-source crap, but if it's the only thing that's going to work I don't have a choice.

---

### Post by janfsd on 2008-06-12
> **OpposingForce said:**
> Thanks, I installed it and it works.  I tried gnash also but it doesn't even load the video, no sound either.  I hate to support this closed-source crap, but if it's the only thing that's going to work I don't have a choice.

Nobody makes you watch Youtube :-P

---

### Post by Yellow Pasque on 2008-06-12
> **OpposingForce said:**
> Thanks, I installed it and it works.  I tried gnash also but it doesn't even load the video, no sound either.  I hate to support this closed-source crap, but if it's the only thing that's going to work I don't have a choice.
Tell Adobe to open-source Flash: [http://www.adobe.com/cfusion/mmform/index.cfm?name=wishform](http://www.adobe.com/cfusion/mmform/index.cfm?name=wishform)

And while you're at it, ask for a 64-bit version of Flash for me. ;)

---

### Post by bluestix on 2008-06-13
> **Temüjin said:**
> 

**ADDENDUM2: Sound in Flash**
1. Run:
```
file /usr/lib/libflashsupport.so
```
If this returns info on the file, skip ahead to step 4. If the file isn't found...
2. Save the attached libflashsupport.so.gz to your Desktop
3. ```
cd ~/Desktop; gunzip libflashsupport.so.gz; sudo mv libflashsupport.so /usr/lib
```
4. create symbolic links to /usr/lib/firefox/plugins & /usr/lib/mozilla/plugins:
```
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins; sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
```


[http://ubuntuforums.org/showpost.php?p=5055305&postcount=105](http://ubuntuforums.org/showpost.php?p=5055305&postcount=105)


If after doing this you have no sound in Flash for 64bit Hardy 8.04 do:

sudo ln -s /usr/lib/libflashsupport.so /usr/lib32


I just found that in another forum after about 6 hours of trying other things.

---

### Post by ameyjah on 2008-06-13
Hey thanks a lot. I have ntel Corporation 82801H (ICH8 Family) HD Audio Controller. I had problem of getting sound with ALSA. But OSS worked for me.
Thanks a lot.
[IMG]http://i25.tinypic.com/nv5wrs.jpg[/IMG]

---

### Post by Rhapsody on 2008-06-13
Well I've now got sound working on my X-Fi XtremeGamer (turning off my integrated sound convinced OSS to pipe the output to my X-Fi), but two applications are stubbornly refusing to work with OSS. One is my Firefox Flash plugin (I followed the instructions in the opening post and the symbolic links exist, but still no sound) and Wine (I've enabled the OSS driver in Wine configuration, but the sound test fails and I get no sound). Other than that, things seem to be working OK for once.

---

### Post by anthony2010 on 2008-06-13
Hiya Temujin.

Been away a few days and came back just now, hence delay in replying. Ive copied what came up in the terminal. It is as follows:

antman@SOS9000:~$ sudo update-pciids
[sudo] password for antman: 
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  129k  100  129k    0     0  58677      0  0:00:02  0:00:02 --:--:-- 75046
Done.
antman@SOS9000:~$ sudo lspci | grep dio
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
antman@SOS9000:~$ 

interestingly Ive also lost video on account of an error message stating that my sound card ( onboard) is busy! ( Doing what I wonder? Probably smoking a cigarette and too chilled out to be bothered! hehe)

Could it be that oss or alsa havent yet written drivers for this nvidia thingy? Lastly, in the sound window, the sound devive which used to read nVidia blah blah, now has a straight line through it. Not sure if that means anything?

ant.

---

### Post by Yellow Pasque on 2008-06-13
@Rhapsody, you'll probably need to create a symbolic link for /dev/dsp

```
cd /dev; ls -la | grep dsp
```

---

### Post by goofeyfoot on 2008-06-14
Hello all:

I have a AMD 64 version of the newest Ubuntu.

I did the OSS thing posted here.  I have an XFi Card and that's why I had to do it.  I had no sound with ALSA.

Two questions.

One, now that I have sound (thanks for that by the way - it has plagued me for a long time) the system sounds start out [COLOR="black"]_really_[/COLOR] loud when you boot up the computer.  I like system sounds, but not ear-shattering ones.  Is there some way to regulate the volume on startup?  I am starting out with full volume every time which is kind of annoying.

Two, every now and then the sound quits working while I am working.  The Ossxmix applet LOOKS like I am getting sounds.  The VU meters glow and such.  But I don't hear anything.  And if I run osstest I get this weird message which is posted at the bottom of this post.  Something about a device in "use by" some other application.  Anyway, when you run osstest you don't hear a thing - even though the test looks like it's running fine.

Does anyone know what is wrong?

Thanks again for fixing my sound, cuz I had _nothing_ before!

Best regards

Michael

Here is the printout of the osstest:

michael@michael-desktop:~$ osstest
Sound subsystem and version: OSS 4.0 (b1015/200803240317) (0x00040003)
Platform: Linux/x86_64 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/sbxfi0/pcm0 (audio engine 0): Sound Blaster X-Fi (SB046x/067x/076x) output
Note! Device is in use (by PID 0/VMIX) but will try anyway
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47812.00 Hz (-0.39%)> 
/dev/oss/sbxfi0/pcmin0 (audio engine 1): Sound Blaster X-Fi (SB046x/067x/076x) input
- Skipping input only device

*** All tests completed OK ***
michael@michael-desktop:~$

---

### Post by anthony2010 on 2008-06-15
Re: Hardy 8.04 & OSS4 (Alternative to ALSA)

Hiya Temujin.

Been away a few days and came back just now, hence delay in replying. Ive copied what came up in the terminal. It is as follows:

antman@SOS9000:~$ sudo update-pciids
[sudo] password for antman:
% Total % Received % Xferd Average Speed Time Time Time Current
Dload Upload Total Spent Left Speed
100 129k 100 129k 0 0 58677 0 0:00:02 0:00:02 --:--:-- 75046
Done.
antman@SOS9000:~$ sudo lspci | grep dio
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
antman@SOS9000:~$

interestingly Ive also lost video on account of an error message stating that my sound card ( onboard) is busy! ( Doing what I wonder? Probably smoking a cigarette and too chilled out to be bothered! hehe)

Could it be that oss or alsa havent yet written drivers for this nvidia thingy? Lastly, in the sound window, the sound devive which used to read nVidia blah blah, now has a straight line through it. Not sure if that means anything?

Sorry about the double post. Ive only just figured out the 'quick reply button'

ant.

---

### Post by PRGUY85 on 2008-06-15
Hey, I am having problems with some software (Pidgin and Avant Window Manager) on my desktop which has OSS installed for the X-FI.  My laptop is running 32-bit Hardy and has no issues (no OSS or X-FI) so since I made a fresh Ubuntu install on my desktop and that's the only difference, I want to test out if that's the source of the problems.

I have tried reverting the installation but I don't get any sound off my onboard sound.  How does one complete revert to ALSA?

---

### Post by Tkolini on 2008-06-16
Thankyou so much for getting my xfi to work at last :D

---

### Post by ameyjah on 2008-06-17
hey it seems that [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi) **linux 2.6 x86 deb version is down** 
can someone reupload it to another free server like mediafire . com

---

### Post by Yellow Pasque on 2008-06-17
> **ameyjah said:**
> hey it seems that [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi) **linux 2.6 x86 deb version is down** 
can someone reupload it to another free server like mediafire . com
The link is working fine for me :\

EDIT: This may be related to the new build put out today. You probably tried to access the server while they were updating it.

---

### Post by Yellow Pasque on 2008-06-17
A new build was released today! Thanks to dev, Hannu, cesium, seawright, Ionic and everyone else for this build.
> OSS 4.0 Build 1016 is being announced for Linux, Solaris, FreeBSD and UnixWare.

Changes: (Contributions from the OSS Community)

- Updated ossplay to support stdin and ADPCM, AIFF, ULAW, ALAW formats (community)
- Updated ossrecord to support input amplification (Community)
- Updated ossxmix to support tabbed mixers and Gnome Panel iconification (community)
- Fixes to savemixer app (community)
- VMIX driver moved into OSS audio core.
- Fixes to OSS audio core to support power management
- Driver fixes to Envy24 to add VMIX support
- Driver fixes to Envy24HT to support ESI Juli@ device (Community)
- HDaudio driver updated to support Sony VAIO models. (Community)
- Miscellaneous fixes to all drivers to support the new vmix changes.

---

### Post by Vaune on 2008-06-17
Looks like the download site is still down.  Any have a mirror?  Or should I just wait?

---

### Post by janfsd on 2008-06-17
> **Vaune said:**
> Looks like the download site is still down.  Any have a mirror?  Or should I just wait?

I suppose they still didn't make a deb package. You could try the tar.gz package.

EDIT: Found the correct link:
[http://www.4front-tech.com/release/oss-linux-4.0-1016_i386.deb](http://www.4front-tech.com/release/oss-linux-4.0-1016_i386.deb)
However it doensn't work for me...

---

### Post by MachineHead on 2008-06-18
Hey Temujin,

Does this OSS4 also work with the **Creative X-Fi Fatality**?
I'm switching from onbaord to X-Fi now when I play high-end games in windows.

Regards,

MachineHead

---

### Post by ameyjah on 2008-06-18
i am getting error while installing deb file. 

error
```
dpkg: regarding oss-linux-4.0-1016_i386.deb containing oss-linux:
 oss-linux conflicts with libflashsupport
  libflashsupport (version 1.9-0ubuntu1) is present and installed.
dpkg: error processing oss-linux-4.0-1016_i386.deb (--install):
 conflicting packages - not installing oss-linux
Errors were encountered while processing:
 oss-linux-4.0-1016_i386.deb
```
what should i do. 
I am on hardy gnome

---

### Post by Yellow Pasque on 2008-06-18
ameyjah,
```
sudo apt-get remove libflashsupport
```

---

### Post by warbread on 2008-06-18
Works great on amd_64 Hardy with an M-Audio 24/96.  The ossxmixer is awesome: I finally get the control of my soundcard that I've always wanted!

Spoke too soon.  OSS doesn't seem to want to play with Jack in 64 bit.  Catastrophic crashes abound.  Oh well, it was worth a try.

---

### Post by starnerd67 on 2008-06-19
Hi 
Im new to Ubuntu (and linux)
But im having alot of trouble getting my ESI Juli@ sound card to work. I just read your post about installing the OSS4 and although the installing was successful im not able to get any sound. 
Testing the card with osstest revealed that the optical out (the output i wish to use) works fine, but the anolog (or front out) does not work, and apparently front out is the default being used. 

is there anyway i can switch the default audio out to be s/pdif out rather than front out ???

---

### Post by MJBoa on 2008-06-19
For some reason my blacklist doesn't seem to be working...
I still get ERROR: Module snd_pcm is in use by cx88_alsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm
when doing soundon even after /etc/modprobe.d/blacklist had all that stuff in it. Why?

---

### Post by hyunkell on 2008-06-20
I successfully installed oss4 this morning, and it is working perfectly fine.
For some reason it had a huge impact on sound quality, I can finally enjoy listening to music in Ubuntu, and I just love the amount of different settings in ossxmix.

I still have one little problem, I can't really figure out on my own.
I have 2 Sound Devices:
1: Intel Hidef onboard
2: Logitech Usb Audio (Headset)

Running osstest, I hear that both devices are working, and I have both devices in ossxmix.

Being a Teamspeak user, I want to use my Usb Headset (for Teamspeak only)
I can't figure out how to tell Teamspeak how ot use my Usb Headset though.
Yes, I do have the settings -> options tab, but after installing oss4, 
/dev/dsp1 which used to be my headset, is now used for something else.
Here's a list of my audio devices:

```
lrwxrwxrwx   1 root   root          22 2008-06-20 11:27 dsp -> /dev/oss/hdaudio0/pcm0
lrwxrwxrwx   1 root   root          22 2008-06-20 11:27 dsp0 -> /dev/oss/hdaudio0/pcm0
lrwxrwxrwx   1 root   root          22 2008-06-20 11:27 dsp1 -> /dev/oss/hdaudio0/pcm1
lrwxrwxrwx   1 root   root          27 2008-06-20 11:27 dsp10 -> /dev/oss/usb13953556-1/pcm0
lrwxrwxrwx   1 root   root          29 2008-06-20 11:27 dsp11 -> /dev/oss/usb13953556-2/pcmin0
lrwxrwxrwx   1 root   root          22 2008-06-20 11:27 dsp2 -> /dev/oss/hdaudio0/pcm2
lrwxrwxrwx   1 root   root          22 2008-06-20 11:27 dsp3 -> /dev/oss/hdaudio0/pcm3
lrwxrwxrwx   1 root   root          22 2008-06-20 11:27 dsp4 -> /dev/oss/hdaudio0/pcm4
lrwxrwxrwx   1 root   root          22 2008-06-20 11:27 dsp5 -> /dev/oss/hdaudio0/pcm5
lrwxrwxrwx   1 root   root          25 2008-06-20 11:27 dsp6 -> /dev/oss/hdaudio0/spdout0
lrwxrwxrwx   1 root   root          24 2008-06-20 11:27 dsp7 -> /dev/oss/hdaudio0/pcmin0
lrwxrwxrwx   1 root   root          24 2008-06-20 11:27 dsp8 -> /dev/oss/hdaudio0/pcmin1
lrwxrwxrwx   1 root   root          24 2008-06-20 11:27 dsp9 -> /dev/oss/hdaudio0/pcmin2
lrwxrwxrwx   1 root   root          25 2008-06-20 11:27 dsp_ac3 -> /dev/oss/hdaudio0/spdout0
lrwxrwxrwx   1 root   root          22 2008-06-20 11:27 dsp_mmap -> /dev/oss/hdaudio0/pcm0
lrwxrwxrwx   1 root   root          22 2008-06-20 11:27 dsp_multich -> /dev/oss/hdaudio0/pcm0
lrwxrwxrwx   1 root   root          22 2008-06-20 11:27 dsp_out -> /dev/oss/hdaudio0/pcm0
lrwxrwxrwx   1 root   root          22 2008-06-20 11:27 mixer0 -> /dev/oss/hdaudio0/mix0
lrwxrwxrwx   1 root   root          27 2008-06-20 11:27 mixer1 -> /dev/oss/usb13953556-0/mix0

```

Trying to use anything like /dev/mixer1 unfortunately does not work :(

Some more info:

ossinfo
```
Version info: OSS 4.0 (b1016/200806162350) (0x00040003) 
Platform: Linux/x86_64 2.6.24-19-generic #1 SMP Wed Jun 4 15:10:52 UTC 2008 (hyulap)

Number of audio devices:	12
Number of audio engines:	16
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 Intel HD Audio interrupts=949206 (949206)
    HD Audio controller Intel HD Audio
    Vendor ID    0x808627d8
    Subvendor ID 0x15580571
     Codec  0: ALC883 (0x10ec0883/0x05720000)
     Codec  1: Conexant2bfa (0x14f12bfa)
 2: ossusb0 USB audio core services
 3: usb13953556-0 USB sound device
 4: usb13953556-1 USB sound device
 5: usb13953556-2 USB sound device


Mixer devices
 0: High Definition Audio ALC883 (Mixer 0 of device object 1)
 1: USB sound device (Mixer 0 of device object 3)

Audio devices
HD Audio play front               /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio play rear                /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio play center/LFE          /dev/oss/hdaudio0/pcm2  (device index 2)
HD Audio play side                /dev/oss/hdaudio0/pcm3  (device index 3)
HD Audio play pcm4                /dev/oss/hdaudio0/pcm4  (device index 4)
HD Audio play modem-out           /dev/oss/hdaudio0/pcm5  (device index 5)
HD Audio play spdif-out           /dev/oss/hdaudio0/spdout0  (device index 6)
HD Audio rec mix                  /dev/oss/hdaudio0/pcmin0  (device index 7)
HD Audio rec mix                  /dev/oss/hdaudio0/pcmin1  (device index 8)
HD Audio rec modem-out            /dev/oss/hdaudio0/pcmin2  (device index 9)
USB sound device play             /dev/oss/usb13953556-1/pcm0  (device index 10)
USB sound device rec              /dev/oss/usb13953556-2/pcmin0  (device index 11)

```

Any ideas how to get my Headset to work in Teamspeak?
Thanks,

Hyu

---

### Post by janfsd on 2008-06-20
It seems that there are some problems with the latest deb package. Although a fixed package has already been released. Check this for more info:
[http://4front-tech.com/forum/viewtopic.php?p=9388#9388](http://4front-tech.com/forum/viewtopic.php?p=9388#9388)

---

### Post by jagnet on 2008-06-21
Ive just tried Temüjin's install from the 2nd post. Sound worked OK in Ubuntu but not in firefox 3.0 .
Though Im using Ubuntu 2.6.24-19 64bit. 

I found a solution if anyones interested here >

[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)


...now if I could just find a way to get all FIVE speakers working with OSS would be great (using acer 8920G) 

:)

---

### Post by rexb on 2008-06-21
+1.

Respect for your job.

Sony VAOI VGN-AR770 (vaio)
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Codec: SigmaTel CXD9872AKD (STAC9872AKD or STAC92xx), Conexant ID 2c06 and Realtek ALC262

Ubuntu 8.04 (hardy) 2.6.24-xx-generic
Ubuntu 8.10 (intrepid) 2.6.27-xx-generic


**OSS ( 4.1 ):**
> 
speaker                         - working
headphone                       - working
speaker auto mute               ! not (there is no way to fix this, driver's restriction!!!)
(S/PDIF) Digital Audio Output   - working
(HDMI) Digital Audio Output     ! not(as far as I know problem with nvidia)
build-in mic                    - working
external mic                    - working
build-in modem                  ! not

**ALSA ( 1.0.18 ):**
> 
speaker                         - working
headphone                       - working
speaker auto mute               - working
(S/PDIF) Digital Audio Output   ! not
(HDMI) Digital Audio Output     ! not(as far as I know problem with nvidia)
build-in mic                    **[COLOR="Red"]- fixed, working[/COLOR]**
external mic                    **[COLOR="Red"]- fixed, working[/COLOR]**
build-in modem                  ! not (how to fix - see below)


**mic's:**
*to fix the problem with mic's, use the next options:*
options snd-hda-intel model=vaio probe_mask=1

*in the next file:*

/etc/modprobe.d/alsa-base


**built-in modem:**
see - [http://www.linuxant.com/drivers/]("http://www.linuxant.com/drivers/")

---

### Post by haneya on 2008-06-23
i followed all the steps but Do I have to choose "oss - open sound system " in system>pref>sound for all of them ??cuz when i choose "oss open sound system" with sound playback system sound not working (login and logout sounds) and i cant find any device in default mixer tracks , and the sound recording not working " mic " i tried it with ALSA , oss and pulse audio server (not working ) so what i have do ??

ossinfo :
```
 ossinfo
Version info: OSS 4.0 (b1016/200806162356) (0x00040003) 
Platform: Linux/i686 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 (anas-laptop)

Number of audio devices:	3
Number of audio engines:	7
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 Intel HD Audio interrupts=526132 (526132)
    HD Audio controller Intel HD Audio
    Vendor ID    0x808627d8
    Subvendor ID 0x1179ff10
     Codec  0: ALC861 (0x10ec0861/0x11791205)
     Codec  1: Unknown (0x11c13026)
 2: ossusb0 USB audio core services


Mixer devices
 0: High Definition Audio ALC861 (Mixer 0 of device object 1)

Audio devices
HD Audio play front               /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio play center/LFE          /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio rec rec                  /dev/oss/hdaudio0/pcmin0  (device index 2)

```

ubuntu 8.04 
toshiba satellite

---

### Post by Yellow Pasque on 2008-06-23
haneya, for system sounds, choose ESD. I guess I need to update that part of the guide. Thanks for the feedback.

---

### Post by haneya on 2008-06-23
thx for your reply , but still the mic problem ?? any suggestions

---

### Post by GuildsmanCoren on 2008-06-23
I hope this is the right place to ask this.

I'm a brand new Ubuntu user coming from Windows. I really want to like Ubuntu, but I can't get my soundcard to work and this most definitely will be a dealbreaker if I can't fix it. :(
I'm using an Auzentech Prelude 7.1, which I've heard people have been getting to work using OSS. So I followed the guide on the first page to the letter, and everything went fine except I still get no sound:

> ...
Building module ymf7xx
depmod -a
Starting Open Sound System
OSS is already loaded.

coren@Coren-PC:~/Desktop$ sudo soundon
OSS is already loaded.
coren@Coren-PC:~/Desktop$ sudo ossdetect -v
Detected Creative SB X-Fi (EARLY BETA)
Detected Intel High Definition Audio (P35)
Detected Generic USB audio device (BETA)
coren@Coren-PC:~/Desktop$ sudo ossinfo
No /dev/mixer device available in your system.
Perhaps Open Sound System is not installed or running.
coren@Coren-PC:~/Desktop$

Now if I understand this right, ossdetect is telling me my Auzentech is being correctly identified as an X-Fi, but then ossinfo tells me it won't work. Can anyone tell me why not?

I've tried reinstalling from scratch but I keep getting the same thing...

My sound preferences panel won't show any devices and trying to open volume control gives me a "No volume control Gstreamer plugins and/or devices found" message.

Any help would be greatly appreciated :)

EDIT: a reboot changed the situation a bit: I now get the "High Definition Audio" device in my sound devices list and the OSS mixer shows me a lot of settings for said device. However, the X-fi still doesn't show up in the device list and the ossxmix program only shows "play", "rec" and "recsrc" settings, no sign of the expected multichannel settings. Most importantly, still no sound coming from my Prelude... :(

Updated ossinfo:

> coren@Coren-PC:~$ ossinfo
Version info: OSS 4.0 (b1016/200806162350) (0x00040003) 
Platform: Linux/x86_64 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Coren-PC)

Number of audio devices:	12
Number of audio engines:	16
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 Intel HD Audio interrupts=85918 (85918)
    HD Audio controller Intel HD Audio
    Vendor ID    0x8086293e
    Subvendor ID 0x1458a002
     Codec  2: ALC885 (0x10ec0885/0x1458a002)
 2: sbxfi0 Sound Blaster X-Fi interrupts=24934 (24934)
    PCI device 1102:0005, subdevice 415a:0034
 3: ossusb0 USB audio core services


Mixer devices
 0: High Definition Audio ALC885 (Mixer 0 of device object 1)
 1: Sound Blaster X-Fi (Mixer 0 of device object 2)

Audio devices
HD Audio play front               /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio play rear                /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio play center/LFE          /dev/oss/hdaudio0/pcm2  (device index 2)
HD Audio play side                /dev/oss/hdaudio0/pcm3  (device index 3)
HD Audio play pcm4                /dev/oss/hdaudio0/pcm4  (device index 4)
HD Audio play spdif-out           /dev/oss/hdaudio0/spdout0  (device index 5)
HD Audio rec mix                  /dev/oss/hdaudio0/pcmin0  (device index 6)
HD Audio rec mix                  /dev/oss/hdaudio0/pcmin1  (device index 7)
HD Audio rec mix                  /dev/oss/hdaudio0/pcmin2  (device index 8)
HD Audio rec spdifin              /dev/oss/hdaudio0/spdin0  (device index 9)
Sound Blaster X-Fi output         /dev/oss/sbxfi0/pcm0  (device index 10)
Sound Blaster X-Fi input          /dev/oss/sbxfi0/pcmin0  (device index 11)


---

### Post by Yellow Pasque on 2008-06-23
Guildsman, are you using your onboard audio for anything? If not, I would recommend disabling it in the BIOS and running (sudo) soundoff, ossdetect, soundon again.

> no sign of the expected multichannel settings
The X-fi drivers are limited to stereo output at this time. I suggest taking it up with Creative and telling them to support their hardware in Linux, either by hiring professional coders, or better yet, putting financial support behind OSS4.

---

### Post by GuildsmanCoren on 2008-06-24
> **Temüjin said:**
> Guildsman, are you using your onboard audio for anything? If not, I would recommend disabling it in the BIOS and running (sudo) soundoff, ossdetect, soundon again.


The X-fi drivers are limited to stereo output at this time. I suggest taking it up with Creative and telling them to support their hardware in Linux, either by hiring professional coders, or better yet, putting financial support behind OSS4.

Oh :( That's too bad. Well, actually even stereo won't work, but I'll do as you suggested and turn off onboard audio.

As a matter of fact, Auzentech are working on official Linux drivers, they're scheduled for Q4 2008. I guess I'll have to be patient.

Thanks for your answer anyway :)

---

### Post by sharkey77 on 2008-06-24
Tried and failed, still no sound.  Went to system preferences > sounds and updated all but system to OSS.  OSS mixer also only shows MONO

```

Version info: OSS 4.0 (b1016/200806162356) (0x00040003) 
Platform: Linux/i686 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 (MediaPC)

Number of audio devices:	1
Number of audio engines:	6
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: ich0 Intel ICH5 (24D5) interrupts=203671 (203671)
 2: ossusb0 USB audio core services


Mixer devices
 0: ICH AC97 Mixer (STAC9758) (Mixer 0 of device object 1)

Audio devices
Intel ICH5 (24D5)                 /dev/oss/ich0/pcm0  (device index 0
```)

---

### Post by OpposingForce on 2008-06-25
> **sharkey77 said:**
> Tried and failed, still no sound.  Went to system preferences > sounds and updated all but system to OSS.  OSS mixer also only shows MONO

```

Version info: OSS 4.0 (b1016/200806162356) (0x00040003) 
Platform: Linux/i686 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 (MediaPC)

Number of audio devices:	1
Number of audio engines:	6
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: ich0 Intel ICH5 (24D5) interrupts=203671 (203671)
 2: ossusb0 USB audio core services


Mixer devices
 0: ICH AC97 Mixer (STAC9758) (Mixer 0 of device object 1)

Audio devices
Intel ICH5 (24D5)                 /dev/oss/ich0/pcm0  (device index 0
```)

Did you try restarting your computer?  And do you have an xfi sound card?  If so which one do you have?

---

### Post by AndrewZorn on 2008-06-25
Well, it messed up my video drivers, but this was more of a proof-of-concept for me.  My Razer Barracuda AC-1 finally works in Ubuntu, and past that, the SPDIF monitor/passthrough works too!!!  This semi-solves my problem that an HDMI switch works in Linux but not Windows, letting me play my PS3 with less hassle if I can start using Linux more 24/7.

---

### Post by Shardsofmetal on 2008-06-25
Is there a way to fix the exponentially increasing volume issue, where the first 3/4 of the volume does very little? Also, I followed the instructions to get sound in flash working, but that did not help. If it makes a difference, I'm running the 64-bit version of Ubuntu.

Also, how do I assign keys to run the scripts to increase and decrease volume, and mute and unmute? Thanks

---

### Post by terry_gardener on 2008-06-25
i installed the oss4.1 with the instruction earlier in the thread but when i try to play any media file i get no sound but when i do osstest i get sound. 

i have reinstalled the codecs and media player software ie vlc and totem and mplayer. 

when player in totem and vlc get picture but no sound, when playing in mplayer get em says unable to initialise sound. 

i have applied the volume control patch and flash patch. 

so sound ever in youtube vids. 

when goto the sound options system-pe=references-sound and change the tabs to oss and click test get error. 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

any ideas. 

one more thing i was using alsa with onboard sound snd-hda-intel 
i have disabled the sound in bios and also blacklisted the alsa drivers.

---

### Post by janfsd on 2008-06-25
> **terry_gardener said:**
> 
when goto the sound options system-pe=references-sound and change the tabs to oss and click test get error. 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

I get the same error when trying to change to esd... But i can change to oss without problems. Is the auto setting working?

---

### Post by terry_gardener on 2008-06-25
which ever option i picked get same problem

---

### Post by sharkey77 on 2008-06-25
> Originally Posted by OpposingForce

Did you try restarting your computer? And do you have an xfi sound card? If so which one do you have?

ummm, yes I restarted the computer.  I'm not that much of a noob.  Xfi?  Not to my knowledge.  The soundcard is built into the motherboard.  

Intel ICH5, STAC9758

---

### Post by sharkey77 on 2008-06-25
It has digital out too, but I don't use that.

Link to details:  [http://support.gateway.com/s/Manuals/Desktops/9526013.pdf#page=31](http://support.gateway.com/s/Manuals/Desktops/9526013.pdf#page=31)

---

### Post by sharkey77 on 2008-06-25
Here's a better link wtih the specs:

[http://support.gateway.com/s/PC/901_Series/2900090/2521072/2521072sp9.shtml](http://support.gateway.com/s/PC/901_Series/2900090/2521072/2521072sp9.shtml)

```
Audio Sigmatel® Soft Audio 6-channel AC97 revision 2.3 codec (STAC9758)
```

---

### Post by F-3582 on 2008-06-29
Hi. I got some troubles with this:

As one guy already pointed out Rhythmbox seems to produce some serious distortion with OSS4. Well, unfortunately it looks like this applies on every player I've tried. At first everything works perfectly, but after a while OSS4 gives me those distortions with every program I tried, be it Flash, Amarok, Audio Overload or even the Gnome sound test. The only thing that doesn't sound distorted is osstest.

The only thing that helps is reinstalling OSS4 completely.

```
~$ ossinfo
Version info: OSS 4.0 (b1016/200806170542) (0x00040003) 
Platform: Linux/i686 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 (rechner)

Number of audio devices:	1
Number of audio engines:	6
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: ich0 Intel ICH4 (24C5) interrupts=21890 (36537)
 2: ossusb0 USB audio core services


Mixer devices
 0: ICH AC97 Mixer (ALC655) (Mixer 0 of device object 1)

Audio devices
Intel ICH4 (24C5)                 /dev/oss/ich0/pcm0  (device index 0)
```

Are there any workarounds for this?

EDIT: Sorry, was my own fault. I accidentally set vmix0-channels to "Multich".

EDITT: Found another strange thing: When starting Opera audio playback gets horribly desynchronized. Not a big deal, because Amarok just needs to stop playback and start it again, others, however (like Audio Overload) need to be restarted entirely. Also VLC needs the option "Try Workaround for buggy OSS drivers" enabled or the audio gets desynced there, as well.

---

### Post by coolen on 2008-06-29
Just wondering, how does this play with PulseAudio? I recently bought a laptop whose sound card may well require OSS over ALSA, and I'd love to keep PA. Is this something that's being planned?

Thanks for the info, by the way. It's been enlightening.

---

### Post by FlyingWV on 2008-06-29
Temüjin,

Another big thank you. I've spent the last day or so reading about the nightmares that I would face trying to get my sound to work, because I have the Creative X-Fi sound card. I read and read, looking at many alternatives, and after browsing through this thread I applied your how to.

Needless to say, it worked amazingly well, listing to a music cd right now.

Thank you again.

---

### Post by F-3582 on 2008-06-30
> **coolen said:**
> Just wondering, how does this play with PulseAudio? I recently bought a laptop whose sound card may well require OSS over ALSA, and I'd love to keep PA. Is this something that's being planned?

Thanks for the info, by the way. It's been enlightening.

It doesn't work with Pulseaudio at all. However, you won't need it, either, because the ossxmixer is well capable of doing almost everything Pulseaudio can do, just as individual volume for every application.

---

### Post by coolen on 2008-06-30
> **F-3582 said:**
> It doesn't work with Pulseaudio at all. However, you won't need it, either, because the ossxmixer is well capable of doing almost everything Pulseaudio can do, just as individual volume for every application.

Ahh, thank you. I would like to stream music over my home network...however, I think being able to play it would be my first priority :)

---

### Post by jonhewer on 2008-06-30
does this tutorial also work on debian lenny?

thanks

---

### Post by Divide_Overflow on 2008-06-30
Any idea when OSS 4.1 is due to come out?

I thought I saw some references by folks actively running that version already. I'm hoping that they will advance the support for the X-fi chipset a bit past early beta as my initial attempts to get 4.0 working were unsuccessful.  (This could easily be attributed to my own ham-handed, novice attempts to follow an early version of this guide.)  

I dual boot this machine into both XP and Ubuntu.  I'm loving Ubuntu more and more, but not having any working sound is keeping me from shifting allegiance completely.  I understand that my choice of sound cards was unfortunate, as Creative is not playing nicely with open development but I do look forward to the day when it "just works".  Alsa has sat for a long time with pending support for the X-fi.  OSS looks like it might be the item to fill the gap 'till a more robust drive is available by any other provider (OSS, Alsa or god forbid, Creative themselves).

---

### Post by cdos on 2008-07-01
Temüjin,

Great guide.  Very helpful so far.

I've noticed that youtube won't work in Firefox 3 while ESD is running.  So I end up having to kill ESD and restart Firefox.  Do you know how I might fix this?

Thanks.

---

### Post by Yellow Pasque on 2008-07-01
> **cdos said:**
> Temüjin,

Great guide.  Very helpful so far.

I've noticed that youtube won't work in Firefox 3 while ESD is running.  So I end up having to kill ESD and restart Firefox.  Do you know how I might fix this?

Thanks.
cdos, I'm not sure, although it's not the first time I've heard of ESD not behaving.

Check your System -> Preferences -> Sound settings. I'm a little confused about the ESD/OSS stuff myself. As I've mentioned before, I don't use system sounds myself, but I'd like to make sure they work for those who do. Maybe I'll hook up my test hard disk and play around with that tonight.

---

### Post by Yellow Pasque on 2008-07-01
Kubuntu users: There is a proposed patch on Launchpad for kmix (volume control) compatibility. I posted a comment in it and assigned it to a kdemultimedia dev. (Jonathan Riddell). [https://bugs.launchpad.net/ubuntu/+source/kdemultimedia/+bug/123957](https://bugs.launchpad.net/ubuntu/+source/kdemultimedia/+bug/123957)

---

### Post by megamoo on 2008-07-03
I've have been going through the `Installing OSS 4.0 From a .deb package` and I get to stage 7 when it says `Add a new custom application launcher to the panel that runs the command: ossxmix.... ` how do you do that ??

This may be a stupid question but I'm very new to linux... how new you ask ??  Well I got stuck for three days cos I was trying to install a package with a "_" instead of a "-" :redface:

---

### Post by Yellow Pasque on 2008-07-03
Not a stupid question. Just right click on empty space in the panel (or maybe you call it the upper toolbar) and select "Add to Panel"

In GNOME, there are no "toolbars". Instead, we use panels. Ubuntu has panels on the top and bottom of your screen by default, but there's really nothing special about those panels. If you prefer them on the side, you can do that too.

If you prefer something more Windows-like, then try a Kubuntu LiveCD.

---

### Post by megamoo on 2008-07-04
ahhh that helped and now im listening to music
thank you :guitar:

---

### Post by hyunkell on 2008-07-05
I tried oss4 out, and I actually like it quite alot, problem is, I cannot get my usb headset to work with it.
Until I have found a solution to the problem I need a way to go back to my old oss3 in order to use my headset, which I really do need on a regular basis.

Which steps would I need to take in order to undo the oss4 installation, and go back to how my system worked before?

Thanks,
hyu

---

### Post by Yellow Pasque on 2008-07-05
> **hyunkell said:**
> I tried oss4 out, and I actually like it quite alot, problem is, I cannot get my usb headset to work with it.
Until I have found a solution to the problem I need a way to go back to my old oss3 in order to use my headset, which I really do need on a regular basis.

Which steps would I need to take in order to undo the oss4 installation, and go back to how my system worked before?

Thanks,
hyu

If you installed from a .deb:
```
sudo dpkg -r oss-linux
```

Then, install the OSS3 .deb

---

### Post by hyunkell on 2008-07-05
> **Temüjin said:**
> If you installed from a .deb:
```
sudo dpkg -r oss-linux
```

Then, install the OSS3 .deb

I am unable to find an oss3 deb :(
The only thing I found was oss-install which doesn't seem to work:

[http://oss.pastebin.com/mfd1011](http://oss.pastebin.com/mfd1011)

---

### Post by jimmyjim11 on 2008-07-06
is ther some way of getting sound in tv time have a hauppauge hvr 1100 with picture but no sound,I have sound in firefox and vlc etc :confused::confused:

---

### Post by cdos on 2008-07-06
> **Temüjin said:**
> cdos, I'm not sure, although it's not the first time I've heard of ESD not behaving.

Check your System -> Preferences -> Sound settings. I'm a little confused about the ESD/OSS stuff myself. As I've mentioned before, I don't use system sounds myself, but I'd like to make sure they work for those who do. Maybe I'll hook up my test hard disk and play around with that tonight.

So, I think this is an issue with OSS4 version 1016 as per [http://www.4front-tech.com/forum/viewtopic.php?t=2747](http://www.4front-tech.com/forum/viewtopic.php?t=2747).  Downgrading to version 1015 corrected these mixing issues for me.  So for anyone who has issues and would like to solve it, I suggest downgrading until 1017 is released.

---

### Post by MattCatt on 2008-07-08
sudo dpkg -i oss-linux-4.0-1016_i386.deb give this:

```
Selecting previously deselected package oss-linux.
(Reading database ... 111043 files and directories currently installed.)
Preparing to replace oss-linux 4.0-1016 (using oss-linux-4.0-1016_i386.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux-4.0-1016_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.24-19-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
OSS is already loaded.
Errors were encountered while processing:
 oss-linux-4.0-1016_i386.deb

```

---

### Post by F-3582 on 2008-07-08
The OSS4 deinstallation script seems to be a little delicate in terms of corruption. Follow [these instructions]("http://www.4front-tech.com/forum/viewtopic.php?t=2054") to "fix" it.

---

### Post by Yellow Pasque on 2008-07-08
> **F-3582 said:**
> The OSS4 deinstallation script seems to be a little delicate in terms of corruption. Follow [these instructions]("http://www.4front-tech.com/forum/viewtopic.php?t=2054") to "fix" it.
I have a Debian/Ubuntu-specific guide (gives the edit command for n00bs to copy+paste) based on those directions (and a link for it in the OSS4 guide, at the end of the post above the attached files).
[http://ubuntuforums.org/showpost.php?p=5055305&postcount=105](http://ubuntuforums.org/showpost.php?p=5055305&postcount=105)

---

### Post by mab1376 on 2008-07-12
```
mark@mark-desktop:~$ file /usr/lib/libflashsupport.so
/usr/lib/libflashsupport.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), not stripped
mark@mark-desktop:~$ cd ~/Desktop; gunzip libflashsupport.so.gz; sudo mv libflashsupport.so /usr/lib
[sudo] password for mark: 
mark@mark-desktop:~/Desktop$ sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins; sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
ln: creating symbolic link `/usr/lib/firefox/plugins/libflashsupport.so': File exists
ln: creating symbolic link `/usr/lib/mozilla/plugins/libflashsupport.so': File exists
mark@mark-desktop:~/Desktop$
```

did i fix the flash support correct?

---

### Post by SammyBoy247 on 2008-07-12
First - great howto and great thread.  Had trouble trying the move on my own this was a lot more straight forward.

Having said that I do have some issues that I'm hoping are easily sorted.

heres my OSSINFO output

```
Version info: OSS 4.0 (b1016/200806162350) (0x00040003) 
Platform: Linux/x86_64 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 (sammyboy-desktop)

Number of audio devices:	1
Number of audio engines:	6
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: via82330 VIA VT8237 interrupts=999658 (999658)
 2: ossusb0 USB audio core services


Mixer devices
 0: VIA823x AC97 Mixer (ALC655) (Mixer 0 of device object 1)
    Device file /dev/oss/via82330/mix0, Legacy device /dev/mixer0
    Priority: 10
    Caps: 

Audio devices
VIA VT8237                        /dev/oss/via82330/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Engine      1: Busy (IN/OUT) label 'VMIX' 
      Engine      2: Busy (OUT) by PID 15319 / esd label 'esd' 
      Engine      3: Available for use 
      Engine      4: Available for use 
      Engine      5: Available for use 
      Engine      6: Available for use 
```



I have sound from system and video playback but I've lost embeded video from firefox/gecko, no video or audio.

**Exaile** 
[INDENT]kicks out massively distorted sound (or, if you drop exailes internal volume to mute all you can hear is calming white noise.[/INDENT]

**Amarok** 
[INDENT]throws all it's toys out of the pram hits X in the balls, pulls the pin on a grenade and takes out any nearby innocent apps[/INDENT]

Hope someone can help, I know a previous post mentioned video codec problems, any way any help appreciated.

Cheers

---

### Post by F-3582 on 2008-07-12
I assume you use the mplayerplug-in for embedded video. You might have to configure MPlayer for OSS, first. Same goes for Amarok and Exaile.

---

### Post by mab1376 on 2008-07-12
how do you do that, amarok doesn't work for me, however rhythmbox does.
personally i prefer amarok, also is there any troubleshooting i could do to make my flash player have audio through OSS4?

i followed the directions on post 1 with no luck.

---

### Post by F-3582 on 2008-07-12
> **mab1376 said:**
> how do you do that, amarok doesn't work for me, however rhythmbox does.
personally i prefer amarok, also is there any troubleshooting i could do to make my flash player have audio through OSS4?

i followed the directions on post 1 with no luck.
Refer to this guide:

[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)

---

### Post by jsaulters on 2008-07-12
Thank you, your guide rocks!  

Previously, I'd get flash working, and then I'd lose my CD or DVD audio...I was just going in circles.  Your guide is more thorough than others.  I dunno, but maybe blacklisting ALSA made the difference.

Anyways, thanks very much!

---

### Post by Yellow Pasque on 2008-07-13
If you've done the above and it still doesn't work after rebooting, download the attached file and compile it, I use the home directory (~/) as an example.

For 32-bit/x86:
```
cd ~/; gunzip flashsupport.c.gz
cc -shared -Wall -Werror -fPIC -O2 flashsupport.c -o libflashsupport.so
sudo chown root libflashsupport.so
sudo chmod 755 libflashsupport.so
sudo mv libflashsupport.so /usr/lib/
sudo ldconfig.real -vp | grep flash
```

For 64-bit/x86_64, **If you're using 32-bit Flash/nspluginwrapper, then execute the bolded commands and use the -m32 flag:** If you're using the 64-bit Flash Alpha, do not execute the bolded commands and DO NOT use the -m32 flag.
```
**sudo apt-get -y install gcc-multilib**
cd ~/; gunzip flashsupport.c.gz
cc -shared -Wall -Werror -fPIC -O2 **-m32** flashsupport.c -o libflashsupport.so
sudo chown root libflashsupport.so
sudo chmod 755 libflashsupport.so
**sudo mv libflashsupport.so /usr/lib32/**
sudo mv libflashsupport.so /usr/lib/ # native 64-bit Flash Alpha only
sudo ldconfig.real -vp | grep flash
```

The last command should not output an error, but something like this:
```
	libflashsupport.so (libc6) => /usr/lib32/libflashsupport.so
	libflashplayer.so.0 (libc6) => /usr/lib/libflashplayer.so.0
```

Finally, you can remove the .c file if you wish:
```
rm flashsupport.c
```

---

### Post by megamoo on 2008-07-13
I had problems with with my x-fi sound card and i followed temujin's  guide to installing oss4 and i managed to get music playing (see a page or two ago in this thread).  

But i haven't used the ubuntu half of the computer for a week and now when i open Amarok i get the error 

"xine was unable to initialize any audio drivers". 
 
This was the problem before i fixed it, but i was trying many things and i can't remember what was the actual fix. I am 90% sure that i've deleted a file or done something to break it. :(

Please can someone help with a link or an idea for how to fix this issue, even an idea might jog my memory and ill figure out what i did before.
please please please help me ](*,)

---

### Post by mriedel on 2008-07-13
> Open Sound System is now free for personal and non-commercial use and comes with a license key that will allow you to run OSS. The license key is valid for up to 6 months at a time after which you will need to download and install OSS again

I'd rather wait a year for ALSA to bring out a driver for my x-fi and use my onboard sound meanwhile than update to OSSv4 under such conditions.

---

### Post by F-3582 on 2008-07-13
> **mriedel said:**
> I'd rather wait a year for ALSA to bring out a driver for my x-fi and use my onboard sound meanwhile than update to OSSv4 under such conditions.
Just run ossupdate once after installing the .deb and OSS4 will get "activated" for free. Forever.

EDIT: Temüjin, you might wanna add this to your guide. It is a very easy way to keep your OSS4 installation up-to-date, too.

---

### Post by mriedel on 2008-07-14
Hmh, I'm still kinda suspicious (it was originally releases as closed source, then that statement on the download page...). It is completely under GPL now, right?

---

### Post by F-3582 on 2008-07-14
It's been under GPL for a year, now. And they added the BSD license by the end of last year, if I recall correctly.

You might want to read this [Wikipedia article]("http://en.wikipedia.org/wiki/Open_Sound_System") and this [Insane Coding blog essay]("http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html") about OSS which explains the OSS discrepancy a little. I personally like OSS a lot more than ALSA and now that it even introduced software mixing, there's no way I'm gonna go back.

---

### Post by mriedel on 2008-07-14
Thanks, gonna read up there

---

### Post by Derviansoul on 2008-07-17
hello

I tried it, i got it working but i haven't got any surround with analog and the spdif wont work!!and the ossxmixer wont save the changes, giving me noise from the microphones every time that i restart. what i would like is to put alsa back again since oss4 support for spdif and surround isn't the best!!
can anyone tell me how to reconfigure alsa back again??

I'ven't got: sudo /etc/init.d/alsasound

i done this: 
```
sudo apt-get install alsa-base alsa-oss oss-compat
      sudo apt-get install libesd-alsa0

```

i remove all the blacklisted drivers on the end of: /etc/modprobe.d/blacklist/

and finally
```

sudo dpkg-reconfigure linux-sound-base

```

what else should i do? i can't seem to get alsa running again:S

please help



EDIT: After trying to install alsa with a fresh kernel, and failing the only way to do it, was to remove my kernel and rebuild it again, and recompile all the alsa drivers, thanks anyway.

---

### Post by benlucky on 2008-07-20
6. Navigate to where you have the deb file saved (e.g. if it's your home dir, cd ~/ ). Note the name of the file will be oss-linux_4.0-1016_amd64.deb if you downloaded that version
```
sudo dpkg -i oss-linux_v4.0-1016_i386.deb
sudo soundon
```

Thanks in advance for any help you can give, but I am new to Ubuntu. I had followed these directions last week and got my X-Fi card to work well enough with nearly all apps, playing music and video in many players. I got greedy, however, and wanted to get sound in Flash for youtube stuff. When I updated libflashsupport.so and got sound in Firefox 3 for the flash (momentary cheer) I then realized that I broke sound for any other application. 

I purged oss to reinstall per the directions in Addendum 4, but I get errors when I try to dpky the .deb file that had worked before. Here is what I get in the terminal:

```
ben@sprocketUB:~/Documents/Downloads$ sudo dpkg -i oss-linux-4.0-1016_amd64.deb 
Selecting previously deselected package oss-linux.
(Reading database ... 153732 files and directories currently installed.)
Unpacking oss-linux (from oss-linux-4.0-1016_amd64.deb) ...
 * Shutting down ALSA...                                                 [ OK ] 
Setting up oss-linux (4.0-1016) ...
Building OSS Modules for Linux-unknown 2.6.24-19-generic

OSS build environment set up for REGPARM kernels

Building module osscore
Failed to compile OSS
make -C /lib/modules/2.6.24-19-generic/build M=/usr/lib/oss/build modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.24-19-generic/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /usr/lib/oss/build/osscore.o
/bin/sh: scripts/genksyms/genksyms: not found
make[2]: *** [/usr/lib/oss/build/osscore.o] Error 127
make[1]: *** [_module_/usr/lib/oss/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Starting Open Sound System
Detected Creative SB X-Fi (EARLY BETA)
Detected Generic USB audio device (BETA)
Relinking OSS kernel modules for "2.6.24-19-generic SMP mod_unload "
This may take few moments - please stand by...

OSS build environment set up for REGPARM kernels

Building module osscore
Failed to compile OSS
make -C /lib/modules/2.6.24-19-generic/build M=/usr/lib/oss/build modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.24-19-generic/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /usr/lib/oss/build/osscore.o
/bin/sh: scripts/genksyms/genksyms: not found
make[2]: *** [/usr/lib/oss/build/osscore.o] Error 127
make[1]: *** [_module_/usr/lib/oss/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2

Relinking the OSS kernel modules failed

```

Again, I give thanks in advance for any ideas.

---

### Post by dancer58 on 2008-07-20
Just info
I am using Hardy and could not get alsa to work at all. Had many suggestions but nothing worked'
I installed oss 4.1 and sound works great

---

### Post by Roasted on 2008-07-21
Heh... I installed OSS, giving it a shot over the already-working Alsa. I got OSS to work, but I literally see NO advantage of it over Alsa. Some people have told me that it sounds better than Alsa, blah blah. Nah, it doesn't. Same damn thing.

Now, for simplicity reasons I want to go back to Alsa, and I can't. I have no device listed under sys-pref-sounds.

I'm using onboard audio. Realtek AC850 or something to that effect.

I even compiled the latest Alsa drivers. However, when I ./configure the alsa-drivers directory, it goes and goes and goes. Then I make, then sudo make install, and I get error 1, something about compiling. I was like, uh, okay?

How do I fix it? Or for that matter, how do I just get Alsa working?

---

### Post by fogelfink on 2008-07-21
I have tried following this thread - after many frustrations with ALSA & Pulse Audio I thought I give OSS a try - but now my system crashes every time I try to start OSS. 

Here's the output from my terminal at the point of crashing:

abraxas@abraxas:~$ sudo soundon
[sudo] password for abraxas: 
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.
abraxas@abraxas:~$ sudo rm /usr/lib/oss/starting
abraxas@abraxas:~$ sudo soundon
Segmentation fault
Loading module hdaudio failed - ignored
Segmentation fault
Loading module ossusb failed - ignored

What should I do now? I have posted a longer story of my struggle to get a working sound setup here: [http://ubuntuforums.org/showthread.php?t=865693](http://ubuntuforums.org/showthread.php?t=865693)
I am absolutely frustrated and have no idea how to get any sort of sound setup running again.
Your help is very much appreciated.

---

### Post by fogelfink on 2008-07-21
> **Derviansoul said:**
> hello

I tried it, i got it working but i haven't got any surround with analog and the spdif wont work!!and the ossxmixer wont save the changes, giving me noise from the microphones every time that i restart. what i would like is to put alsa back again since oss4 support for spdif and surround isn't the best!!
can anyone tell me how to reconfigure alsa back again??

I'ven't got: sudo /etc/init.d/alsasound

i done this: 
```
sudo apt-get install alsa-base alsa-oss oss-compat
      sudo apt-get install libesd-alsa0

```

i remove all the blacklisted drivers on the end of: /etc/modprobe.d/blacklist/

and finally
```

sudo dpkg-reconfigure linux-sound-base

```

what else should i do? i can't seem to get alsa running again:S

please help



EDIT: After trying to install alsa with a fresh kernel, and failing the only way to do it, was to remove my kernel and rebuild it again, and recompile all the alsa drivers, thanks anyway.

I have similar problems  getting  ALSA  back  to  work after  a failed attempt to switch to OSS.
I compiled ALSA following this thread from theubuntu  docs: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Now I get a sound at login window, but as soon as logging in, I am left with no sound!!!!  All options for sound devices in System/Preferences/Sound return the same error: > audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
Funnily enough I can still get error bleeps from the terminal - some sort of sound at least:confused:

Do I really have to recompile a new kernel to solve this issue?  I am fairly new to linux and am not sure if I know what I am supposed to do when I look at these instructions:  [https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/kernel-baking.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/kernel-baking.html)

Can anyone help me with this?  Any commands, with which I can figure out  what goes wrong?

I am going nuts over getting my sound to work - I primarily use my computer to play my music collection,  and am stranded staring at my screen trying  to follow tutorials for days on end, simply trying to get a sound out of my machine...
No success so far, so your  help is  greatly appreciated.

---

### Post by Derviansoul on 2008-07-21
Hello everyone

I really don't know any other way besides recompiling the kernel, i tried everything but nothing worked, i posted what i've done in this forum, it worked for me maybe it will work for any of us.

the link is [here]("http://ubuntuforums.org/showthread.php?t=861842")

if anyone tries that, or knows anything better please repost it, on that thread so it can help more people and the one that actually asked first.

regards

---

### Post by dhondu on 2008-07-22
I installed OSS to get my creative Xtremegamer sound card working. My motherboard has an nvidia chipset for audio which was working fine with ALSA.

I set the sound preferences under the system menu to use OSS for playback,movies, system sounds etc. But when i play an mp3 or test the system sounds I hear nothing on my speakers (they are connected to the creative sound card). If i connect them to the motherboard nvidia socket, everything works fine.

Does this mean OSS is using the motherboard chipset just like ALSA was,is there a way to get OSS to use my creative sound card instead. My BIOS has no option for turning off onboard sound.

thanks,

The ossinfo command gives the following output.

Version info: OSS 4.0 (b1016/200806162356) (0x00040003)
Platform: Linux/i686 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Chunnu)

Number of audio devices: 4
Number of audio engines: 9
Number of mixer devices: 2


Device objects
0: osscore0 OSS core services
1: ich0 Nvidia nForce2 interrupts=28024 (28024)
2: sbxfi0 Sound Blaster X-Fi (SB073x) interrupts=66168 (6616
PCI device 1102:0005, subdevice 1102:0031
3: ossusb0 USB audio core services


Mixer devices
0: ICH AC97 Mixer (ALC650) (Mixer 0 of device object 1)
1: Sound Blaster X-Fi (SB073x) (Mixer 0 of device object 2)

Audio devices
Nvidia nForce2 /dev/oss/ich0/pcm0 (device index 0)
Nvidia nForce2 S/PDIF out /dev/oss/ich0/spdout (device index 1)
Sound Blaster X-Fi (SB073x) output /dev/oss/sbxfi0/pcm0 (device index 2)
Sound Blaster X-Fi (SB073x) input /dev/oss/sbxfi0/pcmin0 (device index 3

---

### Post by Roasted on 2008-07-22
Hate to sound like an idiot here, but I'm going to... what's the soul advantage oss has over alsa? Can you youtube+amarok at the same time? or what? I read through these pages failing to understand a solid justification for the change.

---

### Post by Derviansoul on 2008-07-22
> **Roasted said:**
> Hate to sound like an idiot here, but I'm going to... what's the soul advantage oss has over alsa? Can you youtube+amarok at the same time? or what? I read through these pages failing to understand a solid justification for the change.

Hello

I might not be the best person to speak about it, but oss gives you the chance to play 2 sounds at the same time, but on it's side it has some big limitations at least for me, i have a hda_intel, my surround speakers never worked, ossxmix had this annoying thing of not saving the options and mixing up output to input channels on my sound card giving an annoying noise that even if i change them with ossxmixer when i rebooted i had to repeat all the configuration process.
Besides the spdif output wouldn't work with the oss drivers.

Besides being really thankfull to the creator of this post for spending his time creating this guide, he should be more honest about the limitations of oss.
and he should put another guide or a link to a way of reinstalling alsa drivers back again since it took me 2days to install them back again.

regards

---

### Post by mriedel on 2008-07-22
Is there no software mixing for oss4? It has playback for my x-fi but as hardware mixing isn't supported yet, i get no mixing at all. So it's basically ESD grabbing sound on startup and no application sound at all for me.

If there is no software mixing, can i set up some OSS4->Pulse->OSS4 configuration similar to ubuntu's default ALSA->Pulse->ALSA setup?

If both is impossible, is there a way to deactivate a sound device in oss4? I have an x-fi and onboard sound. oss uses the x-fi and shows only that in ossinfo. ossdetect -v shows my onboard sound too, though. I just have no clue how to use that instead.

---

### Post by fogelfink on 2008-07-22
Maybe this thread should have a warning at the outset of that once you installed OSS that's it.  That there is no way to reinstall ALSA without recompiling a new kernel.

What a mess sound is in Ubuntu is unbelieveable - i switched to linux 3 months ago and still have no working setup for my laptop.  And now after the attempt to use OSS, I can't really say that I am looking forward to use ALSA again, which is why I was looking for an alternative in the first place.  

Can it be that difficult to get two soundcards working under linux?  I simply would like to switch between an external USB soundcard (when it is connected) and the internal one, when I am on the move.  I have posted several times on this forum,but I have not come across a solution for this that would work.
I guess I'll learn how to recompile a kernel now...

---

### Post by Roasted on 2008-07-22
I can honestly say after my experiences with OSS and Alsa, that I have yet to find a reason to use OSS. I gave it a shot, but in the end, reinstalling Ubuntu to reinstate the use of Alsa was in order.

---

### Post by F-3582 on 2008-07-22
Even though I appreciate the efforts 4Front have taken to improve OSS4 (by the way: it works flawlessly for me) I'm really looking forward to the next version of PulseAudio. If it can really live up to the [hype]("http://0pointer.de/blog/projects/pulse-glitch-free.html") that is created around it at the moment, I'll be glad to switch back, even if that means recompiling the kernel or reinstalling Linux from scratch.

---

### Post by mriedel on 2008-07-23
I advise anyone to NOT use OSS4. It's all but an improvement over (the sadly misconfigured by default) ALSA/Pulse that Hardy ships with.

X-fi support is just a marketing gag. There's no mixing so it's the same as no support at all.

With my onboard card, I get worse sound quality than I got with ALSA/Pulse and some constant quiet yet annoying background noise.

Also, it's not completely open-source, ossxmix is an epic joke and the binaries are just messy (ossupdate etc).

Keep your hands off OSS and wait for ALSA to release X-fi drivers.

---

### Post by Roasted on 2008-07-23
Quite frankly, I like Alsa. It's easy, simple to use, and it just works. The only drawback is the fact that I have to close Amarok before starting youtube. However, that seems to have been oddly solved if I set Amarok to "autodetect" instead of "alsa." Still trying to figure out what pipeline it's using if the alsa one is being used by youtube... then wtf is amarok using? 

But, whatever. It just works. Maybe the future of pulse will bring something more to the table. But I think it's still important to give the developers credit for what work has been done. Saying Alsa sucks is a long stretch when people have worked on it to even get you sound - period! But, it does a good job, in my opinion. 

:guitar::guitar:

---

### Post by Yellow Pasque on 2008-07-23
I've never gone back to ALSA myself, but I don't recall anyone on the OpenSound forums saying they need to recompile their kernel to do so. I'll look into the matter further when I have time.

> I advise anyone to NOT use OSS4.
That's an overly-general statement based on your experience with the X-fi and an unidentified onboard audio. I've had no issues with my M-Audio Revo and ATI HDaudio (Realtek 888) using OSS 4.0; I can't comment on onboard sound quality, but the Revo sounds better (and works better) than it did with ALSA.

> Also, it's not completely open-source
What OSS4 Linux code is not open-source (besides the Lynx Studio card drivers)?

> Keep your hands off OSS and wait for ALSA to release X-fi drivers.
ALSA just put out another release and no X-fi support. You could be waiting a long time. An alternative is Creative's ALSA driver. It requires kernel recompile, but this guide walks you through it: [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

> If there is no software mixing, can i set up some OSS4->Pulse->OSS4 configuration similar to ubuntu's default ALSA->Pulse->ALSA setup?
vmix is a software mixer, and I believe OSS 4.0 still has softoss if you would prefer to try that (search on the OpenSound forums). As for Pulse, it doesn't work with OSS4 (the last time I checked) and I doubt it will anytime soon because their devs don't see it as a priority.
Pulse doesn't work with OSS4 and from what I've read from the devs, it's not even on their radar.

> he should put another guide or a link to a way of reinstalling alsa drivers back again
Who died and made me the designated guide guy? I've never reinstalled ALSA and don't plan to anytime soon, at least on my main system. Again, I'll look into it if I have some time.

---

### Post by coolbooks on 2008-07-24
I've been using OSS since I first started using linux. Alsa did work but the sound quality was so poor I went looking for something better and found OSS. Since then I've been using OSS on every linux installation. For those of you having problems with OSS remembering your settings there is a command called savemixer. If you run this as root/sudo after you change your OSS settings they will be remembered next boot up.

---

### Post by msmr on 2008-07-24
wtf does this mean 

ERROR: Module snd_usb_audio is in use
ERROR: Module snd_pcm is in use by snd_usb_audio
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_usb_lib is in use by snd_usb_audio
ERROR: Module snd_hwdep is in use by snd_usb_audio
ERROR: Module snd_rawmidi is in use by snd_usb_lib
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_seq_device is in use by snd_rawmidi
ERROR: Module snd_usb_audio is in use
ERROR: Module snd_pcm is in use by snd_usb_audio
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_usb_lib is in use by snd_usb_audio
ERROR: Module snd_hwdep is in use by snd_usb_audio
ERROR: Module snd_rawmidi is in use by snd_usb_lib
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_seq_device is in use by snd_rawmidi
ERROR: Module snd_usb_audio is in use
ERROR: Module snd_pcm is in use by snd_usb_audio
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_usb_lib is in use by snd_usb_audio
ERROR: Module snd_hwdep is in use by snd_usb_audio
ERROR: Module snd_rawmidi is in use by snd_usb_lib
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_seq_device is in use by snd_rawmidi
ERROR: Module snd_usb_audio is in use
ERROR: Module snd_pcm is in use by snd_usb_audio
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_usb_lib is in use by snd_usb_audio
ERROR: Module snd_hwdep is in use by snd_usb_audio
ERROR: Module snd_rawmidi is in use by snd_usb_lib
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_seq_device is in use by snd_rawmidi
ERROR: Module snd_usb_audio is in use
ERROR: Module snd_pcm is in use by snd_usb_audio
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_usb_lib is in use by snd_usb_audio
ERROR: Module snd_hwdep is in use by snd_usb_audio
ERROR: Module snd_rawmidi is in use by snd_usb_lib
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_seq_device is in use by snd_rawmidi
ERROR: Module snd_usb_audio is in use
ERROR: Module snd_pcm is in use by snd_usb_audio
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_usb_lib is in use by snd_usb_audio
ERROR: Module snd_hwdep is in use by snd_usb_audio
ERROR: Module snd_rawmidi is in use by snd_usb_lib
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_seq_device is in use by snd_rawmidi
ERROR: Module snd_usb_audio is in use
ERROR: Module snd_pcm is in use by snd_usb_audio
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_usb_lib is in use by snd_usb_audio
ERROR: Module snd_hwdep is in use by snd_usb_audio
ERROR: Module snd_rawmidi is in use by snd_usb_lib
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_seq_device is in use by snd_rawmidi
ERROR: Module snd_usb_audio is in use
ERROR: Module snd_pcm is in use by snd_usb_audio
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_usb_lib is in use by snd_usb_audio
ERROR: Module snd_hwdep is in use by snd_usb_audio
ERROR: Module snd_rawmidi is in use by snd_usb_lib
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_seq_device is in use by snd_rawmidi
ERROR: Module snd_usb_audio is in use
ERROR: Module snd_pcm is in use by snd_usb_audio
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_usb_lib is in use by snd_usb_audio
ERROR: Module snd_hwdep is in use by snd_usb_audio
ERROR: Module snd_rawmidi is in use by snd_usb_lib
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_seq_device is in use by snd_rawmidi
ERROR: Module snd_usb_audio is in use
ERROR: Module snd_pcm is in use by snd_usb_audio
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_usb_lib is in use by snd_usb_audio
ERROR: Module snd_hwdep is in use by snd_usb_audio
ERROR: Module snd_rawmidi is in use by snd_usb_lib
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_seq_device is in use by snd_rawmidi
ERROR: Module snd_usb_audio is in use
ERROR: Module snd_pcm is in use by snd_usb_audio
ERROR: Module snd_page_alloc is in use by snd_pcm
ERROR: Module snd_usb_lib is in use by snd_usb_audio
ERROR: Module snd_hwdep is in use by snd_usb_audio
ERROR: Module snd_rawmidi is in use by snd_usb_lib
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_seq_device is in use by snd_rawmidi
Failed to disable conflicting sound drivers
Reboot and try running soundon again


how do I disable the USB sound drivers?

---

### Post by Yellow Pasque on 2008-07-24
msmr, it means you still have ALSA modules loaded. See step 2 of the guide, and make sure you restart before attempting to install OSS4.

You may also need to purge the failed install (see the link towards the end of the guide).

---

### Post by Roasted on 2008-07-24
> **coolbooks said:**
> I've been using OSS since I first started using linux. Alsa did work but the sound quality was so poor I went looking for something better and found OSS. Since then I've been using OSS on every linux installation. For those of you having problems with OSS remembering your settings there is a command called savemixer. If you run this as root/sudo after you change your OSS settings they will be remembered next boot up.

Gotta ask... ever check PCM? High PCM can distort audio... That was my problem with Alsa. Kicked it down a bit, and suddenly Alsa is clear. :)

---

### Post by msmr on 2008-07-24
Okay, so the dpkg package for oss4 is there.

however when I do your command for the removal of said package I get this.

msmr@oh-god:/var/lib/dpkg/info$ sudo rm oss-linux*
rm: cannot remove `oss-linux*': No such file or directory
msmr@oh-god:/var/lib/dpkg/info$

---

### Post by msmr on 2008-07-24
I think I have ti removed howver, whenever I did step two isn't it supposed to say smoething... when I put the stuff in it just does.

```
msmr@oh-god:~$ sudo chmod 776 /etc/modprobe.d/blacklist
msmr@oh-god:~$ sudo cat /lib/linux-sound-base/noALSA.modprobe.conf >> /etc/modprobe.d/blacklist
msmr@oh-god:~$ sudo echo "blacklist snd_hda_intel 
> blacklist snd_mixer_oss 
> blacklist snd_pcm
> blacklist snd_timer
> blacklist snd_page_alloc
> blacklist snd_hwdep
> blacklist snd
> blacklist soundcore" >> /etc/modprobe.d/blacklist
msmr@oh-god:~$ 
```

---

### Post by Yellow Pasque on 2008-07-24
Step 2 will return nothing if successful. It's just a quick and dirty way to append some text to a file. You could just as easily open the file with gksudo gedit, paste the blacklist commands at the end, and save and quit.

---

### Post by wingnux on 2008-07-24
This one worked WAAAAAAY better than the full switch to pulseaudio! Thank you VERY MUCH!

---

### Post by Shardsofmetal on 2008-07-25
Is it possible in KDE to get a visual mixer that sits in the tray that controls the main volume (either vmix0-vol or pcm1). Also, is it possible to make my volume up/down buttons control that volume? I did this in Gnome with your instructions, but so far have been unsuccessful in KDE. Kmix launches whenever I press a volume button, but shows no available mixers. I use ossxmix for any advanced mixing, but would like easy access to simply turn up/down the volume. Thanks

---

### Post by coolbooks on 2008-07-25
Yes Roasted I turned down the pcm. I tried everything to get it better. Sound always came out scratchy till I did the switch.

---

### Post by Yellow Pasque on 2008-07-25
> **Shardsofmetal said:**
> Is it possible in KDE to get a visual mixer that sits in the tray that controls the main volume (either vmix0-vol or pcm1). Also, is it possible to make my volume up/down buttons control that volume? I did this in Gnome with your instructions, but so far have been unsuccessful in KDE. Kmix launches whenever I press a volume button, but shows no available mixers. I use ossxmix for any advanced mixing, but would like easy access to simply turn up/down the volume. Thanks

They're working on it. If you're capable of building your own kdemultimedia package, you can apply the patch yourself. IIRC, kmix is integrated in that package, so unfortunately, it's more complicated than it should be.
[http://bugs.kde.org/show_bug.cgi?id=166591](http://bugs.kde.org/show_bug.cgi?id=166591)

FWIW, I got kmix working on Kubuntu 8.04 (KDE 3.5.x) without any patching on my stepdad's PC by simply doing the reconfigure linux-sound-base step. That had an Audigy (LS?) in it. I guess it had some sort of volume control that ended up controlling the master volume.

---

### Post by Shardsofmetal on 2008-07-25
I have the patch and the tarball. Can someone tell me the exact command to type to patch the file? Thanks

Edit: Or, if it's not too much work, if someone wants to upload a patched tarball that would be even easier...

---

### Post by Taladel on 2008-07-25
Okay, I'm pretty new to Ubuntu and I'm trying to get my Creative X-Fi card to work.

I get to step 6 and everything's groovy.

However, when installing the package, I get this:

```
taladel@ubuntu:~/Desktop$ sudo dpkg -i oss-linux-4.0-1016_amd64.deb
Selecting previously deselected package oss-linux.
(Reading database ... 98481 files and directories currently installed.)
Unpacking oss-linux (from oss-linux-4.0-1016_amd64.deb) ...
 * Shutting down ALSA...                                                 [ OK ] 
Setting up oss-linux (4.0-1016) ...
Building OSS Modules for Linux-unknown 2.6.24-19-generic

OSS build environment set up for REGPARM kernels

Building module osscore
Building module ali5455
Building module allegro
Building module als300
Building module als4000
Building module apci97
Building module atiaudio
Building module audigyls
Building module audioloop
Building module audiopci
Building module cmi8788
Building module cmpci
Building module cs4280
Building module cs4281
Building module digi32
Building module digi96
Building module emu10k1x
Building module envy24
Building module envy24ht
Building module fm801
Building module geode
Building module hdaudio
Building module hdsp
Building module ich
Building module imux
Building module lynxone
Building module lynxtwo
Building module maestro
Building module neomagic
Building module ossusb
Building module riptide
Building module s3vibes
Building module sblive
Building module sbxfi
Building module softoss
Building module solo
Building module sonorus
Building module trident
Building module via8233
Building module via97
Building module vortex
Building module ymf7xx
depmod -a
-----------------------------
Detected Creative SB X-Fi (EARLY BETA)
Detected Generic USB audio device (BETA)
-----------------------------

Starting Open Sound System
Previous OSS modules were for a different kernel version - removed
Relinking OSS kernel modules for "2.6.24-19-generic SMP mod_unload "
This may take few moments - please stand by...

OSS build environment set up for REGPARM kernels

Building module osscore
Building module ali5455
Compiling module ali5455 failed
make -C /lib/modules/2.6.24-19-generic/build M=/usr/lib/oss/build modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/lib/oss/build/ali5455.o
In file included from /usr/lib/oss/build/module.inc:245,
                 from /usr/lib/oss/build/ali5455.c:18:
/usr/lib/oss/build/osscore_symbols.inc:180: error: redefinition of ‘____versions’
/usr/lib/oss/build/osscore_symbols.inc:1: error: previous definition of ‘____versions’ was here
make[2]: *** [/usr/lib/oss/build/ali5455.o] Error 1
make[1]: *** [_module_/usr/lib/oss/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2

Relinking the OSS kernel modules failed
```

I'm not exactly sure what to do from here. This is the second time I've tried installing the package and get the same error both times.

Thanks in advance!

---

### Post by Yellow Pasque on 2008-07-25
> **cdos said:**
> I've noticed that youtube won't work in Firefox 3 while ESD is running.  So I end up having to kill ESD and restart Firefox.

I'm not able to reproduce the issue with FF 3.0.1 and the latest OSS4.1 code. Swiftweasel3 kills ESD upon startup (you can fix this by editing the swiftweasel startup script in /usr/local/bin)

---

### Post by msmr on 2008-07-26
continuing my retarded issues with sound.

I have enabled my intergrated sound in the BIOS, which in theory should override my X-FI card.

and I once again did the OSS install featuers (...i decided ASLA wasn't worth the trouble...or meh if it is, I haven't installed enough stuff that a simple reinstall with the X-FI card out wouldn't be too difficult, but I wanted to try)

however, I installed everyting and I have not gotten any sound.

...suggestions?

---

### Post by Yellow Pasque on 2008-07-26
msmr: Delete the X-fi line in installed_devices or relink /dev/dsp ([http://www.opensound.com/wiki/index.php/Tips_And_Tricks#Changing_the_default_sound_output](http://www.opensound.com/wiki/index.php/Tips_And_Tricks#Changing_the_default_sound_output))
```
sudo soundoff
gksudo gedit /usr/lib/oss/etc/installed_devices
sudo soundon
```

---

### Post by Roasted on 2008-07-26
What advantages have you folks seen with OSS?

Have you just gotten better sound quality?
Has your max volume been increased?

---

### Post by Taladel on 2008-07-26
> **Roasted said:**
> What advantages have you folks seen with OSS?

Have you just gotten better sound quality?
Has your max volume been increased?

Well, ALSA doesn't support my card. But OSS4 does. For me it was a matter of necessity.

---

### Post by Roasted on 2008-07-26
> **Taladel said:**
> Well, ALSA doesn't support my card. But OSS4 does. For me it was a matter of necessity.

Hey, that works. But I'm sure quite a few people have switched with Alsa in working condition for them. That's why I wonder if they found some sort of additional advantage with it.

---

### Post by Lovok on 2008-07-26
I installed this the first time around, and everything worked fine. Everything still works fine, but since AmaroK is being funny, I wanted to reinstall this because of the xine error thing, etc etc...

Anyway, the problem I have now is I can't re execute 
```
sudo dpkg -i oss-linux-v4.0-1016_amd64.deb
```
nor can I double click it.
When I double click : 
```
 Could not open 'oss-linux-v4.0-1016_amd64.deb'
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.
```
and when I run it in the terminal :
```
dpkg: error processing oss-linux-v4.0-1016_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 oss-linux-v4.0-1016_amd64.deb
```

As a result, soundon isn't recognized as a command, nor is ossxmix.
I am running Hardy Heron 64bit.

---

### Post by Yellow Pasque on 2008-07-26
Lovok, have you removed the original install?
```
sudo dpkg -r oss-linux
```
Also, re-download the file to make sure it's not corrupt.

---

### Post by Lovok on 2008-07-27
I followed the link under "ADDENDUM3: Recovering From a Failed .deb Install", and none of those instructions included that bit of code. I'll replace 
"sudo rm oss-linux*" with what you're suggesting and see what happens.
I did redownload from the same source, but it's also the same download that worked the first time around.

EDIT: I tried that line of code in the same directory as the .deb I downloaded is located. I got this message :
```
dpkg - warning: ignoring request to remove oss-linux which isn't installed.
```
Also, since my reboot, I've lost sound.
I downloaded the tar.gz2, perhaps doing it from source will help. I have limited Linux experience, and my intuition suggests I simply put the files in the corresponding folders. I shall try this.
I did this, extracted all the files to their locations (oddly enough, there were no files there.. so I don't actually have any oss* files installed). I didn't want to reboot, knowing that something bad would happen :p so I went into init 1, and resumed normal boot into init 2. All the files are gone again, and I still have no sound.
I copy/pasted in nautilus using gksudo.
I followed step 7, still nothing. (never mind this line, it was step 7. from the 2 addendum)
Trying from source again, but this time I will run install.sh x.x
Everything compiled, I can execute things like soundon and ossxmix, but still no sound. I have yet to reboot :|. 
Before I do, here is ossdetect -v and ossinfo respectively :
```
Detected Creative SB X-Fi (EARLY BETA)
Detected Generic USB audio device (BETA)
```
```
Version info: OSS 4.0 (b1016/200807242103) (0x00040003) 
Platform: Linux/x86_64 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 (ZordonMKIII)

Number of audio devices:	2
Number of audio engines:	2
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: sbxfi0 Sound Blaster X-Fi (SB046x/067x/076x) interrupts=18200 (18200)
    PCI device 1102:0005, subdevice 1102:0021
 2: ossusb0 USB audio core services


Mixer devices
 0: Sound Blaster X-Fi (SB046x/067x/ (Mixer 0 of device object 1)

Audio devices
Sound Blaster X-Fi (SB046x/067x/076x) output  /dev/oss/sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi (SB046x/067x/076x) input  /dev/oss/sbxfi0/pcmin0  (device index 1)
```
I suppose I should mention I am using a Creative Labs x-fi platinum card, and didn't install any drivers prior.

YAY : extracting the tar.bz2 and then actually installing it worked :) at least on the soft reboot it does..
xine still fails with AmaroK, but I just won't use it :)
Did a full reboot, and I still have sound. Success \o/

---

### Post by fordfasterr on 2008-07-29
I have a brand new PC from Best Buy, Compaq Presario Model: SR5510F.

Dual Core AMD X2 5000 with 2 gig ram, 500 gig HDD, and dvd/ram drive.

I have the Nvidia Display drivers working via the System > Hardware Drivers icon that has an Nvidia object ... 

I have followed the steps on page 1 of this thread to configure the audio and it worked perfectly.  (the drivers did not work after a fresh Kubuntu install).

The only thing that I cannot get working is the on-board NIC.  At this point I have an old PCI nic installed that worked immediately after a reboot.

Hopefully I can get the on-board NIC to work, but I don't know how to get it going... It is detected, but it will not pick up an IP from my router.

---

### Post by joy99 on 2008-07-30
Hello. First of all, thank you for your work.

I've installed all as you say, and it works fine, but I have a problem with Zattoo: I can't hear it. Is is possible to say, somehow, that it has to use OSS in stead of Alsa? I've looked for the option in the preferences of Zattoo, but there is no option. The rest of the things works fine!

Thanks a lot!

---

### Post by fordfasterr on 2008-07-30
> **joy99 said:**
> Hello. First of all, thank you for your work.

I've installed all as you say, and it works fine, but I have a problem with Zattoo: I can't hear it. Is is possible to say, somehow, that it has to use OSS in stead of Alsa? I've looked for the option in the preferences of Zattoo, but there is no option. The rest of the things works fine!

Thanks a lot!

I can hear sound from youtube, but I can't hear any dvd sounds, even when playing directly from the iso files.

=(  I'm using mplayer / kaffeine

---

### Post by pokera75 on 2008-07-31
Thank you for the great guide. So far it has worked. However, I need to switch my default audio device in oss. And just reading the relinking kernels on the oss web page makes me very nervous.  My sound card showed up in the sound on and every where else along with my onboard audio. Right now the oss sound is being played through the onboard audio and I want it on the Sound card. My sound Card is a Soundblaster X-FI XtremeGamer. 

If you could toss an addendum to the original post about switching the audio devices, I think it would solve many problems.

---

### Post by Yellow Pasque on 2008-07-31
pokera75, good idea. I think I understand the basics behind this, but let me make sure I have it right (I'm pretty drunk right now). In the mean time, if you're not using your onboard audio, I suggest disabling it in the BIOS and running:\
```
sudo soundoff
sudo ossdetect -v
sudo soundon
```

---

### Post by ham213 on 2008-07-31
OMG!!!! I can't thank you enough for this post!!!!!

For some reason, ALSA just up and crashed on my system after an update about a month ago and ALL attempts to revive it failed. I was stuck going back to Micro$oft Winblows XP for video, DVD, and anything audio.

Not only did the instructions work perfectly for my SB Audigy 2, the OSS4 mixer allows for much greater control over the tone and overall sound of my Audigy!!!!

I am totally rocking out to Buckethead once again and in much finer tone than ALSA thanks to your fine instruction.

Thank you, thank you, thank you!

---

### Post by pokera75 on 2008-08-01
Wow I feel dumb. I should have disabled the Onboard Audio from the beginning seeing how it wasn't in use. Maybe if you put that on the original post, it would minimize some of the people with problems.

---

### Post by Muscar on 2008-08-01
I'm a stupid an ignorant shithead  so I installed this thinking it would get my wine sounds working, but now I want to change back to ALSA, how do I do this?

---

### Post by ressac on 2008-08-05
i try evrething but i still don't have a sound in flash, please help me :(

---

### Post by lewisifer on 2008-08-06
I tried this, and I got Ubuntu sound to work. Meaning, when I login, I hear the login music.
However, Amarok does not work "Failed to initialize XINE", and VLC does not give me any sound whatsoever. Neither does the flash plugin in Firefox. I have chosen OSS as the preferred output device under VLC and Amarok shows only XINE as the engine, but I've chosen OSS as the device in there as well.

I have chosen OSS under System > Preferences > Sound too.

Interestingly enough, when I go to the Sounds tab, and click on the play button to play the sounds, I get to hear them. However, When I go to the Devices tab and click Test on any of the Listed items(Sound Events, Music and Movies, etc), I get this error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.


Any ideas would be much appreciated. I'm a noob, so details would be great.


Thanks.

---

### Post by Taladel on 2008-08-06
What happens is that OSS uses a module called vmix to handle multiple programs making sound at the same time. For some reason, vmix isn't attaching to the output, and at build 1016, the devs didn't include the overrides to make it attach. So instead, let's just do this: 
 
[]("http://www.fileupyours.com/view/77985/oss-linux-4.1-080705_amd64.deb")[http://www.fileupyours.com/view/77985/oss-linux-4.1-080705_amd64.deb](http://www.fileupyours.com/view/77985/oss-linux-4.1-080705_amd64.deb) 
contains a compiled copy of newest source from hg repo. 
 
Download this, then run 'osstest' to identify the process using OSS. Note the process number, and then run 'kill (process#)' without the parenthesis. You may have to sudo kill.

After that, run ```
sudo dpkg -i oss-linux-4.1-080706_amd64.deb
```in your download directory. It should upgrade your OSS installation.

If the upgrade fails, run the steps from [this]("http://4front-tech.com/forum/viewtopic.php?t=2054") post, and do dpkg -i again.
 
After install, run 'ossinfo -v2'.

If it doesn't show any "vmix" engines (it should, however), than run:

```
vmixctl attach /dev/dsp
gksudo gedit ~/etc/rc.local
```and add 'vmixctl attach /dev/dsp' to the end of the file.

Also, check out [this page]("http://4front-tech.com/forum/viewtopic.php?t=2792") where I try and work through this problem with one of the developers.

---

### Post by Yellow Pasque on 2008-08-06
> **ressac said:**
> i try evrething but i still don't have a sound in flash, please help me :(
You downloaded the libflashsupport file and gunzipped it and placed it in /usr/lib (or /usr/lib32 if you're using amd64 version)?

> but now I want to change back to ALSA, how do I do this?
I'll work on a guide for this (no, really, I mean it this time :P). Basically, it should just consist of removing OSS4, undoing the blacklisting, reconfiguring linux-sound-base, and installing libesd0-alsa, alsa-base, and alsa-oss. Then rebuild the ALSA kernel modules using: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.
Make sure you /dev/dsp pointing to the correct device and use cat /dev/sndstat to see what has your sound tied up (my money's on esd).

---

### Post by Yellow Pasque on 2008-08-07
[SIZE="4"]**Reverting to ALSA**[/SIZE]
If, for some reason, you want to go back to ALSA, here is the procedure: (I tested this myself on my test system)
```
sudo soundoff
sudo dpkg -r oss-linux
sudo dpkg-reconfigure linux-sound-base
sudo apt-get -y install libesd-alsa0 alsa-oss alsa-base libsdl1.2debian-alsa
gksudo gedit /etc/modprobe.d/blacklist
```
The preceding command opens your blacklist file in the text editor. Delete all the lines from "blacklist snd-seq" down to the end of the file (make sure the last line in the file refers to a snd module and was not added by another program).
Restart the PC.
Now, re-install ALSA kernel modules with this script: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
Go to System -> Preferences -> Sounds and select Autodetect or ALSA
Any applications that you configured for OSS should be changed back to ALSA, although they should work with the alsa-oss wrapper.

Optionally, you can setup and configure PulseAudio. I have no experience with this, but I have seen guides for it (use search). If you do, remember to install the Pulse-compatible libflashsupport package:
```
sudo apt-get install libflashsupport
```

---

### Post by itsjareds on 2008-08-11
Ok, a few questions:

1. My sound doesn't go into the headphones when they're plugged in. It just plays out of the computer. Any way to fix that? Before, when I was using ALSA, it only went through the headphones and not the computer :D

2. How do I get it to work via the volume control?

---

### Post by coolen on 2008-08-11
Are they actually coming through your headphones, or just not muting your speakers?

OSS doesn't have jack sensitivity. To get around this, I wrote a few simple scripts to toggle/mute/unmute the internal speakers, and used xbindkeys to create shortcuts.

```
#! /bin/bash

if [[ $(ossmix -c | head -n 2 | grep ON) == '' ]]
then ossmix jack.int-speaker.mute ON
else ossmix jack.int-speaker.mute OFF
fi
```

This may not work for you. It depends on the fact that my internal speakers occupy the first two lines of output. May be useful to you, though.

For the volume control, did you follow the instructions in the first addendum? I had to reboot to get it all working.

---

### Post by beerfan on 2008-08-11
Temüjin,

I am following your guide step by step in preparation to replace ALSA with OSS. I notice that Ubuntu uses a modular blacklist system with OSS currently blacklisted in /etc/modprobe.d/blacklist-oss so you should probably update your guide to say something like the following.

```

sudo rm /etc/modprobe.d/blacklist-oss
sudo ln -s /lib/linux-sound-base/noALSA.modprobe.conf /etc/modprobe.d/blacklist-alsa

```

This would make reverting easier.

---

### Post by beerfan on 2008-08-11
**HOLY MOLY**

I was getting extremely tired of the hissing noise coming out of my speakers in Ubuntu Hardy with that garbage that comes installed by default. I now have OSS4 installed and I'm listening to some music in Rhythmbox and I cannot believe the difference. I'm not really an audiophile but the difference is incredible. When there's no sound playing my speakers are *silent* and when music is playing the quality is amazing.

I still have some things to resolve apparently (volume controls) but it'll be worth it. I was ready to face complete silence rather than continue suffering from the hissing noise.

---

### Post by Yellow Pasque on 2008-08-11
> **beerfan said:**
> Temüjin,

I am following your guide step by step in preparation to replace ALSA with OSS. I notice that Ubuntu uses a modular blacklist system with OSS currently blacklisted in /etc/modprobe.d/blacklist-oss so you should probably update your guide to say something like the following.

```

sudo rm /etc/modprobe.d/blacklist-oss
sudo ln -s /lib/linux-sound-base/noALSA.modprobe.conf /etc/modprobe.d/blacklist-alsa

```

This would make reverting easier.

This is part of what dpkg-reconfigure linux-sound-base does.

---

### Post by beerfan on 2008-08-11
[Edit: False alarm. After rebooting I now have a mixer]

My issues to resolve are bigger than I thought.

I have sound in Rhythmbox and VLC. However, I have no mixer device.

sudo ossdetect -v
Detected Nvidia High Definition Audio (MCP55)
Detected Generic USB audio device (BETA)

ossinfo
No /dev/mixer device available in your system.
Perhaps Open Sound System is not installed or running.

The first time I installed the deb it complained that some drivers could not be removed and suggested rebooting. I did that and the installation proceeded but seemed to not install correctly due to mpd running and being able to unload ESD or something. Even so, sound was working in those apps.

Since then I have manually uninstalled oss-linux-4.0 and reinstalled. It reported no errors after installing this time. However, I still have no mixer device.

---

### Post by beerfan on 2008-08-12
I can't imagine going back to ALSA now that I've heard the difference in the OSS4 drivers. I've created an entry on Ubuntu Brainstorm to promote supporting OSS4 in Intrepid.

[http://brainstorm.ubuntu.com/idea/12127/](http://brainstorm.ubuntu.com/idea/12127/)

Go hit it if you care. I don't know if that Brainstorm actually works but I guess it can't hurt.

---

### Post by SeaJey on 2008-08-14
**kde** 4.1 mini-howto:

Execute in terminal:
```
mv /usr/lib/oss/lib/libsalsa.so.2.0.0 /usr/lib/oss/lib/libsalsa.so.2.0.0.bak
ldconfig 
```

Install latest gstreamer and plugins from ubuntu ppa:
deb [http://ppa.launchpad.net/gstreamer-team/ubuntu](http://ppa.launchpad.net/gstreamer-team/ubuntu) hardy main
Also uninstall gstreamer-alsa (for sure)

Move gstreamer to the first place in phonon-backends list in "Sound" section of "System Settings".

And sound is magically working now! Volume control at application level too.
Tested with juk-kde4 and dragon player.

Some issues still remain:
Sound configs can be changed only via ossxmix or ossmix.
qtconfig says that there is no gstreamer phonon-backend at all - but it could be only (k)ubuntu trouble.

---

### Post by Yellow Pasque on 2008-08-14
Hey SeaJey, is kmix working for you?

---

### Post by pokipoki08 on 2008-08-15
Headphone jack volume is *very* low, when I unplug the headphone there is no sound at all.

Using ICH7 on-board audio, High Definition Audio STAC9221, on an iMac LCD Intel.

[COLOR="RoyalBlue"]Is there a way to increase the volume?[/COLOR]

```


**ossinfo**

Version info: OSS 4.0 (b1016/200807241529) (0x00040003) 
Platform: Linux/i686 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 (teacher-desktop)

Number of audio devices:	8
Number of audio engines:	12
Number of mixer devices:	1

Device objects
 0: osscore0 OSS core services
 1: hdaudio0 Intel HD Audio interrupts=45034 (45034)
    HD Audio controller Intel HD Audio
    Vendor ID    0x808627d8
    Subvendor ID 0x83847680
     Codec  0: STAC9221 A1 (0x83847680/0x106b1600)
 2: ossusb0 USB audio core services

Mixer devices
 0: High Definition Audio STAC9221 A1 (Mixer 0 of device object 1)

Audio devices
HD Audio play front               /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio play center/LFE          /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio play rear                /dev/oss/hdaudio0/pcm2  (device index 2)
HD Audio play side                /dev/oss/hdaudio0/pcm3  (device index 3)
HD Audio play spdif-out           /dev/oss/hdaudio0/spdout0  (device index 4)
HD Audio rec rec1mux              /dev/oss/hdaudio0/pcmin0  (device index 5)
HD Audio rec rec2mux              /dev/oss/hdaudio0/pcmin1  (device index 6)
HD Audio rec spdifin              /dev/oss/hdaudio0/spdin0  (device index 7)

**ls -l /dev/dsp**
/dev/dsp -> /dev/oss/hdaudio0/pcm0


```

---

### Post by SeaJey on 2008-08-15
> **Temüjin said:**
> Hey SeaJey, is kmix working for you?
Well, kmix-kde4 is useless, but I'll check kmix-kde3 when kde 3.5.10 will be out.

---

### Post by Nitrius on 2008-08-15
Just wondering, why should i use this audio solution and not say, the offical linux drivers from Creative? Got a Creative X-FI Xtrememusic, and just went through this guide, and i got sound working, or atleast so far.

Am just wondering what the difference is?


Edit: It seems that there can only be one program at a time playing sound, is there a way of fixing this?

---

### Post by Philio on 2008-08-19
I followed the guide and have desktop sound, video/audio playback sound all working find. I can't seam to get any sound in Flash though, tried both methods in the guide but no joy...

Any ideas?

---

### Post by Philio on 2008-08-19
> **Nitrius said:**
> Just wondering, why should i use this audio solution and not say, the offical linux drivers from Creative? Got a Creative X-FI Xtrememusic, and just went through this guide, and i got sound working, or atleast so far.

Am just wondering what the difference is?


Edit: It seems that there can only be one program at a time playing sound, is there a way of fixing this?

Well not tried it with 8.04, but 7.10 + the creative driver was a nightmare, it made my system unstable.

It also took a while to install, as you had to recompile the kernel.

---

### Post by wingnux on 2008-08-19
Anyone having choppy sound after performing this change? I'm really happy with oss4 but sound on dosbox is AWFUL! =/

---

### Post by archon231 on 2008-08-20
Hi, I am a n00b, so I'll get right to it;

I have a Creative X-Fi Xtremegamer with no sound in Ubuntu.

I installed OSS using the guide, the test ran with no errors. No sound comes from the first four tests (which makes sense because I believe they are using my onboard card which I am not plugged into)

```
Sound subsystem and version: OSS 4.0 (b1016/200807241529) (0x00040003)
Platform: Linux/i686 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/hdaudio0/pcm0 (audio engine 0): HD Audio play front
Note! Device is in use (by PID 0/VMIX) but will try anyway
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47961.00 Hz (-0.08%)> 
/dev/oss/hdaudio0/pcm1 (audio engine 1): HD Audio play rear
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47968.00 Hz (-0.07%)> 
/dev/oss/hdaudio0/pcm2 (audio engine 2): HD Audio play center/LFE
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47968.00 Hz (-0.07%)> 
/dev/oss/hdaudio0/pcm3 (audio engine 3): HD Audio play side
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47968.00 Hz (-0.07%)> 
/dev/oss/hdaudio0/pcm4 (audio engine 4): HD Audio play pcm4
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47968.00 Hz (-0.07%)> 
/dev/oss/hdaudio0/spdout0 (audio engine 5): HD Audio play spdif-out
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47968.00 Hz (-0.07%)> 
/dev/oss/hdaudio0/pcmin0 (audio engine 6): HD Audio rec mix
- Skipping input only device
/dev/oss/hdaudio0/pcmin1 (audio engine 7): HD Audio rec mix
- Skipping input only device
/dev/oss/hdaudio0/pcmin2 (audio engine 8): HD Audio rec mix
- Skipping input only device
/dev/oss/hdaudio0/spdin0 (audio engine 9): HD Audio rec spdifin
- Skipping input only device

```

Then I get sound with the next test (since it is using my Xtremegamer, which my speakers are plugged into) however I get no sound outside of the stock stuff that plays during the test. Even if Rhythmbox is running at the same time.

```
*** Scanning sound adapter #1 ***
/dev/oss/sbxfi0/pcm0 (audio engine 14): Sound Blaster X-Fi (SB073x) output
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47517.00 Hz (-1.01%)> 
/dev/oss/sbxfi0/pcmin0 (audio engine 15): Sound Blaster X-Fi (SB073x) input
- Skipping input only device

*** All tests completed OK ***
```

My question is obviously, why? But I'm going to guess that I need to set OSS to use my 'sound adapter #1' but I have no clue how to. I tried messing with the volume in ossxmix to no avail. I also noticed that on my 'task bar' the sound icon next to the ossxmix icon is muted and I receive this msg from it when I click it; 

"No volume control GStreamer plugins and/or devices found."

Other than that, here is the output from ossinfo

```
Version info: OSS 4.0 (b1016/200807241529) (0x00040003) 
Platform: Linux/i686 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 (aramaki-ubuntu)

Number of audio devices:	12
Number of audio engines:	16
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 Intel HD Audio interrupts=420611 (420611)
    HD Audio controller Intel HD Audio
    Vendor ID    0x8086293e
    Subvendor ID 0x1458a002
     Codec  2: ALC885 (0x10ec0885/0x1458a002)
 2: sbxfi0 Sound Blaster X-Fi (SB073x) interrupts=144633 (144633)
    PCI device 1102:0005, subdevice 1102:0031
 3: ossusb0 USB audio core services


Mixer devices
 0: High Definition Audio ALC885 (Mixer 0 of device object 1)
 1: Sound Blaster X-Fi (SB073x) (Mixer 0 of device object 2)

Audio devices
HD Audio play front               /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio play rear                /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio play center/LFE          /dev/oss/hdaudio0/pcm2  (device index 2)
HD Audio play side                /dev/oss/hdaudio0/pcm3  (device index 3)
HD Audio play pcm4                /dev/oss/hdaudio0/pcm4  (device index 4)
HD Audio play spdif-out           /dev/oss/hdaudio0/spdout0  (device index 5)
HD Audio rec mix                  /dev/oss/hdaudio0/pcmin0  (device index 6)
HD Audio rec mix                  /dev/oss/hdaudio0/pcmin1  (device index 7)
HD Audio rec mix                  /dev/oss/hdaudio0/pcmin2  (device index 8)
HD Audio rec spdifin              /dev/oss/hdaudio0/spdin0  (device index 9)
Sound Blaster X-Fi (SB073x) output  /dev/oss/sbxfi0/pcm0  (device index 10)
Sound Blaster X-Fi (SB073x) input  /dev/oss/sbxfi0/pcmin0  (device index 11)
```


Thanks for any help :)

---

### Post by kerunt on 2008-08-22
Hey everyone, trying to get my X-Fi Xtreme Audio card to work on 8.04 with no luck :(.

I'm following the guide step by step. When I run ```
sudo apt-get remove alsa-base alsa-oss oss-compat
``` I get this: ```
yura@ybix:~$ sudo dpkg -i oss-linux-4.0-1016_i386.deb
(Reading database ... 117029 files and directories currently installed.)
Preparing to replace oss-linux 4.0-1016 (using oss-linux-4.0-1016_i386.deb) ...
No mixers in the system
* Shutting down ALSA...                                                [ OK ] 
Unpacking replacement oss-linux ...
uSetting up oss-linux (4.0-1016) ...
Building OSS Modules for Linux-unknown 2.6.24-19-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

I then tried ```
sudo soundon
``` and got this: ```
yura@ybix:~$ sudo soundon
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue

```

Some more output from suggested commands:```
yura@ybix:~$ sudo ossdetect -v
/usr/lib/oss/etc/devices.list: No such file or directory
yura@ybix:~$ ossinfo
No /dev/mixer device available in your system.
Perhaps Open Sound System is not installed or running.


```

Audio is the last thing keeping me from completely converting to Ubuntu - any help would be greatly appreciated!

---

### Post by Yellow Pasque on 2008-08-22
kerunt,
[http://ubuntuforums.org/showpost.php?p=5055305&postcount=105](http://ubuntuforums.org/showpost.php?p=5055305&postcount=105)

---

### Post by kerunt on 2008-08-22
Temüjin, thank you. Will try it out when I get home tonight.

---

### Post by C.U.B.E.M.A.N on 2008-08-22
Re: Hardy 8.04 & OSS4 (Alternative to ALSA)

MANY thanks, worked almoast perfectly,  	
Temüjin you have made my day a good one.:popcorn:

---

### Post by tlanfer on 2008-08-23
Hi there,
some weeks ago i tested oss4 and really liked it, especially for the sound quality.
But there is one thing that keeps me from using it permanently: I have three computers. That is a laptop, my desktop pc and my home theathe pc.
But it is only the htpc that is connected to my stereo. Right now im streaming all music from all sources to my htpc using pulseaudio. That works great, except that the sound quality is not the best.
So is there a trick to achieve the same with oss?
Using mpd for music is no alternative, i want ALL of my sound through network.

Thanks

---

### Post by bishamon on 2008-08-23
Hi

A question who got their OSS working. Are you only able to play one media file at a time? I use OSS only because of using my Creative Xfi. Alsa still can't bring it up. On my previous installation, I have finally gotten my OSS4 up and running for my Creative XFi but I find that at any one time, only one media can be played. So if I have 2 windows playing youtube video, only the 1st one will have audio, and it will hold it until I close that windows before "releasing" the control. In fact closing tab in FF is not good enough at times. I have to close the entire browser in order for mplayer to regain the audio. Anyone else facing this? Or is because of Alsa related drivers conflict it? I see that most ppl on this thread had Alsa setup first before moving to OSS.

If this is a "side-effect" on OSS just for my Xfi, think I would prefer to go back to Alsa plus my noboard sound for now. 

I have just reinstall my OS (debian sid) again and I have forgotten to enable my onboard sound. So no sound was installed on setup. A side-track question if anyone knows how to make the OS auto detect the onboard sound and install all the necessary components. I realise in all my years with  linux, I have never configure sound drivers manually. Mostly work on OS installation. I have install linux-sound-base and alsa-oss but I believe there is more than that. 

Thanks

bishamon

---

### Post by toemos on 2008-08-24
hey, dont know if this has already been covered, but i couldnt find anything after my brief search..

everything works great except that i can here a faint buzz when i use my mouse... strange i thought.
i mildly remember reading something somewhere about this, but i cant seem to find it now. 

any help?

---

### Post by b7o0or on 2008-08-24
thanx my frinde


[http://www.7ala-alkon.com/vb](http://www.7ala-alkon.com/vb)

---

### Post by Yellow Pasque on 2008-08-24
To answer some questions:
- The OSS devs are working on making it compatible with PulseAudio right now. I'm following the oss-dev mailing list and from my understanding, P.A. does some strange things with mmap()
- The latest version of OSS4.1 has added support for attaching vmix to the X-fi driver so that multiple sound streams work properly. It also has support for X-fi PCI-e models and the Asus Xonar DX. Directions for obtaining the OSS4.1 beta with mercurial can now be found in the main guide at step 6a.
- For a list of all the changes in OSS 4.1, see [http://mercurial.opensound.com/?shortlog/417](http://mercurial.opensound.com/?shortlog/417)

---

### Post by Yellow Pasque on 2008-08-24
> **toemos said:**
> everything works great except that i can here a faint buzz when i use my mouse... strange i thought.
Yeah, it's strange to hear your mouse. This happened to me with the open-source radeon driver on my old AMD 690G board with a USB/wireless mouse (Logitech MX Laser). It went away when I switched to the radeonhd driver.

What are your hardware specs?

---

### Post by skydog2004 on 2008-08-25
I have been using OSS on my laptop (Sony VGN-NR160E) for some time now and have been dealing with the sound problems when hibernating. My first crude "fix" was to stop all my sound applications then "sudo soundoff" before hibernating and then a "sudo soundon" after restoring.

The problem with OSS is that it will not unload/stop unless all the processes that are using OSS devices are stopped/killed first. When you hibernate OSS does not go away properly, so the restore process brings OSS back in a "stupid" state and really isn't doing anything. If I tried to stop OSS with soundoff at this point it would give lots of errors trying to cleanup the mixer stuff.

I have since come up with a second method, still crude but more convenient (sort of). It is a script that gets put in the /usr/lib/pm-utils/sleep.d directory that detects running processes that are using OSS, kills them and then stops OSS when going into hibernate. On restoring it starts OSS back up again. 

It would be better if it could restore all of the audio applications after restoring, but at least sound works after hibernating without having to do anything like soundoff/soundon. 

It works with vlc if you stop the audio before hibernating, it will not kill vlc and it resumes with vlc still "running".  

I have not tried this with suspend yet...

---

### Post by wingnux on 2008-08-29
Whenever I try to record anything using recordmydesktop I get this error:

wingnux@wingnux-desktop ~/jogos/dreamcast/nullDC 1.0.3 $ recordmydesktop 
Initial recording window is set to:
X:0   Y:0    Width:1152    Height:864
Adjusted recording window is set to:
X:0   Y:0    Width:1152    Height:864
Your window manager appears to be Metacity

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Couldn't open PCM device hw:0,0
Error while opening/configuring soundcard hw:0,0
Try running with the --no-sound or specify a correct device.


So I can't record audio+video, does anybody know how can I solve it?

Thanks in advance.

PS.: Everything else works perfectly under OSS4 ;)

---

### Post by Yellow Pasque on 2008-08-29
wingnux: [http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#recordmydesktop](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#recordmydesktop)

---

### Post by wingnux on 2008-08-29
Thank you very much! =)

---

### Post by coolen on 2008-08-31
I upgraded to Intrepid the other day, and thought I'd try the 4.1RC.

However, I'm getting errors:

```
benji@sterrance:~/oss41build$ sudo make
[sudo] password for benji: 
for n in cmd kernel lib os_cmd kernel/OS/Linux noregparm;do (echo $n && cd $n && make ARCH=i686) || eval 'exit 1'; done
cmd
make[1]: Entering directory `/home/benji/oss41build/cmd'
for n in ossdevlinks ossinfo ossmix ossplay osstest ossxmix savemixer vmixctl;do (echo $n && cd $n && make ARCH=i686) || eval 'exit 1'; done
ossdevlinks
make[2]: Entering directory `/home/benji/oss41build/cmd/ossdevlinks'
cc -ffreestanding -c -O -fno-common -fno-stack-protector -Wall -Werror -DOSS_LITTLE_ENDIAN  -I../../include -I../../kernel/framework/include -I../../kernel/OS/Linux -I../../kernel/nonfree/include -I../.. -I/usr/src/uts/`uname -m` ossdevlinks.c -o ./ossdevlinks.o
cc1: warnings being treated as errors
ossdevlinks.c: In function ‘create_dsplinks’:
ossdevlinks.c:96: error: ignoring return value of ‘system’, declared with attribute warn_unused_result
ossdevlinks.c:276: error: ignoring return value of ‘symlink’, declared with attribute warn_unused_result
ossdevlinks.c:292: error: ignoring return value of ‘symlink’, declared with attribute warn_unused_result
ossdevlinks.c:298: error: ignoring return value of ‘symlink’, declared with attribute warn_unused_result
ossdevlinks.c:314: error: ignoring return value of ‘symlink’, declared with attribute warn_unused_result
ossdevlinks.c:320: error: ignoring return value of ‘symlink’, declared with attribute warn_unused_result
ossdevlinks.c:339: error: ignoring return value of ‘symlink’, declared with attribute warn_unused_result
ossdevlinks.c:367: error: ignoring return value of ‘symlink’, declared with attribute warn_unused_result
ossdevlinks.c:386: error: ignoring return value of ‘symlink’, declared with attribute warn_unused_result
ossdevlinks.c:406: error: ignoring return value of ‘symlink’, declared with attribute warn_unused_result
ossdevlinks.c:425: error: ignoring return value of ‘symlink’, declared with attribute warn_unused_result
ossdevlinks.c: In function ‘create_mixerlinks’:
ossdevlinks.c:487: error: ignoring return value of ‘system’, declared with attribute warn_unused_result
ossdevlinks.c: In function ‘main’:
ossdevlinks.c:941: error: ignoring return value of ‘freopen’, declared with attribute warn_unused_result
make[2]: *** [ossdevlinks.o] Error 1
make[2]: Leaving directory `/home/benji/oss41build/cmd/ossdevlinks'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/home/benji/oss41build/cmd'
make: *** [subdirs] Error 1
benji@sterrance:~/oss41build$
```

Any ideas?

---

### Post by Yellow Pasque on 2008-08-31
coolen: I had this problem on Intrepid as well, because gcc-4.3 treats warnings as errors. My solution was to install gcc-4.2, and change the /usr/bin/gcc symlink to point to /usr/bin/gcc-4.2

---

### Post by coolen on 2008-08-31
Thanks, that did the trick :D

---

### Post by mohrizmus on 2008-09-01
I'm still new to Ubuntu Linux. I have already install Hardy Heron on my pc.Every work well not PCI dial-up modem need to install. I scan the type of modem using utility from Linuxant. I download hsfmodem_7.68.00.12full_i386.deb and install this driver.Then follow the instruction how to configure the modem after install the modem. Reboot the pc and i found no sound.

My PC is Pentium D 2.66, RAM 512 MB,Motherboard Asus P5VDC-X,Harddisk 80GB, AGP card-ATI Radeon 9250, PCI Modem Conexant chip.

Here is the output from terminal console:
[LEFT]mohdrizal@mohdrizal-desktop:~$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge 
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge 
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge 
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge 
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge 
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller 
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge 
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80) 
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) 
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge 
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller 
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c) 
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge 
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge 
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01) 
02:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10) 
03:04.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01) 
03:06.0 Communication controller: Conexant Unknown device 2f50 (rev 01) 
mohdrizal@mohdrizal-desktop:~$  
[/LEFT]

I think some wrong with this driver provided by Linuxant. The sound kernel have been override by wrong sound kernel. Any idea how to solve it. When I run this code hsfconfig --uninstall , I can hear the sound back. Alsa driver provided by Linuxant need to patch. How to patch this driver assuming no internet connection to patch alsa driver. This is the real problem on Linux compare to MAC OSX and Windows. Linuxant should provide alsa driver that had been patched by them. Newcomer to Linux still difficult to install the driver. Need to know the command.


Regards,
mohrizmus

---

### Post by blackcoffeeblue on 2008-09-03
X-Fi XtremeMusic up and running thanks to this guide - Thanks a million dude  :guitar:

---

### Post by cathalcummins on 2008-09-06
I THINK I have installed OSS4 correctly using

[I]sudo /etc/init.d/alsa-utils stop
sudo apt-get -y remove alsa-oss oss-compat alsa-base libesd-alsa0

sudo apt-get -y install linux-headers-`uname -r` build-essential gawk libtool libgtk2.0-dev libesd0 wget linux-sound-base gcc-multilib libesd0-dev mercurial libssl0.9.8 libssl-dev
cd /usr/src
sudo hg clone [http://mercurial.opensound.com/](http://mercurial.opensound.com/) oss-devel
cd ~/
mkdir oss41build
cd oss41build/
sudo sh /usr/src/oss-devel/configure
sudo make
sudo make install
[/I]

I'm using Ubuntu 8.04 and here are a few results:
[I]
sudo ossdetect -v

cathal@cathal-home:~/oss41build$ sudo ossdetect -v
Detected M Audio Delta 44
Detected Nvidia High Definition Audio (MCP61)
USB support available in the system, adding USB driver
Detected Generic USB audio/MIDI device (BETA)[/I]


[I]ossxmix

cathal@cathal-home:~/oss41build$ ossmix
Selected mixer 0/M Audio Delta 44
Known controls are:
peak.out1/2 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
peak.out3/4 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
peak.in1/2 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
peak.in3/4 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
peak.main [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
mon.out1/2 [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
mon.out3/4 [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
mon.in1/2 [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
mon.in3/4 [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
route.out1/2 <DMA|MONITOR|IN1/2|IN3/4> (currently DMA)
route.out3/4 <DMA|IN1/2|IN3/4> (currently DMA)
gain.out1/2 <+4DB|CONSUMER|-10DB> (currently +4DB)
gain.out3/4 <+4DB|CONSUMER|-10DB> (currently +4DB)
gain.in1/2 <+4DB|CONSUMER|-10DB> (currently +4DB)
gain.in3/4 <+4DB|CONSUMER|-10DB> (currently +4DB)
envy24.rate <8000|9600|11025|12000|16000|22050|24000|32000|44100|48000|64000|88200> (currently 48000)
envy24.ratelock ON|OFF (currently ON)
envy24.actrate <decimal value> (currently 48000) (Read-only)
vmix0-enable ON|OFF (currently ON)
vmix0-rate <decimal value> (currently 48000) (Read-only)
vmix0-channels <Stereo|Multich> (currently Stereo)
vmix0-src <Fast|Low|Medium|High|High+|Production|OFF> (currently Fast)
vmix0-vol <monovol> (currently 25.0 dB)
vmix0-out1 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
vmix0-in [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
vmix0-out.pcm7 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out2 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
vmix0-out.pcm8 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out3 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
vmix0-out.pcm9 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out4 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
vmix0-out.pcm10 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0-out5 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
[/I]

and also, bit long winded:

[I]cathal@cathal-home:~/oss41build$ ossinfo -v3
Version info: OSS 4.1 (b rc1/200809061322) (0x00040090) 
Hg revision: changeset: 431:14addb1415d2, tag: tip, date: Wed Sep 03 20:57:44 2008 +0300, summary: Fixes for BeOS/Haiku
Platform: Linux/i686 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 (cathal-home)

Number of audio devices:	13
Number of audio engines:	21
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: oss_envy240 M Audio Delta 44 interrupts=15 (138409)
 2: oss_hdaudio0 nVidia HD Audio interrupts=339 (138392)
    HD Audio controller nVidia HD Audio
    Vendor ID    0x10de03f0
    Subvendor ID 0x10438290
     Codec  0: ALC662 (0x10ec0662/0x10438290)
 3: oss_usb0 USB audio core services


Mixer devices
 0: M Audio Delta 44 (Mixer 0 of device object 1)
    Device file /dev/oss/oss_envy240/mix0, Legacy device /dev/mixer0
    Priority: 0
    Caps: 
    Device handle: PCId6331412-0000:01:06.0-mx01
    Device priority: 0

 1: High Definition Audio ALC662 (Mixer 0 of device object 2)
    Device file /dev/oss/oss_hdaudio0/mix0, Legacy device /dev/mixer1
    Priority: 10
    Caps: 
    Device handle: PCI82901043-0000:00:05.0-mx01
    Device priority: 10


Audio devices
M Audio Delta 44 out1/2           /dev/oss/oss_envy240/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: TRIGGER 
    Modes: OUTPUT 
      Out engine  1: 0/M Audio Delta 44 out1/2
                     Available for use 
    Input formats (0x00009010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
      AFMT_S24_LE	- 24/32 bit signed little endian
    Output formats (0x00009010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
      AFMT_S24_LE	- 24/32 bit signed little endian
    Device handle: PCId6331412-0000:01:06.0-au01
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: STEREO
    Supported number of channels (min - max): 1 - 10
    Native sample rates (min - max): 8000 - 96000 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

M Audio Delta 44 out3/4           /dev/oss/oss_envy240/pcm1  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER 
    Modes: OUTPUT 
      Out engine  1: 1/M Audio Delta 44 out3/4
                     Available for use 
    Input formats (0x00009010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
      AFMT_S24_LE	- 24/32 bit signed little endian
    Output formats (0x00009010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
      AFMT_S24_LE	- 24/32 bit signed little endian
    Device handle: PCId6331412-0000:01:06.0-au02
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: STEREO
    Supported number of channels (min - max): 1 - 8
    Native sample rates (min - max): 8000 - 96000 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

M Audio Delta 44 in1/2            /dev/oss/oss_envy240/pcmin0  (device index 2)
    Legacy device /dev/dsp2
    Caps: TRIGGER 
    Modes: INPUT  
      In engine   1: 2/M Audio Delta 44 in1/2
                     Available for use 
    Input formats (0x00009010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
      AFMT_S24_LE	- 24/32 bit signed little endian
    Output formats (0x00009010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
      AFMT_S24_LE	- 24/32 bit signed little endian
    Device handle: PCId6331412-0000:01:06.0-au03
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: STEREO
    Supported number of channels (min - max): 1 - 12
    Native sample rates (min - max): 8000 - 44100 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

M Audio Delta 44 in3/4            /dev/oss/oss_envy240/pcmin1  (device index 3)
    Legacy device /dev/dsp3
    Caps: TRIGGER 
    Modes: INPUT  
      In engine   1: 3/M Audio Delta 44 in3/4
                     Available for use 
    Input formats (0x00009010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
      AFMT_S24_LE	- 24/32 bit signed little endian
    Output formats (0x00009010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
      AFMT_S24_LE	- 24/32 bit signed little endian
    Device handle: PCId6331412-0000:01:06.0-au04
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: STEREO
    Supported number of channels (min - max): 1 - 10
    Native sample rates (min - max): 8000 - 44100 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

M Audio Delta 44 input from mon. mixer   /dev/oss/oss_envy240/mon  (device index 4)
    Legacy device /dev/dsp4
    Caps: TRIGGER 
    Modes: INPUT  
      In engine   1: 4/M Audio Delta 44 input from mon. mixer 
                     Available for use 
    Input formats (0x00009010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
      AFMT_S24_LE	- 24/32 bit signed little endian
    Output formats (0x00009010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
      AFMT_S24_LE	- 24/32 bit signed little endian
    Device handle: PCId6331412-0000:01:06.0-au05
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: STEREO
    Supported number of channels (min - max): 1 - 2
    Native sample rates (min - max): 8000 - 44100 (8000,9600,11025,12000,16000,22050,24000,32000,44100,48000,88200,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

M Audio Delta 44 (all outputs)    /dev/oss/oss_envy240/multich_out  (device index 5)
    Legacy device /dev/dsp5
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Out engine  1: 5/M Audio Delta 44 (all outputs)
                     Available for use 
      Engine      2: 7/M Audio Delta 44 (all outputs) (vmix)
                     Available for use 
      Engine      3: 8/M Audio Delta 44 (all outputs) (vmix)
                     Available for use 
      Engine      4: 9/M Audio Delta 44 (all outputs) (vmix)
                     Available for use 
      Engine      5: 10/M Audio Delta 44 (all outputs) (vmix)
                     Available for use 
    Input formats (0x00001000):
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001000):
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCId6331412-0000:01:06.0-au06
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: MULTICH
    Supported number of channels (min - max): 10 - 10
    Native sample rates (min - max): 8000 - 96000
    HW Type: Not indicated.
    Minimum latency: Not indicated

M Audio Delta 44 (all inputs)     /dev/oss/oss_envy240/multich_in  (device index 6)
    Legacy device /dev/dsp6
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      In engine   1: 6/M Audio Delta 44 (all inputs)
                     Available for use 
      Engine      2: 7/M Audio Delta 44 (all outputs) (vmix)
                     Available for use 
      Engine      3: 8/M Audio Delta 44 (all outputs) (vmix)
                     Available for use 
      Engine      4: 9/M Audio Delta 44 (all outputs) (vmix)
                     Available for use 
      Engine      5: 10/M Audio Delta 44 (all outputs) (vmix)
                     Available for use 
    Input formats (0x00001000):
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001000):
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCId6331412-0000:01:06.0-au07
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: MULTICH
    Supported number of channels (min - max): 12 - 12
    Native sample rates (min - max): 8000 - 96000
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play front               /dev/oss/oss_hdaudio0/pcm0  (device index 7)
    Legacy device /dev/dsp7
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Out engine  1: 11/HD Audio play front
                     Available for use 
      Engine      2: 17/HD Audio play front (vmix)
                     Available for use 
      Engine      3: 18/HD Audio play front (vmix)
                     Available for use 
      Engine      4: 19/HD Audio play front (vmix)
                     Available for use 
      Engine      5: 20/HD Audio play front (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI82901043-0000:00:05.0-au01
    Related mixer dev: 1
    Sample rate source: 11
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 8
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play rear                /dev/oss/oss_hdaudio0/pcm1  (device index 8)
    Legacy device /dev/dsp8
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 12/HD Audio play rear
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI82901043-0000:00:05.0-au02
    Related mixer dev: 1
    Sample rate source: 11
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play center/LFE          /dev/oss/oss_hdaudio0/pcm2  (device index 9)
    Legacy device /dev/dsp9
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 13/HD Audio play center/LFE
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI82901043-0000:00:05.0-au03
    Related mixer dev: 1
    Sample rate source: 11
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play spdif-out           /dev/oss/oss_hdaudio0/spdout0  (device index 10)
    Legacy device /dev/dsp10
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 14/HD Audio play spdif-out
                     Available for use 
    Input formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI82901043-0000:00:05.0-au04
    Related mixer dev: 1
    Sample rate source: 11
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin0  (device index 11)
    Legacy device /dev/dsp11
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      In engine   1: 15/HD Audio rec mix
                     Available for use 
      Engine      2: 17/HD Audio play front (vmix)
                     Available for use 
      Engine      3: 18/HD Audio play front (vmix)
                     Available for use 
      Engine      4: 19/HD Audio play front (vmix)
                     Available for use 
      Engine      5: 20/HD Audio play front (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI82901043-0000:00:05.0-au05
    Related mixer dev: 1
    Sample rate source: 11
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin1  (device index 12)
    Legacy device /dev/dsp12
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 16/HD Audio rec mix
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI82901043-0000:00:05.0-au06
    Related mixer dev: 1
    Sample rate source: 11
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

[/I]


I still get no sound, the usual

*No volume control GStreamer plugins and/or devices found*

in the tray and


*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused*

In preferences. Can you guys help or am I better off in 


[http://www.4front-tech.com/forum/index.php](http://www.4front-tech.com/forum/index.php)

?



EDIT: I can remove any useless lines to help thread browsing. Please let me know.

EDIT #2: just ran osstest and it played music with the following:

[I]cathal@cathal-home:~$ osstest
Sound subsystem and version: OSS 4.1 (b rc1/200809061322) (0x00040090)
Platform: Linux/i686 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/oss_envy240/pcm0 (audio engine 0): M Audio Delta 44 out1/2
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 48013.00 Hz (0.03%)> 
/dev/oss/oss_envy240/pcm1 (audio engine 1): M Audio Delta 44 out3/4
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 48015.00 Hz (0.03%)> 
/dev/oss/oss_envy240/pcmin0 (audio engine 2): M Audio Delta 44 in1/2
- Skipping input only device
/dev/oss/oss_envy240/pcmin1 (audio engine 3): M Audio Delta 44 in3/4
- Skipping input only device
/dev/oss/oss_envy240/mon (audio engine 4): M Audio Delta 44 input from mon. mixer 
- Skipping input only device
/dev/oss/oss_envy240/multich_out (audio engine 5): M Audio Delta 44 (all outputs)
- Skipping multi channel device
/dev/oss/oss_envy240/multich_in (audio engine 6): M Audio Delta 44 (all inputs)
- Skipping input only device

*** Scanning sound adapter #1 ***
/dev/oss/oss_hdaudio0/pcm0 (audio engine 11): HD Audio play front
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47961.00 Hz (-0.08%)> 
/dev/oss/oss_hdaudio0/pcm1 (audio engine 12): HD Audio play rear
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47961.00 Hz (-0.08%)> 
/dev/oss/oss_hdaudio0/pcm2 (audio engine 13): HD Audio play center/LFE
- Performing audio playback test... 
  <left> OK <right> OK <stereo> 
OK <measured srate 47959.00 Hz (-0.09%)> 
/dev/oss/oss_hdaudio0/spdout0 (audio engine 14): HD Audio play spdif-out
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47959.00 Hz (-0.09%)> 
/dev/oss/oss_hdaudio0/pcmin0 (audio engine 15): HD Audio rec mix
- Skipping input only device
/dev/oss/oss_hdaudio0/pcmin1 (audio engine 16): HD Audio rec mix
- Skipping input only device

*** All tests completed OK ***
[/I]

This, at least, gives me confidence that Linux can communicate with my Delta 44. Still getting error messages though.



EDIT#3: Now, I have added the ossxmix mixer to the startup. When I run osstest, the levels are read in the green and red bars. So the mixer is being routed through.

The mind boggles.

---

### Post by Phkillah on 2008-09-14
this is DEFINITELY the best audio driver for X-fi.

After 2 years of waiting, i can finally have my sound system back here in Linux.

Thanks for the tip ;) Muahahaha

---

### Post by haneya on 2008-09-19
I followed the steps u gave but i had a problem while installing (oss-linux_v4.0-1016_i386.deb) and having this error 
```
$ sudo dpkg -i oss-linux_v4.0-1016_i386.deb
dpkg: error processing oss-linux_v4.0-1016_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 oss-linux_v4.0-1016_i386.deb


```
looks like the file corrupted am not sure but i downloaded it from the orginal site can any one upload it to me plz

---

### Post by Yellow Pasque on 2008-09-19
I recommend you install OSS 4.1rc from source.
[https://help.ubuntu.com/community/OpenSound#Building%20OSS](https://help.ubuntu.com/community/OpenSound#Building%20OSS)

---

### Post by eyelessfade on 2008-09-20
Lets hope 4Front OSS4 gets picked up by kernel.org. Now that would be something :)

---

### Post by wingnux on 2008-09-25
Can anyone please explain me why I keep reading that OSS4 is obsolete and shouldn't be used at all?? I mean, it works way better than pulse or alsa on my pc but everytime I read an article about linux audio APIs they say the same thing...

[http://0pointer.de/blog/projects/guide-to-sound-apis.html](http://0pointer.de/blog/projects/guide-to-sound-apis.html)

---

### Post by Yellow Pasque on 2008-09-25
> **wingnux said:**
> Can anyone please explain me why I keep reading that OSS4 is obsolete and shouldn't be used at all?? I mean, it works way better than pulse or alsa on my pc but everytime I read an article about linux audio APIs they say the same thing...

[http://0pointer.de/blog/projects/guide-to-sound-apis.html](http://0pointer.de/blog/projects/guide-to-sound-apis.html)
The author admitted that he is biased;
> Also note that I am upstream for both PulseAudio and libcanberra and did some minor contributions to ALSA, GStreamer and some other of the systems listed above. Yes, I am biased.

> I mean, it works way better than pulse or alsa on my pc
Mine too. I keep checking the changelogs to see if ALSA will add support for my M-Audio Revo's headphone jack or fix the annoying bug that mutes the left speaker upon startup, but no sign of that and no user forums to ask...

---

### Post by idledecz on 2008-09-28
How do I change the selected mixer w/ OSS?

when I do 
```
ossmix:
Selected mixer 0/High Definition Audio AD1986A

```

Is shown as my selected mixer instead of my X-Fi. osstest works fine when it gets around to testing the X-Fi card. I tried to change the mixer in Kmix but the drop-down box is empty.

Any help is greatly appreciated.

---

### Post by idledecz on 2008-09-28
nvm, got it by removing the onboard drivers from the oss installed_drivers file.

---

### Post by PingerS on 2008-09-28
```
sudo soundoff
sudo dpkg -r oss-linux
sudo dpkg-reconfigure linux-sound-base
sudo apt-get install **libesd0-alsa** alsa-oss alsa-base
gksudo gedit /etc/modprobe.d/blacklist
```

Should be:
```
sudo soundoff
sudo dpkg -r oss-linux
sudo dpkg-reconfigure linux-sound-base
sudo apt-get install **libesd-alsa0** alsa-oss alsa-base
gksudo gedit /etc/modprobe.d/blacklist
```

I think there's an error with the package name in the uninstall instructions - Cheers :)

(Having issues reverting to alsa :S)

---

### Post by SomeGuyDude on 2008-09-29
```
crew@crew-laptop:~$ sudo dpkg -r oss-linux
dpkg - warning: ignoring request to remove oss-linux which isn't installed.
crew@crew-laptop:~$ 
```

Help??

UPDATE: I'm completely hosed. Nothing is working right at this point. I followed the directions exactly for both installing OSS4 and reverting to ALSA.

Now my volume controls don't work, my headphone jack won't mute my speakers, and I lost my login/logout sounds again. Furthermore, under "Default Mixer Tracks", there's nothing. Is there ANY way to sort of "clean up" and revert back to exactly as it was initially? I'm going absolutely insane.

By the way, what moron decided that OSS shouldn't have jack sensitivity? Who doesn't use their headphone jack?!?

---

### Post by PingerS on 2008-09-29
I'm in the same same boat - can't get it working again.

---

### Post by SomeGuyDude on 2008-09-29
Did anyone successfully use the "revert to ALSA" method? It's currently in the Ubuntu help documentation but it seems like there aren't any success stories.

---

### Post by Yellow Pasque on 2008-10-01
> **SomeGuyDude said:**
> Did anyone successfully use the "revert to ALSA" method? It's currently in the Ubuntu help documentation but it seems like there aren't any success stories.
Like I said, I tested it out on a test install of Intrepid before posting it and it worked for me. I fixed the typo for libesd-alsa0 (thanks, PingerS) and added libsdl1.2debian-alsa to the package list.

If anyone has suggestions to make it better, please share.

---

### Post by klikklak on 2008-10-03
Thanks for the guide, in my quest to get surround 5.1 working, I did a fresh intrepid install and oss4 from source.  Osstest works, with some tweaking in ossxmix to get the channels right.  Ossxmix is wonderful, it's jsut the type of interface alsa should have.  Well, it is a bit cluttered and badly documented. 

Anyway, here's my questions: How do I duplicate channels from stereo (only frontx2) to full 5.1?  Second, why doesn't vlc or mplayer play more than stereo sound?  I thought I nailed it when I got osstest to play all channels correctly.

EDIT: Ha!  setting mplayer (preferences->sound->oss config->device) to /dev/dsp_multich did the trick for surround!  I'd still like to know about duplicating stereo sound to both front and rear

---

### Post by Jim March on 2008-10-05
Another ALSA refugee chiming in - the instructions for OSS4 worked perfectly for me in Intrepid Beta1 32bit.

I'm one of a small group of users whose ALSA caused all sound to fade to nothing over the course of 10 seconds or so once you plug headphones in.  Absolutely poltergeist-level freaky, but it was definitely ALSA doing it.

OSS4.1 fixed it just fine :).

I have a laptop with the HDA Intel sound card (SigmaTel 9228 chip), which is likely the one most or completely affected.  See also:

[http://ubuntuforums.org/showthread.php?p=5909858#post5909858](http://ubuntuforums.org/showthread.php?p=5909858#post5909858)

The issue is thus far unfixed (short of swapping in OSS4.1 of course) since Intrepid Alpha 5.

---

### Post by haneya on 2008-10-15
am having a new issue after updating ubuntu kernel(2.6.24-21-generic) today ,well there is no sound at all and i tried osstest ,ossmix here is the output :
```
~$ ossmix
Mixer device 0 doesn't exist.

```

```
$ osstest
Sound subsystem and version: OSS 4.0 (b1016/200807241529) (0x00040003)
Platform: Linux/i686 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008


NOTICE! You don't have any audio devices available.
        It looks like your audio hardware was not recognized
        by OSS. Please contact 4Front technologies for help
        (http://www.opensound.com/support.cgi). Don't forget to
        include your soundon.log file to the support request.

```

```
 ossxmix
No mixers are available

```

```
$ ossinfo
Version info: OSS 4.0 (b1016/200807241529) (0x00040003) 
Platform: Linux/i686 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 (anas-laptop)

Number of audio devices:	0
Number of audio engines:	0
Number of mixer devices:	0


Device objects
 0: osscore0 OSS core services


Mixer devices

Audio devices

```

and this after trying install oss4 again :```
$ sudo dpkg -i oss-linux-4.0-1016_i386.deb 
[sudo] password for anas: 
(Reading database ... 175261 files and directories currently installed.)
Preparing to replace oss-linux 4.0-1016 (using oss-linux-4.0-1016_i386.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux-4.0-1016_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.24-21-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux-4.0-1016_i386.deb

```

---

### Post by Yellow Pasque on 2008-10-15
haneya, follow the link below to remove the botched install:
[http://ubuntuforums.org/showpost.php?p=5055305&postcount=105](http://ubuntuforums.org/showpost.php?p=5055305&postcount=105)

You can then try and install the .deb again. If that doesn't work, follow the above procedure again and then bild from source: [https://help.ubuntu.com/community/OpenSound#Obtaining%20the%20OSS%20Source%20using%20Mercurial](https://help.ubuntu.com/community/OpenSound#Obtaining%20the%20OSS%20Source%20using%20Mercurial)

---

### Post by haneya on 2008-10-16
thanks man it works form , any news about oss 4.1 ??!!

---

### Post by topalof on 2008-10-28
I'm mainly using USB headphones for my sound and had problems with ALSA and PulseAudio all the time. Sometimes it wouldn't detect them at all and I had to reboot to get sound working again. With OSS4 it works all the time, but I'm having two small problems. 

The first isn't really a problem, more a small inconvenience. When I pause anything, on Banshee or Totem for example, and click on play again, the sound will continue for a second or so, stop for a second and continue like it should from there. This small "hiccup" is a little annoying.

Then I have a problem with Skype. The Ubuntu-deb version runs, but has no sound whatsoever. I can only choose between "Default device" and "Pulse" in the audio setup. Neither option works. I read on the OSS website that I need the static OSS version. But that one just gives me a Segmentation fault when I try to run it :( Any suggestions?

---

### Post by SeaJey on 2008-11-04
> Mine too. I keep checking the changelogs to see if ALSA will add support for my M-Audio Revo's headphone jack or fix the annoying bug that mutes the left speaker upon startup, but no sign of that and no user forums to ask...
Well it was fixed in alsa 1.0.18 according to [this](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1754). 
I am monitoring ppa's now to install it and give alsa a try, most to figure out what audiodriver is the best in term of sound quality.

> Then I have a problem with Skype. The Ubuntu-deb version runs, but has no sound whatsoever. I can only choose between "Default device" and "Pulse" in the audio setup. Neither option works. I read on the OSS website that I need the static OSS version. But that one just gives me a Segmentation fault when I try to run it  Any suggestions? 
Did you tried skype-static-oss from this repo:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

---

### Post by RawMustard on 2008-11-05
OSS4.1 is simply amazing!

I never knew my on board sound cards could sound so bloody great.  Compared to OSS4.1 Alsa sounds like it's being played in a shoe box.  I was so impressed by its sound quality on my laptop, I installed it on my main work station with much nicer sound system, again the sound difference just blew me away.

It's a little bit of work to setup (not too hard (easier than alsa)) but the extra inconvenience at the moment is well and truly worth it.
I never knew my sound could even play some of the frequencies it does now and I never knew I had so much control over my sound device using ossmix and ossxmix under linux, alsa never provided any of that.

Anyway, if you read this and you're having trouble with sound on your Debian/ubuntu system, give OSS4.1 a try, I'm pretty sure like me you'll be amazed!

---

### Post by Yellow Pasque on 2008-11-06
> **SeaJey said:**
> Well it was fixed in alsa 1.0.18 according to [this](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1754). 
I am monitoring ppa's now to install it and give alsa a try, most to figure out what audiodriver is the best in term of sound quality.

I used ALSA 1.0.18 compiled from source on a test install of Ubuntu Intrepid64 (w/PulseAudio) and an install of Arch Linux64 (no PulseAudio). The sound quality is good, but I experienced skipping audio (especially when scrolling) on both distros. I tried different players and increasing the sound buffer, but that didn't help.

Maybe you'll have better luck than I will. I'm happy with OSS4 anyway.

---

### Post by Toci on 2008-11-09
Hello, I installed Hardy a couple of months ago and now I upgraded to 8.10 but never have I been able to record one single sound, and right now the only way I got live audio streams to work is through PulseAudio, if I remove it, would I be able to have streams working with OSS?, because at the moment if I chose OSS it gives me an error.

---

### Post by topalof on 2008-11-09
> **SeaJey said:**
> 
Did you tried skype-static-oss from this repo:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
I tried it, at first it seemed to work fine, but when I try to go to the audio options it freezes and takes the whole system with it (I can move the mouse, but nothing else, can't even kill X). Anyway, I still have hardy, I'll probably make a fresh install of Intrepid soon. Hopefully everything works then.

---

### Post by whoscheesemine on 2008-11-11
> Make sure you remove existing versions of libflashsupport.so, including the Ubuntu repository package, which is for PulseAudio. 

After we ''make install'' you tell us to do that about our flash.

What if our flash works just fine without that? Not that I'm questioning your authority its just that with my past experience with computers if something works JUST LET IT WORK! lol

On a more serious note though, its important to know why things work a certain way or another. So, is it absolutely necessary to make this step and why?

---

### Post by mab1376 on 2008-11-11
[http://forums.creative.com/creativelabs/board/message?board.id=soundblaster&thread.id=132288](http://forums.creative.com/creativelabs/board/message?board.id=soundblaster&thread.id=132288)

i've been using this for the past few days, works great!

---

### Post by Yellow Pasque on 2008-11-11
> What if our flash works just fine without that?
I wrote the guide with Hardy/Flash 9 in mind. You're saying you get sound in Flash with OSS4 and no libflashsupport file? Are you using Flash 10/Intrepid? I know Flash 10 has PulseAudio built-in and Ubuntu 8.10 doesn't have a libflashsupport package. Perhaps Flash 10 has built-in support for OSS too.

> Not that I'm questioning your authority
LOL. When did I get authority? I'm just a run-of-the-mill (but proud) computer nerd.

---

### Post by mab1376 on 2008-11-11
I'm running intrepid and whatever flashplayer is included in the ubuntu-restricted-extras for the respective distribution.

everything works perfectly!!

---

### Post by xanas3712 on 2008-11-11
Under hardy, the problem with lagging sound in ETQW made me switch to OSS4, but I tried alsa and pulseaudio under ibex and everything is going good with no lagging sound and I can play music with etqw going just fine.

I post this in this OSS4 thread because if this kind of thing is the reason for switching to OSS4, going to Ibex may correct the issue for you instead, without any potential sacrifices to compatibility.

---

### Post by Toci on 2008-11-12
I followed all the steps and most things work but I still cannot record sound as SoundRecorder tells me:
*"Could not capture using the 'CD Quality, MP3' audio profile. Please verify its settings. You may be missing the necessary plug-ins."*

 Also both Xine and Mplayer tell me that *no audio device was found* but VLC does work for mp3 and mms streams.

 Anybody knows what the problem could be?.

---

### Post by Yellow Pasque on 2008-11-12
Toci,
Have you set the gstreamer preferences in System -> Preferences -> Sound ?
Have you set Xine and Mplayer to use OSS? [http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)
Does ossrecord work?

Also, since SoundRecorder is bugging you about the MP3 plugin, make sure you have the appropriate gstreamer packages (and it's legal in your country ;) ):
```
sudo apt-get install gstreamer0.10-plugins-fluendo-mp3 gstreamer0.10-plugins-ugly
```

---

### Post by Toci on 2008-11-12
Temüjin, thank you so much for the reply!, I followed all the steps and playback works flawlessly now, better than it ever did!.
 
 But recording still doesn't work, and actually even asking to record a .wav or .spx gives me the same error ("You may be missing the necessary plug-ins"). 
 I'm afraid I don't know what ossrecord is, I found some commands and put them in a terminal (osstest, ossinfo, ossrecord - | ossplay -, ossrecord -i?, ossrecord -ivol -l - | ossplay -)  but what I got was music playing, a list of things, a test saying everything worked okay and a few errors, no signs of any sounds being recorded.

---

### Post by Yellow Pasque on 2008-11-12
Toci, when you go to System -> Preferences -> Sound, what do you have selected for Sound Capture and does the Test button work?

---

### Post by Yellow Pasque on 2008-11-12
If you have the sound capture working properly and Sound Recorder is still bugging you about missing plugins, then make sure you:
```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-good
```

---

### Post by Toci on 2008-11-12
> **Temüjin said:**
> Toci, when you go to System -> Preferences -> Sound, what do you have selected for Sound Capture and does the Test button work?

I have tried selecting each option, and none play the test sound.
I have:
ALSA
OSS4 - HD Audio play pcm1
OSS4 - HD Audio play rec rec 1 (which I'm using currently)
OSS4 - HD Audio rec pcm3
PulseAudio

---

### Post by Toci on 2008-11-13
I decided to reinstall "SoundRecorder" (and "volume control" was attached) but when I reinstalled the sound was gone, it's not giving me any errors just silence and there's no "capture" tab in volume control.
 I don't want to switch back to alsa, any suggestions?.

---

### Post by shane2peru on 2008-11-14
Don't flame me for this, but I'm not really seeing an advantage with OSS4.  Alsa works, except my internal mic doesn't work, and now I switched to OSS, and have many minor problems of sound.  I followed the page noted for installing OSS4, and fixed up Gnome to run with OSS4 (which it does).  Many apps work, but many have problems.  Probably the majority of these issues are that the apps are setup originally to use Alsa, hence creating a large bag of problems for about anyone switching over to OSS (this is just my opinion).  This is not meant to discourage people form using OSS, but rather to help me see the advantage.  I'm missing it.

Shane

---

### Post by Yellow Pasque on 2008-11-14
Personally, I find OSS4 performs better for my sound setup. With ALSA, I get skipping during normal audio playback (with and without PulseAudio, in different audio players, using Ubuntu ALSA or compiling from source, with generic or custom kernel). Also, for the longest time, ALSA did not support all of the features of my card (M-Audio Revolution 5.1, finally fully supported in ALSA 1.0.18 ).

---

### Post by shane2peru on 2008-11-14
> **Temüjin said:**
> Personally, I find OSS4 performs better for my sound setup. With ALSA, I get skipping during normal audio playback (with and without PulseAudio, in different audio players, using Ubuntu ALSA or compiling from source, with generic or custom kernel). Also, for the longest time, ALSA did not support all of the features of my card (M-Audio Revolution 5.1, finally fully supported in ALSA 1.0.18).

So I guess the rule of thumb is, if Alsa doesn't work with your setup, certainly give OSS a try.  If Alsa works, then stick with it, or be prepared to do a lot of tweaking. :)  OSS for the most part works for me, but between the two, I'm thinking now that Alsa worked a little better, even though not everything was setup correctly.  Thanks for the info, and thread on switching over to OSS.  

Shane

---

### Post by shane2peru on 2008-11-14
> **Temüjin said:**
> [SIZE="4"]**Reverting to ALSA**[/SIZE]
If, for some reason, you want to go back to ALSA, here is the procedure: (I tested this myself on my test system)
```
sudo soundoff
sudo dpkg -r oss-linux
sudo dpkg-reconfigure linux-sound-base
sudo apt-get -y install libesd-alsa0 alsa-oss alsa-base libsdl1.2debian-alsa
gksudo gedit /etc/modprobe.d/blacklist
```
The preceding command opens your blacklist file in the text editor. Delete all the lines from "blacklist snd-seq" down to the end of the file (make sure the last line in the file refers to a snd module and was not added by another program).
Restart the PC.
Now, re-install ALSA kernel modules with this script: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
Go to System -> Preferences -> Sounds and select Autodetect or ALSA
Any applications that you configured for OSS should be changed back to ALSA, although they should work with the alsa-oss wrapper.

Optionally, you can setup and configure PulseAudio. I have no experience with this, but I have seen guides for it (use search). If you do, remember to install the Pulse-compatible libflashsupport package:
```
sudo apt-get install libflashsupport
```

Error #1:  ```
sudo soundoff
```  This produced an error.  It was loaded in mixer_applet or something, of which I killed with killall mixer_applet, which inturn gave me an error that the sound applet had crashed and wanted to know if it should be restarted.  I said no.


Error #2:
```

 sudo dpkg -r oss-linux
dpkg - warning: ignoring request to remove oss-linux which isn't installed.
```

I have haphazardly continued despite these bumps and not managed to get alsa back up and running.  :( I will keep tinkering, perhaps we can come up with a solution.  I noticed that Oss is still loading on boot, surely a result of not removing it (see error #2).

Shane

---

### Post by Yellow Pasque on 2008-11-14
sudo dpkg -r oss-linux only works if you installed it with a .deb package. If you installed it from a source tarball or with mercurial/hg, you have to run:
```
sudo soundoff
sudo sh /<directory where you installed the source>/setup/Linux/removeoss.sh
```

---

### Post by shane2peru on 2008-11-14
> **Temüjin said:**
> sudo dpkg -r oss-linux only works if you installed it with a .deb package. If you installed it from a source tarball or with mercurial/hg, you have to run:
```
sudo soundoff
sudo sh /<directory where you installed the source>/setup/Linux/removeoss.sh
```

:oops:  Duuuuuh.  I guess I should have figured that out! lol  I had followed the instructions in your sig for installation which is the installation from source, or marcial.  Thanks for that helpful little piece of info!

Shane

---

### Post by shane2peru on 2008-11-14
Well, I certainly don't consider myself a newbie in Linux, but I really feel like it lately.  I can't seem to fix my alsa problem at all.  I have built, re-built and installed from source alsa, and can't seem to get my sound back.  I'm starting too look at a re-install, and I will quit touching my sound and just use it half working as it is.  I just don't have the time to keep messing around with this.  My frustration is really my lack of knowledge.  I purged every alsa package I could find on my machine, and then installed them again, all to no avail. :(  Really quite amazing this sound setup.  I will leave that stuff to the alsa boys from now on.  It is over my head. Thanks for the help with this!

Shane

---

### Post by RawMustard on 2008-11-14
> **shane2peru said:**
> My frustration is really my lack of knowledge.  I purged every alsa package I could find on my machine, and then installed them again, all to no avail. :(  Really quite amazing this sound setup.  I will leave that stuff to the alsa boys from now on.  It is over my head. Thanks for the help with this!

Shane

See that's the problem with alsa, it's complicated and broken, not to mention the sound quality is like  a crystal radio compared to OSS4.

The problem you had with applications not working is because some apps have completely dropped support for OSS, but the apps that rely on a quality sound API and are truly cross platform still have full support for OSS.

Now witness the layer, upon layer, upon layer of band aids being applied to alsa to make it work, ie pulse audio.

Visit the [OSS4]("http://www.4front-tech.com/forum/") forums, the guys there are very helpful at solving your OSS problems, you won't get the same help from the alsa people!

---

### Post by shane2peru on 2008-11-15
> **RawMustard said:**
> See that's the problem with alsa, it's complicated and broken, not to mention the sound quality is like  a crystal radio compared to OSS4.

The problem you had with applications not working is because some apps have completely dropped support for OSS, but the apps that rely on a quality sound API and are truly cross platform still have full support for OSS.

Now witness the layer, upon layer, upon layer of band aids being applied to alsa to make it work, ie pulse audio.

Visit the [OSS4]("http://www.4front-tech.com/forum/") forums, the guys there are very helpful at solving your OSS problems, you won't get the same help from the alsa people!

Yes, I probably should have went over and fixed the issues with OSS on my box, but ... I re-installed.  When they quit applying the bandaids, I will switch over to OSS.  I just use my sound too much to have to mess around with it.  I will give it another go because not everything works correctly on my computer.  It will have to be later when I have a little more time.  

Shane

---

### Post by sempronius on 2008-11-19
As to "skype_static-oss":
> **topalof said:**
> I tried it, at first it seemed to work fine, but when I try to go to the audio options it freezes and takes the whole system with it (I can move the mouse, but nothing else, can't even kill X). Anyway, I still have hardy, I'll probably make a fresh install of Intrepid soon. Hopefully everything works then.


Well, I had some issues with Skype, too.

1) When you say that your system is locked up, you do not necessarily have to switch your computer off, in most cases (but not always) the "alt-sysrq" key combo will allow you to synchronize your file systems, unmount them and cleanly reboot.

2) I had the described behaviour when having vmix enabled for my usb sound adapter and found out that there is a good reason that in the current state of OSS-4 development vmix is only enabled for the primary sound card and by default disabled for any additional sound card/adapter you may use (esp. when it is an usb stick).
So I deactivated vmix for the usb stick and no longer have these system lock-ups.

3) There is one annoying little problem with Skype left:
Sometimes (not that often, but it happens from time to time) when launching Skype or when getting a sound notification or when opening the audio devices options the mouse pointer gets stuck (sticks to the left side of the screen and can only be moved vertically); nothing helps to get the normal mouse function back, but restarting the X server solves the problem.
Anyway, I use a second X server in addition to my main X server, and among a few things Skype is running there, combined with a light-weight window manager like "icewm", restarting this X server is very fast!


Now a few remarks about OSS-4 in general:

a) I hope, it will not suffer from a slow-down (considering one of the developers mentioned he had no longer that much time for it); I also hope, those responsible of Linux distributions don't all go the ALSA and Pulseaudio route. Honestly, I don't like Alsa that much (sound quality is inferior, and some applications, esp. some games like "ezquake" have serious problems with sound latency when used via Alsa and not OSS). As to Pulseaudio, I cannot see any real benefit, in my eyes, it is just another (and overhyped) sound server. And if you like to play games, esp. some older ones, you are lost with Pulseaudio or you have to use esd or some additional sound server to get sound, and you get considerable latency.

b) Regarding Pulseaudio:
Even if you use OSS-4, you can use Pulseaudio at the same time, it works!!
I do not know how universally true this statement is, but at least when using the Mercurial sources of OSS-4 and compiling them you get an OSS-4 which can coexist with Pulseaudio.

c) I am very pleased with the sound quality and overall performance of OSS-4!
You can mix all kinds of sounds (even flash and other sound files, something that failed on me to mix when using Alsa), you get low latency sounds in games and many, many mixer controls (though documentation about them is still lacking)

d) On my system, OSS-4 and Alsa can happily live together! Yes, right. This does not mean at the same time being enabled, but I can easily do a "soundoff", "depmod -a", modprobe snd-intel8x0, and thus switch to Alsa.
Or I can switch back to OSS-4 by doing: /etc/init.d/alsa unload; soundon
All this could, of course, be automated (by a script).

e) There is only ONE issue left for me:
recording via a usb sound adapter does not yet seem to work - and it appears that nobody (according to the posts in the opensound forum) got recording via usb to work. Well, I hope, this will change soon... (though the problem seems to be a difficult one).

f) On the other hand I had the most pleasant experience with sound recording via my onboard sound chip (C-Media 9761A, SIS 7012 chipset): If you happen to have such a sound chip and also use windows, some of you will have noticed how unusable it is for sound recording or for using Skype (microphone volume incredibly weak), even the option "micboost" in the driver does not help enough.
I tried all kinds of drivers (the latest, older, the oldest) by c-media, and also the drivers directly by SIS:
same problem with all these drivers, and same problem under Windows XP, 2000 and Millennium: extremely weak microphone level.

Now with Alsa under Linux the situation was somewhat better, but still the microphone level was low.

Then I tried OSS-4:
Unbelievable!!
Using the TWO available micboost options in "ossxmix" I was able to achieve an undoubtedly sufficient and quite good microphone signal - something that none of the windows drivers ever achieved! I had even considered a hardware flaw, but it is clearly just a driver issue, though this won't help those who only use windows. But under OSS-4, the onboard chip is perfectly usable (for playback and recording).



Well, I could go on in my joy about OSS-4... But this post has already become rather lengthy. :-)


Regards, sempronius

---

### Post by shane2peru on 2008-11-20
Ok, I'm about ready to give this another go.  What is the best recommended install method?  I have used [this link]("https://help.ubuntu.com/community/OpenSound") to help me get OSS4 installed before.  Should I go with mercurial? for upgrading purposes?  I want stability. 

Shane

**EDIT:**  Ok, I installed following the mercurail method, and that seemed to work better.  Not near the bumps in the road this time around.  Still one problem, Skype-oss.  I'm not sure if this is an Ubuntu problem, or OSS problem.  I run the static-oss I downloaded, and run it, opens fine, works fine.  I go to options and make a test call, and it works, except it doesn't pick up my mic, and it never recovers from that test call, it just hangs up.  Any ideas on this?  I'm working on 64bit Intrepid.

**EDIT2:**  Ok, ran dmesg here is what I get:   
```

process `skypeoss' is using obsolete setsockopt SO_BSDCOMPAT
[ 1077.120069] osscore: Input timed out on audio engine 5 (count=0)

```

Shane

---

### Post by Jormungandr on 2008-11-20
Thanks for the guide. My alsa and pulseaudio failed on me today, so OSS was the knight on the white horse. 
Only negative point are my dell XPs buttons not working and ossxmix that isnt functioning. the rest is smooth sailing. 
Ow yeah, and the fact that the volume was at 100%. I think everybody in the building is awake now :p.

---

### Post by Piraja on 2009-01-02
Thanks for this, especially post [#105]("http://ubuntuforums.org/showpost.php?p=5055305&postcount=105")... See my [post]("http://ubuntuforums.org/showpost.php?p=6482124&postcount=1290") from a while back if you wish to know why I'm so thankful, writing this on a LiveCD and hoping to have removed OSS successfully from my Intrepid 64-bit installation... Doesn't always work, as it seems.

**EDIT** (ca. 20 mins later): Removing oss-linux* was not enough. Booting to the laptop install still resulted in the horrid shriek (as described in the other thread [post 1290]("http://ubuntuforums.org/showpost.php?p=6482124&postcount=1290")). So I'm running the LiveCD again and trying to figure out how to fix the issue without having to re-install... 

**2nd Ed.** Fortunately, I do have a separate /home partition. Still, even though the install is just about one week old, I'd rather not re-install everything from the scratch.

**3rd Ed.** Well, now that I've got over the initial [COLOR="DarkOrange"]**_s_h_o_c_k_**[/COLOR] I think I'll just sleep over it and try to fix things tomorrow... Good night dear Ubunteros and all, wherever you are!

---

### Post by Piraja on 2009-01-03
> **Temüjin said:**
> [SIZE="4"]**Reverting to ALSA**[/SIZE]
If, for some reason, you want to go back to ALSA, here is the procedure: (I tested this myself on my test system)
```
sudo soundoff
sudo dpkg -r oss-linux
sudo dpkg-reconfigure linux-sound-base
sudo apt-get -y install libesd-alsa0 alsa-oss alsa-base libsdl1.2debian-alsa
gksudo gedit /etc/modprobe.d/blacklist
```
The preceding command opens your blacklist file in the text editor. Delete all the lines from "blacklist snd-seq" down to the end of the file (make sure the last line in the file refers to a snd module and was not added by another program).
Restart the PC.
Now, re-install ALSA kernel modules with this script: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
Go to System -> Preferences -> Sounds and select Autodetect or ALSA
Any applications that you configured for OSS should be changed back to ALSA, although they should work with the alsa-oss wrapper.

Hmm... I'm trying to fix my broken OSS install [**EDIT**: sorry, I mean I already *removed* it, and am *not* trying to fix it — wrote fast and got tangled] and revert to ALSA (see my previous post from last night), running a root console in recovery mode. I already did dpkg-reconfigure linux-sound-base, i.e. changed back to ALSA like a good boy. But for some reason, I cannot fetch the packages from the repos on my laptop (yes, I have a wired connection). This is pretty much a basic newbie question (I am a novice, anyway), but how do I use the LiveCD to fetch the relevant Intrepid 64-bit ALSA packages from there? I mean, I suppose I should add a variable to apt-get install <here should be a variable, I think?>, but I don't know which variable.

As it comes to the reasons why I tried to change to OSS, I suppose I'll just try to live with MPD's outrageously high CPU footprint in ALSA from now on... OSS seems to be out of the question.

---

### Post by Piraja on 2009-01-03
**POST'S PREVIOUS CONTENT DELETED**, since after I edited the blacklist file as suggested, the Furies screeching at me were stifled (I mean the feedback-like noise that started as soon as certain modules are loaded [I hope my terms are correct], already before the GDM screen came up), and now I have also installed the suggested packages. Now I'm just keeping my fingers crossed for the next move to get my ALSA back...

**DARN!** (10 mins later...) I rejoiced too early about the hell-hounds being stifled. I could log in ONCE without the screeching, but after installing the packages I rebooted and it started again. Now &#8212; its being day-time &#8212; I could also wait for a moment before hard-resetting (or rather while waiting Ctrl-Alt-del to take effect, but it took so long I finally hard-reset) and realized that it's indeed a feedback sound: the Compaq 6735S has an internal microphone in the front and when I pressed the tiny mic hole the pitch and volume of the horrible noise changed a bit.

What to do now? I'm a confused ignorant dilettante, as you can see...

**SO**, is there a way to at least disable the microphone for the time being? I.e. a boot parameter or something like that?

---

### Post by haneya on 2009-01-03
Hi , I tried to remove oss4 and i failed , then tried to update it and failed also after upgrade to Intrepid i dont know what to do? 
 here is the output of sudo make install : 
```
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_cs461x'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_cs461x'
oss_digi96
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_digi96'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_digi96'
oss_emu10k1x
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_emu10k1x'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_emu10k1x'
oss_envy24
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_envy24'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_envy24'
oss_envy24ht
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_envy24ht'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_envy24ht'
oss_fmedia
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_fmedia'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_fmedia'
oss_geode
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_geode'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_geode'
oss_hdaudio
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_hdaudio'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_hdaudio'
oss_ich
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_ich'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_ich'
oss_imux
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_imux'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_imux'
oss_midiloop
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_midiloop'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_midiloop'
oss_midimix
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_midimix'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_midimix'
oss_sblive
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_sblive'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_sblive'
oss_sbpci
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_sbpci'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_sbpci'
oss_sbxfi
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_sbxfi'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_sbxfi'
oss_solo
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_solo'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_solo'
oss_trident
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_trident'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_trident'
oss_usb
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_usb'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_usb'
oss_userdev
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_userdev'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_userdev'
oss_via823x
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_via823x'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_via823x'
oss_via97
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_via97'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_via97'
oss_ymf7xx
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/drv/oss_ymf7xx'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv/oss_ymf7xx'
make[2]: Leaving directory `/home/abdulaziz/oss41build/kernel/drv'
framework
make[2]: Entering directory `/home/abdulaziz/oss41build/kernel/framework'
for n in ac97 audio midi mixer osscore remux sndstat uart401 vmix_core;do (echo $n && cd $n && make ARCH=i686) || eval 'exit 1'; done
ac97
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/framework/ac97'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/framework/ac97'
audio
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/framework/audio'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/framework/audio'
midi
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/framework/midi'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/framework/midi'
mixer
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/framework/mixer'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/framework/mixer'
osscore
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/framework/osscore'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/framework/osscore'
remux
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/framework/remux'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/framework/remux'
sndstat
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/framework/sndstat'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/framework/sndstat'
uart401
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/framework/uart401'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/framework/uart401'
vmix_core
make[3]: Entering directory `/home/abdulaziz/oss41build/kernel/framework/vmix_core'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/kernel/framework/vmix_core'
make[2]: Leaving directory `/home/abdulaziz/oss41build/kernel/framework'
make[1]: Leaving directory `/home/abdulaziz/oss41build/kernel'
lib
make[1]: Entering directory `/home/abdulaziz/oss41build/lib'
for n in libOSSlib;do (echo $n && cd $n && make ARCH=i686) || eval 'exit 1'; done
libOSSlib
make[2]: Entering directory `/home/abdulaziz/oss41build/lib/libOSSlib'
sh ./compile.sh /lib "cc" "-O -fPIC" "make"
make[3]: Entering directory `/home/abdulaziz/oss41build/lib/libOSSlib'
make[3]: `libOSSlib.so' is up to date.
make[3]: Leaving directory `/home/abdulaziz/oss41build/lib/libOSSlib'
make[2]: Leaving directory `/home/abdulaziz/oss41build/lib/libOSSlib'
make[1]: Leaving directory `/home/abdulaziz/oss41build/lib'
os_cmd
make[1]: Entering directory `/home/abdulaziz/oss41build/os_cmd'
for n in Linux;do (echo $n && cd $n && make ARCH=i686) || eval 'exit 1'; done
Linux
make[2]: Entering directory `/home/abdulaziz/oss41build/os_cmd/Linux'
for n in ossdetect ossvermagic;do (echo $n && cd $n && make ARCH=i686) || eval 'exit 1'; done
ossdetect
make[3]: Entering directory `/home/abdulaziz/oss41build/os_cmd/Linux/ossdetect'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/os_cmd/Linux/ossdetect'
ossvermagic
make[3]: Entering directory `/home/abdulaziz/oss41build/os_cmd/Linux/ossvermagic'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/abdulaziz/oss41build/os_cmd/Linux/ossvermagic'
make[2]: Leaving directory `/home/abdulaziz/oss41build/os_cmd/Linux'
make[1]: Leaving directory `/home/abdulaziz/oss41build/os_cmd'
kernel/OS/Linux
make[1]: Entering directory `/home/abdulaziz/oss41build/kernel/OS/Linux'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/abdulaziz/oss41build/kernel/OS/Linux'
noregparm
make[1]: Entering directory `/home/abdulaziz/oss41build/noregparm'
for n in kernel lib kernel/OS/Linux;do (echo $n && cd $n && make ARCH=i686) || eval 'exit 1'; done
kernel
make[2]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel'
for n in drv framework;do (echo $n && cd $n && make ARCH=i686) || eval 'exit 1'; done
drv
make[3]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv'
for n in oss_ali5455 oss_atiaudio oss_audigyls oss_audioloop oss_audiopci oss_cmi878x oss_cmpci oss_cs4281 oss_cs461x oss_digi96 oss_emu10k1x oss_envy24 oss_envy24ht oss_fmedia oss_geode oss_hdaudio oss_ich oss_imux oss_midiloop oss_midimix oss_sblive oss_sbpci oss_sbxfi oss_solo oss_trident oss_usb oss_userdev oss_via823x oss_via97 oss_ymf7xx;do (echo $n && cd $n && make ARCH=i686) || eval 'exit 1'; done
oss_ali5455
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_ali5455'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_ali5455'
oss_atiaudio
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_atiaudio'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_atiaudio'
oss_audigyls
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_audigyls'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_audigyls'
oss_audioloop
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_audioloop'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_audioloop'
oss_audiopci
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_audiopci'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_audiopci'
oss_cmi878x
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_cmi878x'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_cmi878x'
oss_cmpci
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_cmpci'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_cmpci'
oss_cs4281
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_cs4281'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_cs4281'
oss_cs461x
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_cs461x'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_cs461x'
oss_digi96
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_digi96'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_digi96'
oss_emu10k1x
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_emu10k1x'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_emu10k1x'
oss_envy24
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_envy24'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_envy24'
oss_envy24ht
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_envy24ht'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_envy24ht'
oss_fmedia
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_fmedia'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_fmedia'
oss_geode
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_geode'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_geode'
oss_hdaudio
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_hdaudio'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_hdaudio'
oss_ich
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_ich'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_ich'
oss_imux
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_imux'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_imux'
oss_midiloop
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_midiloop'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_midiloop'
oss_midimix
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_midimix'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_midimix'
oss_sblive
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_sblive'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_sblive'
oss_sbpci
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_sbpci'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_sbpci'
oss_sbxfi
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_sbxfi'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_sbxfi'
oss_solo
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_solo'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_solo'
oss_trident
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_trident'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_trident'
oss_usb
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_usb'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_usb'
oss_userdev
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_userdev'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_userdev'
oss_via823x
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_via823x'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_via823x'
oss_via97
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_via97'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_via97'
oss_ymf7xx
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_ymf7xx'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv/oss_ymf7xx'
make[3]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/drv'
framework
make[3]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/framework'
for n in ac97 audio midi mixer osscore remux sndstat uart401 vmix_core;do (echo $n && cd $n && make ARCH=i686) || eval 'exit 1'; done
ac97
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/ac97'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/ac97'
audio
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/audio'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/audio'
midi
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/midi'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/midi'
mixer
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/mixer'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/mixer'
osscore
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/osscore'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/osscore'
remux
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/remux'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/remux'
sndstat
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/sndstat'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/sndstat'
uart401
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/uart401'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/uart401'
vmix_core
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/vmix_core'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/framework/vmix_core'
make[3]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/framework'
make[2]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel'
lib
make[2]: Entering directory `/home/abdulaziz/oss41build/noregparm/lib'
for n in libOSSlib;do (echo $n && cd $n && make ARCH=i686) || eval 'exit 1'; done
libOSSlib
make[3]: Entering directory `/home/abdulaziz/oss41build/noregparm/lib/libOSSlib'
sh ./compile.sh /lib "cc" "-O -fPIC" "make"
make[4]: Entering directory `/home/abdulaziz/oss41build/noregparm/lib/libOSSlib'
make[4]: `libOSSlib.so' is up to date.
make[4]: Leaving directory `/home/abdulaziz/oss41build/noregparm/lib/libOSSlib'
make[3]: Leaving directory `/home/abdulaziz/oss41build/noregparm/lib/libOSSlib'
make[2]: Leaving directory `/home/abdulaziz/oss41build/noregparm/lib'
kernel/OS/Linux
make[2]: Entering directory `/home/abdulaziz/oss41build/noregparm/kernel/OS/Linux'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/abdulaziz/oss41build/noregparm/kernel/OS/Linux'
make[1]: Leaving directory `/home/abdulaziz/oss41build/noregparm'
sh build.sh
Check devices for oss_ali5455
Check devices for oss_atiaudio
Check devices for oss_audigyls
Check devices for oss_audioloop
Check devices for oss_audiopci
Check devices for oss_cmi878x
Check devices for oss_cmpci
Check devices for oss_cs4281
Check devices for oss_cs461x
Check devices for oss_digi96
Check devices for oss_emu10k1x
Check devices for oss_envy24
Check devices for oss_envy24ht
Check devices for oss_fmedia
Check devices for oss_geode
Check devices for oss_hdaudio
Check devices for oss_ich
Check devices for oss_imux
Check devices for oss_midiloop
Check devices for oss_midimix
Check devices for oss_sblive
Check devices for oss_sbpci
Check devices for oss_sbxfi
Check devices for oss_solo
Check devices for oss_trident
Check devices for oss_usb
Check devices for oss_userdev
Check devices for oss_via823x
Check devices for oss_via97
Check devices for oss_ymf7xx
cp: cannot stat `lib/libsalsa/.libs/libsalsa.so.2.0.0': No such file or directory
Warning: No libsalsa library compiled
done ossinfo
done ossmix
done osspartysh
done ossphone
done ossplay
done ossrecord
done osstest
done ossxmix
done ossdevlinks
done savemixer
done vmixctl
done ossdetect
cp -R prototype/* /
cd "/usr/lib/oss"/build && sh install.sh

OSS build environment set up for REGPARM kernels

Building module osscore
Building module ali5455
Compiling module ali5455 failed
make[1]: Entering directory `/usr/lib/oss/build'
make -C /lib/modules/2.6.27-9-generic/build M=/usr/lib/oss/build modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
make[3]: *** No rule to make target `/usr/lib/oss/build/ali5455.c', needed by `/usr/lib/oss/build/ali5455.o'.  Stop.
make[2]: *** [_module_/usr/lib/oss/build] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/lib/oss/build'
make: *** [install] Error 4

```

---

### Post by Piraja on 2009-01-03
> **Piraja said:**
> **SO**, is there a way to at least disable the microphone for the time being? I.e. a boot parameter or something like that?
... **or** perhaps I could blacklist it??

**EDIT:** Never mind, I'm too impatient to keep trying to fix the feedback issue. I decided to re-install Intrepid &#8212; so I can begin tweaking from scratch again (yet, I do have a separate /home partition and backups of some scripts & settings).

"If it's not broken," I remember reading somewhere on this forum, "you haven't tweaked it enough yet."

**AND YET**... sometimes [simple solutions]("http://ubuntuforums.org/showpost.php?p=6488371&postcount=1293") "just work" (argrh!).

---

### Post by jwhitene on 2009-03-13
> **Temüjin said:**
> The OSS4 Install Guide has moved to: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

After failing to get alsa working after several months of googling, both with 8.04 and 8.10, OSS installed flawlessly.  Currently listening to music at work again:)

---

### Post by MatthiasM on 2009-03-19
> **Temüjin said:**
> [SIZE="4"]**Reverting to ALSA**[/SIZE]
If, for some reason, you want to go back to ALSA, here is the procedure: (I tested this myself on my test system)
```
sudo soundoff
sudo dpkg -r oss-linux
sudo dpkg-reconfigure linux-sound-base
sudo apt-get -y install libesd-alsa0 alsa-oss alsa-base libsdl1.2debian-alsa
gksudo gedit /etc/modprobe.d/blacklist
```
The preceding command opens your blacklist file in the text editor. Delete all the lines from "blacklist snd-seq" down to the end of the file (make sure the last line in the file refers to a snd module and was not added by another program).
Restart the PC.
Now, re-install ALSA kernel modules with this script: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
Go to System -> Preferences -> Sounds and select Autodetect or ALSA
Any applications that you configured for OSS should be changed back to ALSA, although they should work with the alsa-oss wrapper.

Optionally, you can setup and configure PulseAudio. I have no experience with this, but I have seen guides for it (use search). If you do, remember to install the Pulse-compatible libflashsupport package:
```
sudo apt-get install libflashsupport
```

I did some extra commands to get rid of OSS4 ([Source]("http://www.4front-tech.com/forum/viewtopic.php?t=3108"))
```
sudo sh /usr/lib/oss/scripts/restore_drv.sh
```
and add the OSS modules to the blacklist
```
sudo cat /lib/linux-sound-base/noOSS.modprobe.conf >> /etc/modprobe.d/blacklist
```

If really everything is misconfigured and nothing works try the hard way:
```
sudo apt-get install --reinstall linux-image-$(uname -r)
```

---

### Post by HousieMousie2 on 2009-03-23
Hello again,

I made it through all of the instructions... but...

sudo soundon causes a system crash.

```

ossinfo

No /dev/mixer device available in your system.
Perhaps Open Sound System is not installed or running.
```

So, clearly OSS is not running.

```

sudo ossdetect -v

Detected Creative SB X-Fi (PCI-e) *EARLY BETA*
USB support available in the system, adding USB driver
Detected Generic USB audio/MIDI device (BETA)
```

```

lsmod

Module                  Size  Used by
ipv6                  267908  10
af_packet              23812  2
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0
acpi_cpufreq           10796  1
cpufreq_ondemand        9740  1
cpufreq_stats           7104  0
cpufreq_userspace       5284  0
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0
cpufreq_conservative     8712  0
sbs                    15112  0
sbshc                   7680  1 sbs
container               5632  0
video                  19856  0
output                  4736  1 video
dock                   11280  0
battery                14212  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0
dm_crypt               15364  0
dm_mod                 62660  1 dm_crypt
ac                      6916  0
coretemp                8448  0
f71882fg               11524  0
sbp2                   24072  0
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0
serio_raw               7940  0
psmouse                40336  0
wacom                  18048  0
nvidia               6912564  26
i2c_nforce2             7680  0
button                  9232  0
agpgart                34760  1 nvidia
evdev                  13056  4
pcspkr                  4224  0
i2c_core               24832  2 nvidia,i2c_nforce2
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
ext3                  136840  3
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0
sr_mod                 17956  0
sd_mod                 30720  5
cdrom                  37408  1 sr_mod
pata_amd               14212  0
usbhid                 32128  0
hid                    38784  1 usbhid
pata_jmicron            7040  0
ohci1394               33584  0
ohci_hcd               26640  0
ahci                   28548  0
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0
ehci_hcd               37900  0
forcedeth              51980  0
sata_nv                27528  4
ata_generic             8324  0
usbcore               146412  5 wacom,usbhid,ohci_hcd,ehci_hcd
libata                159600  6 pata_amd,pata_jmicron,ahci,pata_acpi,sata_nv,ata_generic
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
thermal                16796  0
processor              36488  2 acpi_cpufreq,thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1

```
```

lspci -v  (greatly abridged, obviously)


0b:00.0 PCI bridge: Creative Labs Unknown device 7006 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=0b, secondary=0c, subordinate=0c, sec-latency=64
        Memory behind bridge: feb00000-febfffff
        Capabilities: <access denied>

0c:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
        Subsystem: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at febfc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

A little help?

---

### Post by akarun on 2009-04-04
Hi,
I installed oss4.1 following the instructions and sound works awesome in my system. I have a lenovo y530 and all the speakers are now roaring with full volume :)

However, I haven't got my microphone to work. I basically want to be able to use skype. I tried ossrecord, audacity no sound is being recorded :(

Here are the various info that may help to figure out what might be wrong with my setup

ossinfo:
```

arun@Phoenix:~$ ossinfo
Version info: OSS 4.2 (b 081213/200903151801) (0x00040100) OSS_HG
Hg revision: changeset: 666:e3a598571f2a, tag: tip, date: Sun Mar 15 13:22:13 2009 +0200, summary: v4.1 pull 090315                                                                                                       
Platform: Linux/i686 2.6.28-11-generic #40-Ubuntu SMP Fri Apr 3 17:39:51 UTC 2009 (Phoenix)                  

Number of audio devices:        11
Number of audio engines:        15
Number of MIDI devices:         0 
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 Intel HD Audio interrupts=62090313 (62090317)
    HD Audio controller Intel HD Audio
    Vendor ID    0x8086293e
    Subvendor ID 0x17aa3a0d
     Codec  0: ALC888 (0x10ec0888/0x17aa3d78)
     Codec  1: Motorola3055 (0x10573055)
     Codec  3: Unknown (0x10de0003/0x10de0101)
 2: oss_usb0 USB audio core services

MIDI devices (/dev/midi*)

Mixer devices
 0: High Definition Audio ALC888 (Mixer 0 of device object 1)

Audio devices
HD Audio play front               /dev/oss/oss_hdaudio0/pcm0  (device index 0)
HD Audio play rear                /dev/oss/oss_hdaudio0/pcm1  (device index 1)
HD Audio play center/LFE          /dev/oss/oss_hdaudio0/pcm2  (device index 2)
HD Audio play side                /dev/oss/oss_hdaudio0/pcm3  (device index 3)
HD Audio play pcm4                /dev/oss/oss_hdaudio0/pcm4  (device index 4)
HD Audio play spdif-out           /dev/oss/oss_hdaudio0/spdout0  (device index 5)
HD Audio play spdifout            /dev/oss/oss_hdaudio0/spdout1  (device index 6)
HD Audio play modem               /dev/oss/oss_hdaudio0/mdmout0  (device index 7)
HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin0  (device index 8)
HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin1  (device index 9)
HD Audio rec modem                /dev/oss/oss_hdaudio0/mdmin0  (device index 10)

  /dev/dsp -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_in -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_out -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_ac3 -> /dev/oss/oss_hdaudio0/spdout0
  /dev/dsp_mmap -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_multich -> /dev/oss/oss_hdaudio0/pcm0

```

ossmix:
```

arun@Phoenix:~$ ossmix
Selected mixer 0/High Definition Audio ALC888
Known controls are:                          
codec1.jack.int-speaker.mode1 <front|rear|center/LFE|side|pcm4|input> (currently front)
codec1.jack.int-speaker1 [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)               
codec1.jack.int-speaker.mute1 ON|OFF (currently OFF)                                   
codec1.jack.int-speaker.mode2 <front|rear|center/LFE|side|pcm4|input> (currently front)
codec1.jack.int-speaker2 [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)               
codec1.jack.int-speaker.mute2 ON|OFF (currently OFF)                                   
codec1.jack.int-speaker.mode3 <front|rear|center/LFE|side|pcm4|input> (currently front)
codec1.jack.int-speaker3 [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)               
codec1.jack.int-speaker.mute3 ON|OFF (currently OFF)                                   
codec1.jack.black.mode1 <front|rear|center/LFE|side|pcm4|input> (currently front)      
codec1.jack.black1 [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)                     
codec1.jack.black.mute1 ON|OFF (currently OFF)                                         
codec1.jack.int-mic.mode <front|rear|center/LFE|side|pcm4|input> (currently front)     
codec1.jack.int-mic [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)                    
codec1.jack.int-mic.mute ON|OFF (currently OFF)                                        
codec1.jack.black.mode2 <front|rear|center/LFE|side|pcm4|input> (currently front)      
codec1.jack.black2 [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)                     
codec1.jack.black.mute2 ON|OFF (currently OFF)                                         
codec1.record.mix.mute.mic1 ON|OFF (currently OFF)                                     
codec1.record.mix.mute.int-mic1 ON|OFF (currently OFF)                                 
codec1.record.mix.mute.headpho1 ON|OFF (currently OFF)                                 
codec1.record.mix.mute.int-spe1 ON|OFF (currently OFF)                                 
codec1.record.mix.mute.int-spe2 ON|OFF (currently OFF)                                 
codec1.record.mix.mute.int-spe3 ON|OFF (currently OFF)                                 
codec1.record.mix.mute.input-m1 ON|OFF (currently OFF)                                 
codec1.record.mix1 [<leftvol>:<rightvol>] (currently 46.4:46.4 dB)                     
codec1.record.mix.mute.mic2 ON|OFF (currently OFF)                                     
codec1.record.mix.mute.int-mic2 ON|OFF (currently OFF)                                 
codec1.record.mix.mute.headpho2 ON|OFF (currently OFF)                                 
codec1.record.mix.mute.int-spe4 ON|OFF (currently OFF)                                 
codec1.record.mix.mute.int-spe5 ON|OFF (currently OFF)                                 
codec1.record.mix.mute.int-spe6 ON|OFF (currently OFF)                                 
codec1.record.mix.mute.input-m2 ON|OFF (currently OFF)                                 
codec1.record.mix2 [<leftvol>:<rightvol>] (currently 46.4:46.4 dB)
codec1.misc.mic [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
codec1.misc.int-mic [<leftvol>:<rightvol>] (currently 46.4:46.4 dB)
codec1.misc.headphone [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
codec1.misc.int-speaker1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
codec1.misc.int-speaker2 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
codec1.misc.int-speaker3 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
codec1.misc.input-mix <mic|int-mic> (currently mic)
codec1.misc.front-mute ON|OFF (currently OFF)
codec1.misc.input-mix-mute1 ON|OFF (currently OFF)
codec1.misc.front1 [<leftvol>:<rightvol>] (currently 46.4:46.4 dB)
codec1.misc.front2 <front|input-mix> (currently front)
codec1.misc.rear-mute ON|OFF (currently OFF)
codec1.misc.input-mix-mute2 ON|OFF (currently OFF)
codec1.misc.rear1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
codec1.misc.rear2 <rear|input-mix> (currently rear)
codec1.misc.center/lfe-mute ON|OFF (currently OFF)
codec1.misc.input-mix-mute3 ON|OFF (currently OFF)
codec1.misc.center/lfe1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
codec1.misc.center/lfe2 <center/LFE|input-mix> (currently center/LFE)
codec1.misc.side-mute ON|OFF (currently OFF)
codec1.misc.input-mix-mute4 ON|OFF (currently OFF)
codec1.misc.side1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
codec1.misc.side2 <side|input-mix> (currently side)
codec1.misc.pcm4-mute ON|OFF (currently OFF)
codec1.misc.input-mix-mute5 ON|OFF (currently OFF)
codec1.misc.pcm41 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
codec1.misc.pcm42 <pcm4|input-mix> (currently pcm4)
vmix0-enable ON|OFF (currently ON)
vmix0-rate <decimal value> (currently 48000) (Read-only)
vmix0-channels <Stereo|Multich> (currently Multich)
vmix0-src <Fast|Low|Medium|High|High+|Production|OFF> (currently Fast)
vmix0-outvol <monovol> (currently 20.0 dB)
vmix0-invol <monovol> (currently 25.0 dB)
vmix0.pcm11 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm12 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm13 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm14 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)


```

Any help would be great.

Thanks,
Arun

---

### Post by Yellow Pasque on 2009-04-05
Arun,
I think you'll get more help on this subject at the OSS4 forum
Make sure you did this step right:
[https://help.ubuntu.com/community/OpenSound#System%20Sounds%20on%20KDE%204.x](https://help.ubuntu.com/community/OpenSound#System%20Sounds%20on%20KDE%204.x)

Also: [http://packages.medibuntu.org/jaunty/skype-static-oss.html](http://packages.medibuntu.org/jaunty/skype-static-oss.html)

---

### Post by akarun on 2009-04-05
Thanks! I will give it a shot.
I am sure I did the step right. I am now on windows (due to a different problem with my internet in Linux)
Will come back to you soon.
Cheers,
Arun

---

### Post by akarun on 2009-04-05
I must agree that I didn't do that step carefully.
For my audio output, I could succesfully choose oss as the preferred over alsa
However in audio input, I don't see any devices. This is a cause for concern isn't it?

Thanks,
Arun

---

### Post by perixx on 2009-04-25
Hello Temüjin,


You'll not remember me, but I've been attempting to install oss nearly 1 year ago (you've been very helpful in my thread on how to get rid of the failed installation back then).

Now, after my Alsa system has blown in my face some 4 weeks ago, I've finally decided to give it another shot, since I couldn't get Alsa back to work. After getting the latest hg repository release and following the steps exactly on the help.ubuntu.com page, as you suggested, OSS is up and running!

Mplayer is working fine, both in Firefox and as a standalone (just had to switch settings to oss), also Flashplayer 10 is working neatly, after applying the libflashsupport patch.

The only thing that wont budge, is to have my Maudio card (standard now) working along with my ADI onboard chip (Intel for real? Deactivated in BIOS now), as it wouldn't with Alsa. I'd like to have the opportunity to select the desired sound output per application, e.g. headset via onboard for ekiga or the likes, while playing music with my superior sound card... 
perhaps you've got an idea?

Thanks for your competent hints so far!


perixx

---

### Post by Yellow Pasque on 2009-04-25
perixx, 
Are you using Xubuntu 8.04 as your signature indicates? If so, make sure you have the right oss plugins to make ekiga work:
```
sudo apt-get install libpt-1.10.10-plugins-oss libsdl1.2debian-oss
sudo apt-get remove libpt-1.10.10-plugins-alsa libsdl1.2debian-alsa
```

Enable your onboard audio and then post the output of ossinfo.

---

