---
title: "no system sounds"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by davidsrsb on 2007-07-11
asus m2n-e sli motherboard, Ubuntu 7.04
This board has a on board CM6501 usb audio. I have now got this working by compiling alsa 1.0.14 and selecting usb audio in stead of alsa in system-pref-sound.
"test" now works and audacity shows microphone capture works.
cat /dev/urandom > /dev/audio1 works
alsaconf still cannot detect any card
alsamixer does not work
The system sounds are silent
PCM and PCM1 sliders are on the recording tab, not showing on the playback tab

---

### Post by LDRoamer on 2007-07-12
I just got a USB sound card and have the same problem as you. However I am thinking what I need to do is to load a usb sound driver. All I did was insert the card into my usb port and change the audio to USB as you describe. This link has information on setting up USB sound cards:

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=USB&card=Generic&chip=Generic&module=usb-audio](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=USB&card=Generic&chip=Generic&module=usb-audio)

I haven't tried it yet as I am not at my Linux machine but I will give it a bash later on.

---

### Post by davidsrsb on 2007-07-12
The kernel sound driver is working or "test" would not work
I am going to experiment with the usb driver and .asounrc param to see if I can coax alsa to work too

---

### Post by LDRoamer on 2007-07-13
You are right. When I looked at my machine last night I realized just what you said. I had some notion that there was another alsa driver that wasn't loading and alsa would then start working (but that was wrong). In my case I have no system sounds and the alsa mixer just shows a volume bar and says PCM. I can get some sound now which is better than it was before (no sound at all) but I would like to get it working. Googling around it seems that this device  (c-media) does work on other Linux installations.

---

### Post by LDRoamer on 2007-07-13
I have it working now. The answer was almost too simple. I saw this in another post and this is what did the trick for me:

 had the same problem with my USB speakers, and after much searching found this solution:
Code:

asoundconf list

your USB headset/speakers should be in there (mine were just called "Audio"), now:
Code:

asoundconf set-default-card Audio

replace "Audio" with whatever your device is called. Now reboot and you're done.
__________________

In my case my usb sound card had the name "default" I didn't realize that in fact this what the real name of the card and not a reference to the fact that it was the default card in the system. In my case I had unloaded the driver for the on board chip (es1869) as it was causing a conflict in my system causing boot up times to be very long and some applications took forever to open. What finally twigged me was reading the post where the headset just showed up as "audio".  I loaded the snd_es18xx driver and sure enough I had two cards listed, the es1869 and default. Following the instructions above was all I needed to do.

---

### Post by davidsrsb on 2007-07-15
asoundconf list just gets "default"

---

### Post by LDRoamer on 2007-07-16
This is exactly what mine did. All I had  was the one USB sound card (onboard chip was disabled).


> **davidsrsb said:**
> asoundconf list just gets "default"

To get my USB card to work I had to run:

asoundconf set-default-card default

I would think in your case its worth trying that to see if it works.

---

### Post by davidsrsb on 2007-07-18
It turns out that this sound chip has problems under XP too. Asus seem to have produced a board with broken audio. I am having words with my supplier.

---

### Post by razordead on 2008-02-08
> **LDRoamer said:**
> I have it working now. The answer was almost too simple. I saw this in another post and this is what did the trick for me:

 had the same problem with my USB speakers, and after much searching found this solution:
Code:

asoundconf list

your USB headset/speakers should be in there (mine were just called "Audio"), now:
Code:

asoundconf set-default-card Audio

replace "Audio" with whatever your device is called. Now reboot and you're done.

This solved my problem LD. I now have working system sounds as well as Flash sound in Firefox.

I have iMic USB audio.

---

