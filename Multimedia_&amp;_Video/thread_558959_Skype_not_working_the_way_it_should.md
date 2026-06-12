---
title: "Skype not working the way it should"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by mossgarden on 2007-09-24
I have:
Acer Asipire 3100
Skype 1.4 Beta
Feisty Fawn 7.04


My microphone isn't working, I hear very well what other person is saying but nobody hears me. Also Sound Recorder doesn't record my voice. I get error message: "Your audio capture setting are invalid. Please correct them in the Multimedia settings."

I have tried already A LOT of things, but nothing seems to work. I'm suspecting that it might have something to do with soundcard and drivers (I'm not very familiar with these things so I don't know.)

I checked this one but [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) it's I guess just for Intel (which I don't have...)

Anyway I'm pretty noobie with Ubuntu still so if you need any other information, ask. And if there's some other thread that might help me, I'd be happy to know. (But as I said I have tried quite  a lot things... soon I may have to install Vista back as a second OS :()

---

### Post by cleanbarn on 2007-09-30
What I did was disable the onboard sound card and switch to USB Audio.

It may not be necessary for you to recompile ALSA as described in the HdaIntelSoundHowto  If you try it use sudo sudo ./configure --with-cards=hda-intel,usb-audio  when you compile the alsa-driver. 

Buy or borrow a usb headset with microphone.

Use lsmod | grep snd to find out what your snd driver is. 

Add the name of your snd driver to the end of /etc/modprobe.d/blacklist
(sudo nano /etc/modprobe.d/blacklist )

Edit the /etc/modprobe.d/alsa-base

---

### Post by cleanbarn on 2007-09-30
What I did was disable the onboard sound card and switch to USB Audio.

Sorry about the incomplete post earlier.

It may not be necessary for you to recompile ALSA as described in the HdaIntelSoundHowto If you try it use sudo sudo ./configure --with-cards=hda-intel,usb-audio when you compile the alsa-driver.

Buy or borrow a usb headset with microphone.

Use lsmod | grep snd to find out what your snd driver is.

Add the name of your snd driver to the end of /etc/modprobe.d/blacklist
(sudo nano /etc/modprobe.d/blacklist )

Edit the /etc/modprobe.d/alsa-base 
(sudo nano /etc/modprobe.d/alsa-base)
comment out the line that reads
options snd-usb-audio index=-2
by inserting a # as the first character so it reads
# options snd-usb-audio index=-2

Now reboot.  Set the volumes back up ( the new driver sets them to zero).

I had to try skype a couple of times after this to get it to work.  But skype and my microphone work now.

---

