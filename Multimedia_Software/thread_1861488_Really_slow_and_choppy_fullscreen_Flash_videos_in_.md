---
title: "Really slow and choppy fullscreen Flash videos in Ubuntu 11.10"
date: 2011-10-15
forum: Multimedia Software
---

### Post by razor7 on 2011-10-15
Hi, i have readed this questions but no luck at all 
[http://askubuntu.com/questions/38028/performance-being-really-choppy-with-ati-driversç](http://askubuntu.com/questions/38028/performance-being-really-choppy-with-ati-driversç)
[http://askubuntu.com/questions/54044/choppy-flash-video-playback](http://askubuntu.com/questions/54044/choppy-flash-video-playback)

My PC specs:

 - Processor: Core i7 860
 - Mother: Gigabyte GA-H55M-USB3
 - Ram: 4GB G-Skill 1333
 - Video: PCie Sapphire ATi HD 4890 Installed propietary drivers.

glxinfo
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series           
OpenGL version string: 3.3.11005 Compatibility Profile Context
OpenGL shading language version string: 3.30
OpenGL extensions:

When try to view fullscreen YouTube videos (or any other flash video) the video is almost unplayable, really slow and choppy.

The funny thing is that right beside this box, I have a Code2Quad with Asus p5qc mobo 2gb ram and the same ATi video card, qith same Ubuntu setup, propietary drivers and ubuntu 11.10) and the videos play just fine!

Any ideas?

Thanks a lot!

---

### Post by dniMretsaM on 2011-10-15
Make sure you have the right Flash installed. Your best bet is to use the Firefox add-on [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") [[direct link]("https://addons.mozilla.org/firefox/downloads/latest/161939/platform:2/addon-161939-latest.xpi?src=dp-btn-primary")] which will install the correct version of Flash (either the version from the repositories or 11 beta. I recommend the beta) and set it up correctly for your system.

---

### Post by razor7 on 2011-10-15
> **dniMretsaM said:**
> Make sure you have the right Flash installed. Your best bet is to use the Firefox add-on [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") [[direct link]("https://addons.mozilla.org/firefox/downloads/latest/161939/platform:2/addon-161939-latest.xpi?src=dp-btn-primary")] which will install the correct version of Flash (either the version from the repositories or 11 beta. I recommend the beta) and set it up correctly for your system.


Installed Flash-Aid, and just installed the same flash plugin 11.0.1.152 as Ubuntu Software Center (flashplugin-installer 11.0.1.152ubuntu1).

The results didn't change, the video is almost unplayable at fullscreen

Please remember that my side box has the same software specs, but less hardware specs and work just fije.



Really not understand why!

---

### Post by winnibob on 2011-10-16
I'm experiencing the same problem with an ATI HD6850 on ubuntu 11.10 x86_64, same flash version, catalyst drivers 11.8 installed (version 2:8.881-0ubuntu4).
No solution yet.

PC specs :
- Processor: Core i7 860
- Mother: Asus P7P55D-E PRO
- Ram: 8GB G-Skill 1600
- Video: PCie Sapphire ATi HD 6850 Installed propietary drivers.

---

### Post by kroutal on 2011-10-16
I have exactly the same problem. I have an nvidia card and an intel integrated card. The bug occurs on both cards. I also have it on chromium

---

### Post by winnibob on 2011-10-16
I did some changes in flash config, compiz config and in the catalyst driver config and after a reboot the problem seems to be solved for me.

As far as I can remember, here are the settings I changed and their state now (sorry if the translation is not exact, I'm using the french version) : 

**Flash config**
Hardware acceleration : enabled

**Compiz config**
OpenGL -> Sync to VBlank : Yes
Composite -> Refrash rate : 60Hz (same as in catalyst)

**Catalyst Control center**
Display Manager -> Digital Monitor -> Options -> Use GPU for scaling
Display options -> Tear Free -> Activate Tear Free
3D -> More options -> Wait for vertical sync -> Always

I hope it will help you, let me know if you need more information.

EDIT : I forgot to tell that I installed flash with "flashplugin installer" from the repositories, just in case it may make a difference...

---

### Post by razor7 on 2011-10-16
Hi, tested that but no luck!

Just created a bug repoirt because is affecting several people. Please follow this link and add yourself to the affected list.

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/876103](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/876103)

Best regards!

---

### Post by sirjeff2000 on 2011-10-19
I also had the problem with MP4 files. Dell laptop insperion pentium 4, 2 gig of mem.
I replaced Unity with the Gnome classic desktop. Video working fine now.

Here's a linke to describe what to do.

[http://tombuntu.com/index.php/2011/09/11/install-the-classic-desktop-in-ubuntu-11-10/](http://tombuntu.com/index.php/2011/09/11/install-the-classic-desktop-in-ubuntu-11-10/)

---

### Post by miztic on 2011-11-30
I'm having a similar problem, the odd thing is, the video works fine for the first few minutes and THEN becomes choppy.

Core2Duo T7700 2.4Ghz, 3GB memory, nVidia 8600M-GT.

Full screen video used to work fine before upgrading to 11.10/unity.

Also, it's not just flash, I just tested with mplayer and a locally (on SSD) stored h.264 clip , the first few minutes work fine, then it becomes choppy.

Once an application becomes choppy, nothing will fix it, after mplayer became choppy, it would be from frame 1 when starting it subsequent times, and no amount of fiddeling with the settings (like cutting resolution in half) changes anything.

next I switched to VLC with the same video, ran fine for a good 2 minutes and then froze... subsequent times of starting VLC with the movie clip makes vlc freeze on frame 1. 

very strange behavior, it's like something is buffering somewhere and then runs out of space.

---

### Post by mystika1 on 2011-12-01
Hi,
I have had horrible video playback the last few days after the new flash plugin 11 was installed. I finally got this fixed when I downloaded flashplayer 10.3 from adobe   [http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_10.3.183.10_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_10.3.183.10_archive.zip)  then went into a terminal a typed "locate libflashplayer.so and removed all flashplayer files then extracted the 10.3 libflashplayer.so  file to usr/lib/firefox 8.0/plugins. I am back to viewing pleasure.

HTH,
Penny

---

### Post by fixtrot on 2011-12-06
And how do I "remove" them etc?

---

### Post by mystika1 on 2011-12-06
Ok.
First..use synaptic to remove flash from there. 
Also..someone else may have a simpler way to do this but I am not a guru and did the best that I could so here ya go...
I use a program called kate to do all of my text editing. You may have a different program but for this I will walk you through what I did.

First...in a terminal type
> gksudo kate
Type in your password.
When kate pops up select "open" then choose "root"  from the menu on the  left. You will see files that pop up in a list on the right.  Select "usr" then "lib" then scroll to firefox 8.0(or whatever firefox version you have) then scroll to "plugins." If you see libflashplayer.so you need to click on it to highlight it and right click and scroll down to "move to trash"

I only had to remove flash from this file. You may have flash installed in other files. 

Now here is how I installed the older 10.3
I hope that I can make this as simple as possible in order to help you. Please let me know if you need further help.  Again..there are prob a million ways of doing this and some may be faster but it got the job done so.....
I created a folder called "flash" in my downloads. I then went to adobe and downloaded the 10.3 file to the newly created "flash" folder. Right click on the downloaded file and select extract here. A file should show up. Click on it to open it. 
Open the file called 10_3r183_10. You should see several files now. I used the flashplayer 10_3r183_1_10_linux.tar.gz Right click on it and select "extract to "
A large window will pop up for you to choose where to extract the file to. Choose "file system" then "usr"  then "lib" then "firefox 8"(or whatever version of firefox yo have..then finally "plugins" and click on the extract button at the bottom.  You should now see a new libflashplayer.so file there. You will also see a usr file there as well but it is not needed here. You can delete that usr file in the same way as described earlier with kate. 

Now I would restart your machine and try playing a video.

HTH,

Penny

---

### Post by miztic on 2011-12-12
Update: I switched to plain gnome and fullscreen video works fine now. Unity is definitely interfering somehow.

---

### Post by zyvy on 2012-03-04
i had the same problem, to fix it
i used flash-aid addon for firefox 

use wizard mode - adobe stable
check override GPU
check enable HWVideo Decode
check npviewer tweak for 64bit system with 32-bit plugin

after instalation restart firefox and fullscren videos like youtube work good now at least for me, maybe itwill help any1 else

---

### Post by revoice on 2012-03-19
What worked out great for me (but not 100% perfect)

1. Installed properly AMD Drivers 12.2 fglrx
2. With compiz settings manager disabled Refresh Rate detection, set it to 120hz (composite) and disabled Sync to VBlank (opengl)

I have a HD6950 (can't believe im fighting youtube though...)

hope it helps!

---

