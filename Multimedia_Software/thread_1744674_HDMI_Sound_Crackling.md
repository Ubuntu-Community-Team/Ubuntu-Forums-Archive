---
title: "HDMI Sound Crackling"
date: 2011-04-30
forum: Multimedia Software
---

### Post by AemonCG on 2011-04-30
Hello,

I've been trying to configure my revo R3700 over the last day and I'm finally there. HDMI sound is working apart from the fact that all sound is crackling. Sound is working through analogue without issue its just HDMI that is distorted

I initially did the command 

aplay -Dplughw:1,7 /usr/share/sounds/alsa/Front_Center.wav 

Which produced no crackling or distortion. I then tried a mp3 which was distorted and crackling, upon trying the same command as above later on, this too started to be distorted

Searched through the forum and theres a few people that have had this issue and have resolved it simply by edited alsamixer however this isn't working.

Has anyone been able to resolve this issue.

Thanks

---

### Post by lidex on 2011-04-30
Another thing that can cause this is your profile selection in 'Sound Preferences' on the 'Hardware' tab.

---

### Post by AemonCG on 2011-05-01
The only option for HDMI is Digital Stereo (HDMI) Output

i also have internal audio my analogue running with multiple. Could one of these be interfering with the drivers?

Just to add as well I'm on 10.10, don't think i mentioned it in the original post.

---

### Post by lidex on 2011-05-01
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by AemonCG on 2011-05-02
As requested

[http://www.alsa-project.org/db/?f=1ff97541df4e8c1a3c5288d5e6808dbc35478ecc](http://www.alsa-project.org/db/?f=1ff97541df4e8c1a3c5288d5e6808dbc35478ecc)

Cheers

---

### Post by lidex on 2011-05-04
You probably need more recent drivers for better support of the hardware. Upgrade your kernel firstly:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo update-grub
```
**Reboot**
Next follow the link in my sig for the alsa-upgrade script.

---

