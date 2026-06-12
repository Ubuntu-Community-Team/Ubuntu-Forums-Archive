---
title: "Amarok won't play audio CD"
date: 2010-02-27
forum: Multimedia Software
---

### Post by wagoner on 2010-02-27
I installed Karmi Koala Kubuntu 9.10 a few months ago, but I haven't found a way to play my audio cd's.  Amarok used to play them when I used Kubuntu 7.10, but not with the latest install.  I can launch Amarak, and I can select Amarok --> Play Media from the menu and I can see my CD and the tracks in the directory.  I can click OK or select a track, but nothing happens.

I have been able to play a few mp3 files that I downloaded to the hard drive with Amarok, so the sound works.  could it be that it can't play the .wav format?

---

### Post by mc4man on 2010-02-27
While may be of no value - I use gnome and amarok 1.4 (pana), but what happens if you click on "Local Music" and then click on  Audio Cd and load/play from there?

---

### Post by wagoner on 2010-02-27
I can't find "Local Music", but I was able to select directories from the Settings --> Configure Amarok in the menu.  I selected my CD rom and it caused it to spin up.  It didn't load the tracks into the playlist however.  

Amamok finally crashed.  I got this error message.
> Application: Amarok (amarok), signal: Segmentation fault
[Current thread is 1 (Thread 0xb787b710 (LWP 6738))]


---

### Post by mc4man on 2010-02-28
Went ahead and installed it on my karmic install and it's there (local music, ect. ) but seems very easy to crash. 
Once it crashes the audio cd disappears from amarok 2 till you eject the disk and re-insert.
Have it on a lucid tester where it works a bit better - more recent version.

Personally find 1.4 or the pana redo much more suitable, [easy to build]("http://ubuntuforums.org/showthread.php?t=1400314&page=2") or use [the ppa ]("https://launchpad.net/~bogdanb/+archive/ppa")for the amarok14 version.

Any way a few screens

---

### Post by wagoner on 2010-02-28
Thank you for all of the help.  I haven't figured out how to install amarok14 yet.  Do I need to uninstall amarak 2.2.0 first?  I added the source with the key.

```
adam@dell16:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AE74AE63                            
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys AE74AE63        
gpg: requesting key AE74AE63 from hkp server keyserver.ubuntu.com                                                      
gpg: key AE74AE63: public key "Launchpad PPA for Bogdan Butnaru" imported                                              
gpg: Total number processed: 1                                                                                         
gpg:               imported: 1  (RSA: 1)                                                                               
adam@dell16:~$ sudo apt-get update          
```

I'm guessing that I need to sudo apt-get uninstall amarok
and then sudo apt-get install something else?

---

### Post by mc4man on 2010-02-28
I've never used the ppa, but taking a glance I see that he now suggests using his amarok14 ppa instead.

[https://edge.launchpad.net/~bogdanb/+archive/amarok14/](https://edge.launchpad.net/~bogdanb/+archive/amarok14/)

Anyway from a konsole this would take care of

```
sudo apt-get update && sudo apt-get remove amarok && sudo apt-get install amarok14
```

---

### Post by wagoner on 2010-02-28
Amarok14 wasn't found with the ppa or the key or whatever, so I added the 
```
deb http://ppa.launchpad.net/bogdanb/amarok14/ubuntu karmic main 

```
from above to the sources.  I uninstalled amarok first, Kpackagekit gave me a dependency error, so I then I tried
```
sudo apt-get install amarok14
```
It ran for several minutes and that gave me another error.  I looked at the other install method (build from source?), but it might be too difficult for me.  Maybe I will try when I have more time.

Should I just install another player?  I guess nobody actually plays CD's anymore.

---

### Post by wagoner on 2010-03-27
The system had broken dependencies after the attempted install of amarok14.  That has been fixed.  Today I installed banshee, and it plays my audio CD's without problems.  Problem solved.:)

---

