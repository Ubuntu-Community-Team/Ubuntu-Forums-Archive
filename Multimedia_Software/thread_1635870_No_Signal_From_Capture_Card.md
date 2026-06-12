---
title: "No Signal From Capture Card"
date: 2010-12-02
forum: Multimedia Software
---

### Post by muss02 on 2010-12-02
I am new to Ubuntu and Linux in general and have been trying to put together a mythbox for myself.  I installed Ubuntu 10.10 and the newest version of the Mythbox backend.  My capture card that I am having issues with is a Hauppauge Wintv-HVR-1850 card, I followed the instructions on installation from linuxtv.org and did not get any errors.  I tried to set up Mythtv and it didn't get a signal and couldn't find any channels.  I would like to know if my card is even working so I tried using xawtv but still could not get a signal from my card.  
 
Does anyone have any ideas on how I can verify that my card is installed correctly?  Any help is appreciated, thanks.

---

### Post by Moozillaaa on 2010-12-02
If you want only to confirm the card function, try to import the signal in VLC, with these commands: (you do know how to use the command line terminal?)

```
sudo aptitude install scantv 

v4l2-ctl -i 0

ivtv-tune -c73 (73, if the PVR is outputting on that channel)

vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1
```

---

### Post by muss02 on 2010-12-02
Thank you for the tip, I will try that later when I get home.  I seem to be getting more and more familiar with the terminal as I go so I should be able to handle the commands.  I will let you know the results.

---

### Post by muss02 on 2010-12-03
Just to let you know I tried the code you suggested and got VLC to come up, but nothing would play.  I am assuming because of this I probably still have an issues with my card installation.  I know the card is good because it works through MediaPortal on Windows xp.  If anyone has any suggestions on how to get a Wintv HVR-1850 working then let me know.  Thanks for your help.

---

### Post by Moozillaaa on 2010-12-03
I use a Haup card also - PVR 500.

When you entered this code:
```
ivtv-tune -c73
``` (again, substitute whatever channel your device is broadcasting; default for most devices is 3)

...did it return:
```
signal detected'
```?

The second line syntax is for another software package - video4linux; do you have any version of it installed? It is for video capture, and Haup cards are supported...

---

