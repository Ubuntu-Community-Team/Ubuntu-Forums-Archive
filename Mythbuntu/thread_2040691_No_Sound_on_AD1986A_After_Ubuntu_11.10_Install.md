---
title: "No Sound on AD1986A After Ubuntu 11.10 Install"
date: 2012-08-11
forum: Mythbuntu
---

### Post by exit2600x on 2012-08-11
I installed Mythbuntu 11.10 and ran updates.  I get no sound at all.  I have a Asus M2NPV-VM motherboard with the Analog Devices AD1986A onboard sound card.  Sound worked from the install cd, but after install, no sound.  I ran:

cat /proc/asound/card0/codec* | grep Codec
Codec: Analog Devices AD1986A

I've tried changing the audio device under system/preferances/volume control to what looks like the correct audio device.  I've also tried the other ones listed.  None of them work.  I have tried muting and unmuting in alsamixer.  

Can anyone help?

---

### Post by exit2600x on 2012-08-11
I tested the sound on the install disk.  It works on the install disk just fine.  I re-installed and during the install I told it NOT to install updates.  I am stuck with the same problem as before, no sound at all.

---

### Post by exit2600x on 2012-08-11
Bump

I think I found the cause of my troubles...NVIDIA

Sound works until you install there proprietary driver in version 10.10.  

I can't use this without the video driver, I can't use this without sound.  

a;sdlfkjsa;lfdja;lskfjhbasklj;

---

### Post by marlow59 on 2012-08-11
did you try to reinstall alsa-mixer after installinf the NVIDIA driver ?

---

### Post by marlow59 on 2012-08-11
did you try to reinstall alsa-mixer after installing the NVIDIA drivers ?

---

### Post by exit2600x on 2012-08-11
Yes, I did this:

sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get clean && sudo apt-get autoremove
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo apt-get install ubuntu-desktop
sudo apt-get install sound-indicator
reboot

Audio devices show up as: 

HDAnvidia (on board audio)
HDAnvidia (hdmi)

I use the first one, I made sure in alsamixer that nothing was muted. 

I have tried many things at this point and I am about done.  Ty for the help, but I am done trying to fix this at this point.

](*,)

Brick wall has done enough damage.

---

