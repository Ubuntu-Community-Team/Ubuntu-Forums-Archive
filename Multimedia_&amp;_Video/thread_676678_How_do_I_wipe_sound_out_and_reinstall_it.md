---
title: "How do I wipe sound out and reinstall it?"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by nethbar on 2008-01-24
I have a thread up here:
[http://ubuntuforums.org/showthread.php?t=674709](http://ubuntuforums.org/showthread.php?t=674709)
about being unable to get my sound to play.  I'm wondering if it just might be easier if I could clean out my sound altogether (configuration, modules, etc.)

How can I thoroughly clean out my sound settings so I can do a clean installation?

---

### Post by renzokuken on 2008-01-24
have you tried installing the latest alsa packages from source?

get them from the alsa site then compile then to upgrade alsa to the latest version. worth a try, its how i got my sound working.

any ideas what sound chipset you have?

---

### Post by nethbar on 2008-01-24
I have a Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01) (according to lspci).  The modules are all loaded as they are on the Live CD (which has working sound) but it may be that some upgrade clobbered my sound.

I've never compiled anything from source before.  Can you point me someplace to get me started?

Thanks

---

### Post by mad_max0204 on 2008-01-24
Just download. There is a readme file in the package. Also there is a full documentation on alsa page.

---

### Post by Yellow Pasque on 2008-01-24
Before building from source, try:
> sudo dpkg-reconfigure alsa-base

---

### Post by renzokuken on 2008-01-25
> **nethbar said:**
> 
I've never compiled anything from source before.  Can you point me someplace to get me started?

Thanks

compiling the alsa packages is actually fairly simple. first run the following to install all the tools for compiling source code

```
sudo apt-get install build-essential
```

now, (i'll use the **alsa-driver** source code as an example here) download the latest source tarball from [www.alsa-project.org](www.alsa-project.org) (look top right corner of page) and save it to your home folder.

open a terminal and extract the tarball using

```
tar xjf alsa-driver-1.0.15.tar.bz2
```
enter the folder you just extracted by running
```
cd alsa-driver*
```
now all is left to do run the following 3 commands to compile the source code, waiting for each to finish before starting the next

```
./configure
```
```
make
```
```
sudo make install
```

when all is finished, you have successfully compile alsa-driver. reboot and see if your sound works. you could also then do the same to install alsa-utils, alsa-lib etc etc

---

### Post by Yellow Pasque on 2008-01-25
The above procedure has been scripted for you.
Run the two scripts found in this post. (reboot in between as instructed)
[http://ubuntuforums.org/showpost.php?p=3603812&postcount=13](http://ubuntuforums.org/showpost.php?p=3603812&postcount=13)

---

### Post by nethbar on 2008-01-28
Wow!  Thanks for the fantastic response!  I'll post back with how it all goes.

---

### Post by nethbar on 2008-02-05
FIXED (?):  Woo-hoo.... kinda....
I think the sequence of events went something like this:
- Made system changes, hibernated system
- Powered system back on, discovered sound no longer worked, assumed system changes the cause
- Tried to troubleshoot sound problems myself, stuck
- Posted here, received excellent help (THANK YOU for all of the excellent, guided steps that were posted.  I've run in to sound issues a lot when trying out Linux and it's made it hard.  Your advice will make it easier to try out more hardware and help others with it too)
- Read over solutions, got busy
- Finally rebooted to start fixing and discovered sound works fine on a full reboot

So I guess I'm facing an APM/ACPI issue? It's never worked quite right; I can manually hibernate or standby but letting the laptop do it on its own causes problems. I'll bring it back up, the login screen comes up but within seconds the laptop powers off. When I power it back on, Ubuntu loads just like I was coming out of hibernation only there's no login screen and poof, there's all my open work.

When I hibernate, there's a sound related error I've caught:

**cs46xx: failure waiting for FIFO command to complete**

but I don't know where to look for a complete log. Searching elsewhere hasn't turned up anything helpful.

Trying to come out of standby or hibernate is impossible with a my PCMCIA wireless card plugged in (Linksys job using ndiswrapper). It will either hang or... hang I guess. It doesn't seem to matter if I powered down with the card in or not.

Any advice?  Should I move my post or could sound be causing the power hangup instead of the reverse?

---

