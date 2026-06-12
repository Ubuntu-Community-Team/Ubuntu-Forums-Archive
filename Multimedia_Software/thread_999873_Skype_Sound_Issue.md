---
title: "Skype Sound Issue"
date: 2008-12-02
forum: Multimedia Software
---

### Post by Shadowriser on 2008-12-02
I have recently once again switched from windows. I got my games all mostly working. But Skype is my house phone and without it fully working I will be forced to go back to windows.

My issue is if I start Ubuntu and use VLC, Amarok or even Firefox website with sound Skype mic will not work. To get around this I normally shut down and start skype first. The second issue is I will be in a skype confence call with 2-3 other users and my mic randomly mutes. The only fix that sometimes works is keeping my alsa mixed open on the record page and make sure its not auto muting. 

Any help would be greatly apprenticed. 

My system for reference.
Intel Core 2 Duo 6400@2.1 Ghz
4G of DDR2 800
Asus Mb 
Creative X-FI Platinum
9800 GTX+ Video

---

### Post by psyke83 on 2008-12-02
> **Shadowriser said:**
> I have recently once again switched from windows. I got my games all mostly working. But Skype is my house phone and without it fully working I will be forced to go back to windows.

My issue is if I start Ubuntu and use VLC, Amarok or even Firefox website with sound Skype mic will not work. To get around this I normally shut down and start skype first. The second issue is I will be in a skype confence call with 2-3 other users and my mic randomly mutes. The only fix that sometimes works is keeping my alsa mixed open on the record page and make sure its not auto muting. 

Any help would be greatly apprenticed. 

My system for reference.
Intel Core 2 Duo 6400@2.1 Ghz
4G of DDR2 800
Asus Mb 
Creative X-FI Platinum
9800 GTX+ Video

Providing the version of Ubuntu can make all the difference. For Hardy and Intrepid: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Shadowriser on 2008-12-03
Using 8.10

---

### Post by rajendrag on 2008-12-03
May be you get more information at this thread.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/202089](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/202089)

Few days ago, i also had sound problem with skype. I use Ubuntu 8.04 and i could play rhythmbox, or videos but skype had sound related problem. I tried the following workaround as suggested in the thread (by Jerome Lacoste):

Work-around:

remove the snd_hda_intel module and reload it. To be able to remove it, I need to close all applications using it, i.e. pulseaudio. Thus I have to close my current session.

Detailed work-around

1- close session (log out)
2- CTRL+ALT+F1 to go to a tty
3- log in
4- sudo rmmod snd_hda_intel
5- sudo modprobe snd_hda_intel
6- CTRL+ALT+F7 and log in again


This workaround worked for me and the skype started working fine for me. 

Raj

---

### Post by Shadowriser on 2008-12-03
I installed some pre-release updates via the update manager. Which broke my X-FI drivers. So I just simply reinstalled the X-FI drivers and so far no mic issues. Thanks for all your help guys.

---

