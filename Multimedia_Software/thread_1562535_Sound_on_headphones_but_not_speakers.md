---
title: "Sound on headphones but not speakers"
date: 2010-08-27
forum: Multimedia Software
---

### Post by pseudosmart on 2010-08-27
I have installed 10.04 on my sony vaio, model VPCF115FM, and when I plug in my headphones I can hear sound, but not from the speakers when I unplug the headphones. I have checked the alsamixer to make sure nothing was muted. Any ideas? Thanks in advance.

---

### Post by lidex on 2010-08-28
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by B-Mart on 2010-08-29
nice to see you again lidex XD (I posted on another thread after you)
I did what you instructed here (got sound to work...but just on headphones) and my alsa report is here
[http://www.alsa-project.org/db/?f=c642104ad4735102afd2ab5a490a1e002cda95e8](http://www.alsa-project.org/db/?f=c642104ad4735102afd2ab5a490a1e002cda95e8)

Tell me whats up.

---

### Post by pseudosmart on 2010-09-07
Apparently all I had to do was search the repository and install backports to make the speakers work. Thanks for your help.

---

### Post by lidex on 2010-09-15
*B-Mart:*
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1  
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

No joy - try replacing the model with hp-m4

---

### Post by Pakiisp on 2010-09-15
nice information specialy for me, thank you.

---

### Post by B-Mart on 2010-09-16
Actually I didn't need to help, forgot to reply...thanks anyway Lidex :D

---

### Post by Dive N Shoot on 2010-10-09
> **lidex said:**
> *B-Mart:*
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert these lines at the bottom:
```
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1  
```Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

No joy - try replacing the model with hp-m4

I have the same model laptop and am having the same problem.  I tried the above and it didn't work.  I tried changing to hp-m4 and when I did my video driver failed and I changed it back to hp-hdx and the video is working again.

Here is the link to my alsa check from above
[http://www.alsa-project.org/db/?f=6c5760453a98a60e43426d9baef880daf50fe492](http://www.alsa-project.org/db/?f=6c5760453a98a60e43426d9baef880daf50fe492)

Thanks for your time,
Mike

---

### Post by lidex on 2010-10-09
> **Dive N Shoot said:**
> I have the same model laptop and am having the same problem.  I tried the above and it didn't work.  I tried changing to hp-m4 and when I did my video driver failed and I changed it back to hp-hdx and the video is working again.

Here is the link to my alsa check from above
[http://www.alsa-project.org/db/?f=6c5760453a98a60e43426d9baef880daf50fe492](http://www.alsa-project.org/db/?f=6c5760453a98a60e43426d9baef880daf50fe492)

Thanks for your time,
Mike

I would remove those entries from alsa-base.conf.
Next upgrade your alsa install via the link in my sig.

---

### Post by Dive N Shoot on 2010-10-09
It worked.  Thank you very much!

---

