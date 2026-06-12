---
title: "MythTV - will it ever work?"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by Patrick Dixon on 2007-02-09
I'm now on my 4th install of ubuntu/MythTV.

The first one seemed to work except that I had a problem with the motherboard sound and ended up rebuilding it (via - Windows) before the sound would work.

Having done that, the next install appeared to work, but video had major breakup and sound glitches.  Neither of these were present running the Hauppauge Nova-T card directly to mplayer.

The next two installs suffered from both the above problem and/or major blank periods with the disk churning but nothing happening.  I have hard booted this machine more times now that all the Windows installs I've ever had.

So I'm completely disillusioned.  The machine has a 2G Athlon 64 on a Asus A8V-MX m/b with 51MB of RAM and much SATA/PATA HD space.  The card has built-in video and audio.  I'm trying to run it as a combined front/back end.  Don't really care about the desktop.

I've tried both the SuperM1 and the Parker guides (using the Parker guide for lirc & UK programme info) and both seem to give the same results.

So what am I doing wrong?  Everything appears to be installed and working but MythTV just doesn't work!  Are the repo updates currently broken? (I'm on Edgy)

I'm totally lost and on the point of giving up in disgust, so any help would be much appreciated.

---

### Post by dannyboy79 on 2007-02-09
superM1's has been running Mythtv .20 for a long time now to the best of my knowledge. I would suggest you talk with him thru some kind of one-on-one chat program and you'll be fine. I have the PVR-350 and have installed eveything I just haven't ran the mythtv-setup yet due to not having time. superm1 got me squared away so the ivtv install worked with dapper and my mysql got all squared away (admin user). so he said all I need to do is run the mythtv-setup and I should be good to go. hopefully he can help ya.

one thing I just noticed when I did sudo aptitude show mythtv. it states right at the bottom the following:

If you are intended on installing this on a standalone/non-desktop machine, you should look into the metapackages available:
 ubuntu-mythtv-master-backend ubuntu-mythtv-secondary-backend ubuntu-mythtv-frontend ubuntu-mythtv-master-backend-frontend
 ubuntu-mythtv-secondary-backend-frontend

so if I were you I would look into this since you doin't care about a desktop. also, if you don't want a linux desktop, why not go with knoppMyth. here is a comment I read about it dated Jul 25 of 2005! so by now it's gotta be sweat.

. Since seeing this [http://revision3.com/systm/mythtv/](http://revision3.com/systm/mythtv/) show. I have been documenting my trials going through the install process here. ([http://rss.monroe-kc.com](http://rss.monroe-kc.com)) I have most things working and up but still have a few issues, such as ripping my dvd's and transcoding stuff correctly. On another note the video functions do work great and using the recording shows functions works like a charm. Once you have a show recorded you can easly cut commercials. I am looking into getting a silent frontend computer(maybe a xbox). 

System Specs: 
PIII 733 
384 Memory 
Hauppauge 250 Card 
Hitachi 160Gig Hdd 
NEC DVD-Combo drive

---

### Post by barney_1 on 2007-02-09
Patrick,

I would encourage you to keep after it.  I have had mythtv running for quite some time now and couldn't be happier.  I used the guide from the ubuntu wiki:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

Which helped me to setup my storage partition and the program itself.  It has been running without a hitch for at least two months now.

It was a bit of a trick to get lirc functioning properly, but after about a day and a half (with the help of some voodoo) I figured it out.

It's sooooo worth the effort!
(one last thing, and I can't stress this enough, make sure you bios is up-to-date!)

---

### Post by Patrick Dixon on 2007-02-09
I followed Superm1s guide, and I don't think there's anything wrong with the guide (except step 12 which I've already mentioned to him), I just don't think Mythtv works.  Maybe it's a drivers thing, or maybe the constant updating of Linux packages means there's some kind of incompatibilities between all the various elements, but I have it all installed 'correctly' and it still doesn't work!

And how the hell are you supposed to debug something when you have to keep hitting the off button to kill the thing when it crashes?

---

### Post by Patrick Dixon on 2007-02-09
> **barney_1 said:**
> Patrick,

I would encourage you to keep after it.  I have had mythtv running for quite some time now and couldn't be happier.  I used the guide from the ubuntu wiki:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

Which helped me to setup my storage partition and the program itself.  It has been running without a hitch for at least two months now.

It was a bit of a trick to get lirc functioning properly, but after about a day and a half (with the help of some voodoo) I figured it out.

It's sooooo worth the effort!
(one last thing, and I can't stress this enough, make sure you bios is up-to-date!)

Thanks - followed that guide and the ir remote works absolutely fine - it's just pictures and sound that seems to be the problem ;-(

---

### Post by basketcase on 2007-02-09
I've lost count the number of times I have tried to get MythTV to work.  The install seems easiest on Ubuntu, but I have yet to be successful.  

If it wasn't one thing, it was another.  Either Ubuntu, or Myth, or Video, or LIRC, every time I try to install Myth, it's something new.  Tonight it is MySQL and some QSQLError::exec: database not open error.  

I even tried BeyondTV for Windows, but couldn't even get my remote work, purchased USB-UIRT, and still didn't work.  So now I'm back to Myth tonigh.  Even tried the latest version of KnoppMyth and FedoraMyth.  

I think a Tivo is in my future.  If you take into consideration what I have into hardware now, and what I have in time, I can justify a Tivo.  

Good luck in whatever you decide.

---

### Post by majoridiot on 2007-02-10
i've been running myth for about six months and couldn't be happier with it.  just today, i
installed a backend on edgy with a pvr-150 and firewire and a remote frontend on a regular 
dapper desktop with lirc and a remote... both from the ubuntu community link posted above.

counting from the point the hard drives were formatted and ubuntu was installed and updated,
i had both ends up and running perfectly in less than two hours- and the delay was due only
to the repos being slow as molasses for some reason (56K-70kbps?!)

other than a few small bugs, mythtv has been quite reliable on my systems.  i know from the
forum posts that it makes some people crazy... but i suspect that is due more to oddball hardware
and mixing and matching installation instructions more than it is due to a problem with myth
itself.

i know people don't want to hear it... but if you want the best shot of getting myth running on
ubuntu, do it on a clean dapper install with mario's packages and the community guide.

or keep suffering in vain. :S

---

### Post by basketcase on 2007-02-10
Why dapper and not edgy where .20 are in the repos?  

> **majoridiot said:**
> i've been running myth for about six months and couldn't be happier with it.  just today, i
installed a backend on edgy with a pvr-150 and firewire and a remote frontend on a regular 
dapper desktop with lirc and a remote... both from the ubuntu community link posted above.

counting from the point the hard drives were formatted and ubuntu was installed and updated,
i had both ends up and running perfectly in less than two hours- and the delay was due only
to the repos being slow as molasses for some reason (56K-70kbps?!)

other than a few small bugs, mythtv has been quite reliable on my systems.  i know from the
forum posts that it makes some people crazy... but i suspect that is due more to oddball hardware
and mixing and matching installation instructions more than it is due to a problem with myth
itself.

i know people don't want to hear it... but if you want the best shot of getting myth running on
ubuntu, do it on a clean dapper install with mario's packages and the community guide.

or keep suffering in vain. :S

---

### Post by Titus A Duxass on 2007-02-10
I've installed Edgy + Myth on four different machines so far, each without problems. It takes about 1 to 1.5 hours to get going.
Admittedly my first installs were stressful but that was back in the days of 0.18.

As majoridiot stated, it's probably down to oddball hardware.  Try using a simple graphics card instead of the on-board one. (I use old 440 cards that you can pick up for about 20€).

---

### Post by Patrick Dixon on 2007-02-10
The first install (on an existing edgy desktop) worked fine with separate a PCI sound card.  I had to wipe that one to check the on-board sound in windows and fix the problem.  Subsequent re-installs using the same procedure, gave me glitching video and popping audio, and general sluggishness and crashing problems.  Going back to the PCI audio card made no difference to the problems.

So what's changed?  I don't know, but I can only assume MySql or one of the many drivers or utilities has changed somewhere in the repos.  The whole thing is built on a pack of cards, and some invisible problem can easily cause it not to work.

The superm1 instructions are great, but you can't follow them to the letter as there's at least one stage that doesn't work, and you have to diverge if you need a non-USA programme guide anyway.  I'm quite confident that all the elements are correctly installed and talk to each other - they just don't work correctly together.  I picked the DVB-T card specifically 'cos it was rated best supported for MythTV, but I even had problems with that until I moved PCI slots.

So if you installed it successfully in less that 2hrs, believe me, you're very, very lucky.

---

### Post by Titus A Duxass on 2007-02-10
Patrick,
You are correct, you do have to diverge from SuperM1's guide at some stage.  I have to when I run mythfilldatabase.

You mention, in that you had problems with Stage 12. What is stage 12?

I use SuperM1's guide only so far and then I do my own variations. If you tell me where your problems are, I'll through in my tuppence worth.

---

### Post by Patrick Dixon on 2007-02-10
Thanks!

See this thread for a discussion of the 'stage 12 issue' [http://www.ubuntuforums.org/showthread.php?t=348436&](http://www.ubuntuforums.org/showthread.php?t=348436&)

However, I've resolved that one now (although not by following the either the guide or the other workround - which didn't work for me!).

The first time I installed, I used the parker guide [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) (which is also excellent) as I already had an edgy desktop installed.  That worked fine (with a separate PCI soundcard) but I have tried re-installing that way since and I'm still getting this picture breakup, sound glitching problem.  I suspect that there is some problem either with something hogging resources - impossible to find as the system is so bogged down (when you run live TV or record something) you can't even run 'top', or a problem with the DVB-T card driver.  However, it has all worked once, so the hardware must be capable - otherwise I'd have written it off a week and a half ago.

---

### Post by Titus A Duxass on 2007-02-10
I had problems with the same area, now I follow the guide up to and including this:
sudo apt-get install mythtv-frontend gdm ubuntu-artwork xterm openbox gnome-screensaver xserver-xorg gsfonts-x11 xfonts-100dpi xfonts-75dpi msttcorefonts xfonts-base mysql-server mythtv-backend mythtv-database usplash-theme-ubuntu

Then I install gnome-core, I find by doing this I can get auto-login of mythtv and automatic starting of the frontend on boot.

Then I install all the other bits like nvidia drivers, codecs, dvd software, etc. using Automatix2.

Then I exit the session and log back in as user mythtv and do a mythtv-setup from the CLI.

Once myth is setup with out failure I reboot.

That logs in myth automatically and then brings up the mythfrontend automatically (the myth backend is already running).

That's a very brief summary of my install, the major difference is that you are using DVB-T.  I have no experience with DVB-T.

Does you hardware work stand-alone?

I assume that you have set the on-board memory sharing to the maximum allowed.

---

### Post by Patrick Dixon on 2007-02-10
OK, I have just done clean install number 5 of ubuntu and mythtv following superm1s instructions as closely as possible, deviating only where necessary to make things work and to use UK programme information.

As before everything works but there is video breakup and sound glitching - basically mythtv is just not keeping up.

The hardware all works standalone - running mplayer.

The video card is set for 64MB of vga buffer - which is the max.

Running top with Live TV running, mythfrontend & Xorg are consuming 55-60% of CPU and 45-50% of memory.  Nothing else is consuming anything else of any significance.  IIUC, mythfrontend is supposed to run on a mni-itx card and this is a 2G Althlon 64 with 1/2G RAM - so it can't possibly be underpowered!

So all those people who've installed Mythtv in under 2hrs successfully (this has taken 7hrs just to download from all the repos and run through all the steps) please tell me where I'm going wrong.

---

### Post by dannyboy79 on 2007-02-10
i am guessing that it's your tv-card. i am pretty sure superm1's install uses the ivtv drivers. i didn't think that the dvblahblah card doesn't work with the ivtv but I could be wrong. i am sorry you can't get this to work but we do know that it DOES work for many people.

---

### Post by Patrick Dixon on 2007-02-10
How can it possibly be the tv card?

The card* worked fine in the first install, works fine with mplayer on the same machine & installation (that mythtv live tv doesn't work on), and is one of the most recommended cards for Mythtv.  It's supported in ubuntu edgy with drivers.

* Hauppauge Nova-T (cx88)

---

### Post by dannyboy79 on 2007-02-10
all i know is that almost every guide I have seen has used the ivtv drivers which DON'T work with the DVB-T card. you have to use different drivers. you can read here [http://www.mythtv.org/docs/mythtv-HOWTO-3.html](http://www.mythtv.org/docs/mythtv-HOWTO-3.html) 
about how often the pvr cards are referenced.

then here is the info on the dvb- type cards.
[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)

---

### Post by Patrick Dixon on 2007-02-10
Yes, but obviously this card is working, otherwise I wouldn't get live tv with mplayer.

Also the parker guide* says that the card is supported out of the box on edgy (he has 2) - which seems correct.

* see link above

PS. from your 2nd link it says it works with kernels newer than 2.6.12.  Edgy is 2.6.17-10-generic:

Hauppauge

New WinTV-NOVA-T_PCI
(since 07/2004) [26]

ca. 100 EURO
	works with patches from [27] or >= kernel 2.6.12

---

### Post by Patrick Dixon on 2007-02-10
Here's the output I get from mythfrontend if I start it in a window.  It looks like something in X is broken.  Any idea what?

2007-02-10 19:34:31.477 VideoOutputXv: XvMCTex: Init failed
2007-02-10 19:34:31.478 VideoOutputXv Error: Could not find suitable XVideo surface.
2007-02-10 19:34:31.478 VideoOutputXv: Falling back to X shared memory video output.
                              *** May be slow ***
2007-02-10 19:34:31.905 TV: Changing from None to WatchingLiveTV
2007-02-10 19:34:31.913 Video timing method: USleep with busy wait
2007-02-10 19:34:31.913 Using realtime priority.
2007-02-10 19:34:34.427 VideoOutputXv: XvMCTex: Init failed
2007-02-10 19:34:34.427 VideoOutputXv Error: Could not find suitable XVideo surface.
2007-02-10 19:34:34.427 VideoOutputXv: Falling back to X shared memory video output.
                              *** May be slow ***
2007-02-10 19:34:34.665 AFD: Opened codec 0x9ae780, id(MPEG2VIDEO) type(Video)
2007-02-10 19:34:34.721 AFD: Opened codec 0x99ea00, id(MP3) type(Audio)
2007-02-10 19:34:34.721 AFD: Opened codec 0xab9b20, id(MP3) type(Audio)
2007-02-10 19:34:34.721 AFD: Opened codec 0x9ac480, id(DVB_SUBTITLE) type(Subtitle)
2007-02-10 19:34:34.804 Opening OSS audio device '/dev/dsp'.
2007-02-10 19:34:34.810 NVP: Enabling Audio
2007-02-10 19:34:36.006 VideoOutputXv Error:
***
* Your system is not capable of displaying the
* full framerate at 1024x768 resolution.  Frames
* will be skipped in order to keep the audio and
* video in sync.

---

### Post by basketcase on 2007-02-10
Wow...more successful then I've ever been. 

Ubuntu 6.06 per the wiki and the parker guide.  

I can't get Nvidia TV-Out or PVR-350 Out though. It does show up on the monitor just fine.  Also I unhooked my digital cable box and it's just running on straight cable now.  One step at a time.

---

### Post by dannyboy79 on 2007-02-10
what driver are you using for your vid card? the one that is used to actually display the live tv? i thought I saw you have the 5200, maybe that card can't keep up as the end error states? have you asked superm1 for any ideas?

---

### Post by dannyboy79 on 2007-02-10
i gogled the XvMCTex error and found these links. check them out.

 [http://www.google.com/search?client=opera&rls=en&q=VideoOutputXv:+XvMCTex:+Init+failed+and+dvb-t+card&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.com/search?client=opera&rls=en&q=VideoOutputXv:+XvMCTex:+Init+failed+and+dvb-t+card&sourceid=opera&ie=utf-8&oe=utf-8)

---

### Post by basketcase on 2007-02-10
> **dannyboy79 said:**
> what driver are you using for your vid card? the one that is used to actually display the live tv? i thought I saw you have the 5200, maybe that card can't keep up as the end error states? have you asked superm1 for any ideas?
nvidia-glx for the on-board s-video
followed the wiki for tv-out on the PVR-350. 

the XPC system does not have 2 PCI slots, so I can't use my 5200.  I could move everything over to a PIII 8xx MHz box, that has multiple PCI slots.

---

### Post by Patrick Dixon on 2007-02-10
> **dannyboy79 said:**
> i gogled the XvMCTex error and found these links. check them out.

 [http://www.google.com/search?client=opera&rls=en&q=VideoOutputXv:+XvMCTex:+Init+failed+and+dvb-t+card&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.com/search?client=opera&rls=en&q=VideoOutputXv:+XvMCTex:+Init+failed+and+dvb-t+card&sourceid=opera&ie=utf-8&oe=utf-8)

Yes I googled that too, but unfortunately I'm none the wiser.

---

### Post by Titus A Duxass on 2007-02-12
Patrick,
I was amusing myself this weekend by reading the MythTV How-To that can be found on the MythTV website.

It would appear that your problems are most likely to be caused by your on-board graphics.

---

### Post by Patrick Dixon on 2007-02-12
Thanks I'll check it out, although I am perplexed that this appeared to work fine on the initial install and I have no idea what is different this time around (I've tried to repeat it exactly).

I'm also surprised that people claim that a frontend can work with a Mini-ITX board (which also has on-board graphics) when a 2G Althon 64 can't keep up!

---

### Post by dannyboy79 on 2007-02-12
the mini-itx board might have specific hardware combination that did work. you have a combination of certain hardware that is giving you issues, why don't you try to change up the hardware if you can. go to used computer parts store and pick up the same exact hardware that are called out in guides or reviews and then you can be sure it'll work. that's all I can suggest at this time.

---

### Post by Patrick Dixon on 2007-02-12
> **Titus A Duxass said:**
> Patrick,
I was amusing myself this weekend by reading the MythTV How-To that can be found on the MythTV website.

It would appear that your problems are most likely to be caused by your on-board graphics.
Checked it out, but can't find anything that indicates this????

---

### Post by Patrick Dixon on 2007-02-12
> **dannyboy79 said:**
> the mini-itx board might have specific hardware combination that did work. you have a combination of certain hardware that is giving you issues, why don't you try to change up the hardware if you can. go to used computer parts store and pick up the same exact hardware that are called out in guides or reviews and then you can be sure it'll work. that's all I can suggest at this time.

Well I could go out and spend more money to add to the 2 1/2 weeks of time that I've already wasted, but to be honest, I'm not really inclined to throw good money after bad.

There seems to be no real information available when you run into anything but the most basic of MythTV problems, and I feel very pessimistic about it's future.  It really seems to be pot luck as to whether anything works or not, and I can't see that Linux will ever be a good platform for any application that requires video and sound to be working properly to get a result.

---

### Post by kpatz on 2007-02-12
What version of the nVidia drivers are you using?  **dmesg | grep -i nvidia**

Your xorg.conf should have a device section that has a driver name of "nvidia".  If you're using "nv", install the nVidia driver.

Do you have a file /etc/X11/XvMCConfig?  What's in it?  The nVidia drivers use libXvMCNVIDIA_dynamic.so.1.  Some of the messages in your log indicate problems with XvMC so give that a look.

---

### Post by dannyboy79 on 2007-02-12
> **kpatz said:**
> What version of the nVidia drivers are you using?  **dmesg | grep -i nvidia**

Your xorg.conf should have a device section that has a driver name of "nvidia".  If you're using "nv", install the nVidia driver.

Do you have a file /etc/X11/XvMCConfig?  What's in it?  The nVidia drivers use libXvMCNVIDIA_dynamic.so.1.  Some of the messages in your log indicate problems with XvMC so give that a look.

kpatz, I've already told him that and he said he looked into that with no real answers.

---

### Post by Patrick Dixon on 2007-02-12
> **kpatz said:**
> What version of the nVidia drivers are you using?  **dmesg | grep -i nvidia**

Your xorg.conf should have a device section that has a driver name of "nvidia".  If you're using "nv", install the nVidia driver.

Do you have a file /etc/X11/XvMCConfig?  What's in it?  The nVidia drivers use libXvMCNVIDIA_dynamic.so.1.  Some of the messages in your log indicate problems with XvMC so give that a look.
root@mediaserver:/home/dixon# cat /etc/X11/XvMCConfig
libXvMC.so.1

I'm not using nvida drivers at all - it's a via chipset

root@mediaserver:/home/dixon# lspci -v
[snip]
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8129
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 233
        Memory at d0000000 (32-bit, prefetchable) [size=64M]
        Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at f8af0000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 2
        Capabilities: [70] AGP version 3.0
[/snip]

I'm now on my 5th clean install (back to a desktop install and the parker guide as per the first attempt that seemed to work), and I don't get those errors any more.  It would be nice to know the cause of this though:- [mpegts @ 0xb7352500]Parser not found for Codec Id: 94212 !

Googling it, produces questions, but no answers.

I strongly suspect that something in the ubuntu depositries has 'broken' between the first and subsequent installs (probably video driver or mpeg decoding), but there is no way on knowing or correcting it.  Dapper is not an option as the motherboard is not supported and can't even get a network connection to build a new kernel.


mythfrontend 'live tv' log:-

2007-02-12 14:04:07.350 New DB connection, total: 2
2007-02-12 14:04:07.412 Connected to database 'mythconverg' at host: localhost
2007-02-12 14:04:07.710 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-02-12 14:04:07.789 Using protocol version 31
2007-02-12 14:04:08.000 TV: Attempting to change from None to WatchingLiveTV
2007-02-12 14:04:08.001 Using protocol version 31
2007-02-12 14:04:09.035 DPMS Deactivated
2007-02-12 14:04:09.757 NVP: Disabling Audio, params(-1,2,44100)
2007-02-12 14:04:09.902 VideoOutputXv: XvMCTex: Init failed
2007-02-12 14:04:09.977 VideoOutputXv: XVideo Adaptor Name: 'XV_SWOV'
2007-02-12 14:04:11.625 TV: Changing from None to WatchingLiveTV
2007-02-12 14:04:11.665 Using realtime priority.
[mpegts @ 0xb7352500]Parser not found for Codec Id: 94212 !
[mpegts @ 0xb7352500]Parser not found for Codec Id: 94212 !
2007-02-12 14:04:13.305 VideoOutputXv: XvMCTex: Init failed
2007-02-12 14:04:13.306 VideoOutputXv: XVideo Adaptor Name: 'XV_SWOV'
2007-02-12 14:04:13.705 AFD: Opened codec 0x92e68c0, id(MPEG2VIDEO) type(Video)
2007-02-12 14:04:13.742 AFD: Opened codec 0x92e6480, id(MP3) type(Audio)
2007-02-12 14:04:13.743 AFD: Opened codec 0x92fa680, id(MP3) type(Audio)
2007-02-12 14:04:13.743 AFD: Opened codec 0x92fabf0, id(DVB_SUBTITLE) type(Subtitle)

---

### Post by dannyboy79 on 2007-02-12
> **Patrick Dixon said:**
>  I can't see that Linux will ever be a good platform for any application that requires video and sound to be working properly to get a result.
i can't believe that you have just stated this and actually mean it. This so called "application" IS BASED ALL ON VIDEO & SOUND so what in the world do you mean. Mythtv displays and records live tv and you're complaining that Mythtv won't work right just because your video and sound doesn't work right. Well, I would say that there's your major malfunction, it's your thinking. If you  feel that you've troubleshoot to your hearts content and still can't get it with your hardware. than ask superm1 exactly what he uses and buy that stuff and try again but don't make silly comments about linux as a platform just because you can't get something working. the 2 links I posted for you, 1 about mythtv requirements and inner workings in detail as well as the dvb type cards should have given you a great idea as to the capability of what mythtv can do with what hardware. i do hope you get it working as I know it does based on these links.


[http://www.linuxjournal.com/article/8658](http://www.linuxjournal.com/article/8658)

[http://www.linux.com/article.pl?sid=06/03/02/1756255](http://www.linux.com/article.pl?sid=06/03/02/1756255)

[http://entertainment.newsforge.com/article.pl?sid=05/06/27/209236&from=rss](http://entertainment.newsforge.com/article.pl?sid=05/06/27/209236&from=rss)

[http://anandtech.com/linux/showdoc.aspx?i=2190](http://anandtech.com/linux/showdoc.aspx?i=2190)

[http://www.linuxforums.org/multimedia/linux_as_a_media_centre.html?](http://www.linuxforums.org/multimedia/linux_as_a_media_centre.html?)

---

### Post by Unisted on 2007-02-12
I'm no programmer and I haven't got my setup working fully yet but I would check:

- Is everything is working in the first instance?

- Does video/ audio play correctly from DVDs, avi's, mp3's?

- The error message you got indicated that there was not enough graphics memory to run the video so it attempted to obtain memory from another source which was also insufficient. As others have said, are your drivers correct?

Your first install had everything running correctly for a while... what has changed? do you always install all updates if they are available? Did you install mplayer/ vlc, all the codecs etc.. etc..

In the frustration of things not working you may have missed something off... I know I have and as you say, if it's worked once you know it has the potential to work again!

---

### Post by Patrick Dixon on 2007-02-12
> **dannyboy79 said:**
> i can't believe that you have just stated this and actually mean it. This so called "application" IS BASED ALL ON VIDEO & SOUND so what in the world do you mean.  That's exactly what I mean.  What's the point of basing an app on Linux that requires Sound and video to be working, when getting sound and video working is such a major issue on Linux?  Looking through these forums and googling to get answers, you can easily see that there are many, many problems and very few answers.

> **dannyboy79 said:**
> Mythtv displays and records live tv and you're complaining that Mythtv won't work right just because your video and sound doesn't work right. Well, I would say that there's your major malfunction, it's your thinking. If you  feel that you've troubleshoot to your hearts content and still can't get it with your hardware. than ask superm1 exactly what he uses and buy that stuff and try again but don't make silly comments about linux as a platform just because you can't get something working.  If mythtv can only be installed and made to work on specific hardware then surely that hardware should be spec'd at the top of the HowTo?  But I don't think that's the point.  If I wanted to buy more hardware, I'd be better off buying something that was setup and ready to go anyway - which is probably why most people just go Windows. > **dannyboy79 said:**
>  the 2 links I posted for you, 1 about mythtv requirements and inner workings in detail as well as the dvb type cards should have given you a great idea as to the capability of what mythtv can do with what hardware.  There's nothing in those links that tells me this can't work on the hardware I have, and I specifically bought a DVB-T card that was rated 9 out of 10 (the highest score) so that I knew it was supported.
> **dannyboy79 said:**
> i do hope you get it working as I know it does based on these links.Thanks, I appreciate the help, but there's no point in just telling me it 'can work' when it doesn't for me.  If anybody can point me to some specific reason why it shouldn't work on the hardware I have, I'll give up now!  Even better point me in the direction of a fix.

I have one last thing to try, which is to leave the /var/lib director on the same partition as / - which is the way I originally had it, but not what superm1 says to do.  Clean install number 6 coming up ...

---

### Post by Unisted on 2007-02-12
After a little googling on XV_SWOV

I found other users having problems with what appears to be your hardware:

[http://threebit.net/mail-archive/mythtv-dev/msg06821.html](http://threebit.net/mail-archive/mythtv-dev/msg06821.html)

To get the full story you'll have to read the other mails under the same heading but hopefully it'll come to a resolution!

However, reverting back to my first post, it still appears that your hardware is not set up correctly yet.

In addition, in Parkers guide it asks you to check that TV playback works with the videocard before installing Mythtv. Did this step work?

The windows/ linux debate is not important here. Your frustrations are probably making you make mistakes. If I were you I would take a clean break and start afresh tomorrow. This is of course entirely your own choice and you do not have to take my (or anyone elses) advice unless you want too. We're just trying to help!

Of course it might not be the hardware and might be your hard drive partitioning - [http://www.gossamer-threads.com/lists/mythtv/users/248992](http://www.gossamer-threads.com/lists/mythtv/users/248992)

---

### Post by Patrick Dixon on 2007-02-12
> **Unisted said:**
> After a little googling on XV_SWOV

I found other users having problems with what appears to be your hardware:

[http://threebit.net/mail-archive/mythtv-dev/msg06821.html](http://threebit.net/mail-archive/mythtv-dev/msg06821.html)

To get the full story you'll have to read the other mails under the same heading but hopefully it'll come to a resolution!Thanks, but unfortunately it doesn't appear to be the same thing - I don't have the OSD displayed permanently - neither doe it seem to be the A8V-MX hardware I'm using.

> **Unisted said:**
> However, reverting back to my first post, it still appears that your hardware is not set up correctly yet.I think it is.  The first log I posted may have showed a problem, becuase the Alternate Install/AMD64 setup appeared not to select the correct driver.  Changing it to VIA and subsequent installs give the above log.

> **Unisted said:**
> In addition, in Parkers guide it asks you to check that TV playback works with the videocard before installing Mythtv. Did this step work?Yes - live TV plays fine using mplayer.

---

### Post by dannyboy79 on 2007-02-12
> **Patrick Dixon said:**
>  That's exactly what I mean.  What's the point of basing an app on Linux that requires Sound and video to be working, when getting sound and video working is such a major issue on Linux?  Looking through these forums and googling to get answers, you can easily see that there are many, many problems and very few answers.

I have to disagree with you, you stating there is a lack of answers. answers are everywhere, you have to LOOK for them. Yes there may be issues with sound but I don't agree that there are issues with video with particular hardware due to manufacturers support. The sound issues are only because the manufacturer of the hardware doesn't provide linux the correct information and or windows drivers so that linux developers can reverse engineer drivers for linux. You have to remember, everything related to linux is FREE. you don't have to pay for anything, so if you have a hicup here and hicup there, DEAL WITH IT. you want to pay for software and not deal with issues, than like you said, go to windows if you want to line the pockets of gates.

> **Patrick Dixon said:**
> 
If mythtv can only be installed and made to work on specific hardware then surely that hardware should be spec'd at the top of the HowTo?  But I don't think that's the point.  If I wanted to buy more hardware, I'd be better off buying something that was setup and ready to go anyway - which is probably why most people just go Windows.  There's nothing in those links that tells me this can't work on the hardware I have, and I specifically bought a DVB-T card that was rated 9 out of 10 (the highest score) so that I knew it was supported.

The hardware that it works on is documented, in every successful review of mythtv. hence why I posted all those links of reviews of mythtv. heck, there supported hardware is even listed on the main mythtv website. what the website doesn't list is the actually COMBINATIONS of hardware. there are so many different combinations of hardware that they can't actually test each and every one. You keep mentioning that the DVB type cards are so compatible. Well, in one of the links I posted this comment stood out at me and this review was dated November of 2006.

-Compresses video in software using rtjpeg (from Nuppelvideo) or mpeg4 (from libavcodec). Full support for Hardware MPEG-2 encoder cards (Hauppauge PVR-250 / PVR-350). Preliminary support for DVB cards and the new pcHDTV tuner card.

You'll notice it states **Preliminary** so again I am not sure when the support for dvb type cards started but they're obviously not as supported as the ivtv driver based cards.

> **Patrick Dixon said:**
>  Thanks, I appreciate the help, but there's no point in just telling me it 'can work' when it doesn't for me.  If anybody can point me to some specific reason why it shouldn't work on the hardware I have, I'll give up now!  Even better point me in the direction of a fix. 

I have tried helping you, and apparently all you want to do is bash the application as well as linux so there is really no more point in attempting to gogle stuff for you and point out different things when you have already made up your mind.


> **Patrick Dixon said:**
> I have one last thing to try, which is to leave the /var/lib director on the same partition as / - which is the way I originally had it, but not what superm1 says to do.  Clean install number 6 coming up .. . 
hopefully this will work for you. again, good luck.

---

### Post by dannyboy79 on 2007-02-12
here is a link that was within the links I gave you. these are specific hardware listed and there rating of how good mythtv was with them. 

[http://pvrhw.goldfish.org/tiki-pvrhwdb.php](http://pvrhw.goldfish.org/tiki-pvrhwdb.php)

---

### Post by Patrick Dixon on 2007-02-12
> **dannyboy79 said:**
> I have to disagree with you, you stating there is a lack of answers. answers are everywhere, you have to LOOK for them. Yes there may be issues with sound but I don't agree that there are issues with video with particular hardware due to manufacturers support. The sound issues are only because the manufacturer of the hardware doesn't provide linux the correct information and or windows drivers so that linux developers can reverse engineer drivers for linux. You have to remember, everything related to linux is FREE. you don't have to pay for anything, so if you have a hicup here and hicup there, DEAL WITH IT. you want to pay for software and not deal with issues, than like you said, go to windows if you want to line the pockets of gates.
Look, free's great, free and don't work isn't!


> **dannyboy79 said:**
> The hardware that it works on is documented, in every successful review of mythtv. hence why I posted all those links of reviews of mythtv. heck, there supported hardware is even listed on the main mythtv website. what the website doesn't list is the actually COMBINATIONS of hardware. there are so many different combinations of hardware that they can't actually test each and every one. You keep mentioning that the DVB type cards are so compatible. Well, in one of the links I posted this comment stood out at me and this review was dated November of 2006.

-Compresses video in software using rtjpeg (from Nuppelvideo) or mpeg4 (from libavcodec). Full support for Hardware MPEG-2 encoder cards (Hauppauge PVR-250 / PVR-350). Preliminary support for DVB cards and the new pcHDTV tuner card.

You'll notice it states **Preliminary** so again I am not sure when the support for dvb type cards started but they're obviously not as supported as the ivtv driver based cards.
I don't have an MPEG-2 encoder card, I have a DVB-T card, and as I said earlier support for the card is documented as being in kernels subsequent to 2.6.12.


> **dannyboy79 said:**
> I have tried helping you, and apparently all you want to do is bash the application as well as linux so there is really no more point in attempting to gogle stuff for you and point out different things when you have already made up your mind.



hopefully this will work for you. again, good luck.Look, I appreciate you trying to help, but just telling me to buy new hardware isn't doing for me I'm afraid.

---

### Post by dannyboy79 on 2007-02-12
are you using this card Hauppauge/TT Nova-T budget
(L64781/Grundig 29504-401(tsa5060)) 


or this card Hauppauge/TT Nova-T budget
(tda10045/Philips tdm1316l(tda6651tt) + TDA9889) ?

these are the only ones listed on the official supported hardware that are similar to the 1 you listed on page 2 or 3 of this thread. you will notice that they both use a different driver. 1 is budget and 1 is budget-ci. 

here is a link talking about how hard it is getting your onboard video card to work with mythtv because your video card has problems with initializing XvMC just as the error had told you. [http://forums.viaarena.com/messageview.aspx?catid=28&threadid=71150&enterthread=y](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=71150&enterthread=y)

according to the link above, you need to install the latest unichrome driver which I don't think is in ubuntu by default. [http://www.openchrome.org/](http://www.openchrome.org/)

---

### Post by Unisted on 2007-02-12
Well as Dannyboy79 says it appears to be the combination that is causing you problems.

But, to find the problem you clearly have to resolve the following:

> 2007-02-12 14:04:09.035 DPMS Deactivated
2007-02-12 14:04:09.757 NVP: Disabling Audio, params(-1,2,44100)
2007-02-12 14:04:09.902 VideoOutputXv: XvMCTex: Init failed
2007-02-12 14:04:09.977 VideoOutputXv: XVideo Adaptor Name: 'XV_SWOV'

I spent 10 minutes searching on these terms and came up with a few suggestions, it appears you have a rare issue that perhaps has not been encountered on these forums before. 

You can either:

a) Persist with the search, the information will be out there somewhere and perhaps after a week or two you might find/ learn the 'answer' and then be able to assist other users having the same/ similar problems contributing to the ubuntu community.

b) give up and buy windows media centre or use [www.xlobby.com](www.xlobby.com)

I don't like to criticise but you've obviously heard about Mythtv and about Ubuntu/ Linux and know enough to install and set it up, most likely to a better level that I do but your posts are accusing Linux/ Ubuntu/ Mythtv of being wrong when we've not seen the review/ link to the 9/10 Mythtv compatibility tv card you are referring to and I'm still not really sure where the problem is yet... I assume when running Mythtv and accessing the TV function you are having problems watching tv?

You know the card works as you've done the test outside of Mythtv, you know Ubuntu works for this reason also (sound/ video). However, have you tried recording tv outside of Mythtv? Does this generate choppy playback? Have you tried scheduling a recording whilst not watching the recording to see if that creates issues.

Of course this all depends on which lane you pick...

---

### Post by dannyboy79 on 2007-02-12
i found this within the main mythtv website, have you read thru this entire thing??  [http://www.ethics-gradient.net/myth/mythdvb.html](http://www.ethics-gradient.net/myth/mythdvb.html)

as far as you buying a DVB card because you read that it's rating was a 8 out of 10 or whatever you stated, well you probably should have noticed that support for dvb type cards didn't enter mythtv until verison 16!! We are at 20, so it's not like you chose a card that has been tested with this software extensively! be that as it may, you chose a dvb card. have you thought about not using mythtv and just recording the live stream using dvbstream and mplayer?

---

### Post by Patrick Dixon on 2007-02-12
> **dannyboy79 said:**
> are you using this card Hauppauge/TT Nova-T budget
(L64781/Grundig 29504-401(tsa5060)) 


or this card Hauppauge/TT Nova-T budget
(tda10045/Philips tdm1316l(tda6651tt) + TDA9889) ?

these are the only ones listed on the official supported hardware that are similar to the 1 you listed on page 2 or 3 of this thread. you will notice that they both use a different driver. 1 is budget and 1 is budget-ci. 

Look guys can we put this one to bed?  As I said about 4 pages ago, the card is this one:- 

[http://www.linuxtv.org/wiki/index.php/WinTV-NOVA-T_PCI](http://www.linuxtv.org/wiki/index.php/WinTV-NOVA-T_PCI)
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_PCI)

and some (linux) user reviews:
[http://www.dabs.com/ProductView.aspx?Quicklinx=Z9G&fb=215&InMerch=1&v=3](http://www.dabs.com/ProductView.aspx?Quicklinx=Z9G&fb=215&InMerch=1&v=3)

There's no question it's supported in the edgy kernels
> **dannyboy79 said:**
> 
here is a link talking about how hard it is getting your onboard video card to work with mythtv because your video card has problems with initializing XvMC just as the error had told you. [http://forums.viaarena.com/messageview.aspx?catid=28&threadid=71150&enterthread=y](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=71150&enterthread=y)

according to the link above, you need to install the latest unichrome driver which I don't think is in ubuntu by default. [http://www.openchrome.org/](http://www.openchrome.org/)That link is about 12 months old and refers to a different chipset/motherboard.  Support for the A8V-MX motherboard and chipset is in the edgy kernel.  It's not in the dapper kernel, which is why I'm not using that.  12 months ago, there was virtually no linux support for the mother board, but these thing progress.

I've looked at the unichrome/openchrome stuff (and compiled & installed the openchrome driver - no difference).  From what I can gather unichrome with XvMC support is supposed to be in the latest distros, but the bleeding edgy stuff is in openchrome.  There are now 3 diverging *chrome trunks, so goodness only-knows what works with what.

---

### Post by Patrick Dixon on 2007-02-12
> **Unisted said:**
> Well as Dannyboy79 says it appears to be the combination that is causing you problems.

But, to find the problem you clearly have to resolve the following:

2007-02-12 14:04:09.035 DPMS Deactivated
2007-02-12 14:04:09.757 NVP: Disabling Audio, params(-1,2,44100)
2007-02-12 14:04:09.902 VideoOutputXv: XvMCTex: Init failed
2007-02-12 14:04:09.977 VideoOutputXv: XVideo Adaptor Name: 'XV_SWOV'

I spent 10 minutes searching on these terms and came up with a few suggestions, it appears you have a rare issue that perhaps has not been encountered on these forums before. 

OK, the first line is it disabling monitor power savings (ie normal), the second is because I had disabled audio to see if it made any difference (I didn't), the third I don't know and the fourth is 'information'.

> **Unisted said:**
> You can either:

a) Persist with the search, the information will be out there somewhere and perhaps after a week or two you might find/ learn the 'answer' and then be able to assist other users having the same/ similar problems contributing to the ubuntu community.

b) give up and buy windows media centre or use [www.xlobby.com](www.xlobby.com)

I don't like to criticise but you've obviously heard about Mythtv and about Ubuntu/ Linux and know enough to install and set it up, most likely to a better level that I do but your posts are accusing Linux/ Ubuntu/ Mythtv of being wrong when we've not seen the review/ link to the 9/10 Mythtv compatibility tv card you are referring to and I'm still not really sure where the problem is yet... I assume when running Mythtv and accessing the TV function you are having problems watching tv?

You know the card works as you've done the test outside of Mythtv, you know Ubuntu works for this reason also (sound/ video). However, have you tried recording tv outside of Mythtv? Does this generate choppy playback? Have you tried scheduling a recording whilst not watching the recording to see if that creates issues.

Of course this all depends on which lane you pick...
The video is choppy and the sound breaks up:

- watching live TV
- watching recorded TV (after it's finished recording and which was recorded when live TV was not being watched)

but it's fine when watching live tv with mplayer

However, I don't suppose my wife will be that impressed with running mplayer to watch tv and changing the channel in a terminal session - so that's not really a solution.

---

### Post by Patrick Dixon on 2007-02-12
This is the video driver that's loaded:

root@mediaserver:/home/dixon# modinfo via
filename:       /lib/modules/2.6.17-10-generic/kernel/drivers/char/drm/via.ko
author:         Various
description:    VIA Unichrome / Pro
license:        GPL and additional rights
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        drm
srcversion:     127CB9085BACC9494D6D2F6

---

### Post by dannyboy79 on 2007-02-12
> **Patrick Dixon said:**
> Look guys can we put this one to bed?  As I said about 4 pages ago, the card is this one:- 

[http://www.linuxtv.org/wiki/index.php/WinTV-NOVA-T_PCI](http://www.linuxtv.org/wiki/index.php/WinTV-NOVA-T_PCI)
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_PCI)

and some (linux) user reviews:
[http://www.dabs.com/ProductView.aspx?Quicklinx=Z9G&fb=215&InMerch=1&v=3](http://www.dabs.com/ProductView.aspx?Quicklinx=Z9G&fb=215&InMerch=1&v=3)

There's no question it's supported in the edgy kernels
That link is about 12 months old and refers to a different chipset/motherboard.  Support for the A8V-MX motherboard and chipset is in the edgy kernel.  It's not in the dapper kernel, which is why I'm not using that.  12 months ago, there was virtually no linux support for the mother board, but these thing progress.

I've looked at the unichrome/openchrome stuff (and compiled & installed the openchrome driver - no difference).  From what I can gather unichrome with XvMC support is supposed to be in the latest distros, but the bleeding edgy stuff is in openchrome.  There are now 3 diverging *chrome trunks, so goodness only-knows what works with what.

well this is right there in the link you provided:
**Issues and Problems **
The passthrough adds significant interference to the signal when the computer is operating, enough to impair analogue picture quality severely, and cause the occasional stream glitch in some other DVB-T units. 


and you say that you have issues with sound and video, no? why don't you post the output of lspci -v so we can see what hardware you're using. obviously if you're having problems and yet you keep posting how much this hardware is supported than you may not be providing us with the whole story.

---

### Post by Patrick Dixon on 2007-02-12
> **dannyboy79 said:**
> well this is right there in the link you provided:
**Issues and Problems **
The passthrough adds significant interference to the signal when the computer is operating, enough to impair analogue picture quality severely, and cause the occasional stream glitch in some other DVB-T units. 
I have no idea what that means.  AFAIK there is no passthough on this card (it's a DVB tuner only), and I don't have any other DVB-T units installed either.

> **dannyboy79 said:**
> and you say that you have issues with sound and video, no? why don't you post the output of lspci -v so we can see what hardware you're using. obviously if you're having problems and yet you keep posting how much this hardware is supported than you may not be providing us with the whole story.
dixon@mediaserver:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
        Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
        Flags: bus master, medium devsel, latency 64
        Memory at dc000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [80] AGP version 3.0
        Capabilities: [50] Power Management version 2
        Capabilities: [60] HyperTransport: Slave or Primary Interface
        Capabilities: [58] #00 [0000]

00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
        Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
        Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
        Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
        Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 Sout
h] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: f6a00000-f8afffff
        Prefetchable memory behind bridge: cff00000-d7efffff
        Capabilities: [80] Power Management version 2

00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
 (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
        Flags: bus master, medium devsel, latency 64, IRQ 193
        I/O ports at ec00 [size=8]
        I/O ports at e880 [size=4]
        I/O ports at e800 [size=8]
        I/O ports at e480 [size=4]
        I/O ports at e400 [size=16]
        Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [c0] Power Management version 2
        Capabilities: [e0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable
-

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/
C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
        Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8
235 PIPC Bus Master IDE
        Flags: bus master, medium devsel, latency 32
        I/O ports at fc00 [size=16]
        Capabilities: [c0] Power Management version 2

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
 (rev 90) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 201
        I/O ports at e080 [size=32]
        Capabilities: [80] Power Management version 2

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
 (rev 90) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 209
        I/O ports at e000 [size=32]
        Capabilities: [80] Power Management version 2

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
 (rev 90) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 193
        I/O ports at dc00 [size=32]
        Capabilities: [80] Power Management version 2

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
 (rev 90) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 217
        I/O ports at d880 [size=32]
        Capabilities: [80] Power Management version 2

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90) (prog-if 20 [EHC
I])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 64, IRQ 209
        Memory at febff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
        Capabilities: [88] Debug port

00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
        Subsystem: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
        Flags: medium devsel
        Capabilities: [c0] Power Management version 2

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 A
C97 Audio Controller (rev 70)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b9
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at d400 [size=256]
        Capabilities: [c0] Power Management version 2

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
        Subsystem: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
        Flags: bus master, medium devsel, latency 128
        Capabilities: [58] HyperTransport: Interrupt Discovery and Configuration

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80ed
        Flags: bus master, medium devsel, latency 64, IRQ 217
        I/O ports at d000 [size=256]
        Memory at febff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Power Management version 2

00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCIE Bridge (prog-if 00
 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0

00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge (prog-if 00
[Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: f8b00000-feafffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra
nsport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address
Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con
troller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella
neous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA A
dapter (rev 01) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8129
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 233
        Memory at d0000000 (32-bit, prefetchable) [size=64M]
        Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at f8af0000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 2
        Capabilities: [70] AGP version 3.0

02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port (prog-if 00 [No
rmal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
        Capabilities: [40] Express Root Port (Slot-) IRQ 0
        Capabilities: [68] Power Management version 2
        Capabilities: [70] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable
+

02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port (prog-if 00 [No
rmal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=02, secondary=04, subordinate=04, sec-latency=0
        Capabilities: [40] Express Root Port (Slot-) IRQ 0
        Capabilities: [68] Power Management version 2
        Capabilities: [70] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable
+

05:0c.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio
Decoder (rev 05)
        Subsystem: Hauppauge computer works Inc. Unknown device 9002
        Flags: bus master, medium devsel, latency 64, IRQ 225
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

05:0c.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decode
r [MPEG Port] (rev 05)
        Subsystem: Hauppauge computer works Inc. Nova-T DVB-T Model 909
        Flags: bus master, medium devsel, latency 64, IRQ 225
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2

05:0c.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decode
r [IR Port] (rev 05)
        Subsystem: Hauppauge computer works Inc. Nova-T DVB-T Model 909
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2

---

### Post by dannyboy79 on 2007-02-12
i guess I didn't notice that it stated that the newer cards don't have that passthrough any longer, at least we can rule that out as a reason why it's not working. would you wife or girlfriend be able to use the mouse to control tv using xine? this is from the link:

If you're using Xine, copy the channels.conf to ~/.xine (the xine config directory). Then start xine, bring up the control pannel, and click the DVB tab and Voila. You can use your mouse wheel to browse the channels list. After a while xine will extract the program guide from the DVB signal and augment the channel list with info about what's currently on. Cool uh!

i wish I could help you more but from the error message you provided you have an issue with your x-server. besides suggesting you get a cheap XFX GeForce 6200 Turbocache, I can't help you anymore. it's 29.99 after rebates, 39.99 before. here ya go: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2844188&Sku=P450-7894](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2844188&Sku=P450-7894)

---

### Post by fenian on 2007-02-12
In the Mytvtv Utilities/Setup section under Tv Settings>Playback did you select VIA XvMC as the preferred MPEG2 decoder?If you haven't alresdy done so you may want to install the OpenChrome drivers...

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by Patrick Dixon on 2007-02-13
> **dannyboy79 said:**
> 
If you're using Xine, copy the channels.conf to ~/.xine (the xine config directory). Then start xine, bring up the control pannel, and click the DVB tab and Voila. You can use your mouse wheel to browse the channels list. After a while xine will extract the program guide from the DVB signal and augment the channel list with info about what's currently on. Cool uh!
Well it might be if it worked ... but it doesn't.  Plus I don't get any sound with gxine (it's fine with mplayer), and life is just far too short.

OK, clean install number 5, followed by compilation of openchrome and much googling/fiddling just gives me the same (poor) results. I'm not ready to try another linux, buy some more hardware or compile the latest bleeding edge version of Mythtv, so I'm going to knock this on the head and put it down to (a bad) experience.

What frustrates the hell out of me, was that this did work first time round, but now, no matter what I do, I end up with this problem. AFAICS, the only thing that (may) have changed, is what apt-get is pulling down from the ubuntu depositories - but goodness only knows.

Thanks for all your help and suggestions.

---

### Post by dannyboy79 on 2007-02-13
well I use dapper and I found out that .20 wasn't in the repos so I downloaded mythtv from superm1's repos. is this maybe the issue? as I stated once before, since the desktop isn't important to you, have you tried knoppmyth or other distro's that have myth built right in?

---

### Post by Titus A Duxass on 2007-02-13
Patrick,
> have you tried knoppmyth or other distro's that have myth built right in? - This is a really good idea. If you still have the desire try running MythDora, it's all on one DVD including DVB-T card drivers.

Sorry to hear that you have given up, though I am not surprised.

I would go out and get an old nvidia 440 graphics card and give that a whirl.

---

### Post by Titus A Duxass on 2007-02-13
Patrick,
Does this apply to you > [http://www.ubuntuforums.org/showthread.php?t=360532](http://www.ubuntuforums.org/showthread.php?t=360532)?

What kernel are you running and what kernel were you running when you did your first install?

---

### Post by Patrick Dixon on 2007-02-13
> **Titus A Duxass said:**
> Patrick,
Does this apply to you ?

What kernel are you running and what kernel were you running when you did your first install?

I've tried both 2.6.17-10-generic and the latest one which is 2.6.17-11.  I've also reinstalled without doing an apt-get upgrade, so the only things pulled down are MySQL and MythTv and their dependencies.  Still no joy though.

Load averages seem to run at between 2 and 3 when watching LiveTV, so I guess something in the sound & video MPEG2 decoding and VGA writing is just taking too many resources.

---

### Post by dannyboy79 on 2007-02-13
patrick, you didn't answer my post about you retrieving the packages from superm1's repo. have you considered this? or are you on edgy?

---

### Post by Patrick Dixon on 2007-02-13
> **dannyboy79 said:**
> patrick, you didn't answer my post about you retrieving the packages from superm1's repo. have you considered this? or are you on edgy?

I'm on edgy and can't run dapper because the kernel doesn't support the motherboard (ethernet/sata/dma etc are broken).

---

### Post by dannyboy79 on 2007-02-13
well you could use dapper and compile you're own kernel couldn't you? have you thought of buying that 29.99 pci-e vid card I linked you to from tigerdirect.com? what about this, say you don't really want to have to invest in a card. well what if you buy it and it works, you would see how awesome myth is. if it doesn't work, you can always return it for something else if they won't give you a refund. tigerdirect.com has tons of stuff. in fact they have a wd 500gb 16mb cache hard drive for $149.99 if the vid card doesn't end up working. and we all know that we can always use more hard drive space.

---

### Post by Patrick Dixon on 2007-02-13
> **dannyboy79 said:**
> well you could use dapper and compile you're own kernel couldn't you? have you thought of buying that 29.99 pci-e vid card I linked you to from tigerdirect.com? what about this, say you don't really want to have to invest in a card. well what if you buy it and it works, you would see how awesome myth is. if it doesn't work, you can always return it for something else if they won't give you a refund. tigerdirect.com has tons of stuff. in fact they have a wd 500gb 16mb cache hard drive for $149.99 if the vid card doesn't end up working. and we all know that we can always use more hard drive space.

Well, I might have considered that if the Ethernet had worked, but without a network connection it's just a bit too tedious to contemplate (and I've lent my PCI ethernet card to someone else)!

My plan for Mythtv, was eventually to use this machine as a backend server, and use a mini-itx or something like the MSI Axis 700 as a frontend - hence my reluctance to start buying video cards for it.  The Axis 700 and EPIA mini-itxs have a fairly similar chipsets to my current motherboard (although less cpu power), so I'd probably just end up with the same problem.

I'm also in the UK!

---

### Post by chapmani on 2007-02-16
> My plan for Mythtv, was eventually to use this machine as a backend server, and use a mini-itx or something like the MSI Axis 700 as a frontend - hence my reluctance to start buying video cards for it. The Axis 700 and EPIA mini-itxs have a fairly similar chipsets to my current motherboard (although less cpu power), so I'd probably just end up with the same problem.

I'm also in the UK!
Patrick:

Now that I'm more clear on your intentions, I think I can comment.  I wasn't sure if you wanted to use your Ubuntu machine as a general purpose computer, as well as run Myth, or just as a Myth box.  You've spent a LOT of mostly waisted time trying to get Myth to work inside Ubuntu.

May I suggest Knoppmyth [http://mysettopbox.tv/]("http://mysettopbox.tv/").  The name is somewhat misleading now as it lost it's Knoppix link a few versions ago.  Current versions are built from custom compiled raw Debian.  The CD installs Linux and Myth in one shot.  It knows about most hardware including DVB-T cards.  The forums at mysettopbox.tv are full of Europeans with that same capture card and will be helpful with any problems you encounter.

I know people have experienced problems with older Via chipsets, but I think more modern ones like yours are OK.

If nothing else, it is worth a shot.  Since you're wanting a dedicated Myth box I think that KnoppMyth is the best solution

---

### Post by dannyboy79 on 2007-02-16
great suggestion. I tried suggesting that plenty ofg threads ago. maybe this time he'll try it.

---

### Post by Patrick Dixon on 2007-02-17
Yes, I had a look at Knopmyth and downloaded the installation iso.

However, this isn't quite a dedicated mythtv box, it also will have to run Slimserver and serve music (which is what it has been doing for the past year).  As a result, the HD that I am installing the OS on, has a large partition of music data that I don't want to loose.  The Knopmyth installation was extremely unclear on what it was going to do with existing partitions, so I aborted the install.

On further investigation, it seems that the ubuntu/myth problem might be something to do with pci interrrupts.   Making recordings with no frontend running, and reviewing them on a windows box, shows that the recordings are corrupted.  However the card is fine in a windows box, and playing to the screen using dvbstream/mplayer works OK (although not if I also run something with a lot of disk access at the same time - eg hdparm -tT /dev/hda).

Since the Nova-T PCI card didn't work in one of the two PCI slots (it found signal but never locked on to a channel), I'm wondering if the driver has a problem supporting shared PCI interrupts, or if there is a problem with the motherboard, or motherboard/linux combination.

Unfortunately, I don't know how to diagnose either.

---

### Post by Patrick Dixon on 2007-02-17
Here's a snip of the error messages I'm seeing in dmesg / mythbackend.log


[17181962.576000] cx88[0]/2: general errors: 0x00000100
[17181962.576000] cx88[0]/2: cx8802_stop_dma
[17181962.576000] cx88[0]/2: cx8802_restart_queue
[17181962.576000] cx88[0]/2: cx8802_start_dma w: 0, h: 0, f: 2
[17181962.576000] cx88[0]/2: setting the interrupt mask
[17181962.580000] cx88_wakeup: 3 buffers handled (should be 1)
[17181962.580000] cx88_wakeup: 3 buffers handled (should be 1)
[17181962.584000] cx88_wakeup: 6 buffers handled (should be 1)
[17181962.584000] cx88[0]/2: general errors: 0x00000100
[17181962.584000] cx88[0]/2: cx8802_stop_dma
[17181962.584000] cx88[0]/2: cx8802_restart_queue
[17181962.584000] cx88[0]/2: cx8802_start_dma w: 0, h: 0, f: 2
[17181962.584000] cx88[0]/2: setting the interrupt mask
[17181962.592000] cx88[0]/2: general errors: 0x00000100
[17181962.592000] cx88[0]/2: cx8802_stop_dma
[17181962.592000] cx88[0]/2: cx8802_restart_queue
[17181962.592000] cx88[0]/2: cx8802_start_dma w: 0, h: 0, f: 2
[17181962.592000] cx88[0]/2: setting the interrupt mask
[17181962.592000] cx88_wakeup: 4 buffers handled (should be 1)
[17181962.592000] cx88[0]/2: general errors: 0x00000100
[17181962.592000] cx88[0]/2: cx8802_stop_dma
[17181962.592000] cx88[0]/2: cx8802_restart_queue
[17181962.592000] cx88[0]/2: cx8802_start_dma w: 0, h: 0, f: 2
[17181962.592000] cx88[0]/2: setting the interrupt mask
[17181963.528000] cx88[0]/2: general errors: 0x00000100
[17181963.528000] cx88[0]/2: cx8802_stop_dma
[17181963.528000] cx88[0]/2: cx8802_restart_queue
[17181963.528000] cx88[0]/2: cx8802_start_dma w: 0, h: 0, f: 2
[17181963.528000] cx88[0]/2: setting the interrupt mask
[17181963.640000] cx88[0]/2: general errors: 0x00000100
[17181963.640000] cx88[0]/2: cx8802_stop_dma
[17181963.640000] cx88[0]/2: cx8802_restart_queue
[17181963.640000] cx88[0]/2: cx8802_start_dma w: 0, h: 0, f: 2
[17181963.640000] cx88[0]/2: setting the interrupt mask
[17181964.588000] cx88[0]/2: general errors: 0x00000100
[17181964.588000] cx88[0]/2: cx8802_stop_dma
[17181964.588000] cx88[0]/2: cx8802_restart_queue
[17181964.588000] cx88[0]/2: cx8802_start_dma w: 0, h: 0, f: 2
[17181964.588000] cx88[0]/2: setting the interrupt mask
[17181964.604000] cx88[0]/2: general errors: 0x00000100
[17181964.604000] cx88[0]/2: cx8802_stop_dma
[17181964.604000] cx88[0]/2: cx8802_restart_queue
[17181964.604000] cx88[0]/2: cx8802_start_dma w: 0, h: 0, f: 2
[17181964.604000] cx88[0]/2: setting the interrupt mask
[17181964.668000] cx88[0]/2: general errors: 0x00000100
[17181964.668000] cx88[0]/2: cx8802_stop_dma
[17181964.668000] cx88[0]/2: cx8802_restart_queue
[17181964.668000] cx88[0]/2: cx8802_start_dma w: 0, h: 0, f: 2
[17181964.668000] cx88[0]/2: setting the interrupt mask
[17181965.532000] cx88[0]/2: general errors: 0x00000100
[17181965.532000] cx88[0]/2: cx8802_stop_dma
[17181965.532000] cx88[0]/2: cx8802_restart_queue
[17181965.532000] cx88[0]/2: cx8802_start_dma w: 0, h: 0, f: 2
[17181965.532000] cx88[0]/2: setting the interrupt mask
[17181965.552000] cx88[0]/2: general errors: 0x00000100
[17181965.552000] cx88[0]/2: cx8802_stop_dma
[17181965.552000] cx88[0]/2: cx8802_restart_queue
[17181965.552000] cx88[0]/2: cx8802_start_dma w: 0, h: 0, f: 2
[17181965.552000] cx88[0]/2: setting the interrupt mask


There are only 2 PCI slots on this mb, and only the Nova-T card is fitted.  There's also on-board Video, Sound and LAN, all of which I'm using.  I've tried disabling all the serial, parallel and usb ports, but without improvement.

If this hadn't worked once, I'd think it was just an incompatible mb.  The only other thing I can think of, is that pre-installing mythtv, I though I would need the V4L drivers and so I downloaded source and compiled them.  I'm not even sure the modules installed correctly, and I didn't think I was using them, but maybe an updated driver was installed or something?  I don't know how you track driver versions and changes for DVB cards ...

---

### Post by Patrick Dixon on 2007-02-17
Some progress I think ... although I'm not quite sure why!

I downloaded the tar of the latest v4l-dvb drivers and did make and then make install.

On rebooting, my card was recognised and various drivers loaded but not the cx88_dvb one.  Consequently myth couldn't find a card.

So, adding the cx88_dvb module by modpobe cx88_dvd, put me back where I was before - picture breakup and error messages.

So I then did a apt-get install --reinstall linux-image-$(uname -r) to restore the original modules ... and rebooted.

However, now (after modprobe cx88_dvb again, as it still doesn't seem to want load the module on boot now), I have no error messages and no picture breakup!  I do however have some picture freezing/stuttering, but I suspect this is a different problem and may be related to the sound card and/or Xorg settings.

Any idea what's going on here?

dixon@mediaserver:~$ lsmod |grep cx88
cx88_dvb               16644  20
cx88_vp3054_i2c         5248  1 cx88_dvb
dvb_pll                15364  2 cx88_dvb
video_buf_dvb           7684  1 cx88_dvb
cx8800                 35212  0
compat_ioctl32          2304  1 cx8800
cx8802                 19332  1 cx88_dvb
cx88xx                 67364  3 cx88_dvb,cx8800,cx8802
ir_common              31236  1 cx88xx
i2c_algo_bit            8712  2 cx88_vp3054_i2c,cx88xx
tveeprom               15888  1 cx88xx
videodev               28160  2 cx8800,cx88xx
v4l2_common            25216  2 cx8800,videodev
v4l1_compat            15236  2 cx8800,videodev
btcx_risc               5896  3 cx8800,cx8802,cx88xx
video_buf              26116  5 cx88_dvb,video_buf_dvb,cx8800,cx8802,cx88xx
i2c_core               22528  9 cx22702,cx88_dvb,cx88_vp3054_i2c,dvb_pll,i2c_ec,cx88xx,i2c_algo_bit,tveeprom,i2c_viapro

---

### Post by superm1 on 2007-02-17
I've been chatting with Patrick through PMs the last week or two about this when I've had some free time (I haven't been able to be too active lately due to school).

I'm leaning towards something in this system being flaky.  It almost seems like a fluke that it worked the first time around.  

These clips that you have now that are stable recording, do they play fine on other machines/playback software?

---

### Post by Patrick Dixon on 2007-02-17
> **superm1 said:**
> 

These clips that you have now that are stable recording, do they play fine on other machines/playback software?Just been trying that, and yes they look good.  I never get any sound at all playing the mythtv mpg files back on windows media player, but I assume that's something WMP related.

I suspect this isn't the most linux-friendly motherboard, but I'm guessing that something in the V4L driver install remains even after the 'standard' modules are reinstalled.  I think it's a fluke that it ever worked at all, as nobody would have deliberately gone through the sequence I've gone through - twice ;-)

Incidentally the 'top' profile when playing live tv is now very different from before.  The  card driver is up to about 10%, frontend is now at about 30% and Xorg is not very much at all.

---

### Post by Patrick Dixon on 2007-02-18
Another update -

I've realised what re-installing the modules does.  It re-writes /boot/grub/menu.lst putting the most recent kernel at the top of the list.  Thus I am actually booting 2.6.20-something which I installed as one of the many things I tried when attempting to solve the original problem.

So, the 2.6.20 kernel actually works, except that it doesn't install the cx88-dvb module at boot.  When I first tried it, I didn't figure that out, and so thought it was just another dead-end.

The 2.6.16 and 2.6.17 kernels don't seem to work with my hardware combination, even after building the latest v4l-dvb modules.

I still have a slight 'smoothness' issue with replay (the recorded pictures are fine on a windows machine, and I even get sound now I have set the alsa drivers in mythtv?).  I'm now using bob de-interlace and XvMc with the via on-board VGA and a crappy CRT monitor.

So, should I just go the whole hog and install fiesty and Mythtv from the fiesty sources?

---

### Post by dannyboy79 on 2007-02-18
well why not??? you've tried everything else in the world. i know it's been a long UNfun road but your will save soooooo many others from dispare. I as well as others thank you for being a tester and a person who has truely stuck in there no matter what. I do hope you get it resolved. good luck

---

### Post by superm1 on 2007-02-18
> **Patrick Dixon said:**
> Another update -

I've realised what re-installing the modules does.  It re-writes /boot/grub/menu.lst putting the most recent kernel at the top of the list.  Thus I am actually booting 2.6.20-something which I installed as one of the many things I tried when attempting to solve the original problem.

So, the 2.6.20 kernel actually works, except that it doesn't install the cx88-dvb module at boot.  When I first tried it, I didn't figure that out, and so thought it was just another dead-end.

The 2.6.16 and 2.6.17 kernels don't seem to work with my hardware combination, even after building the latest v4l-dvb modules.

I still have a slight 'smoothness' issue with replay (the recorded pictures are fine on a windows machine, and I even get sound now I have set the alsa drivers in mythtv?).  I'm now using bob de-interlace and XvMc with the via on-board VGA and a crappy CRT monitor.

So, should I just go the whole hog and install fiesty and Mythtv from the fiesty sources?
Well with regard to feisty - a new mythtv build just got uploaded today.  It should show up in feisty mirrors really soon (next few days).  So you really will be a very valuable asset to me and other maintainers by being able to test feisty mythtv and such.  


It sounds like you are inconceivably close in getting this going now, I'm very glad you've toughed it through all the crap with this.

---

### Post by Patrick Dixon on 2007-02-21
Update.

I was unable to get mythtv frontend to playback smoothly, and on further investigation, it seems that ide disk accesses were very slow (~ 2MB/s for buffered disk reads) and the sata dives were never recognised at all.

However, the good news was that the DVB-T card would work in PCI slot 1, with "noirqdebug" passed at boot.  This flag seemed to prevent the "nobody cared" messages, closely followed by disabling the common interrupt.

So I decided to do yet another clean install using the feisty amd64 alternative disk.

However, I am now back with the original problem.  The picture and sound are corrupted and the I have a log (dmesg) full of these:

[  311.284354] cx88[0]/2-mpeg: general errors: 0x00000100
[  311.285795] cx88_wakeup: 3 buffers handled (should be 1)
[  311.285799] cx88[0]/2-mpeg: general errors: 0x00000100
[  312.298223] cx88[0]/2-mpeg: general errors: 0x00000100
[  312.301226] cx88_wakeup: 3 buffers handled (should be 1)
[  312.303387] cx88_wakeup: 13 buffers handled (should be 1)
[  312.303391] cx88[0]/2-mpeg: general errors: 0x00000100
[  312.314405] cx88[0]/2-mpeg: general errors: 0x00000100
[  313.315734] cx88[0]/2-mpeg: general errors: 0x00000100
[  313.324325] cx88_wakeup: 3 buffers handled (should be 1)
[  313.325023] cx88_wakeup: 3 buffers handled (should be 1)
[  313.325026] cx88[0]/2-mpeg: general errors: 0x00000100
[  314.336682] cx88[0]/2-mpeg: general errors: 0x00000100
[  314.339628] cx88_wakeup: 16 buffers handled (should be 1)
[  314.339631] cx88[0]/2-mpeg: general errors: 0x00000100
[  314.339849] cx88_wakeup: 0 buffers handled (should be 1)
[  314.350593] cx88[0]/2-mpeg: general errors: 0x00000100
[  315.434143] cx88[0]/2-mpeg: general errors: 0x00000100
[  315.437011] cx88_wakeup: 17 buffers handled (should be 1)
[  315.437015] cx88[0]/2-mpeg: general errors: 0x00000100
[  315.448030] cx88[0]/2-mpeg: general errors: 0x00000100
[  316.452808] cx88[0]/2-mpeg: general errors: 0x00000100
[  316.462259] cx88[0]/2-mpeg: general errors: 0x00000100
[  317.334636] cx88[0]/2-mpeg: general errors: 0x00000100
[  317.486535] cx88_wakeup: 5 buffers handled (should be 1)
[  317.486951] cx88[0]/2-mpeg: general errors: 0x00000100

The good news is the the 2.6.20-6 kernel seems to have sorted out all of the interrupt error issues, and PCI slot 1 works without any "noirqdebug" flag.  Sata disks have returned and ide access speeds are back over 50MB/s.

But I've reluctantly concluded that MythTv will never work with this motherboard (Asus A8V-MX).  I am sure there is a bug somewhere in the interrupt or dma handling, but even if I could figure out the right place to post it, I very much doubt whether anyone would be interested enough to do anything about it.

In installing MythTv from feisty sources, following the backend/frontend instructions. I came across the following which I hope may help someone:

The MySQL myth database didn't seem to be created by the apt-get install, and I had to create it manually:

mysql -u root -p  < /usr/share/mythtv/sql/mc.sql

In mythtv-setup, when you 'Finish' in the 'Video Source' menu, the programme appears to hang.  You need to switch back to the command window (Ctl-Tab) to answer a load of interactive questions.  (This step would surely be better not done interactively?)


/etc/cron.daily/mythtv-backend doesn't seem to be installed.

---

### Post by Patrick Dixon on 2007-02-21
Oh, and I forgot to mention

cx88-dvb still doesn't get automatically installed (although the card is correctly recognised and several other related(?) modules do), so I had to add it manually to /etc/modules.

---

### Post by superm1 on 2007-02-21
> **Patrick Dixon said:**
> Update.

I was unable to get mythtv frontend to playback smoothly, and on further investigation, it seems that ide disk accesses were very slow (~ 2MB/s for buffered disk reads) and the sata dives were never recognised at all.

However, the good news was that the DVB-T card would work in PCI slot 1, with "noirqdebug" passed at boot.  This flag seemed to prevent the "nobody cared" messages, closely followed by disabling the common interrupt.

So I decided to do yet another clean install using the feisty amd64 alternative disk.

However, I am now back with the original problem.  The picture and sound are corrupted and the I have a log (dmesg) full of these:

[  311.284354] cx88[0]/2-mpeg: general errors: 0x00000100
[  311.285795] cx88_wakeup: 3 buffers handled (should be 1)
[  311.285799] cx88[0]/2-mpeg: general errors: 0x00000100
[  312.298223] cx88[0]/2-mpeg: general errors: 0x00000100
[  312.301226] cx88_wakeup: 3 buffers handled (should be 1)
[  312.303387] cx88_wakeup: 13 buffers handled (should be 1)
[  312.303391] cx88[0]/2-mpeg: general errors: 0x00000100
[  312.314405] cx88[0]/2-mpeg: general errors: 0x00000100
[  313.315734] cx88[0]/2-mpeg: general errors: 0x00000100
[  313.324325] cx88_wakeup: 3 buffers handled (should be 1)
[  313.325023] cx88_wakeup: 3 buffers handled (should be 1)
[  313.325026] cx88[0]/2-mpeg: general errors: 0x00000100
[  314.336682] cx88[0]/2-mpeg: general errors: 0x00000100
[  314.339628] cx88_wakeup: 16 buffers handled (should be 1)
[  314.339631] cx88[0]/2-mpeg: general errors: 0x00000100
[  314.339849] cx88_wakeup: 0 buffers handled (should be 1)
[  314.350593] cx88[0]/2-mpeg: general errors: 0x00000100
[  315.434143] cx88[0]/2-mpeg: general errors: 0x00000100
[  315.437011] cx88_wakeup: 17 buffers handled (should be 1)
[  315.437015] cx88[0]/2-mpeg: general errors: 0x00000100
[  315.448030] cx88[0]/2-mpeg: general errors: 0x00000100
[  316.452808] cx88[0]/2-mpeg: general errors: 0x00000100
[  316.462259] cx88[0]/2-mpeg: general errors: 0x00000100
[  317.334636] cx88[0]/2-mpeg: general errors: 0x00000100
[  317.486535] cx88_wakeup: 5 buffers handled (should be 1)
[  317.486951] cx88[0]/2-mpeg: general errors: 0x00000100

The good news is the the 2.6.20-6 kernel seems to have sorted out all of the interrupt error issues, and PCI slot 1 works without any "noirqdebug" flag.  Sata disks have returned and ide access speeds are back over 50MB/s.

But I've reluctantly concluded that MythTv will never work with this motherboard (Asus A8V-MX).  I am sure there is a bug somewhere in the interrupt or dma handling, but even if I could figure out the right place to post it, I very much doubt whether anyone would be interested enough to do anything about it.

In installing MythTv from feisty sources, following the backend/frontend instructions. I came across the following which I hope may help someone:

The MySQL myth database didn't seem to be created by the apt-get install, and I had to create it manually:

mysql -u root -p  < /usr/share/mythtv/sql/mc.sql

In mythtv-setup, when you 'Finish' in the 'Video Source' menu, the programme appears to hang.  You need to switch back to the command window (Ctl-Tab) to answer a load of interactive questions.  (This step would surely be better not done interactively?)


/etc/cron.daily/mythtv-backend doesn't seem to be installed.
A few comments about the feisty package briefly since I haven't written docs for it yet.  /etc/cron.daily/mythtv-backend is indeed disappearing.  This is because zap2it doesn't want users filling up at the same time of the night.  You can set up in the frontend menu to have the backend run mythtfilldatabase regularly.

If the database wasn't installed, you didn't install mythtv-database.  There are a few new oddities about the feisty package:
```
mythtv
```
This is a package that will install mysql-server, frontend, backend, mythtv-database
```
mythtv-frontend
```
Installs just a frontend
```
mythtv-backend
```
Installs just a backend.
```
master-mythtv-backend
```
Installs backend, mythtv-database, mysql-server
```
ubuntu-mythtv-frontend
```
Installs a standalone frontend with automatic login and such.

The big reasoning for these changes is to prepare for a live mythtv standalone install disk.

When you launched mythtv-setup, how did you do it?  It shouldn't have had any interactive debconf questions afaik.

Patrick, sorry about the troubles with this board - Now people will at least know to stay away from it.  I'll get it listed in the feisty troubleshooting section once I start the feisty docs.

---

### Post by Patrick Dixon on 2007-02-21
I did a:-

sudo apt-get install mythtv-frontend gdm ubuntu-artwork xterm openbox gnome-screensaver xserver-xorg gsfonts-x11 xfonts-100dpi xfonts-75dpi msttcorefonts xfonts-base mysql-server mythtv-backend mythtv-database usplash-theme-ubuntu

so that looks like it should have installed:-

mythtv-frontend
mysql-server
mythtv-backend
mythtv-database

> /etc/cron.daily/mythtv-backend is indeed disappearing. This is because zap2it doesn't want users filling up at the same time of the night.OK that makes sense.  It's useful to be able to set a manual update off when you set the thing up for the first time though ...

> When you launched mythtv-setup, how did you do it? It shouldn't have had any interactive debconf questions afaik.From an openbox terminal session, logged in as the regular user (ie not mythtv)

I set the grabber to be the UK Alternative and the Channel Frequency Table to default - it used to just give an error message and allow you out, but now it wants to ask you about various channels it's adding from the radiotimes site.

> Patrick, sorry about the troubles with this board - Now people will at least know to stay away from it. I'll get it listed in the feisty troubleshooting section once I start the feisty docs.I am starting to understand what the issue is a bit better now.  I've throttled the ide disk back to UDMA5 in the bios, and I get error-free pictures now.  Disk access is around 23MB/s (about half that with UDMA6).  I have a very 'frame-dropped' looking display, but I have yet to sort out the via unichrome drivers, so that may improve things.  Also for some strange reason the 'W' aspect ratio keyboard key doesn't seem to do much other than 'say' it's changing ratios.  Maybe that's the vesa driver too.

I now realise, that when I first installed mythtv and had it working, I was using an old ~5GB HD for /, with a larger /var/lib/ partition on the secondary channel of the same ide channel.  Therefore I strongly suspect that DMA/HD transfer rates would have been running at a much lower rate than UDMA6 on a modern 250GB HD, and that's probably why it worked.

So there may be a DMA bug with the cx88-dvb driver, or it may be a conflict between it and the mb.  It would be nice to report it to an interested party, but as I said before, I'm not sure who that would be!

---

### Post by Patrick Dixon on 2007-02-21
> **Patrick Dixon said:**
> Oh, and I forgot to mention

cx88-dvb still doesn't get automatically installed (although the card is correctly recognised and several other related(?) modules do), so I had to add it manually to /etc/modules.

Apparently this is known and will be fixed in the 2.6.21 kernel.

---

### Post by Patrick Dixon on 2007-02-21
I think I may have cracked it!

Installing the openchrome via drivers seems to have given me decent pictures.  I did have to re-instate the noirqdebug and pci=routeirq boot flags, as there seems to be 'an issue' with the common pci interrupt being disabled with the via openchrome driver.  I'm not 100% sure that pci=routeirq is required, but it doesn't seem to do any harm.

I've also changed to the ALSA:default and default mixer settings, and I had to change the Passthrough audio device to ALSA:iec953:(AES0 0x02) to get sound and picture to lipsync.

And even more good news is that mythweb installs straight from the apt-get install - no passwords or permissions needed changing.

---

### Post by superm1 on 2007-02-21
> **Patrick Dixon said:**
> I think I may have cracked it!

Installing the openchrome via drivers seems to have given me decent pictures.  I did have to re-instate the noirqdebug and pci=routeirq boot flags, as there seems to be 'an issue' with the common pci interrupt being disabled with the via openchrome driver.  I'm not 100% sure that pci=routeirq is required, but it doesn't seem to do any harm.

I've also changed to the ALSA:default and default mixer settings, and I had to change the Passthrough audio device to ALSA:iec953:(AES0 0x02) to get sound and picture to lipsync.

And even more good news is that mythweb installs straight from the apt-get install - no passwords or permissions needed changing.
Sounds like you are making great progress with all of this:)

About that mythweb fix, edgy release time was horrible, because I had that fixed the day edgy got released but it couldn't get into the repositories by the time the switch got flipped to "release edgy".

---

### Post by Patrick Dixon on 2007-02-22
A couple of questions on the fiesty mythtv package:-

1) I'm getting these plugin 2 errors from the frontend, any idea what they mean?

2007-02-22 11:36:07.545 Using runtime prefix = /usr
2007-02-22 11:36:07.552 Gnome-Screensaver support enabled
2007-02-22 11:36:07.552 DPMS is disabled.
2007-02-22 11:36:07.713 New DB connection, total: 1
2007-02-22 11:36:07.742 Connected to database 'mythconverg' at host: localhost
2007-02-22 11:36:07.743 Total desktop dim: 1024x768, with 1 screen[s].
2007-02-22 11:36:07.771 Using screen 0, 1024x768 at 0,0
2007-02-22 11:36:07.812 Current Schema Version: 1160
2007-02-22 11:36:07.813 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-02-22 11:36:07.813 Enabled verbose msgs:  important general
2007-02-22 11:36:08.307 Total desktop dim: 1024x768, with 1 screen[s].
2007-02-22 11:36:08.308 Using screen 0, 1024x768 at 0,0
2007-02-22 11:36:08.308 Switching to wide mode (MythCenter-wide)
2007-02-22 11:36:08.347 Using the Qt painter
2007-02-22 11:36:08.868 Joystick disabled.
2007-02-22 11:36:08.994 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-02-22 11:36:09.628 Registering Internal as a media playback plugin.
2007-02-22 11:36:11.082 MythPlugin::Init() dlerror:
2007-02-22 11:36:11.082 Unable to initialize plugin '2'.
2007-02-22 11:36:11.083 Unable to run plugin '2': not initialized
2007-02-22 11:36:11.083 MythPlugin::Init() dlerror:
2007-02-22 11:36:11.083 Unable to initialize plugin 'myth2'.
2007-02-22 11:36:11.083 Unable to run plugin 'myth2': not initialized

2) I can't seem to get mythtv to respond to the remote.  I did have this working before (using the edgy packages), so I wonder if lirc is enabled in the feisty mythtv packages?  I've tested lirc and the remote commands are recognised and passed, but only the 'diamond' and number keys are recognised, and not to the ~./mythtv/lircrc aliases I've set up!

---

### Post by Patrick Dixon on 2007-02-23
> **Patrick Dixon said:**
> 2) I can't seem to get mythtv to respond to the remote.All seems to work now - must have required a restart.

---

### Post by superm1 on 2007-02-23
> **Patrick Dixon said:**
> A couple of questions on the fiesty mythtv package:-

1) I'm getting these plugin 2 errors from the frontend, any idea what they mean?

2007-02-22 11:36:07.545 Using runtime prefix = /usr
2007-02-22 11:36:07.552 Gnome-Screensaver support enabled
2007-02-22 11:36:07.552 DPMS is disabled.
2007-02-22 11:36:07.713 New DB connection, total: 1
2007-02-22 11:36:07.742 Connected to database 'mythconverg' at host: localhost
2007-02-22 11:36:07.743 Total desktop dim: 1024x768, with 1 screen[s].
2007-02-22 11:36:07.771 Using screen 0, 1024x768 at 0,0
2007-02-22 11:36:07.812 Current Schema Version: 1160
2007-02-22 11:36:07.813 mythfrontend version: 0.20.20060828-3 [www.mythtv.org]("http://www.mythtv.org")
2007-02-22 11:36:07.813 Enabled verbose msgs:  important general
2007-02-22 11:36:08.307 Total desktop dim: 1024x768, with 1 screen[s].
2007-02-22 11:36:08.308 Using screen 0, 1024x768 at 0,0
2007-02-22 11:36:08.308 Switching to wide mode (MythCenter-wide)
2007-02-22 11:36:08.347 Using the Qt painter
2007-02-22 11:36:08.868 Joystick disabled.
2007-02-22 11:36:08.994 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-02-22 11:36:09.628 Registering Internal as a media playback plugin.
2007-02-22 11:36:11.082 MythPlugin::Init() dlerror:
2007-02-22 11:36:11.082 Unable to initialize plugin '2'.
2007-02-22 11:36:11.083 Unable to run plugin '2': not initialized
2007-02-22 11:36:11.083 MythPlugin::Init() dlerror:
2007-02-22 11:36:11.083 Unable to initialize plugin 'myth2'.
2007-02-22 11:36:11.083 Unable to run plugin 'myth2': not initialized

2) I can't seem to get mythtv to respond to the remote.  I did have this working before (using the edgy packages), so I wonder if lirc is enabled in the feisty mythtv packages?  I've tested lirc and the remote commands are recognised and passed, but only the 'diamond' and number keys are recognised, and not to the ~./mythtv/lircrc aliases I've set up!

Are you still getting these plugin errors?  I'll have to double check the build that feisty got from ubuntu build server.  I'm only running it on a VM with hand built packages.

---

### Post by Patrick Dixon on 2007-02-23
> **superm1 said:**
> Are you still getting these plugin errors?  I'll have to double check the build that feisty got from ubuntu build server.  I'm only running it on a VM with hand built packages.
Yes.

Also no sign of optimize_mythdb.pl anywhere?

Presumably, removing /etc/cron.daily/mythtv-backend & using the frontend to update the listings, means that frontend has to be running at the right time, or you don't get any listings update?  If so, it seems the wrong way to do it, as you really can only guarantee that the backend is running most of the time.

Also, does it mean, you have to have the uk_rt.xmltv in 'user' ~/.mythtv rather than 'mythtv' ~/.mythtv ?

---

### Post by carlb on 2007-02-28
I have recently gone through similar experiences with installing two systems.  One of things that helped me along was switching over to Automatix2 to install my Nvidia driver, codecs and other media software.   That resolved problems I had with the video and sound on the two separate systems.  I did this after a clean install of Ubuntu 6.10.  I added Mythtv after doing that and it  is working quite well.

I have not gotten Lirc to work for a remote I purchased and I suspect there are some underlying problems with Lirc.  I plan to switch to a wireless keyboard with mouse in lieu of a remote.

Also, once you get this stuff working don't let the updater update the OS, otherwise you could be back to square one.

---

