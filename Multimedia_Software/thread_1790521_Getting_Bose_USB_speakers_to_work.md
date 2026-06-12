---
title: "Getting Bose USB speakers to work"
date: 2011-06-25
forum: Multimedia Software
---

### Post by inHisSteps on 2011-06-25
After building my new 64-bit system I received a Bose Companion5 sound system for my birthday:D
Unfortunately I got no sound out of them after setting them up, and when I queried Bose support they said "The Bose(R) Companion(R) 5 speaker system is not compatible with the Linux operating system.":(

Fortunately, there were references over the last few years to various Linux users who were getting sound out of the same audio system.  I contacted my motherboard makers thinking that there was a problem with my onboard audio needing to be "sent" to the USB connector.  I will try to clearly present my process for installing USB speakers on ***Natty***.

1) realize that USB audio bypasses the soundcard or onboard sound, and since the processing is occuring in the external device, it needs to be active and connected while you are booting. (I ran it on a Windows XP laptop just prior to rebooting my ubuntu computer to make sure it worked)
2)boot your computer without any speakers plugged into the stereo jack. (Might not be necessary)
3) run:  cat /proc/asound/cards
  You should see the primary sound card as #0, and the USB card may be listed as #1
4) Take a look at how alsa is set up:  cat /etc/modprobe.d/alsa-base.conf
  You will probably find that your usb sound module is purposely turned off.
  Here I am indebted to another flavor of linux for the answer (which worked great under ubuntu) -- see the directions given by latux:  
[http://crunchbanglinux.org/forums/topic/9852/how-to-assign-usb-audio-as-primary-sound-device-in-alsa/](http://crunchbanglinux.org/forums/topic/9852/how-to-assign-usb-audio-as-primary-sound-device-in-alsa/)
  for editing the /etc/modprobe.d/alsa-base.conf file as *superuser*.
5) After rebooting I was able to go directly to System -> Preferences -> Sound to select the Bose USB Audio as output without the extra configuration steps latux mentions, and Voila! :D

---

### Post by Buurmas on 2011-12-20
For the record, all I needed to do was reboot (10.04 Lucid).

Long version: I turned on my Bose Companion 5 speakers & plugged them in to the USB Port. I went to System / Preferences / Sound and clicked Output and saw only one device: "Internal Audio Analog Stereo". I tried to play something, but no sound. I rebooted and then went to System / Preferences / Sound and then Output again and Voila! There was an option for Bose USB Audio Analog Surround 4.1.

---

### Post by FlyWheel on 2012-01-25
I am on 11.10 and the bose usb analog 4.1 and 5.1 showed up, but I can't get any sound. The setting does not stay when I exit the sound app.  The mute stays amber instead of green like there is nothing on the usb port.:confused:

---

### Post by originalebb on 2012-02-15
I followed the instructions and couldn't get my USB audio to work.   Until I noticed listed in the options of the alsa-base.conf file is the  option to turn off the USB audio.  See below:
[INDENT]# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
[B]options snd-usb-audio index=-2
[/B]options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
[/INDENT]If  you follow the instructions from the link above, you may not get your  USB audio to work.  The easiest thing to do is to change the bolded  option to -1.  This is the crux of the fix that is in the link.

---

