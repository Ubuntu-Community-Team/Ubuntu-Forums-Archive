---
title: "Streaming online vids jerky"
date: 2011-04-26
forum: Multimedia Software
---

### Post by tygsxr on 2011-04-26
Hi can anybody please tell me why some online video players are coming up with just a grey or black screen and the ones that do come i am waiting till they are downloaded(i mean in the scrub bar at bottom of player is full) are playing jerky.. i am using mozilla 3.6.16 with shockwave flash 10.1 and the gnash swf player add-on.I know its not the pc because when i first installed ubuntu about three months ago all sites played fine. i feel it changed after one of the updates. Cheers

---

### Post by Slidemansailor on 2011-04-26
Me too, though I'm just getting started.  I just tried to connect to my online bank and it locked up flashing their picture show at me.  

I suspect it is related to my complete inability to play my Pandora streaming audio which is supposed to be as easy as pie on common flash players.  The Pandora bar gets stuck half way across the loading up phase.

This does nothing nice for my long-term annoyance at Adobe for constantly sending me intermittently destructive updates to the Windows that I finally got fed up with.

Okay, I'm trying to calm down, but I want an alternative flash player to Adobe.  I want them and Microspore to get out of my life altogether.

---

### Post by tygsxr on 2011-04-29
Hey buddy i found a fix for my streaming video problems it was the gnash plugin i had to enter a code into the terminal.. here it is

**sudo apt-get remove gnash && sudo apt-get install flashplugin-installer**

---

### Post by graphius on 2011-05-11
> **tygsxr said:**
> Hey buddy i found a fix for my streaming video problems it was the gnash plugin i had to enter a code into the terminal.. here it is

**sudo apt-get remove gnash && sudo apt-get install flashplugin-installer**

I have tried that as well as a full purge. Firefox says shockwave and flash are installed, but the Adobe site says I need to install the plugin. I used to be able to stream Hockey Night In Canada from CBC.ca, but not anymore...
ARRGH and into the playoffs too....

---

### Post by graphius on 2011-05-14
I fixed my problem. Maybe it will work for you. All I had to do was remove firefox and ubuntu-restricted-extras, then reinstall.

> sudo apt-get remove firefox
sudo apt-get remove ubuntu-restricted-extras
sudo apt-get install firefox ubuntu-restricted-extras

You may also have to remove the hidden folder .macromedia in your home directory

not sure why flash broke, it must have been some legacy code on my system, but it seems to all work now...

---

