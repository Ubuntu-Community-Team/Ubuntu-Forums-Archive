---
title: "Creative Labs Sound Blaster X-Fi"
date: 2009-06-19
forum: Multimedia Software
---

### Post by niroshido on 2009-06-19
Hello, i was following the guide stickied above this thread. Obviously i would not be posting if i had resolved the prob

firstly i am going to start one day my pc was put into car, working earlier that morning, arrived to house and found windows xp was not working "missing file" . I attempted a repair and reinstall, neither worked, i then downloaded Ubuntu and it works, to a degree. I like music yet the Sound card mentioned  above does not work.

I get no sound, attempted to find the module from AlsaProject but

>  [SIZE=2]
[/SIZE]  [SIZE=2][[Testing]]("http://www.alsa-project.org/main/index.php?title=Matrix:Tag-Testing&action=edit") [[PCI]]("http://www.alsa-project.org/main/index.php/Matrix:Tag-PCI") Card delivered to developers. Completely new architecture. Creative have supplied a data sheet to developers. Development work has started.Preliminary support need testers.The patch is now merged into sound-unstable GIT tree topic/ctxfi [/SIZE][SIZE=2]branch: git://git.kernel.org/pub/scm/linux/kernel/git/tiwai/sound-unstable-2.6.git.The corresponding alsa-driver snapshot tarball is: [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz)[/SIZE] The driver module is named as snd-ctxfi. 
i cannot find the file, any assistance would be appreciated.

Sorry if this is a copy of other threads over same problem


edit: i forgot to mention that i am using a dell xps 710, whilst this has little relevance i still feel the need to include it. The steps from the pinned thread i followed. there were no drivers for the specific module nor anything on AlsaProject. Another thing i noticed was when i went to F2 when BIOS was loading and checked sound in the settings there on board sound was active, should i deactivate this.? im sorry for being noob

---

### Post by niroshido on 2009-06-22
am i allowed to bump?

---

### Post by Magick93 on 2009-06-22
Hi

If you use OSS I believe that has support for Creative X-fi. 

There are also linux drivers for X-fi from Creative that you can download.

---

### Post by Silent Warrior on 2009-06-23
About those two drivers, though, note that the OSS-variant is the older release. Also, I've had no luck compiling Creative's package against the 2.6.28-13-kernel (-12 works fine for me) - YYMV, as they say.
Creative's drivers are good enough for me - music plays, PulseAudio does its thing... I made a related topic recently where something interesting turned up - X-Fi-support is expected in the 2.6.31-kernel. So, if we can all wait until then, we should be happy campers. :)

---

### Post by niroshido on 2009-06-25
hi all, sorry for delay on the responce and thanks, i've yet to try anything new to my OS but i will check up both of your recommendations. also to Silent Warrior from iceland ehhh! u workin for CCP? (yes i will jump to a conclusion that if u live on the island that u do work for CCP, if u do thats freakin awesome!)

---

### Post by Silent Warrior on 2009-06-25
Actually... At the moment I'm back in Sweden for summer-break - I'm a student at LHI ([www.lhi.is](www.lhi.is)). (Those CCP, were they the bunch who made Eve or something? I ain't no code-monkey...)

---

### Post by niroshido on 2009-06-25
> **Silent Warrior said:**
> Actually... At the moment I'm back in Sweden for summer-break - I'm a student at LHI ([www.lhi.is]("http://www.lhi.is")). (Those CCP, were they the bunch who made Eve or something? I ain't no code-monkey...)

heheh cool hope its going well for you, and yes CCP made Eve not only that i think its ironic i yet again am mentioning something eve related to another swedish person, i have 10 friends that i made from the game of which are swedish :D

also this :
> Quick install
 
============= 
In terminal,
 
1) Goto source directory 
2) Execute make command as root 
   make 
   make install

im sorry this is a complete WTF does this mean, moment how can i do this?

---

### Post by Silent Warrior on 2009-06-25
Open a terminal and go to the directory where you extracted the XFi<whatever>.tar.gz - you should have a directory with the same name, at least I do. Once there, simply type ```
sudo make && sudo make install
```hit enter, and wait for it to complete. Or you could run the commands separately - this line will run the two commands directly after one another, which will make it difficult if you need to do some troubleshooting.

---

### Post by niroshido on 2009-06-27
> **Silent Warrior said:**
> Open a terminal and go to the directory where you extracted the XFi<whatever>.tar.gz - you should have a directory with the same name, at least I do. Once there, simply type ```
sudo make && sudo make install
```hit enter, and wait for it to complete. Or you could run the commands separately - this line will run the two commands directly after one another, which will make it difficult if you need to do some troubleshooting.

holy mother of anubis,  I HAZ SOUND!! it freakin worked, now why it took so long...

when you mentioned to change directory i typed in cmds like "cd ~/Desktop" this takes you to the desktop folder?, well i could'nt find the darn folder for the audio there it was only when i typed in "cd ~" takes you to home from here i typed "ls" whilst in home directory, i then saw the files of which i came across 2 things a red directory (highlighted red) which was the tar.gz file, so i tried to cd to that, that failed so i went to the one above which was the black named one, and bam i was in it. I then used the commands you gave and it installed etc. i then had to go to sound change the audio out, then go to the sound button on the top and select "creative X-FI alsa mixer" then it worked!! :D on the other hand, music does not play from youtube videos on firefox

im delighted, thank you for the help, also this helped [URL="http://ubuntuforums.org/showthread.php?t=73885"]http://ubuntuforums.org/showthread.php?t=73885
[/URL]

---

### Post by TheSpartin on 2009-08-07
Hey, ive had to do the exact same thing and have the exact same problem except i have NO sound in firefox but i do have sound every where else, what can i do to get firefox to have sound also.  (im a complette noob about all of this)

---

### Post by Silent Warrior on 2009-08-08
I think there are other topics better suited for your problem, TheSpartin. See if there's anything in Networking, or whatever it's called. Also, I assume you mean sound in Flash, rather than straight HTML? A bit of a scourge in Linux-land, that...

No, I may have told a lie. I found something in the 64-bit section. If you happen to be running a 64-bit installation, have a look at the sticky about installing Flash - it should be near the top. If that doesn't help, make some good use of the forum's search-feature. :)

---

### Post by woodsyboredom on 2010-12-02
I am trying to get this sound card working. Downloaded the driver; running sudo command in terminal and when I do I get this message:

make -C /lib/modules/2.6.35-23-generic/build M=/home/woodsy/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  LD      /home/woodsy/Desktop/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/woodsy/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/woodsy/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14: fatal error: sound/driver.h: No such file or directory
compilation terminated.
make[2]: *** [/home/woodsy/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/woodsy/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [all] Error 2

What gives? this happens after I enter sudo make in terminal when i'm at the source directory. any help much appreciated.

---

