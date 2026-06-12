---
title: "Mythtv and using update manager to get to Hardy"
date: 2008-04-24
forum: Multimedia Software
---

### Post by NTolerance on 2008-04-24
Set up my Mythtv box exactly one year ago with a clean install of Feisty.  Used update-manager to successfully upgrade to Gutsy last October.  Now it's time for another upgrade.  Anyone have success doing something similar with Hardy?  I know there's gonna be some "cruft" as people say, but the whole MySQL aspect of Mythtv is quite daunting to me, which is why I'd like to do an upgrade instead of a clean install.  Suggestions?

---

### Post by NTolerance on 2008-04-25
bump

---

### Post by NTolerance on 2008-04-29
bump

---

### Post by jeremybear on 2008-05-01
I would advise that you wait a while, perhaps until 8.10 is released.

Gutsy was working great for me, but the Hardy upgrade caused quite a few problems, some of which I have not yet found a solution for:
* Customized Hauppauge Remote Control config. broke - lirc is set up differently, and I haven't figured it out yet
* System generates spurious keypresses in Live TV: very annoying
* NVidia Quadro card needed reinstallation
* Mini-PCI Atheros WLAN card needed reinstallation
* AverMedia Volar USB driver (or related problem) has increased the lock time on weak/co-channel interfered DVB channels from 3 sec to 30 sec.

In other words, quite a piece of work, and my wife is not happy!
("Why do you need to upgrade anyway?")

---

### Post by NTolerance on 2008-05-02
> **jeremybear said:**
> I would advise that you wait a while, perhaps until 8.10 is released.

Gutsy was working great for me, but the Hardy upgrade caused quite a few problems, some of which I have not yet found a solution for:
* Customized Hauppauge Remote Control config. broke - lirc is set up differently, and I haven't figured it out yet
* System generates spurious keypresses in Live TV: very annoying
* NVidia Quadro card needed reinstallation
* Mini-PCI Atheros WLAN card needed reinstallation
* AverMedia Volar USB driver (or related problem) has increased the lock time on weak/co-channel interfered DVB channels from 3 sec to 30 sec.

In other words, quite a piece of work, and my wife is not happy!
("Why do you need to upgrade anyway?")

Thank you very much for your feedback.  I spent a lot of time configuring lirc so I will hold off per your advice.  Funny to see how many posts about mythtv are accompanied by a comment about a significant other.  My girlfriend uses it more than I do so any technical issues are mission critical around my household.  And upgrades are definitely met with resistance.  :lolflag:

Does the version of mythtv included with Hardy offer any notable features over the Gutsy version?

---

### Post by jeremybear on 2008-05-03
The new version of MythTV (0.21) on Hardy includes:

* Autodiscovery - if you have a frontend on another PC, it will find the backend server automatically
* Storage groups - very useful if you want to store your recordings across several hard drives
* Multiple recordings on one DVB multiplex - you can schedule recording of one programme immediately after another without being told there is a "conflict"
* New deinterlacing options - hmm.. these cause more trouble than they are worth; see [http://www.uluga.ubuntuforums.org/showthread.php?t=723345]("http://www.uluga.ubuntuforums.org/showthread.php?t=723345")

Anothing thing to be aware of is that if you are running a MythTV frontend on another PC (to watch TV in another room, for example) you must have the same version of MythTV on the backend server.  That's how I got into this mess in the first place: I upgraded my frontend machine to Hardy with no problems at all, until I started mythfrontend, when it said something like "You are running Protocol 40 and the server you are trying to connect to is running Protocol 32".  
Then I upgraded the backend machine (bleeding edge AMD64, dual core, restricted drivers, etc.) and wished I hadn't!!

---

