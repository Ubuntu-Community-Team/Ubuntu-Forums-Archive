---
title: "No Sound in Ubuntu"
date: 2010-07-08
forum: Multimedia Software
---

### Post by gmbhangar on 2010-07-08
I have installed ubuntu 10.04 and I am also having windows xp on my system. I am new to ubuntu, I am not hearing any sound in it..my sound card is
 
Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03) Subsystem: Hewlett-Packard Company Device 0890

---

### Post by mörgæs on 2010-07-08
Maybe this will help:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by TheStroj on 2010-07-08
The most common problem on not having sound by me was bad permission settings. Go to System > Administration > Users & Groups > Advanced settings > 'input password' > go to 2nd tab > set yourself all permissions > you're done.

(Sorry if all the programs/directories aren't correct, I'm not using english version of Ubuntu)

---

### Post by gmbhangar on 2010-07-08
> **TheStroj said:**
> The most common problem on not having sound by me was bad permission settings. Go to System > Administration > Users & Groups > Advanced settings > 'input password' > go to 2nd tab > set yourself all permissions > you're done.

(Sorry if all the programs/directories aren't correct, I'm not using english version of Ubuntu)

When I click on Advanced settings nothing happens..

---

### Post by gmbhangar on 2010-07-08
> **mörgæs said:**
> Maybe this will help:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
 
I could not find anything here.

---

### Post by YsL on 2010-07-08
System > Preferences > Sound > Hardware and make sure in the Settings for the selected device is Analog or Digital Output not Input.

---

### Post by gmbhangar on 2010-07-08
> **YsL said:**
> System > Preferences > Sound > Hardware and make sure in the Settings for the selected device is Analog or Digital Output not Input.

There is nothing in hardware and in output it says dummy output

---

### Post by lidex on 2010-07-08
Dummy output is a clue. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by gmbhangar on 2010-07-09
> **lidex said:**
> Dummy output is a clue. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)
 
1.code:uname -a
Linux bhangar 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
2.code:aplay -l
aplay: device_list:223: no soundcards found...
3.dpkg -l | grep "alsa"
ii alsa-base 1.0.22.1+dfsg-0ubuntu3 ALSA driver configuration files
ii alsa-utils 1.0.22-0ubuntu5 ALSA utilities
ii bluez-alsa 4.60-0ubuntu8 Bluetooth audio support
ii gstreamer0.10-alsa 0.10.28-1 GStreamer plugin for ALSA
4.head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

---

### Post by lidex on 2010-07-09
First try an alsa re-install:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**

---

### Post by gmbhangar on 2010-07-10
> **lidex said:**
> First try an alsa re-install:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
 
No sound yet

---

### Post by lidex on 2010-07-10
OK, now try this:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```

---

### Post by gmbhangar on 2010-07-10
> **lidex said:**
> OK, now try this:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```

nothing HAPPENED

---

### Post by lidex on 2010-07-10
I'm a little confused. You ran those commands - one at a time - in terminal and got no response? Did you reboot?

---

### Post by gmbhangar on 2010-07-10
> **lidex said:**
> I'm a little confused. You ran those commands - one at a time - in terminal and got no response? Did you reboot?
 
yes

---

### Post by lidex on 2010-07-10
It would help diagnose if I could see them.

---

### Post by gmbhangar on 2010-07-10
> **lidex said:**
> It would help diagnose if I could see them.
 
1.Linux bhangar 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
 
2,aplay: device_list:223: no soundcards found...
 
3,ii alsa-base 1.0.22.1+dfsg-0ubuntu3 ALSA driver configuration files
ii alsa-utils 1.0.22-0ubuntu5 ALSA utilities
ii bluez-alsa 4.60-0ubuntu8 Bluetooth audio support
ii gstreamer0.10-alsa 0.10.28-1 GStreamer plugin for ALSA
 
4.head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

---

### Post by lidex on 2010-07-10
OK. Try this:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**
You can safely ignore any file not found errors.
Now this. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

