---
title: "Ubuntu 11.04 beta2 64-bit installer is crashing midway"
date: 2011-04-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by wrldwzrd89 on 2011-04-15
Title says it all, really. The installer is crashing midway through the install process - which has left the computer in an unbootable state. What's happening is this: First time, I clicked Try Ubuntu. That worked. Experimented with a few things, then clicked Install. The Installer started, and began copying files... then my computer suddenly rebooted without my doing anything, during the file copy process. So, I tried again, this time clicking Install Ubuntu instead of Try Ubuntu. Same problem (spontaneous reboot), but it occurred a lot sooner - before I could click anything else.

Such a shame... I really wanted to try Ubuntu 11.04 but if it won't even install, I can't.

---

### Post by VMC on 2011-04-15
> **wrldwzrd89 said:**
> Title says it all, really. The installer is crashing midway through the install process - which has left the computer in an unbootable state. What's happening is this: First time, I clicked Try Ubuntu. That worked. Experimented with a few things, then clicked Install. The Installer started, and began copying files... then my computer suddenly rebooted without my doing anything, during the file copy process. So, I tried again, this time clicking Install Ubuntu instead of Try Ubuntu. Same problem (spontaneous reboot), but it occurred a lot sooner - before I could click anything else.

Such a shame... I really wanted to try Ubuntu 11.04 but if it won't even install, I can't.

Is this a Manual install or install along side? If you have your partitions setup before hand then use the Manual install it should work.

I don't know about using the other installs as I always use the Manual installs.

---

### Post by sanguinoso on 2011-04-15
My process for testing the new releases is to install them in a virtual machine so you don't leave your machine in an unbootable state. Unfortunately as it is still a beta release all the issues haven't been worked out yet and this could just be a bug. Have you searched on launchpad? If you can't find a similar bug to yours it might be a good idea to report it at [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu). If you do this remember to include your system specs and exactly where it failed.

---

### Post by wrldwzrd89 on 2011-04-15
YES! 3rd try's the charm, it didn't crash - installed successfully.

---

### Post by Blasphemist on 2011-04-15
So let me start with the fact that I've installed this without issue and a few questions please. When you selected try Ubuntu did you do anything after the desktop came up? Just might help to know if it was really running well. After you chose to install, were you connected to a network? If you weren't wired to one, did you connect to a wireless net? Did you choose to download updates while installing and did you choose to install 3rd party software (FluendoMP3 Plugin)? 

Did you get to the allocate disk space prompt and if so what did you choose? Was this your first installation of Ubuntu or was this to be an upgrade? You'd have been asked about upgrading or replacing your existing install or using the whole drive or choosing options manually. Did you get to this and if so what did you choose? If you got past this, did you enter a name and password? Did you choose a location and keyboard layout? Was the slideshow playing that plays during download of files?

Let's start with these. We'll need to know details of when and what it may be doing to know where to start.

---

### Post by wrldwzrd89 on 2011-04-16
Here's the options I used that finally worked:

Do NOT download updates while installing
Do NOT install this 3rd party software

Connected to a wired network (the computer I'm installing it on has VERY unreliable wireless).
Wiped the whole drive clean for the install, each time. Let Ubuntu decide what the partition scheme should be.
First time it crashed, I got past all the user input screens, and it died just as the slideshow was about to advance to slide 2.
Second time, the crash happened almost immediately after clicking "Install Ubuntu" on the very first screen after it boots.
Third time, it installed okay (YAY!) but is still quite unstable, and exhibits the spontaneous reboot behavior at seemingly random times. For example, it rebooted on its own while I was trying (and failing) to figure out how the heck you restore your files from a Back in Time backup after upgrading the OS.

---

### Post by kansasnoob on 2011-04-16
It may help to gather some system hardware info:

```
lspci | grep VGA
```

&#65279;```
cat /proc/cpuinfo | head -10
```

```
free -m
```

---

### Post by wrldwzrd89 on 2011-04-16
Yeah, I would if I hadn't given up on this. *sigh*

---

### Post by kansasnoob on 2011-04-16
> **wrldwzrd89 said:**
> Yeah, I would if I hadn't given up on this. *sigh*

You could do that just using the terminal in a live session, no need to install :)

Pretty much any Linux live CD/USB should work.

---

