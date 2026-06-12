---
title: "Uber Noob Help Please"
date: 2006-03-09
forum: Multimedia &amp; Video
---

### Post by GmAz on 2006-03-09
Ok, I am trying to install the newest NVidia drivers (8178).  I download the .run file from nvidia.  I even figured out how to install binutils like the installer needed.  However, when it tells me that it needs to compile the kernel or something of the like, it says it can't find my kernel source.  How do I get around this?  I can install the drivers with:

sudo apt-get install nvidia-glx

command from the terminal, and it works, but I would like the newest drivers.  Also, I want to install the NForce drivers for my motherboard.  It gives me the same error about compiling the kernel.  I really want to use linux.  Right now, my system dual boots, but I am a computer enthusiast and its time to go for Linux.  Also, 5.10 doesn't recognize all my hardware beyond my video card and motherboard.  Is this a bad thing?  It runs, but what if my hardware manufacturer doesn't have linux drivers.  Thanks!

---

### Post by Sutekh on 2006-03-09
If you want to install the latest (8178 ) drivers then follow Method 2 in this HOWTO

[Ubuntu Forums - HOWTO: Latest NVIDIA Drivers]("http://ubuntuforums.org/showthread.php?t=75074")

---

### Post by GmAz on 2006-03-09
I tried to use that guide already and it never seems to go right.  Something always happens thats wrong.  I will try one more time.

---

### Post by Sutekh on 2006-03-09
[QUOTE=GmAz]I tried to use that guide already and it never seems to go right.  Something always happens thats wrong.  I will try one more time.[/QUOTE]
Where do you go wrong?  I've used it many times so I can probably help you step through it.

---

### Post by GmAz on 2006-03-09
Ok, I messed up the times before, when i did the uname-r, I was only looking at the amd64 part, but it was amd64-generic.  It should go through this time.  I just overlooked the -generic part.

---

### Post by Sutekh on 2006-03-09
[QUOTE=GmAz]Ok, I messed up the times before, when i did the uname-r, I was only looking at the amd64 part, but it was amd64-generic.  It should go through this time.  I just overlooked the -generic part.[/QUOTE]
Ok that's most likely the problem.  To allow the NVIDIA installer to compile the module it needs the correct kernel headers, so getting amd64 and amd64-generic mixed up probably caused the issue.

---

### Post by GmAz on 2006-03-09
Ok, now a new issue.  Its telling me that it appears that I am compiling the NVIDIA Kernel module with a different compiler than the one i used to compile the running kernel.  It says I used gcc 3.4, but i have gcc 4.0 now.  Do I want to continue?  It only gives me to continue or abort installation.

---

### Post by Sutekh on 2006-03-09
No you need to abort this time.

Unfortunately the kernel was compiled using gcc-3.4, which means that you must install gcc-3.4 before the NVIDIA installed can compile its module.

This is the step you need to do before starting the NVIDIA installer

First install gcc-3.4 (if you don't already have it)
```
sudo apt-get install gcc-3.4
```
Then right before you start the installer use this code to make the gcc-3.4 the active compiler, no the gcc-4.0 one.
```
cd &#8220;directory where you have the nvidia installer&#8221;
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
```

---

### Post by GmAz on 2006-03-09
Sweet!!  It worked.  Now, is the process the same for the NForce drivers (i.e. downloading the headers and what not and setting the gcc to 3.4)?  If I do that, will I have to redo anything for my video drivers?  

New Question:  I have a Sound Blaster Audigy 2 ZS Sound Card and creative has no linux drivers on their site.  Do these exist elsewhere or is there a way to make my audio work.

I found this on google:

[http://files.printf.dk/guides/audigy2.htm](http://files.printf.dk/guides/audigy2.htm)

would that work?

---

### Post by Sutekh on 2006-03-10
[QUOTE=GmAz]Sweet!!  It worked.  Now, is the process the same for the NForce drivers (i.e. downloading the headers and what not and setting the gcc to 3.4)?  If I do that, will I have to redo anything for my video drivers?  [/QUOTE]I read on a forum for people with my mobo, that installing nforce drivers is uneccessary.  But I'll check on that.

[QUOTE=GmAz]
New Question:  I have a Sound Blaster Audigy 2 ZS Sound Card and creative has no linux drivers on their site.  Do these exist elsewhere or is there a way to make my audio work.

I found this on google:

[http://files.printf.dk/guides/audigy2.htm](http://files.printf.dk/guides/audigy2.htm)

would that work?[/QUOTE]
It may.  There is another good place to check out sound issues.

[http://www.alsa-project.org/]("http://www.alsa-project.org/")

Check out this page, regarding soundcards

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix")

There are several Audigy 2 ZS soundcard entries there.  It looks like they use the same sound driver emu10k1 as that link you posted.  Frankly I'm surprised sound wasn't working out of the box for you.

---

### Post by GmAz on 2006-03-10
I was wrong, it recognized my Sound Card just fine.  I do have a question about my wifi card, which is very important because my only connection is wireless unless I set up my system in the living room (like it is now) and I really want it wireless.  Here is the link to my thread:

[http://ubuntuforums.org/showthread.php?p=809045#post809045](http://ubuntuforums.org/showthread.php?p=809045#post809045)

Thanks again for help with video!

---

### Post by Sutekh on 2006-03-10
Not a problem!

---

### Post by GmAz on 2006-03-10
Another question about what we did above and my wifi adapter.  in step 9, it says to do:

sudo apt-get --purge remove linux-restricted-modules-amd64-generic

is this step necessary?

---

### Post by Sutekh on 2006-03-10
Yeah I've been thinking about that in recent times, becuase the -restricted-modules are required if you use the nvidia-glx package.  So those modules, specifically the nvidia ones, must conflict with the module compiled by the official NVIDIA installer.  

Do you think that caused your Wifi problems?

---

### Post by GmAz on 2006-03-10
Yes, I was reading other posts in this forum and the networking forum and several people have pointed at that step as the culpret.  I found the madwifi tutorial on how to re-install it, but the repository of the file its no longer there.  I googled the file and found a new place for it, but its a different file name.  I tried it anyways and it didn't work.   I used the 'lspci -v' command and my system recognizes the wireless card, but it isn't sellectable in my networking control panel.

---

### Post by Sutekh on 2006-03-11
[QUOTE=GmAz]Yes, I was reading other posts in this forum and the networking forum and several people have pointed at that step as the culpret.  I found the madwifi tutorial on how to re-install it, but the repository of the file its no longer there.[/QUOTE]

You downloaded the wifi file using apt-get?  Check in /var/cache/apt/archives and see if the file is still there.  It should be unless you deleted it or ran apt-get clean.

---

