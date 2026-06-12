---
title: "How to reinstall sound files on 10.10"
date: 2010-11-10
forum: Multimedia Software
---

### Post by krelverehan on 2010-11-10
I've just done a fresh install of ubuntu 10.10 and it works great, but I was feeling adventurous one day and mess up my sound experimenting with different drivers.

What I am asking is what would be all the programs I could reinstall to get it back to the original install?

I've all ready tried ```
sudo apt-get --purge --reinstall install libasound2
```
What other programs could I try?

Thanks!
-KV

---

### Post by lidex on 2010-11-10
That depends. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by krelverehan on 2010-11-10
> **lidex said:**
> Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

[http://www.alsa-project.org/db/?f=f498ddf9533ecac1da0e1ec1eeea20eb2a0268c9](http://www.alsa-project.org/db/?f=f498ddf9533ecac1da0e1ec1eeea20eb2a0268c9)

---

### Post by lidex on 2010-11-10
Check your bios and make sure you didn't disable onboard audio. 
An alsa re-install would be my next suggestion.
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
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

---

### Post by krelverehan on 2010-11-10
I'm sorry but it didn't seem to work, even after the reboot...

This is my new output from alsa-info:

[http://www.alsa-project.org/db/?f=f9928064d87d2600dcfdd392a44cade65876aff7](http://www.alsa-project.org/db/?f=f9928064d87d2600dcfdd392a44cade65876aff7)

---

### Post by lidex on 2010-11-11
Remove your pulse config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by krelverehan on 2010-11-11
> **lidex said:**
> Remove your pulse config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

Maybe this is a problem, it looks as if a few of those files don't even exist:

```
krel@namcle:~$ rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
*rm: cannot remove `/home/krel/.asound*': No such file or directory*
krel@namcle:~$ sudo rm /etc/asound.conf
[sudo] password for krel: 
*rm: cannot remove `/etc/asound.conf': No such file or directory*
```

Still no sound after reboot...

---

### Post by kitzogen on 2010-11-28
> **lidex said:**
> Check your bios and make sure you didn't disable onboard audio. 
An alsa re-install would be my next suggestion.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
``````
sudo apt-get purge linux-sound-base alsa-base alsa-utils

``````
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

This worked for me, thanks

---

### Post by windozh8ter on 2011-03-14
Thank you, Lidex. I had removed all alsa and pulseaudio installs via Synaptic. Then I couldn't boot to Ubuntu and wondered why. Your suggestions got me up and running again.

---

