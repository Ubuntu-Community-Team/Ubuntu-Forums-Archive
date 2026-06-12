---
title: "[SOLVED] Help Me!! New Ubuntu User!!!"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by KuroRai on 2007-07-05
Ok, so iInstalled Ubuntu, had  A LOT of trouble egtting it to dual-boot, but ppl on this forum were really helpful and we solved it...

iAm loving Ubuntu, it looks like a really nice sleek stable OS...

however iAm experiencing ONE HUGE set back, which if iAm unable to solve, will make me have to go and find another free OS, although iCouldn't find one that looked as good as Ubuntu and wrked with all my hardware...

Now the problem is sound... iHave looked a bit in the forums, but no one has a situation like mine.

my soundcard is detected, the volume is on and what not.. it even makes the drum sound when you log in... but thats the only sound iHear... when i try to play anything in the login window settings no sound comes out.

When iTry to play mp3s or any media (video and music) on Totem Movie Player or Rythmbox Music Player, the application just freezes up and iHave to force quit it. YES I HAVE THE CODECs!!! iDownloaded all teh GStreamer ones... but still no luck... iHAVE CHECK THE VOLUME CONTROLS but they don't help... although iDon't mind rechecking them the way you guys ask me too if you want me to. iJust hope some people are on rite now...

so please help me!!!

P.S. sry for my bad spelling!!! iAm trying to type really fast, thanks in advance!!!

---

### Post by NeoLithium on 2007-07-05
Have you installed the proper multimedia codecs? Check out this to open the proper repositories:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)
and this to install the proper codecs, assuming that you're using feisty:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

---

### Post by KuroRai on 2007-07-05
when iEnter "sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll" into teh terminal it asks me for my password (within the terminal) but it won't let me type anything... iTried copy/pasting it in to... doesn't wrk..

---

### Post by KuroRai on 2007-07-05
but iHave downlaoded all the gstreamer codecs from the ubuntu add/remove application...

---

### Post by NeoLithium on 2007-07-05
It does actually take in your user password, however it doesn't show any stars or acknowledgement of the keystrokes. Just enter your password as normal, typed correctly and hit enter, it will accept it :)

---

### Post by KuroRai on 2007-07-05
Some extra info:

destiny@Destiny:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by KuroRai on 2007-07-05
yes thank you! it is now installing all teh ones iDidn't ahve before... but this doesn't explain the frezeeing when iTry to play files does it? iWill leave this thread open til after iHave checked these new files out... thank you again!

---

### Post by NeoLithium on 2007-07-05
Depending on what you're trying to open, you'll need to enable the extra repositories and install all the codecs listed as in my links.  You can just copy and paste. When asking for the passsword, enter yours in, and hit enter, though it doesn't show up, it will accept it and begin installing what you need.

EDIT - You're welcome.  Ubuntuguide is a great place for new people to take a look around and get used to things.  Hopefully it will all work out for you, but if not. the forum is always here to guide you along :)

---

### Post by KuroRai on 2007-07-05
ok so iDownlaoded all the packages, but same probleem, neither the play nor the login window settings panel wrks still!!! HELP ME PLEASE !!! :'(

---

### Post by NeoLithium on 2007-07-05
Assuming that you're using Feisty Fawn (7.04), you downloaded the w32codecs package as well?

---

### Post by lisati on 2007-07-05
> **KuroRai said:**
> when iEnter "sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll" into teh terminal it asks me for my password (within the terminal) but it won't let me type anything... iTried copy/pasting it in to... doesn't wrk..

When Sudo asks for your passord, what you type is usually "hidden".....just type in your password and then press "enter"

---

### Post by KuroRai on 2007-07-05
iAm using fiesty, the wm32 codec? havnt gotten that one, lemme get it...

---

### Post by KuroRai on 2007-07-05
destiny@Destiny:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

---

### Post by KuroRai on 2007-07-05
what now!?!!?!?

---

### Post by NeoLithium on 2007-07-05
Follow the link in my above post to add the additional repositories. If you take it word by word, you'll have the proper repo to install the w32codecs package :)

---

### Post by KuroRai on 2007-07-05
iDon't understnad what you are trying to tell me to do, and the site you gave gives nothign but "sudo apt-get install w32codecs" which doesn't wrk...

---

### Post by KuroRai on 2007-07-05
iHave downlaoded mPlayer, still doesn't wrk...

---

### Post by NeoLithium on 2007-07-06
It's ok. I'll walk you through what it explains on that page, type this in a terminal window (Applicatoins -> Accessories -> Terminal):
```

gksu gedit /etc/apt/sources.list
```

It will ask you for your password. Enter your user password (the same you use to login) and hit enter.  then it will pop open a text editor window with a great deal of stuff. Don't worry, just take what is below, and copy and paste it in:

```

## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
#deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted
#deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe
#deb-src http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
#deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
#deb http://edevelop.org/pkg-e/ubuntu feisty e17
#deb http://e17.dunnewind.net/ubuntu feisty e17
#deb-src http://edevelop.org/pkg-e/ubuntu feisty e17

```

Once that has been pasted to OVERRIDE everything that is in the window, save the file and exit the text editor.  Then in the terminal window, copy and paste this command:

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```

Then once that has been copied and pasted, hit enter if it didn't go through, then in the same window type:
```

sudo apt-get update
```

VOILA! The additional repos are enabled, and you can install the w32codecs package, you'll probably also have a few additional updates to go thorugh.

---

### Post by KuroRai on 2007-07-06
doesn't wrk

destiny@Destiny:~$ gksu gedit /etc/apt/sources.list
(gedit:9684): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by ajmorris on 2007-07-06
> **KuroRai said:**
> doesn't wrk

destiny@Destiny:~$ gksu gedit /etc/apt/sources.list
(gedit:9684): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


your sudo config file may be empty check it in /etc/sudoers

if that has the password in it and sudo still wont work try

```
su
```

then do  ```
gedit /etc/apt/sources.list
```

---

### Post by KuroRai on 2007-07-06
grrr, none of this wrks! this is such a BIG HUGE down side to ubuntu... me is not liking this OS very much rite now...

---

### Post by ajmorris on 2007-07-06
> **KuroRai said:**
> grrr, none of this wrks! this is such a BIG HUGE down side to ubuntu... me is not liking this OS very much rite now...

you say none of it works.....
do you get any error messages in the output of the commands from my last post?
(su [enter], gedit /etc/apt/sources.list [enter]

---

### Post by zero244 on 2007-07-06
One of the easiest ways to get your audio, video codecs is install Automatix2 and install them from there.
Thats how I installed my codecs and they work perfectly.

---

### Post by reen254 on 2007-07-06
as neo lithium explained.. doing so i got this.. at the end aof a long download list..
Fetched 5133kB in 1m8s (74.4kB/s)                                                                                           
Reading package lists... Done
but i m still unable to play .avi{only audio works} which it says requires xvid mpeg4 codec
.mpg files play fine.. using totem movie player

---

### Post by KuroRai on 2007-07-06
ok see, the first first time iUsded totem movie player, the video worked (after iGot the codec) but no sound... so iDon't think vidoe is a problem... sound wrks SOMETIMES (after iLogin it doesn't seem to wrk, even if iLog out)... however even if iDo get video and audioup, my secxond problem smashes me back down.. when iTry to play .ogg or .avi or .mp3 in totem, or mp3s in ryhtmbox, they both frezze up... this happens to ALL  players... it could just be the codec is frezzing it, but iHave NO CLUE as to how ubuntu wrks, seeing as how yesterday was my first day...

---

### Post by KuroRai on 2007-07-06
iAm going to try atuomatix tho, thatsnks for teh rec

---

### Post by KuroRai on 2007-07-06
btw ren, what you should do is go into the add/remove software of ubuntu, search for "gstreamer" at the top, downlaod all those codecs that you want...

---

### Post by KuroRai on 2007-07-06
I FIGURED IT OUT!!! iWas thinking about all teh changes iMAde to ubuntu in the few hours iControled it, and iRemeembered iHad activated desktop effects... now altho iHad turned it off, iRemember turning on drivers for my video card... it was before this that only video played.... now that iHave turned it offf, everything wrks! iMust have dled the fix to the sound before, but it didn't wrk becasue the probelm was with video, not the file...thanks for your help tho guys!!!

---

