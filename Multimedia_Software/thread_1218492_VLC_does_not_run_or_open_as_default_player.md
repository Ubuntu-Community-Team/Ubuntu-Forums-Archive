---
title: "VLC does not run or open as default player"
date: 2009-07-20
forum: Multimedia Software
---

### Post by Danial on 2009-07-20
Hi,
First of all Thanks for looking into this thread.  Before I started this thread, I have searched for VLC issues and unfortunately not able to resolve the problem.  I had tried all steps in the sticky thread "Comprehensive Multimedia & Video Howto" and still did not get anywhere.  So finally, I am here posting this thread hoping to find a way to resolve.  Admittedly, I am a noob and may have done something which I was not to supposed to.:( If I deserve a smack on my head - feel free)

So here is my dilemma..

I have been using VLC without any problem in Jaunty.  However, after some system updates (about 2 months ago), VLC decides to not to open at all.  I can not open any media file (default player - VLC) by right clicking on media file and play with VLC.  I can not open VLC from Applications > Sound & Video > VLC. It appears that it is trying to load and then noting.  Only way (thanks to one of the post here) is to do Alt F2 and type VLC.  But that does not holds any settings or playlist - always have to start from the scratch.  I have tried to do a complete removal and install again to no avail.  After complete removal I ran the command  
sudo apt-get autoclean and autoremove in terminal.  restat PC, Re-install VLC from Synaptic and back to the square one.  System Monitor doe snot show any process for VLC.  By the way, I do have ALSA and Pulse Audio installed (honestly do not hteir use very well).  So what I am doing wrong here and how do I fix it?  If you need some detail information regarding system, please let me know on how to get it and I will get it.  As of now, Software Resources > Third Party Sofware has following repositories: 

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) (jaunty partner)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) (jaunty partner source)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) (jaunty free non-free)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) (jaunty free non-free source)
[http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) (jaunty main)
[http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) (jaunty main source)
[http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) (jaunty main)
[http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) (jaunty main source)

Any help, your time, and guidance all are very appreciated.

Thanks,
Danial

---

### Post by benerivo on 2009-07-20
Have you tried removing the vlc configuration files from your home directory?

---

### Post by mc4man on 2009-07-20
A couple of things, noting I use hardy and no ppa's

I wouldn't mix ppa's for the same app (in this case vlc

So pick either kow or korn, and then disable the other one (System -> Admin. -> Software Sources -> Third party.
Just uncheck the 2 listings for the one your not going to use (at this point not much difference, kow will do minor updates, korn probably not.

Then close, reload.

After that I'd search vlc in synaptic, and remove the 5 core packages - vlc, vlc-data, libvlc2, libvlccore2, and vlc-nox (plus any plugins if any
(right click on package, mark for removal, after all are marked click apply

Then reinstall vlc

for the first start up open a terminal and use this
```

vlc --reset-config --reset-plugins-cache
```

---

### Post by Danial on 2009-07-21
[QUOTE=mc4man;

Then reinstall vlc

for the first start up open a terminal and use this
```

vlc --reset-config --reset-plugins-cache
```[/QUOTE]

Thanks to both of you guys...  

I tried to locate config VLC files in HOME folder (none found).  Un-install and re-installed as Mc4MAN advised.  
Now, I can run the VLC from terminal but not as default player and can not close terminal if I want to keep playing music thru VLC - Pretty much the same as before... Apparently, VLC 1.01 does not like me anymore.  Can I go back and install previous version of it?  CAn anyone step me thru for previous versioninstallation?

I sure appreciate your time.
Danial

---

### Post by anand.vivek on 2009-07-21
Thank you Guys..!!I'm having the same problem as Danial and tat code solved tat within seconds.:P Thanks to mc4man once again:D

---

### Post by benerivo on 2009-07-21
> **Danial said:**
> ...I tried to locate config VLC files in HOME folder (none found)...

Try```
sudo updatedb
```
```
locate vlc | grep /home
```

---

### Post by Danial on 2009-07-21
> **benerivo said:**
> Try```
sudo updatedb
```
```
locate vlc | grep /home
```

I see, I did miss few files.  I deleted all of those, ran the command to reset the config, VLC started from terminal.  With not much of hope, quit from terminal and tried to open from Application > Sound & Video > VLC
 Viola  so the VLC came up running...  closed there, from the browser, double click on the media file and yes I am back in business...   

[COLOR="Green"]**[FONT="Trebuchet MS"][SIZE="7"][SIZE="6"][SIZE="5"]THANK YOU VERY MUCH for HELP and Guidance...[/SIZE][/SIZE] [/SIZE][/FONT]**[/COLOR]


:popcorn:

---

