---
title: "HP speakers not working in Ubuntu 10.04 64-bit"
date: 2010-09-23
forum: Multimedia Software
---

### Post by fiction52s on 2010-09-23
I'm a new Ubuntu user and I've only been using it for a couple of days. I realized that my external speakers do not work. 

I've been looking around for ways to solve it.

I used alsamixer to look up my chip and card and stuff and it was

HDA Intel
Realtek ALC888

I ran a script which said it could get my speakers working by updating the alsa drivers, but not System->Preferences->Sound doesn't even show any sound card (Sound Blaster Xtreme Audio is what I have) and alsamixer fails to run. I'm just trying to get my speakers to work. help?

edit: also System->Preferences->Sound now doesn't show my webcam mic or internal sound either...

---

### Post by lkjoel on 2010-09-23
> **fiction52s said:**
> I'm a new Ubuntu user and I've only been using it for a couple of days. I realized that my external speakers do not work. 

I've been looking around for ways to solve it.

I used alsamixer to look up my chip and card and stuff and it was

HDA Intel
Realtek ALC888

I ran a script which said it could get my speakers working by updating the alsa drivers, but not System->Preferences->Sound doesn't even show any sound card (Sound Blaster Xtreme Audio is what I have) and alsamixer fails to run. I'm just trying to get my speakers to work. help?

edit: also System->Preferences->Sound now doesn't show my webcam mic or internal sound either...
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by lidex on 2010-09-25
> **fiction52s said:**
> I'm a new Ubuntu user and I've only been using it for a couple of days. I realized that my external speakers do not work. 

I've been looking around for ways to solve it.

I used alsamixer to look up my chip and card and stuff and it was

HDA Intel
Realtek ALC888

I ran a script which said it could get my speakers working by updating the alsa drivers, but not System->Preferences->Sound doesn't even show any sound card (Sound Blaster Xtreme Audio is what I have) and alsamixer fails to run. I'm just trying to get my speakers to work. help?

edit: also System->Preferences->Sound now doesn't show my webcam mic or internal sound either...
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by fiction52s on 2010-09-25
Because I had so recently installed Ubuntu I simply wiped it off and restarted it. Everything is currently at default and alsa is picking up my speakers in System->Preferences->Sound but no sound is coming out of the speakers.

@lidex:

I ran the script. Here is the site it gave me:

[http://www.alsa-project.org/db/?f=71b4c50a1eb103eec9b5e2c4277f8fdb7fd85f17](http://www.alsa-project.org/db/?f=71b4c50a1eb103eec9b5e2c4277f8fdb7fd85f17)

@lkjoel:

I followed the instructions on the link in your signature and it didn't work. installing the deb file somehow crashed the system each time it was run.  If no one else can help me I will try it again later now that I have a fresh system.

---

### Post by lkjoel on 2010-09-25
> **fiction52s said:**
> 
@lkjoel:

I followed the instructions on the link in your signature and it didn't work. installing the deb file somehow crashed the system each time it was run.  If no one else can help me I will try it again later now that I have a fresh system.
Download the script from Post-Fix your sound! into your homedir.
Then type this into a Terminal:
```
cd ~
chmod +x CPanel.sh
./CPanel.sh osspart1
# RESTART COMPUTER NOW
./CPanel.sh osspart2
./CPanel.sh -r
```

---

### Post by lidex on 2010-09-25
Please do not start screwing around with OSS yet, or I won't be able to help you. Can you post these outputs please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

