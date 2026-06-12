---
title: "Can't remove Flash 7 plugin"
date: 2009-02-05
forum: Multimedia Software
---

### Post by Stephen Shellard on 2009-02-05
**Post Script 8th February:**  [I]This thread has successfully provided me with solutions to a number of problems, _not just the removal of Flash 7.0._

Anyone experiencing problems around the installation of Flash 10, may benefit from following this thread.  Related issues include: no sound on u-tube videos,  freezing of BBC iPlayer on attempting to stream radio or "listen again", complete failure of BBC iPlayer to deliver on "listen again" television options.  At the conclusion to this the absence of Pulse Audio from my system proved to be a critical factor and one which I did not anticipate or have any prior knowledge. Much thanks to Red Road 55 and Gandaran. Read on...[/I]


I have read through many threads on the subject of problems with Flash player but none seem to touch on the particular difficulty I have encountered.  I am using Hardy 8.04  and following many problems with video and streaming BBC radio have now got things to work.  This has been achieved by removing Flash 10 and Flash non free (and indeed everything else flash related that I can see in the package manager - SWFDec  gnash etc)and relying on what would appear to be the default -  Flash 7.0 re 68 (visible as installed and active in Tools/Add ons/plugins)

I should however like to upgrade to Flash 10 and have attempted to do so with resulting reduced functionality.  

Looking at other threads it would appear that I should remove _all_ previous versions of flash.  My problem is, I do not know how to remove the Flash 7.0 re 68 plugin. (I can disable it by the way, but this would still appear to interfere with new versions if I install them.)  I have tried reinstalling Firefox but Flash 7 reappears like a bad penny.

Help greatly appreciated.

---

### Post by redroad55 on 2009-02-05
with this you can remove all others and then reinstall 10 all is included in this code except the flash 7 your talking about so include it after purge :
> sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree
Best to you

---

### Post by Stephen Shellard on 2009-02-06
OK - I've had a go at this, or to exact, a couple of gos:  here's the output:

[PHP]stephen@Zoostorm:~$ sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla libflashplayer.so
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
Package flashplugin-nonfree is not installed, so not removed
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
E: Couldn't find package nspluginwrapper
stephen@Zoostorm:~$ sudo apt-get purge x-shockwave-flash futuresplash
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package x-shockwave-flash
stephen@Zoostorm:~$ sudo apt-get purge libflashplayer.so
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libflashplayer.so
stephen@Zoostorm:~$[/PHP]


The information I've added to the code you provided came from the output for "about plugins" as entered in Firefox.  I've copied and pasted the relevant part:

> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

This does confirm that Flash 7.0 is present, but obviously I'm not extracting the correct information to remove it. Maybe you can put me right on this.

Many thanks for your attention.

---

### Post by redroad55 on 2009-02-06
Hi, Go to Applications > System > Admin. > Synaptic Pkg. manager ..

enter your password : in synaptic scroll down to the libflash entries that have green box..Click on box, in window select unmark and hit apply at top of page do this for every libflash entry... 

when you've completed this go to applications > add/remove .. at top middle of page in box next to "show:" make sure "third party is selected (there is a drop down there in order to select it if it is not)..now adobe flash 10 should be present at top of list .. click in box then hit apply .. That should do it ..Post back your results ..Best to you

---

### Post by Stephen Shellard on 2009-02-06
I have checked for libflash entries in synaptic. None are installed. (I looked first by scrolling down as suggested, then did a search on libflash, which did generate a list of five, none installed.)

---

### Post by gandaran on 2009-02-06
post the output of this command
**locate libflash**
this will tell you where the plugin is installed and possibly you can just delete the libflashplayer.so file.

---

### Post by Stephen Shellard on 2009-02-06
Here's the output:

[PHP]stephen@Zoostorm:~$ locate libflash
/home/stephen/.mozilla/plugins/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
/var/lib/dpkg/info/libflash-mozplugin.list
/var/lib/dpkg/info/libflash-mozplugin.postrm
stephen@Zoostorm:~$
stephen@Zoostorm:~$[/PHP]

I suppose I might usefully delete the files which are clearly related to flash plugins for firefox?  (i.e. not the open office plugin)  I shall try to restrain myself from doing so in the hope of confirmation that this would not be catastrophic. 

I have previously used > whereis to search for things so I am curious to know why it is ineffective in this case. (I did give it a try, and the output was unhelpful.)

Thanks.

---

### Post by gandaran on 2009-02-06
just delete this one (libflashplayer.so)
/home/stephen/.mozilla/plugins/libflashplayer.so
check in synaptic if this package **libflash-mozplugin** is installed, if it is remove it

---

### Post by Stephen Shellard on 2009-02-06
First the good news.  Flash 7 is gone. So thanks to Gandaran and Red Road 55. I think I've learnt something useful. 

Sadly there's still a lot to learn.  I have installed (using synaptic package manager)  flash plugin non free and Adobe Flash 10.  Result.  BBC Radio listen again service freezes. Utube gives me  pictures but no sound.  Ah well.  I still feel there's been progress.  Any thoughts on a simple resolution to make this a perfect thread?

Thanks again.

---

### Post by redroad55 on 2009-02-06
so currently in firefox browser what is there when you look in add ons..Post back

also just to make sure do you have the mdibuntu repositories present in your software sources?

---

### Post by Stephen Shellard on 2009-02-06
> Adobe Reader 9.0
Default Plugin
Demo Print Plugin for unix/linux
Div X Web Player
Helix DNA Plugin: RealPlayer G2 Plug-in Comfortable
Helix DNA Plugin:Real Player G2 Plug-in Compatible (compatible;Totem)
iTunes Application Detector
QuickTime Plugin 7.2.0
ShockWave Flash 10.0 r15
Totem Web Browser Plugin 2.22.1
VLC Multimedia Plugin (compatible Totem 2.22.1)
Window Media Player Plug-in (compatible; Totem)


Currently all enabled.

---

### Post by redroad55 on 2009-02-07
I am using 8.04 also but I am using Gecko and have java installed and have had no problems streaming anything >> I have to ask if you have the medibuntu repository in your soft ware sources if not then[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

Take a look at this guide : [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")
give it a read and if you decide it's for you just pay attention to the version 8.04 for you and of course you won't need to install flash ..If you need any help or have questions just post back..best to you

---

### Post by gandaran on 2009-02-07
> **Stephen Shellard said:**
> First the good news.  Flash 7 is gone. So thanks to Gandaran and Red Road 55. I think I've learnt something useful. 

Sadly there's still a lot to learn.  I have installed (using synaptic package manager)  flash plugin non free and Adobe Flash 10.  Result.  BBC Radio listen again service freezes. Utube gives me  pictures but no sound.  Ah well.  I still feel there's been progress.  Any thoughts on a simple resolution to make this a perfect thread?

Thanks again.
for BBC it's best you install the mplayer-mozilla plugin (yes you can have totem and mplayer plugin installed, mplayer plays  real video/audio stream totem doesn't), add the medibuntu repository and install the w32codecs package.
about the flash sound problem, if you running ubuntu 8.04 and install the flashplugin-nonfree you are using flash 9 not flash 10 even if it's installed, it's not good to have two flash versions installed, remove the flashplugin-nonfree! flash 9 has the sound problem, flash 10 fixes that sound issue, if you are only using flash 10 in either 8.04 or 8.10 and you still have problems with flash sound then you have to fix pulseaudio
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Stephen Shellard on 2009-02-07
Hurrah! Complete success, though not without a few twists and turns.  First I installed medubuntu repositiory,  mplayer and w32 codecs, as suggested.  I took this route as my original intention had always been to try and get Flash Player 10 to work;  however there was still no sound in utube and a freeze in BBC Radio iPlayer.  So, I followed the Pulse Audio link, as provided by Gandaran.  Working through this I discovered (what I should probably already have known) - that Pulse Audio was not installed on my system.  This is curious in that the website in question states clearly:  "PulseAudio is already installed and active on Hardy and Intrepid by default"  Well, not on my system.  For others considering this as a possible issue in their own struggles with Flash, Pulse Audio now appears in my Applications/Sound&Video  submenu.

At any rate having installed pulse audio and returned to the provided link and run the suggested code and rebooted, it all works.  

Thanks again to Gandaran and Redroad 55.

---

