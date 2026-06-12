---
title: "sound stopped working in 11.04"
date: 2011-05-02
forum: Multimedia Software
---

### Post by chris_vs on 2011-05-02
in 10.10 my internal audio and my external usb 5.1 soundcard worked fine, and everything was still ok after i upgraded to 11.04. i then tried to install an equaliser called "alsaequal" which required the alsa-driver-1.0.24 package, which i compiled ok. now i've lost all sound and can only see dummy output listed in sound preferences, and no hardware is detected. 
sudo aplay -l doesn't detect anything either! i've folled all the steps on the sticky thread in multimedia, i tried purging and reinstalling all the alsa packages which didnt work, and then tried compilling alsa source packages, which wound up with errors. i was following this thread: [http://ubuntuforums.org/showthread.php?t=1725874](http://ubuntuforums.org/showthread.php?t=1725874) which suggested running the alsa-info.sh script. i ran this and uploaded the output here: [http://www.alsa-project.org/db/?f=cf43db194d49896b16c94e6f71961380d1e9d23f](http://www.alsa-project.org/db/?f=cf43db194d49896b16c94e6f71961380d1e9d23f)
i dont really understand any of this, but it seems to have detected my internal pci card but not my usb card.
any help would be really appreciated after the hours spend fruitlessly trawling through these forums!
cheers

---

### Post by chris_vs on 2011-05-02
anyone?

---

### Post by chris_vs on 2011-05-02
bump

---

### Post by chris_vs on 2011-05-03
can no one here help at all??

---

### Post by lidex on 2011-05-04
Your alsa driver is not installed correctly. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by chris_vs on 2011-05-07
that worked great cheers...although i feel sure i've tried that command before! its a common one that others have suggested in various other threads/forums, although i think i tried it before with apt-get rather than aptitude...would this make much difference?

---

### Post by lidex on 2011-05-08
Aptitude is a little more intelligent in handling dependencies, etc. Also that command handles modules and libasound, which the other version does not.

---

### Post by sleekweasel on 2011-12-06
Trying to apply that solution, it complained that it couldn't find the kernel module (I'm on a 64 bit kernel, does that make a difference?) and more worryingly, this:

$ sudo apt-get install --reinstall libasound2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/417 kB of archives.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for libasound2

I resolved this with this - in case it helps someone else:

 sudo dpkg -i /var/cache/apt/archives/libasound2_1.0.24.1-0ubuntu10_amd64.deb

I'm still concerned that my apt is screwed somehow though - I'm not sure where to report that, since it seems like a config issue on my machine rather than a generally applicable bug.

---

### Post by rybu on 2012-01-25
> **sleekweasel said:**
> Trying to apply that solution, it complained that it couldn't find the kernel module (I'm on a 64 bit kernel, does that make a difference?) and more worryingly, this:

$ sudo apt-get install --reinstall libasound2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/417 kB of archives.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for libasound2

I resolved this with this - in case it helps someone else:

 sudo dpkg -i /var/cache/apt/archives/libasound2_1.0.24.1-0ubuntu10_amd64.deb

I'm still concerned that my apt is screwed somehow though - I'm not sure where to report that, since it seems like a config issue on my machine rather than a generally applicable bug.

Did you ever figure out what this problem was?  I seem to be having the same one.  But your suggestion doesn't seem to be resolving the issue. :(

---

### Post by FlyWheel on 2012-01-26
I get the same result with reinstall. I am on 11.10 and have new usb Bose companion 5 speakers.  On reboot I can get the test speakers to work, but the default changes back to internal analog from the bose usb every time I open the sound control. As soon as I try to run something with sound, like movie player, the sound quits working and it will not start working again until reboot.  I have changed the alsa-base.conf to have :options snd-usb-audio index=-1 and removed the last 2 lines so that it can become the default, but it makes no difference.  Anyone know what's up?

---

### Post by rybu on 2012-01-29
Similar but unresolved thread: [http://ubuntuforums.org/showthread.php?t=1915782](http://ubuntuforums.org/showthread.php?t=1915782)

---

