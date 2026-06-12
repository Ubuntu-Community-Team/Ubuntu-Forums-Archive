---
title: "Flash (YouTube) = Solid Black Screen."
date: 2008-07-09
forum: Multimedia Software
---

### Post by Roasted on 2008-07-09
Four hours ago, I was sitting here installing themes from gnome-look.org and listening to videos on YouTube.

I left. Watched a movie. Came back.

I began looking over more themes from where I left off. I went to YouTube, put on a video, and noticed it didn't load. I have a solid flash screen in place of the video. No controls, no message, just... it's just there.

I have Ubuntu Hardy Heron 8.04 64 bit edition installed.
Flash 9 plugin installed.
I also reinstalled Flash 9 through Synaptic. No difference.

---

### Post by Roasted on 2008-07-09
Easiest fix ever. I simply rebooted Firefox.

What would cause this to happen? Anybody have an idea?

(I was going to delete the thread but figured I'd let it stand for future reference to others).

---

### Post by k1ngb0b0 on 2008-10-12
> **Roasted said:**
> Easiest fix ever. I simply rebooted Firefox.

What would cause this to happen? Anybody have an idea?

(I was going to delete the thread but figured I'd let it stand for future reference to others).

I have the exact same problem and rebooting DOES fix it.

Did you ever find out the cause of it?  I don't mind rebooting firefox but it's kind of annoying when I have several tabs open (I multi-task).

---

### Post by nerktord on 2008-10-12
This is probably due to a problem with the flash-plugin. I know they've had some problems in the past, which caused the flash player to frequently crash the browser, or not load correctly. Apparently it's fixed now. Personally I haven't come across a single crash for awhile.

---

### Post by SeePU on 2009-02-28
How do you 'reboot' Firefox?!?  Do you mean reboot your system or 'quit' Firefox and start it again?

---

### Post by SeePU on 2009-02-28
I re-started Kubuntu.   No change.  I then rebooted the computer.   Again, no change, I get the black screen when trying a Youtube video.  

:mad:

---

### Post by SeePU on 2009-02-28
I googled and also found the answer from the Ubuntu forums!

Damn it!!!!!!!   I had installed the 'Flashblock' feature and I didn't realize when you have it enabled (because you want a *SPECIFIC* web page not to play the flash part), IT THEN DISABLES FLASH FOR ANY OTHER WEB PAGE (including YouTube)!   Is there no way to set it for specific pages?   Just asking generally, now... I will look it up.   But, duh!!!!!  #-o

---

### Post by mtech84 on 2009-08-21
whats this only youtube videos are not playing.... rest i can play...

system is ubuntu 9.04 32bit... tell me what to do...

i am using flash free plugin.... 

why youtube god please help....

---

### Post by crabsody on 2009-10-17
I got the same problem. Sometimes works ok but if I watch some videos then it goes black again!!! Any ideas?

---

### Post by Radissthor on 2009-10-20
I have the same problem. Only a black screen shows on youtube. I have no problem with other web pages.... Please, please!! any help?

---

### Post by Radissthor on 2009-10-21
I finally found the solution in another post. 

Just go to [http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004)

click ctrl+F and type FOT004

There you'll find the following code for the terminal:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

That does it. You have to restart Firefox and youtube will be playing perfectly.

---

### Post by karrank% on 2009-10-24
> **Radissthor said:**
> I finally found the solution in another post. 

Just go to [http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004)

click ctrl+F and type FOT004

There you'll find the following code for the terminal:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

That does it. You have to restart Firefox and youtube will be playing perfectly.

fixed it for me, thanks Ubuntu Community!

---

### Post by princeza on 2009-10-25
> **Radissthor said:**
> I finally found the solution in another post. 

Just go to [http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004)

click ctrl+F and type FOT004

There you'll find the following code for the terminal:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

That does it. You have to restart Firefox and youtube will be playing perfectly.

Thanks a lot. Worked like magic.

---

### Post by oe1ssu on 2009-11-08
Worked perfect!

Thanks!

---

### Post by hoss2001 on 2009-12-31
There's another cause for this problem.  I was having a blank screen with certain flash movies (not sites) using flash player 10.0.32. I didn't have flashblock installed or multiple flash installs. What I discovered was that there are some flv files that require the latest version of flash player. I'm running 10.0.42.34 and everything works.

---

### Post by Jetro on 2011-03-02
Still an issue here with Opera 11 in Ubuntu 10.10

So much for the future :3

---

### Post by tivrfoa on 2011-09-13
Open a new window worked here.

---

### Post by gbgustafson on 2012-05-24
The[B] flash video black screen problem with Ubuntu Maverick 10.10 and Firefox 12.

[/B]The problem started when I changed from 2009 hardware to a 2006 motherboard. 

Version 11 flash-installer (2012) was installed automatically in updates and it broke YouTube video and other internet sites with flash video sources.

 All the internet advice about removing plugins and extensions in firefox Ver 12 failed to help. Re-installing flash-installer also failed to help (there were 3 ways to do that!).  Old versions of firefox did not change the situation, still a black screen on certain YouTube (flash) videos.

The hardware issue meant that ver 11 flashplugin should be removed and go back to ver 10, which worked a year ago on the old hardware. Doing just that alone had some effect, but it was unreliable, due to "missing plugin" messages from internet sites.

**The final solution**:

1. **CLEAN-UP**.
sudo apt-get --purge remove adobe-flash-properties-gtk 
sudo apt-get --purge remove adobe-flashplugin browser-plugin-gnash 
sudo apt-get --purge remove gnash gnash-common mozilla-plugin-gnash; 
sudo apt-get clean; 
sudo apt-get update

2. **UNINSTALL** with  synaptic package manager.
 flashplugin-installer   

3.** INSTALL** with synaptic package manager.
flashplugin-installer                             10.1.85.3ubuntu1

 This was tricky. Search for "flashplug" in synaptic. There are four matches. Click
on flashplugin-installer. Go to the "**package**" menu in synaptic and click on "**force** **version**."  A window appears. Click to select version 10. Then mark it to install.
Finally, install ver 10 of the flashplugin-installer.

4. **LOCK VERSION**. 
 In synaptic, lock version 10.1.85.3ubuntu1 of flashplugin-installer
 In detail, highlight flashplugin-installer (ver 10), then go to the "package" menu and  click on "lock version."
   
5.** EDIT** /etc/adobe/mms.cfg

 sudo gedit /etc/adobe/mms.cfg
  Create mms.cfg if it does not exist, including the directory.
  Add these contents to the end of the file.

OverrideGPUValidation=true
# Lets you prevent Flash Player from automatically checking for and installing
# updated versions.  0 = Not Disabled (default), 1 = Disabled
# Gets rid of "missing plugin" fatal error message
AutoUpdateDisable = 1

6. **TEST FIREFOX**.

Enable flash in firefox "add-ons" menu. Disable everything else, including extensions.
Turn them back on one at a time, after firefox is playing flash videos with no black screen. ;)

---

### Post by Burt47 on 2012-05-31
Hello all,

I get the black box screen on you tube on most vids on you tube.
Occasionally one will work.  I have removed and reinstalled 
adobe many times but it still does not work properly.  I'm at an impasse...
Any ideas out there?

                                                        Burt47

---

