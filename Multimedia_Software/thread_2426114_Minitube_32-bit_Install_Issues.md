---
title: "Minitube 32-bit Install Issues"
date: 2019-09-04
forum: Multimedia Software
---

### Post by enigma9o7 on 2019-09-04
I use minitube on my pentium 4 as it supports 720p (whereas browser too slow) and has easy to use interface for my kids.

Recently it quit working, showing search results but not actual playing  videos, and research online tells me I need version 3.1 to solve this.

Ubuntu bionic repos have 2.5.2 or something old.

Official Minitube website only has 3.1 as 64-bit deb for Ubuntu 18.10. 

So I tried to build 3.1 myself on 32-bit 18.04 base.   It requires libmpv-dev version 29, which has a whole bunch of  other dependencies (as I first just tried installing that manually) not  in bionic repos. So I cheated - I changed bionic to cosmic in my apt  sources.list to sudo apt install  libmpv-dev (then restored sources file back to bionic).

Minitube make was successful. However, when I execute, I get the initial search screen, then segfault.

For further experimentation, since I now have the necessary libs  installed, I installed minitube3.1-1_i386.deb from debian sid, and it does the  exact same thing as the one I built, intro screen then segfault. For the  heck of it I also tried version 2.9-1_i386.deb from debian buster and  that runs without crashing, but it has the same issue as the one from ubuntu  repos. 

Any ideas?

---

### Post by mc4man on 2019-09-04
run minitube from a terminal, likely issue is wrong version of qt5 or some useless message about mpv failed to initialize

---

### Post by enigma9o7 on 2019-09-04
It's just the segfault.  That QT message I see often and think its irrelevant...[ATTACH=CONFIG]283932[/ATTACH]

---

### Post by mc4man on 2019-09-04
Well I just built the 3.1 source here in 18.04 using a google api key I generated, works fine.
 
Used libmpv-dev for bionic from here - [https://launchpad.net/~mc3man/+archive/ubuntu/bionic-media](https://launchpad.net/~mc3man/+archive/ubuntu/bionic-media)
It uses the ppa's ffmpeg-shared libs so if you were tempted to use you'd need to first remove all cosmic packages you installed, particularly any  cosmic ffmpeg shared libs..
(- The ppa llibmpv will be getting an update in near future..

screen reflects choosing Browse > music..

---

### Post by enigma9o7 on 2019-09-05
> **mc4man said:**
> Well I just built the 3.1 source here in 18.04 using a google api key I generated, works fine.

Just confirming 32-bit, right?

---

### Post by mc4man on 2019-09-05
> **enigma9o7 said:**
> Just confirming 32-bit, right?

I use amd64 bit but that's irrelevant, all the sources have i386 packages.

---

### Post by enigma9o7 on 2019-09-05
Ok will give it a try with that ppa (on another 32-bit 18.04 machine) and report back later today, that would be great if it works.

Note - PPA includes what I need, making now.  On both machines.  To attempt to fix my cosmic install, I executed this command to reinstall the package I installed from cosmic and it's dependencies.  ```
sudo apt-cache depends **libmpv-dev** | grep '[ |]Depends: [^<]' | cut -d: -f2 | tr -d ' ' | xargs sudo apt --reinstall install -y
```

---

### Post by enigma9o7 on 2019-09-06
<dupe dont see how to delete>

---

### Post by enigma9o7 on 2019-09-06
So 2nd machine finished make, it starts playing.  Audio only.  No video.  Terminal shows '[unknown] Error disabling idle display sleep "The name org.freedesktop.ScreenSaver was not provided by any .service files"

edit:Installed libcuda1 to eliminate that error, didn't change anything. 

Machine 1 finished make, still segfault.

---

### Post by mc4man on 2019-09-06
Please post 
```
apt-cache policy libavcodec-dev libavcodec58 libmpv-dev
```

---

### Post by enigma9o7 on 2019-09-06
Thanks mc4man.  I can tell from that my machine 1 still has stuff from cosmic sources, so I'll get that sorted out and make again, i.e.
```
user@user-HP-d530-CMT-DQ500C:~$ apt-cache policy libc6
libc6:
  Installed: 2.28-0ubuntu1
  Candidate: 2.28-0ubuntu1
  Version table:
 *** 2.28-0ubuntu1 100
        100 /var/lib/dpkg/status
     2.27-3ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
```

But machine2 was never frankenbuntu'd and still has a video issue.  I guess it's not a install issue anymore tho.

Machine1```
user@user-HP-d530-CMT-DQ500C:~$ apt-cache policy libavcodec-dev libavcodec58 libmpv-dev
libavcodec-dev:
  Installed: (none)
  Candidate: 7:4.1+git~bionic2
  Version table:
     7:4.1+git~bionic2 500
        500 http://ppa.launchpad.net/mc3man/bionic-media/ubuntu bionic/main i386 Packages
     7:3.4.6-0ubuntu0.18.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/universe i386 Packages
     7:3.4.2-2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
libavcodec58:
  Installed: 7:4.1+git~bionic2
  Candidate: 7:4.1+git~bionic2
  Version table:
 *** 7:4.1+git~bionic2 500
        500 http://ppa.launchpad.net/mc3man/bionic-media/ubuntu bionic/main i386 Packages
        100 /var/lib/dpkg/status
libmpv-dev:
  Installed: 2:0.29.1~bionic2
  Candidate: 2:0.29.1~bionic2
  Version table:
 *** 2:0.29.1~bionic2 500
        500 http://ppa.launchpad.net/mc3man/bionic-media/ubuntu bionic/main i386 Packages
        100 /var/lib/dpkg/status
     0.27.2-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
```

Machine2 ```
bodhi@bodhi-C51GM03:~$ apt-cache policy libavcodec-dev libavcodec58 libmpv-dev
libavcodec-dev:
  Installed: (none)
  Candidate: 7:4.1+git~bionic2
  Version table:
     7:4.1+git~bionic2 500
        500 http://ppa.launchpad.net/mc3man/bionic-media/ubuntu bionic/main i386 Packages
     7:3.4.6-0ubuntu0.18.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/universe i386 Packages
     7:3.4.2-2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
libavcodec58:
  Installed: 7:4.1+git~bionic2
  Candidate: 7:4.1+git~bionic2
  Version table:
 *** 7:4.1+git~bionic2 500
        500 http://ppa.launchpad.net/mc3man/bionic-media/ubuntu bionic/main i386 Packages
        100 /var/lib/dpkg/status
libmpv-dev:
  Installed: 2:0.29.1~bionic2
  Candidate: 2:0.29.1~bionic2
  Version table:
 *** 2:0.29.1~bionic2 500
        500 http://ppa.launchpad.net/mc3man/bionic-media/ubuntu bionic/main i386 Packages
        100 /var/lib/dpkg/status
     0.27.2-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
```

---

### Post by mc4man on 2019-09-06
I know for sure that if there is a version mismatch between minitube, libmpv, and the ffmpeg libs used to build vs. those used at runtime it'll cause a segfault (mpv failed to initialize
You should also make sure there is no other version of minitube installed in addition to no cosmic or Debian packages.
(- in this case by version mismatch I mean the exact source, not for example libavcodec58 vs. libavcodec57

If you wait till tonight (EST here), I'm going to upload a newer ffmpeg-shared and libmpv built off of it to the ppa. I may also add a minitube 3.1 package though won't be terribly concerned if minitube breaks down the road due to youtube changes.

The main advantage of the package built minitube is there is no need for a personal  google api key ( and it should work...

Edit:the ppa has minitube now, works fine here. Otherwise the ppa's libmpv should work fine as long as no conflicting ffmpeg shared libs or self built/installed minitube is present.

---

### Post by enigma9o7 on 2019-09-09
Hey thanks a lot.  I will try the PPA version of minitube today.

Regarding the api key, the 2.52 version I was using from ubuntu repo required the key, using a profile.d script to set it up.

Although I did get an email  couple months ago from google saying they were capping my keys data based on historical usage or something... and thats the key I used when I built.... don't think that could be the reason for no video tho... anyways will try yours very soon.

edit: No luck.  Same result as my build.  No video on machine2, and segfault on machine 1.  I still haven't fixed the other packages I took from cosmic which I plan to do now, hopefully that'll solve the segfault.

Machine2 (audio but no video):
```
$ minitube
[unknown] QApplication: invalid style override passed, ignoring it.
[unknown] Error disabling idle display sleep "The name org.freedesktop.ScreenSaver was not provided by any .service files"
```

---

### Post by enigma9o7 on 2019-09-09
Reinstalled OS on machine1 so no more version weirdness, just LTS base + minitube from ppa.  Still segfaults after briefly showing the intro screen.  Nothing in terminal output besides ignorable style override.  Machine is Intel Pentium 4.  I may try to build it again now that everything's clean, but first gotta reinstall everything else.

---

### Post by mc4man on 2019-09-09
What do you mean by **lts base**?
Maybe consider installing an ubuntu version that supports 32 bit OOTB  like xubuntu or lubuntu

(- I see that in the couple of days since I put that package in there have been 45 amd64 & 5 i386 installs, haven't heard of any runtime failures except for yourself

---

### Post by enigma9o7 on 2019-09-11
Sorry wasn't clear.  I installed bodhi legacy, which is based on 18.04LTS, then did all updates to 18.0.4.3.  .  It's faster than lubuntu on that old hardware, but in case somehow it's a bodhi-specific issue I'll try your build of minitube under live usb lubuntu if building myself doesnt work, and if it in fact does behave different under lubuntu I'll be curious to figure out why... I suspect it won't... but will try.

---

### Post by mc4man on 2019-09-11
Changes today make the player currently useless

---

### Post by enigma9o7 on 2019-09-11
Yeah I saw that behavior on machine2 (the one with no video) now is just skipping thru everything.    Still need to get past this segfault on machine1 regardless (with the assumption flavio will fix the api issue), make was successful no problem with just your ppa, but still segfault.  Next to confirm its the same with lubuntu...

edit: confirmed, segfault with lubuntu 18.0.4.3.  All I did was boot live usb, connect to wifi, add your ppa, install minitube, and run.   Shows search screen for a second then segfault.

---

### Post by enigma9o7 on 2019-09-12
My install and make issues are completely solved thanks to your ppa, so thanks much for that.

But. I think I'm going to have to give up on minitube.   The video issue on machine2 is probably not something I can do anything about, its using noveau drivers, and nvidia-304 would be the latest it could use and that's not available for 18.04 and I already tried in the past to make it work before with patches and it caused video glitches and other issues.     And machine1 segfault even on clean OS install, that's not anything I know how to further debug.

---

### Post by mc4man on 2019-09-12
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
has 304 for 18.04

---

### Post by enigma9o7 on 2019-09-12
> **mc4man said:**
> [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
has 304 for 18.04

Yes, but it's not installable from that ppa.  I went down this road before, I did manage to get it installed eventually manually, even think I wrote-up on here how to do it.

```
$ sudo apt install nvidia-304
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-304 : Depends: xorg-video-abi-11 but it is not installable or
                       xorg-video-abi-12 but it is not installable or
                       xorg-video-abi-13 but it is not installable or
                       xorg-video-abi-14 but it is not installable or
                       xorg-video-abi-15 but it is not installable or
                       xorg-video-abi-18 but it is not installable or
                       xorg-video-abi-19 but it is not installable or
                       xorg-video-abi-20 but it is not installable or
                       xorg-video-abi-23
              Depends: xserver-xorg-core
              Recommends: libcuda1-304 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by mc4man on 2019-09-13
> **enigma9o7 said:**
> Yes, but it's not installable from that ppa.  I went down this road before, I did manage to get it installed eventually manually, even think I wrote-up on here how to do it.

```
$ sudo apt install nvidia-304
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-304 : Depends: xorg-video-abi-11 but it is not installable or
                       xorg-video-abi-12 but it is not installable or
                       xorg-video-abi-13 but it is not installable or
                       xorg-video-abi-14 but it is not installable or
                       xorg-video-abi-15 but it is not installable or
                       xorg-video-abi-18 but it is not installable or
                       xorg-video-abi-19 but it is not installable or
                       xorg-video-abi-20 but it is not installable or
                       xorg-video-abi-23
              Depends: xserver-xorg-core
              Recommends: libcuda1-304 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
That does seem the case, the xorg-video-abi that 18.04 is now using (release or HWE) isn't supported. Not sure why they bother to still have in ppa..
You may be able to use smtube, best from the smplayer ppa, benefits  a little setup..

---

### Post by enigma9o7 on 2019-09-13
Yes, smtube does work as an alternative, spent time yesterday getting command lines I liked for the media players and works ok, can't make window size ideal for variety of video resolutions, but the biggest downside in my use case (5-year old kids who can hardly read) is no search history, so they can't just click on stuff I've typed before (i.e. abc songs, phonics, coloring, etc), instead seeing the popular videos list as the start screen.  Minitube is ideal for them and I wish I could get it working again.

---

### Post by enigma9o7 on 2019-09-23
I saw minitube 3.2 was released, with bugfixes for video issues.  Hoping it might solve my video problem on one machine and possibly even segfault on the other, I tried to make it.  Both machines cannot make tho, get error about operator[]...  


```
In file included from src/ytvideo.cpp:1:0:
src/ytvideo.h: In constructor &#8216;YTVideo::YTVideo(const QString&, QObject*)&#8217;:
src/ytvideo.h:40:10: warning: &#8216;YTVideo::ageGate&#8217; will be initialized after [-Wreorder]
     bool ageGate;
          ^~~~~~~
src/ytvideo.h:38:10: warning:   &#8216;bool YTVideo::loadingStreamUrl&#8217; [-Wreorder]
     bool loadingStreamUrl;
          ^~~~~~~~~~~~~~~~
src/ytvideo.cpp:19:1: warning:   when initialized here [-Wreorder]
 YTVideo::YTVideo(const QString &videoId, QObject *parent)
 ^~~~~~~
src/ytvideo.cpp: In lambda function:
src/ytvideo.cpp:106:38: [COLOR=#ff0000]error[/COLOR]: no match for &#8216;operator[]&#8217; (operand types are &#8216;const QJsonValue&#8217; and &#8216;const char [5]&#8217;)
                     int itag = format["itag"].toInt();
                                      ^
src/ytvideo.cpp:107:41: [COLOR=#ff0000]error[/COLOR]: no match for &#8216;operator[]&#8217; (operand types are &#8216;const QJsonValue&#8217; and &#8216;const char [4]&#8217;)
                     QString url = format["url"].toString();
                                         ^
src/ytvideo.cpp:109:48: [COLOR=#ff0000]error[/COLOR]: no match for &#8216;operator[]&#8217; (operand types are &#8216;const QJsonValue&#8217; and &#8216;const char [7]&#8217;)
                         QString cipher = format["cipher"].toString();
                                                ^
Makefile:2241: recipe for target 'build/obj/ytvideo.o' failed
make: *** [build/obj/ytvideo.o] Error 1 
```

mc4man, if you are able to successfully package it for your ppa, I'd love to try it.  (or of course idea for why I can't make).  I of course am using librariers/etc from your ppa that did allow me to make version 3.1 without error.

---

### Post by mc4man on 2019-09-24
> **enigma9o7 said:**
> I saw minitube 3.2 was released, with bugfixes for video issues.
Seems like a qt 5.9  issue from [this  commit ]("https://github.com/flaviotordini/minitube/commit/30ec199bb0fdd5641676b636cab04c4ed0f8c98e")
If I build 3.2 on 19.10 (qt 5.12) there's no such failure. 

[Filed issue]("https://github.com/flaviotordini/minitube/issues/151"), who knows..
Edit: so gist is 3.2 and up will only work with qt-5.10+, so once 3.1 breaks down the road that's that for 18.04
(- there are ways for individual users to use higher qt in local ways, nothing I'd care about..

---

### Post by enigma9o7 on 2019-10-01
I just can't give up.  I'm trying to make right now with this: [https://launchpad.net/~beineri/+archive/ubuntu/opt-qt-5.12.0-bionic](https://launchpad.net/~beineri/+archive/ubuntu/opt-qt-5.12.0-bionic)

Seems to work.  from minitube folder cloned from git, of course after adding mp4man ppa,:
```

sudo add-apt-repository ppa:beineri/opt-qt-5.12.0-bionic
sudo apt install qt512-meta-full
/opt/qt512/bin/qt512-env.sh
/opt/qt512/bin/qmake "DEFINES += APP_GOOGLE_API_KEY=MyAPIKey"
make

```

I first tried it with the minimal qt512 and got a project error during qmake about x11 module, so used the full instead of figuring out exactly what I needed.  Dunno if running the env script is required, as I didnt try it without, but I did have to use the full path for qmake to report version 5.12.

---

### Post by enigma9o7 on 2019-10-01
Unfortunately, 3.2 didn't solve my issues, same behaviour as 3.1.  I still get audio but no video on one machine, and segfault after search screen on the other.

---

