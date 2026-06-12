---
title: "Can Skype ever work?"
date: 2009-01-07
forum: Multimedia Software
---

### Post by memories on 2009-01-07
I've never had any luck whatsoever getting Skype to work on Ubuntu. I first tried with an Audigy Gamer, but I'm not trying with onboard audio (AC97 or whatever). 

I don't hear any sound nor can I record. I'm testing using the Skype test call. Skype in virtualbox on windowz works fine. 

I'm using PulseAudio, but I'm really confused about my sound setup to be honest. I think the emu10k1 modules are still being loaded for the audigy, which is still plugged in. I just have all my equipment plugged into the mobo and all my apps are set to use that as the default device. 

I also have a webcam which I think has a mic on it.. 

**Please help!**

---

### Post by ubuser_7 on 2009-01-07
I can only agree. My skype worked for a bit, and then I moved to pulseaudio, now I cannot make calls at all. Even earlier, whenever I used skype, my network would freeze every so often. 

Have been googling and posting on forums, but nothing seems to work. Also tried the OSS version, nothing works :( 

Looking forward to some solutions here.

---

### Post by sonicb00m on 2009-01-07
Pulse audio is a waste of time in my opinion. Causes more problems than it solves. It's so ALPHA I don't understand why it's been added to Ubuntu. I never have trouble sharing devices with alsa. The only benefit I could see from pulseaudio was real time effects processing and controlling your devices in a consistent way. Unfortunately, it falls way short of the mark.

Uninstall it and use ALSA and skype will work just fine.

---

### Post by laceration on 2009-01-07
Skype has worked good for me, but it doesn't always know or remember which sound devices to use.  Here is the d'oh #-o fix  This got me more than a few times.

Open Skype
Click the Skype icon in the lower left corner
Click options
Choose Sound Devices on left --should be obvious from there

---

### Post by Roasted on 2009-01-09
I hear that. Man, I don't know who's to blame... whether it's pulseaudio or skype. All I know is I've spent the last 3 hours trying to get skype to work and I can't figure it out. Something like skype shouldn't be this difficult to figure out. Brings a tear to my eye having to boot to Vista to get something like this to work. grrrr.

---

### Post by ushimitsudoki on 2009-01-09
All I can say is that I've stuck with ALSA for a number of reasons, and Skype works for me on 64-bit Ubuntu.

I *really* don't understand the whole Pulse Audio love-fest, and would love to read why it is considered an improvement over ALSA.

---

### Post by Roasted on 2009-01-09
How did you remove pulse audio without getting any problems? I heard of some people who ran into issues where they cannot log in after a reboot because of some missing file that pulseaudio is looking for.

I just never saw the point in pulse to begin with. It seemed to offer nothing constructive for the average user, yet it aided in continuous headaches for users.

what can you tell me about removing it?

---

### Post by eye208 on 2009-01-09
> **Roasted said:**
> How did you remove pulse audio without getting any problems? I heard of some people who ran into issues where they cannot log in after a reboot because of some missing file that pulseaudio is looking for.

I just never saw the point in pulse to begin with. It seemed to offer nothing constructive for the average user, yet it aided in continuous headaches for users.

what can you tell me about removing it?
See here: [http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

---

### Post by Roasted on 2009-01-09
Just curious, what does esound offer that would require me to have it installed after removing pulse?

---

### Post by wolfen69 on 2009-01-09
i removed pulseaudio without any issues. it's worth doing.

---

### Post by eye208 on 2009-01-09
> **Roasted said:**
> Just curious, what does esound offer that would require me to have it installed after removing pulse?
It's not required unless you use Second Life.

---

### Post by Roasted on 2009-01-09
I've heard that removing pulseaudio can be a bad thing. Some people said that future updates you pull down rely on certain pulse packages. So if they aren't there, updates can be corrupt. Can anybody confirm this?

I'm going to image my system before I do any major changes, but nonetheless I gotta wonder if those few people having major problems when removing pulse are something I should look into and consider before doing this.

---

### Post by jrusso2 on 2009-01-09
> **memories said:**
> I've never had any luck whatsoever getting Skype to work on Ubuntu. I first tried with an Audigy Gamer, but I'm not trying with onboard audio (AC97 or whatever). 

I don't hear any sound nor can I record. I'm testing using the Skype test call. Skype in virtualbox on windowz works fine. 

I'm using PulseAudio, but I'm really confused about my sound setup to be honest. I think the emu10k1 modules are still being loaded for the audigy, which is still plugged in. I just have all my equipment plugged into the mobo and all my apps are set to use that as the default device. 

I also have a webcam which I think has a mic on it.. 

**Please help!**

Skype kind of works until I try to use the webcam then it just crashes.  Works good on Mandriva though.

---

### Post by eye208 on 2009-01-09
> **Roasted said:**
> I've heard that removing pulseaudio can be a bad thing. Some people said that future updates you pull down rely on certain pulse packages. So if they aren't there, updates can be corrupt. Can anybody confirm this?
Note that removing Pulse does not require manual changes in system configuration files. We just uninstall two packages using the regular package manager. Reinstalling "ubuntu-desktop" (or any other base desktop metapackage) will undo these changes. If you are in doubt, reinstall "ubuntu-desktop" before doing the full system upgrade. This takes only a minute.

> I'm going to image my system before I do any major changes, but nonetheless I gotta wonder if those few people having major problems when removing pulse are something I should look into and consider before doing this.
Those who had "major problems" simply forgot to disable system sounds before removing Pulse. This is a known bug in Ubuntu's version of GNOME which will cause the desktop to freeze when trying to play the login/logout sounds without Pulse running. I ran into that problem too on my first attempt. That's why I wrote the HOWTO.

---

### Post by Roasted on 2009-01-16
Just replying back here since I kind of forgot about Skype, anybody got it working in Ubuntu? I understand that video isn't supported in Ubuntu but what about audio with pulse? Anybody else?

---

### Post by modestmelody on 2009-01-17
> **Roasted said:**
> Just replying back here since I kind of forgot about Skype, anybody got it working in Ubuntu? I understand that video isn't supported in Ubuntu but what about audio with pulse? Anybody else?

I have had no problems getting audio to work in Skype after taking just a couple of simple steps from this page:

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

```
sudo nano /etc/pulse/daemon.conf
```

Then add this to the bottom (or change numbers accordingly):
default-fragments = 8
default-fragment-size-msec = 5


Then:
```
sudo nano ~/.asoundrc
```

And added this:

pcm.pulse { type pulse }
ctl.pulse { type pulse }


Then go into Skype and select Sound In as your mic (for me, the USB device associated with my webcam) and Sound Out and Ringer as "pulse".


The only trouble I have is that I often cannot see video being sent to me, though I can view myself and those I'm calling can see me.  If anyone wants to share a fix for that I'd appreciate it.

:guitar:

---

### Post by Roasted on 2009-01-19
I tried that. No dice.

I can't even get my mic to work in Ubuntu. This is unreal.

---

