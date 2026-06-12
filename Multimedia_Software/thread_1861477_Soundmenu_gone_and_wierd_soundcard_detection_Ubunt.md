---
title: "Soundmenu gone and wierd soundcard detection Ubuntu 11.10"
date: 2011-10-15
forum: Multimedia Software
---

### Post by Truckerpunk on 2011-10-15
After my upgrade to 11.10 I noticed the sound menu in the panel was gone, and I heard no boot sound when logging in. My speakers makes a "popping" noise now and then (once a min or so). I checked under system settings -> sound, and no card is listed there, but I can hear sound from various applications (banshee and firefox). I ran alsamixer in the terminal and it shows my soundcard...

I'd like to have my sound menu back as well as stable audio playback.
Any ideas are appreciated.  

aplay -l shows my soundcard(s) as well, and I did a reinstall of 
alsa with:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils

without luck... Running low on ideas myself.

Just found out, every time I rightclick the sound will lag,, Annoying. =(

---

### Post by Truckerpunk on 2011-10-20
Found a solution!!

Here what I did to get Ubuntu to recognize my soundcard, and display volume controls correctly in the panel:

sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get clean && sudo apt-get autoremove
sudo apt-get install alsa-base 
sudo apt-get install pulseaudio

then restart your machine, your sound should be OK now.

---

### Post by ballantony on 2011-10-21
Worked!  Thank you

Had to sudo aptitude ubuntu-desktop first though, to get my sound icon back.

---

### Post by Black_Sector on 2011-10-23
I am tempted to try this, only I am using XFCE. Can I get Pulse Audio on my panel if I am using XFCE?

---

### Post by Roy Baty on 2012-02-07
> **Truckerpunk said:**
> Found a solution!!

Here what I did to get Ubuntu to recognize my soundcard, and display volume controls correctly in the panel:

sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get clean && sudo apt-get autoremove
sudo apt-get install alsa-base 
sudo apt-get install pulseaudio

then restart your machine, your sound should be OK now.

I wasn't getting any sound at all except for that occasional popping after upgrading from 11.04, but now it's all working great! Thanks for the tip Truckerpunk. :D

---

