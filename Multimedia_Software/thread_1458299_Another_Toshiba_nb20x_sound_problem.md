---
title: "Another Toshiba nb20x sound problem"
date: 2010-04-19
forum: Multimedia Software
---

### Post by KryptoRoxx on 2010-04-19
I am really new to Ubuntu and Linux period but with this netbook Ubuntu is just plain faster than xp and the battery lasts longer too. I've messed around a little before but so far it's made more sense to me to use Windows over Linux. Now that I've seen some people were able to get the zune to sync with Ubuntu I'm giving it another go.

The problem I'm having though is that I tried to OSS workaround to get sound running but instead my sound card disappeared totally from the system. I restored ALSA (I think) but my sound card is still missing in action. If I could get some help on how to restore that I think I could figure the rest out. I tried the sound problem sticky but I ran into the part where the poster has no solution as well. Any assistance is greatly appreciated and I'm slowly learning how the terminal works.....pretty much what windows does for you but it's more flexible at the same time. I learned on DOS so it's not totally alien....just different commands.

I also found Realtek drivers for the HL 272 which is my sound card for linux but I can't make heads or tails of the instructions to install.....sadly. I did make an attempt but they are confusing for a beginner like me.

---

### Post by lidex on 2010-04-20
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by KryptoRoxx on 2010-04-20
It is a Toshiba Netbook NB205-210.

```
gobility@ubuntu:~$ uname -a
Linux ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
gobility@ubuntu:~$ 

``````
 gobility@ubuntu:~$ aplay -l
aplay: device_list:223: no soundcards found... 
``````
 gobility@ubuntu:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory 
``````
 gobility@ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory 
```
 
It's a Toshiba Netbook NB205-210. Good news though is that the bluetooth dongle that I have does work without any modification.

---

### Post by KryptoRoxx on 2010-04-20
bump, please help me. I'm really stumped on this one.

---

### Post by lidex on 2010-04-20
Click the alsa-upgrade-script link in my sig and follow the instructions there to update alsa,

---

### Post by KryptoRoxx on 2010-04-21
no such luck sadly. Great script though. Everything installed correctly.....I just don't know why Ubuntu was recognizing the sound card when I first installed it but now it doesn't. The sound still works in XP so I know that it works.

---

### Post by lidex on 2010-04-21
At some point you removed pulseaudio, is that correct? Go to this page and follow 'Part A':
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by KryptoRoxx on 2010-04-21
Probably, but when I ran that script it re-installed it as well. I read through the results and it was re-installed. Honestly I can re-install ubuntu and work it from there as well. In the beginning the headphones worked and usually I use my headphones anyway. I haven't done much to the system since I am just learning but I was hoping that I could rescue it. I've learned a little bit more of an understanding of how things work from trying to fix this problem so this next go around will probably be better. At least I don't have to pay for a new copy ;)

---

