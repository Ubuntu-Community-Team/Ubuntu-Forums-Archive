---
title: "No Soundcard detected after install from update manager"
date: 2010-09-01
forum: Multimedia Software
---

### Post by B-Mart on 2010-09-01
Okay, well, as it goes, I was listening to music and decided to check update manager, and after the install I reboot and then POOF, sound is gone, I checked Alsamixer and got "no such file" did aplay -l and got that there was no soundcard found, which I officially can say is bull, since, I DO have a card, hahaha.  I am running a HP G72 and already went through the comprehensive check and kinda got with seeing which driver matched my card...so...yeah...any help would be stellar



*EDIT*
heres some info I forgot to post

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 1484
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d4500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

```

I tried lspci | grep audio, but got nothing

---

### Post by B-Mart on 2010-09-01
maybe I have to just reinstall Alsa 1.0.23-2....


nvm...I have no soundcard detected...

---

### Post by Yoh on 2010-09-01
I have the same problem. Installed updates from update manager, rebooted, and now no sound. "No sound cards detected". 

Sound card is physically installed and recognized by hardware

CODE: 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at f8100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

I am new to Linux (migrated from XP), any help would be appreciated.

---

### Post by B-Mart on 2010-09-01
Dude!  Just got it to work by myself.  Hope you subscribed. 

I just recently moved from XP myself. but yeah.  What I did was just re-updated Alsa, if you had to, you probably still have the files yes?

Then all you have to do is
```
sudo ./AlsaUpgrade-1.0.23-2.sh -d
sudo ./AlsaUpgrade-1.0.23-2.sh -c
sudo ./AlsaUpgrade-1.0.23-2.sh -i 
```

What happened to me was that I guess it wiped my Alsa files because it said it wasn't found after update and restart...If that works let me know, I'm sure I could think of some way to help further.

Good luck!

Quick note actually, make sure to post code between the /code brackets, it saves on forum space...so just use the # sign in the toolbar when you post code :D

---

### Post by Yoh on 2010-09-02
Alright i have probably done something to make matters worse cause its still not detecting my sound card. Is there a way to completely remove and reinstall ALSA?

[http://www.alsa-project.org/db/?f=9a1fd1a7a353dfe8c66e5bfa490757b69ec3108e](http://www.alsa-project.org/db/?f=9a1fd1a7a353dfe8c66e5bfa490757b69ec3108e)
[FONT=Verdana]So two things I notice: 1) no loaded ALSA modules 2) mismatching versions of ALSA utilities

Any help would be appreciated...[/FONT]

---

### Post by w1ntermute on 2010-09-02
> **B-Mart said:**
> Dude!  Just got it to work by myself.  Hope you subscribed. 

I just recently moved from XP myself. but yeah.  What I did was just re-updated Alsa, if you had to, you probably still have the files yes?

Then all you have to do is
```
sudo ./AlsaUpgrade-1.0.23-2.sh -d
sudo ./AlsaUpgrade-1.0.23-2.sh -c
sudo ./AlsaUpgrade-1.0.23-2.sh -i 
```What happened to me was that I guess it wiped my Alsa files because it said it wasn't found after update and restart...If that works let me know, I'm sure I could think of some way to help further.

Good luck!

Quick note actually, make sure to post code between the /code brackets, it saves on forum space...so just use the # sign in the toolbar when you post code :D

I experienced the same problem after the update, but running the upgrade script again as described here sorted it right out.

Thanks!

---

### Post by Yoh on 2010-09-02
I tried it and got "command not found" ??

---

### Post by B-Mart on 2010-09-02
Okay, some basics that I didn't understand when I started is that all file and run commands are all case sensitive, so if there was a mis-capitalization then it would throw the whole program off.  Since it was "Command not found" and not "Files not found" I would assume this is the problem...if not, let me know.  Also, make sure you have those alsa update files that I am talking about...to get them go to this link

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
and follow the directions, if you need help, just let me know :D


you also may want to un-install then re-install alsa first before running the updates.
This is a wee bit more complicated and I only recommend if re-installing the updates is a failure.

**for removing old/conflicting files**
```
rm -r ~/.pulse ~/.asound*
sudo rm/etc/asound.conf
```
Reboot, log in.

Then, Re-Install Alsa.
```
sudo apt-get update
sudo apt-get upgrade
```

```
sudo apt-get purge linux-sound-base alsa-base alsa-utils
```

```
sudo apt-get purge linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
```

You want to re-install gdm and desktop because sometimes the purge wipes them and...yeah, thats more than a headache...trust me.
**then reboot**

then check alsamixer and aplay -l to see if it's found...if it is, HURAY...if not, re-install the update and such and check again.  Thats about all I can say, if you still have trouble, let me know and I can probably think of something else. :D

---

### Post by lidex on 2010-09-03
For those who have used the alsa-upgrade script:
> Ubuntu upgrades/updates might overwrite your Alsa installation once in a while (e.g. Major upgrades, kernel-upgrades or ALSA-package upgrades).
You just need to rerun the upgrade-script using the -i option in this case (if you still have the compiled sources on the disk). 

So is B-Mart better than K-Mart ;)

---

### Post by Yoh on 2010-09-03
All is good in the world, I have sound..

It turned out I didn't have the ALSA update files after all.

Thanks for your help

---

### Post by morealaz on 2010-09-03
you can visit this page:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

you find very good information there for solving your problem:popcorn:

---

### Post by B-Mart on 2010-09-03
Nooo problem, so i'm just mark this one [solved] and stuffs.

---

