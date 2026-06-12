---
title: "No sound on speakers, MSI Notebook, ALC1200 audio."
date: 2010-09-01
forum: Multimedia Software
---

### Post by kennyevo on 2010-09-01
Hy!
I have an MSI EX623X Notebook with alc1200 audio and i have no sound on the built in speakers, but if i plug in the earphones, it works...
Please help me!

Thank you in advance!

Greetings from Hungary!!!

---

### Post by lidex on 2010-09-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by MegaLoler on 2010-09-03
Im not sure if this will work, but try running "alsamixer" in a command prompt and seeing if your speakers are muted or something.

---

### Post by kennyevo on 2010-09-05
I'll try to run the script as soon as i'll have an internet connection at the students' hoster :)

---

### Post by lidex on 2010-09-05
I have a fix documented for an MSI w/ALC1200 you may want to try.
It was a MSI GX73x

Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
 
options snd-hda-intel model=targa-dig
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel probe_mask=1 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by kennyevo on 2010-09-06
Thanks for the help, but it didn't help for me :(
The script's result is here:
```
http://www.alsa-project.org/db/?f=1ebe31c5a460694834fe3aa10e867f66f5323a03
```

---

### Post by kennyevo on 2010-09-12
So, i've found a forum with the solution you've told me, that works with speakers i plug into the jack.
I don't have sound on the built in speakers, please help, this thing is pain in the ...
Thanks in advance!

---

### Post by lidex on 2010-09-15
You have two models specified in alsa-base.conf - not good. Remove the "model=auto" entry. In fact, you should remove everything after the line starting with "snd-pcsp" and then paste in the four lines from my previous post and reboot. No joy - update your alsa install via the link in my sig.

---

### Post by kennyevo on 2010-09-21
I've upgraded my alsa, but now, there is no hardware in the hardware tab...:S

---

### Post by lidex on 2010-09-21
> **kennyevo said:**
> I've upgraded my alsa, but now, there is no hardware in the hardware tab...:S

Let's see updated alsa info.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

