---
title: "No sound for youtube!"
date: 2009-05-15
forum: Multimedia Software
---

### Post by thepeachytricycles on 2009-05-15
Ok I will try and do this in a civil manner. Even though I would like to find the people who decided that this update was ready, and break their necks. 

I have now spent my ENTIRE day off, fixing my computer.  I have fixed my sound card, my network card and my video card, all because of this "update".  If I wanted to to have this kind of hassle with my OS I would have stayed with Windows. 

The one thing I can't fix is getting sound to play with youtube (or any flash for that matter).  I have done every thing to try and fix this;
I have installed: padevchooser, paman, ubuntu-restricted-(whatever it was)
I have checked alsamixer
I have checked pulseaudio
I have made sure that nothing is muted
I even sacrificed a fatted calf in hopes that it would help.

All other sound works, I do not know what else to do. Please help.

In closing to the deciding body who released this "update" I just have one thing to say to you "F*** you very much, Mr. Gates"

---

### Post by connorh123 on 2009-05-15
In aumix, did you make sure that the Vol bar was all the way to the right?

---

### Post by shanefagan on 2009-05-15
Try killing pulseaudio in system monitor 
System>Administration>System monitor. 
Then hit alt+f2 
and type pulseaudio and hit enter and try to play the video again.

Regards
Shane

---

### Post by thepeachytricycles on 2009-05-16
Firstly thank you for your input. 

Connorh123 as it turns out I did not have aumix, I have since installed it and yes the Vol bar is fully to the right. Alas I still do not hear "You are a pirate" by lazy town (a very unnatural show)

And Shanefagen, Dear dear Shanefagen, your suggestion seems to have been spot on. I now hear crackling in place of the dulcet tunes I so wish to hear. A small victory to be sure, annoying non the less.

I thank both of you for you suggestion and I hope that one day I will recieve the infromation I so wish to find.
__

---

### Post by psyke83 on 2009-05-16
If you're using the 64-bit release, see [this]("http://ubuntuforums.org/showpost.php?p=7275171&postcount=1302") comment for a possible explanation.

---

### Post by gandaran on 2009-05-16
thepeachytricycles
provide some info on you system, ubuntu version? 32-bits or 64-bits? which flash packages and flash version is installed? only with some information we can help you.
your problem could have a simple fix but I don't think installing a lot of things will help most likely even mess it up more!

---

### Post by thepeachytricycles on 2009-05-16
System info:
Acer aspire 4315
memory: 1.5 GiB
Processor: intel celeron  CPU 540 @ 1.86 GHz
32-bit
Sound card: Realtak ALC268
Ubuntu 9.04
kernel Linux 2.6.28-11-generic
GNOME 2.26.1
Flash package:
adobe-flashplugin
flashplugin-nonfree
flashplugin-installer
adobe flash player version 10.0.22.87 linux

Yamtech: Though I thank you for your suggestion, that was one of the first things I tried.
[B]
[/B]

---

### Post by WatchingThePain on 2009-05-16
I had that problem and simply installing ubuntu-restricted-extras package seemed to fix it.

---

### Post by thepeachytricycles on 2009-05-16
I have done this, would installing Kubuntu/Xubuntu-restricted-extras do any thing for me? Would installing clive help? I am completely lost here.

---

### Post by gandaran on 2009-05-16
> **thepeachytricycles said:**
> I have done this, would installing Kubuntu/Xubuntu-restricted-extras do any thing for me? Would installing clive help? I am completely lost here.
why install these packages? they install exactly the same codecs as the ubuntu one?
and you already have three adobe flash packages installed, you should only have one, I would recommend you remove the flashplugin-nonfree and adobe-flashplugin packages! keep only the flashplugin-installer package and ensure you still haven't any other adobe flash plugin like flash 9 or even any open source gnash or swfdec flash installed, the more you install the bigger the mess!
I would also recommend to delete your firefox profile (but backup it first) then restart firefox and see what happens.

---

### Post by thepeachytricycles on 2009-05-16
OK I have deleted all but flashplugin-installer. I have made sure that all other packages are not present, including third party. The problem is still persists. 

I am unaware on how to delete my firefox profile.

---

### Post by gandaran on 2009-05-16
> **thepeachytricycles said:**
> OK I have deleted all but flashplugin-installer. I have made sure that all other packages are not present, including third party. The problem is still persists. 

I am unaware on how to delete my firefox profile.
just rename the /home/user/.mozilla to .mozilla.old (this way you are backing-up it) start firefox and go to youtube, play the flash video, see what happens if no change you can restore your old profile.
you can also try running firefox as root (sudo firefox) just to test in youtube, usually sound will work running root firefox, but a warning! do this only to test it on youtube videos, don't change any root firefox settings? 
if sound works with root firefox then it could be a user permission issue.
but most likely it is a pulseaudio problem that you will have to fix.

---

### Post by thepeachytricycles on 2009-05-16
Deleting my profile didn't work. I also tried another web browser (Galeon) to see if it would work, but again just a dead end.
When I ran as a root sound still did not work. 
By permission do you mean setting the groups and making sure that I have access to the different groups? I have set the permissions to access the groups pulse, pulse-access, and pulse-rt so I am in the group.

If I don't get this soon I will reinstall v8.10 and have done with it.

---

### Post by gandaran on 2009-05-17
> **thepeachytricycles said:**
> Deleting my profile didn't work. I also tried another web browser (Galeon) to see if it would work, but again just a dead end.
When I ran as a root sound still did not work. 
By permission do you mean setting the groups and making sure that I have access to the different groups? I have set the permissions to access the groups pulse, pulse-access, and pulse-rt so I am in the group.

If I don't get this soon I will reinstall v8.10 and have done with it.
okay then, reinstalling the system is what I would do if I had a problem like this but I wouldn't go back to 8.10, I would still bet on 9.04, theres no guarantee that is was the updates that broke your sound, I would try again but reinstalling is the last resort and theres still a lot you can try yet.
try this [pulseaudio]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+fixes") fix guide, if it still won't help, then install and build alsa-source, theres no guarantee installing alsa drivers will work too and you will not be able to undo any changes back and also I don't know if you have to reinstall alsa-source every time there is a kernel update! keep this option for last resort before deciding for a complete system reinstall.
the easy way to install alsa-source is to go to synaptic and install only module-assistant, don't install the alsa-source package, let module-assistant do everything for you, run sudo module-assistant in terminal then choose to build alsa drivers, module-assistant will do everything, install, build, and load alsa modules.

---

### Post by psyke83 on 2009-05-17
> **thepeachytricycles said:**
> Deleting my profile didn't work. I also tried another web browser (Galeon) to see if it would work, but again just a dead end.
When I ran as a root sound still did not work. 
By permission do you mean setting the groups and making sure that I have access to the different groups? I have set the permissions to access the groups pulse, pulse-access, and pulse-rt so I am in the group.

If I don't get this soon I will reinstall v8.10 and have done with it.

Please install Flash via the official Ubuntu package (flashplugin-nonfree) and post the following output from this command:

```
$ ldd /usr/lib/flashplugin-nonfree/libflashplayer.so
```

If that file doesn't exist, find the proper location:
```
$ sudo updatedb
$ locate libflashplayer.so
```

Note: if you have multiple libflashplayer.so files on your system, post the output here so that we can see.

---

### Post by kooldino on 2009-05-17
I started having this same issue after I installed adobe nonfree flash player versio 10.  However, I'll occasionally get sound.  It's extremely annoying.

---

### Post by kooldino on 2009-05-19
Bump

---

### Post by rotnacogeid on 2009-05-20
Dear all,

I had the same problem. Here is what I did to fix it.

1. I went to adobe.com to download the latest version of the flash plugin, which as today is:

Adobe Flash Player version 10.0.22.87
Linux 

2. I selected the ".deb for Ubuntu 8.04+" from the drop-down menu.

3. I installed automatically with GDebi.

4. GDebi said that I had the same version installed. I clicked on "Reinstall Package" anyways.

5. I opened a terminal and started a firefox session with sudo:

```
sudo firefox
```

6. I went to [www.youtube.com](www.youtube.com) and started playing one of the videos

7. Back in firefox, I selected the option "Manage content plug-ins" from the Tools menu

8. From the drop-down menu I selected the second adobe flash plugin (I assumed the first one corresponded to version 9 and the second to version 10, which I had just installed)

9. I clicked on the video I was watching with the right button to confirm the plugin version and it was 10 indeed.

10. I closed firefox

11. I started firefox as a normal user (from a gnome menu, no console, no sudo)

12. I went to youtube and I have sound now!

I hope this might help.

Diego

---

### Post by BertP on 2009-06-08
> **kooldino said:**
> I started having this same issue after I installed adobe nonfree flash player versio 10.  However, I'll occasionally get sound.  It's extremely annoying.

I have the adobe flash player installed  and I am getting no sound now BUT if I reboot I get sound from flash and I will  have sound for a few days until it stops.,.   Anyone have any idea what the cause of this problem could be??

(back when I was running 7.10 I used one of the free flash players and did just fine, however many websites require the Adobe one, so  I would really to find the problem)

---

### Post by BertP on 2009-06-08
> **rotnacogeid said:**
> Dear all,

I had the same problem. Here is what I did to fix it.

1. I went to adobe.com to download the latest version of the flash plugin, which as today is:

Adobe Flash Player version 10.0.22.87
Linux 

2. I selected the ".deb for Ubuntu 8.04+" from the drop-down menu.

3. I installed automatically with GDebi.

4. GDebi said that I had the same version installed. I clicked on "Reinstall Package" anyways.

5. I opened a terminal and started a firefox session with sudo:

```
sudo firefox
```

6. I went to [www.youtube.com](www.youtube.com) and started playing one of the videos

7. Back in firefox, I selected the option "Manage content plug-ins" from the Tools menu

8. From the drop-down menu I selected the second adobe flash plugin (I assumed the first one corresponded to version 9 and the second to version 10, which I had just installed)

9. I clicked on the video I was watching with the right button to confirm the plugin version and it was 10 indeed.

10. I closed firefox

11. I started firefox as a normal user (from a gnome menu, no console, no sudo)

12. I went to youtube and I have sound now!

I hope this might help.

Diego

Do you keep your computer on 24/7 I like a do?   If so, after a couple of weeks since a reboot, do you have sound with your flash?

---

