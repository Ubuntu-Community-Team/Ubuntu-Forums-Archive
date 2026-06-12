---
title: "Ubuntu does not recognize the dvd player"
date: 2011-10-06
forum: Multimedia Software
---

### Post by weezyrider on 2011-10-06
I can't seem to get ubuntu to recognize the dvd player. I read everything I can find and it still says unknown, unknown type, unknown everything. I'm just playing with a DVD recorded OTA. I'm trying to set up the dvd recorder to record from a movie camera, but I have to get the disk to play! I can't use the computer since the camera is IEEE1394 and I don't have a card for that plug.
The drive doesn't play audio very well either. Tried media player and vlc. Very choppy.

I'd like to get this working as we have Hi8 tapes we'd like to convert.

---

### Post by Rodney9 on 2011-10-06
This may help - 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by WasMeHere on 2011-10-07
Try this thread: [_[COLOR="Red"]Comprehensive Multimedia & Video Howto[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=766683").
It may take some time to do the tasks in the first post 'the how-to', but the result is very good, you will get a solid multimedia system.

Good luck
Olle

---

### Post by mörgæs on 2011-10-07
Changed the title to a more descriptive one.

---

### Post by weezyrider on 2011-10-07
Both players work in windows XP. It's Ubuntu, as Ubuntu is on it's own hard drive, not partitioned with windows. I prefer dual booting through either the bios or grub.

I found some of the files, software said they were installed. The CD was choppy since it was a copy. I have a player and a reader/writer - both dvd.
Ubuntu doesn't even recognize the reader. It will finally find the reader writer.

---

### Post by WasMeHere on 2011-10-07
I think it is like this:

Ubuntu is not delivered with full multimedia support because some of the software needed is property of companies, that do not allow distribution the Ubuntu way. However you are allowed to download such software to your computer, and Ubuntu provides ways to do it. You do this using the *Comprehensive Multimedia & Video Howto* that I described and linked to in my previous post. Try it and come back if you still have problems!

Good luck
Olle

---

### Post by weezyrider on 2011-10-07
I've printed everything out, copied and pasted commands, and get unable to locate package. free or non free. I'm using 10.10. I assume that's maverick? It says I got medibuntu. Universe, it can't find multiverse. 

E: Unable to locate package multiverse-keyring
E: Type '<html><!--' is not known on line 1 in source list /etc/apt/sources.list.d/multiverse.list
E: The list of sources could not be read.

Wgere do I go from here?

---

### Post by hyper2hottie on 2011-10-07
Post your the contents of 
/etc/apt/sources.list 
and
 /etc/apt/sources.list.d/multiverse.list

---

### Post by WasMeHere on 2011-10-08
Or try to use the GUI frontend *Synaptic*

In Synaptic select the menu 'Settings' -- 'Program Sources' and tick multiverse. Then you update and should have access to the programs and libraries in multiverse.

Maybe you will succeed on your own. Otherwise do what is suggested by hyper2hottie.
> **hyper2hottie said:**
> Post your the contents of 
/etc/apt/sources.list 
and
 /etc/apt/sources.list.d/multiverse.list

---

### Post by weezyrider on 2011-10-10
Synaptic won't open. Get this:

E: Type '<html><!--' is not known on line 1 in source list /etc/apt/sources.list.d/multiverse.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
 Now what?
I have no idea where to find those contents

---

### Post by weezyrider on 2011-10-10
Update manager no longer works, either

---

### Post by weezyrider on 2011-10-10
Neither does Ubuntu software center

---

### Post by weezyrider on 2011-10-10
I just posted this on general. I found some multiverse files. Opened multiverse.list and got

[I]Overview

Purpose

The goal of the Pediatric Perioperative Cardiac Arrest (POCA) Registry is to collect a large set of cases of cardiac arrests and deaths of pediatric patients during the administration of or recovery from anesthesia in order to investigate the possible relationship of anesthesia to these incidents.
[/I]

Looks like this might be part of the hmtl error. Please advise

---

### Post by WasMeHere on 2011-10-10
> **Olle Wiklund said:**
> Try this thread: [_[COLOR="Red"]Comprehensive Multimedia & Video Howto[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=766683").
It may take some time to do the tasks in the first post 'the how-to', but the result is very good, you will get a solid multimedia system.

Good luck
Olle
Maybe you have to do some cleaning first. Will you get satisfactory answers or some indication of errors running this?
```
sudo apt-get update
sudo apt-get upgrade
```
Please post the output!

---

