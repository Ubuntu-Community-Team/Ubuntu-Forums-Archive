---
title: "Sound Amoung Multiple Users When Using sudo or gksu Fails"
date: 2016-12-12
forum: Multimedia Software
---

### Post by kevin77v on 2016-12-12
I run multiple instances of Firefox(and other apps), each with it's own separate user account, loaded via sudo or gksu.   Previously, each instance of FIrefox would be able to play sound.  Then, I was running a Java based game using Oracle's Java runtime environment while watching videos with one of the Firefox accounts.  During this, the sound stopped functioning in this account.  Now, sound does not work in any accounts run with sudo or gsku.  Digging, I'm thinking that this is a sound server permissions issue.  I'm using PulseAudio.  For instance,  if I run   ```
aplay -l
```  as my normal account, I get:  ```
**** List of PLAYBACK Hardware Devices **** card 0: Intel [HDA Intel], device 0: STAC9200 Analog [STAC9200 Analog]   Subdevices: 1/1   Subdevice #0: subdevice #0 card 0: Intel [HDA Intel], device 1: STAC9200 Digital [STAC9200 Digital]   Subdevices: 1/1   Subdevice #0: subdevice #0
```  Running as another account:  ```
sudo -u otheruser aplay -l
```  I get:  ```
[sudo] password for mainuser: aplay: device_list:268: no soundcards found...
```   So, it seems the other users cannot see any devices to use.  I created another desktop user, logged into it and it has access to  sound like my main account, but users that it runs via sudo or gksu also do  not have sound access.  So, it is only via this methods that it fails.  Distribution info: ```
lsb_release -a  No LSB modules are available. Distributor ID:    Ubuntu Description:    Ubuntu 16.04.1 LTS Release:    16.04 Codename:    xenial  
```  Any ideas how to solve this?

---

### Post by kevin77v on 2016-12-12
I solved my own problem, so I'll share it here in case anyone else finds value in it:  Did answer 3 and 4 from here: [https://askubuntu.com/questions/182238/sudo-and-sound-how-to-make-them-work-together/187835](https://askubuntu.com/questions/182238/sudo-and-sound-how-to-make-them-work-together/187835) Then rebooted the computer.  I'm not sure which did it, but I suspect 3 was it.

---

