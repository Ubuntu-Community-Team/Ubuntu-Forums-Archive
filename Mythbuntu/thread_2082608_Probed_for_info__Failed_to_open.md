---
title: "Probed for info:  Failed to open"
date: 2012-11-10
forum: Mythbuntu
---

### Post by Dougustine on 2012-11-10
I am running Ubuntu 12.04, hauppauge HVR2250 dual tuner card and I feel like it the card is installed correctly(though I am not sure) but when I go to capture card set up, I select Mpeg-2 encoder card and I get a probed info failed to open.  the video device is empty as is the vbi device.  Basically, I am asking to confirm if the drivers are correct, and where to enter the info for the video device area.  Needless to say I am just learning the whole linux thing and could really use a hand.

---

### Post by BicyclerBoy on 2012-11-12
That card has digital tuners ATSC/QAM & analog tuners with mpeg2 encoders.
You would want to add all the tuners(4).
Originally support was digital only..

Do you have the firmware package installed?
It could be in linux-firmware-nonfree..
Run in terminal:
dmesg
& look for text like saa71 etc..

A good website/page about this card:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250)
There is a f/w link on that site..

---

### Post by Dougustine on 2012-11-13
thank you!!  So as I understand you, I would have to add four tuner cards in total.  I have not installed the firmware so I will try that.   This is my best lead so far...learning linux is not an easy hobby

---

### Post by BicyclerBoy on 2012-11-13
If the analogue tuner is supported then you setup a total of 4 tuners..
The mythtv setup program should show the devices in the drop-down selector..

Note the analogue tuners (mpeg2 encoder) is a diff type to digital tuners.

I've never used a analogue capture tuner or ATSC tuner..

The firmware could be as simple as
sudo apt-get install linux-firmware-nonfree

I don't know if your tuner cards f/w is in that package but most of that package contents are tuner card f/w..

---

### Post by Dougustine on 2012-11-14
I have, thanks to you all fixed my problem. I disconnected all the bells and whistles from the card(remote control addtion) then reloaded mythbuntu, followed [www.robotbeard.com](www.robotbeard.com) then I listed the hardware using the [COLOR="Red"]dmesg | grep saa7164[/COLOR] command!  this told me the specific firmware that the card was missing, found that at [www.steventoth.com](www.steventoth.com) and presto! card initialized.  Again thank you all for your help

---

### Post by nickrout on 2012-11-15
> **Dougustine said:**
> I have, thanks to you all fixed my problem. I disconnected all the bells and whistles from the card(remote control addtion) then reloaded mythbuntu, followed [www.robotbeard.com](www.robotbeard.com) then I listed the hardware using the [COLOR="Red"]dmesg | grep saa7164[/COLOR] command!  this told me the specific firmware that the card was missing, found that at [www.steventoth.com](www.steventoth.com) and presto! card initialized.  Again thank you all for your helpWhat was the specific firmware, and was it not in the linux-firmware-nonfree package?

---

