---
title: "&quot;All mute&quot; sound on Lucid after attempting to install alsa-linux-all.deb"
date: 2010-05-31
forum: Multimedia Software
---

### Post by hmaseko on 2010-05-31
My Compaq Presario F700 laptop has Conexant HD-Audio SmartAudio 221 (checking from my Windows partition). I had everything working just fine until yesterday when I attempted to manually install an alsa-linux package that I downloaded sometime ago. Although the .deb package failed to install, it seems it messed things up and now there's no sound. The speaker icon shows "All mute" and I have no clue how to fix this. How do I 'unmute' it? Please help. I badly need to get the sound working again as I want to get serious with Linux as soon as possible. Thanks for your assistance.

Harrison.

---

### Post by lidex on 2010-06-01
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
**Reboot.**

**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Also check "System>Preferences>Sound"

---

### Post by siddhuc on 2010-06-03
hi,
after rebooting aand typing the code alsamixer in terminal, i am getting-cannot open mixer: No such file or directory..what could be the problem?

---

### Post by hmaseko on 2010-06-04
Same thing with me, well, I should say same response from the terminal. The thing is, I tried to reinstall those packages mentioned by lidex manually because in my circumstances I do not have Internet access to connect my laptop and as such have to use dialup. Unfortunately, gnome-ppp says "cannot find modem" although I am able to dialup from the Windows partition. What should I do to successfully reinstall those packages manually?

---

### Post by lidex on 2010-06-05
Try this. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

BTW, do these PC's have nvidia chipsets?

---

### Post by hmaseko on 2010-06-05
Yes, mine has an nvidia chipset.

---

