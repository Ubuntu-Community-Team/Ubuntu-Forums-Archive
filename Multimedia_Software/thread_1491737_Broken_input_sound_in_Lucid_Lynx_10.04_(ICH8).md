---
title: "Broken input sound in Lucid Lynx 10.04 (ICH8)"
date: 2010-05-24
forum: Multimedia Software
---

### Post by almejo on 2010-05-24
Hi everyone

For the last 3 release all my hardware have been working like a charm. But after upgrading to Lycid I have problems with skype. I fix the camera issues with the following command

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

But the sound of my microphone is totally jagged. I have an ICH8 Intel integrated card. I have worked the last 2 years (with an ocasionally glith in the volume) but not having Mic is a real PITA

Do anyone knows what can I try to fix it? Please, don't tell me "remove all pulse audio stuff"... It must be another way.

Thanks to all 
Alejandro

---

### Post by pariterre on 2010-05-31
Hi, I have the same problem.

It was working very well on Jaunty and Karmic, but can't do anything on Lucid :(

I have XPS M1730

---

### Post by lidex on 2010-06-01
Have you selected the correct device in 'System>Preferences>Sound' on the 'Input' tab?

---

### Post by Docaltmed on 2010-06-23
I have exactly the same problem. It is not only with skype; this problem also appears with multiple SIP clients. It does *not* occur when recording locally -- as near as I can tell, this only happens with clients like Skype, Ekiga, QuteCom, etc.

---

### Post by lidex on 2010-06-25
Try this. Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
Reboot.

---

### Post by Chuck Glenn on 2010-06-25
I had major issues with my acer aspire one netbook, so when I installed skype on my desktop and had no microphone I assumed the worst.  BUT, the solution for me was simple:  I went to System | Preferences | Sound.  On the "Input" tab I noticed no choices.  So on the "Hardware" tab I noticed the "Profile" at the bottom said "Analog Stereo Output".  I changed this to "Analog Stereo Duplex," then there were choices in the "Input" tab.  I chose the "Connector" that showed level changes when I spoke into my microphone.  Then Skype worked just fine.

---

### Post by pgmario on 2010-06-25
For me, none of the above mentioned solutions worked. Then I found the following advice at [http://forum.skype.com/index.php?showtopic=468941]("http://forum.skype.com/index.php?showtopic=468941"), and now the built in microphone of my acer aspire one works!

> In anycase, in the Skype audio options I disabled skype automatically adjusting the mixer.

Also, in pulse audio Volume control in the input tab, I adjusted the left volume high and the right volume to silent. Pressing the "fallback" button may have something to do with it too, but I'm not certain.

So.. after a few hours of hassle, it works. Even for this newb.

---

### Post by wiresquire on 2010-06-26
> **pariterre said:**
> Hi, I have the same problem.

It was working very well on Jaunty and Karmic, but can't do anything on Lucid :(

I have XPS M1730

I had similar problem with my M1730 internal microphone with 10.04. External Microphone was OK, but I couldn't record via Sound Recorder with Internal microphone.

I googled (a lot!) and eventually found something that worked for me:

Add the line:
options snd-hda-intel model=dell-bios
to the end of the /etc/modprobe.d/alsa-base.conf file.

Then you will need to go into the Sound preferences. Make sure that on the Input you choose Microphone 1, and that the Volume is way up. You should then be able to start talking and see the little indicator bars move - or use Sound Recorder to record something. 

If it doesn't work, you may need to check on the Hardware tab, to make sure that that you choose a Profile with Stereo Input (I am using Analog Stereo Duplex). If you still get nothing, you may need to use alsamixer to check that for Capture, your first Input Source is [Digital Mic].

Note that this is not a generic fix. At best it may work for other Dell machines. There are similar options that may help if you have a different brand/cards.

Good luck
ws

---

### Post by jeromestpierre on 2010-08-26
> **lidex said:**
> Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```Reboot.

The Alsa driver module from this repository worked for me after I selected Microphone 1 in the input tab of Sound Preferences. 

Before running this install, the Sound Preferences Hardware and Input tabs kept getting empty after a few seconds and the whole window was freezing.

Thanks Lidex!

---

