---
title: "Sound (HDMI) not working"
date: 2009-09-18
forum: Mythbuntu
---

### Post by Xetroc on 2009-09-18
Hi, I just installed Mythbuntu, and i have no sound using the HDMI output.

So far i've tried the mediaplayers and youtube, no sound anywhere.

Using the hdmi output on my MSI K9AGM2 motherboard.

Could anyone tell we what i should try, not an expert on linux.

Thanks :)) :popcorn:

---

### Post by Xetroc on 2009-09-18
```
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

It seems like the HDMI drivers are installed, and i've selected the HDMI card in the alsa mixer. I've tried enabling/disabling the IEC958 protocol in the alsa mixer.

No Sound...

Can anyone please help.

---

### Post by Xetroc on 2009-09-18
And i've checked if it's muted using 
```
alsamixer -c 1
```
1 which is the hdmi output

---

### Post by Xetroc on 2009-09-18
argh, thought it was a problem with the ati drivers.

I tried installing the catalyst drivers using
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")
But it didn't work, got and error 
"No supported adapters detected"

I then removed the drivers again using
```
sudo apt-get remove --purge xorg-driver-fglrx
```

no i get
no screen detected

:o omg

---

### Post by trevs.bronco on 2009-09-18
Try [this]("http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto#Update_nvidia_drivers"), it worked for me.

Trev

---

### Post by Xetroc on 2009-09-19
asfar as i know, i've got ATI and not nvidia ?? Should i still upgrade nvidia drivers ? :o

---

### Post by trevs.bronco on 2009-09-19
No, you would update your ATI drivers. I don't know much about the ATI stuff except that it is not recommended for myth. You may be able to get it to work but it will take more effort.

Trev

---

### Post by JugeHuge on 2009-10-02
Have you tried with these guides??
[URL="http://www.mandladventures.com/2008/11/03/ubuntu-810-hdmi-sound-configuration/"]
Ubuntu 8.10 HDMI Sound Configuration[/URL]
[HOWTO: Audio over HDMI with the HD3200 \ RS780 in Ubuntu]("http://www.mediaboxblog.co.uk/blog1.php/2008/08/15/howto-audio-over-hdmi-with-the-hd3200-rs")

Or this one??
[No sound over HDMI with ga-ma78gm-s2h AMD 780G motherboard]("http://www.gossamer-threads.com/lists/mythtv/users/333112#333112")

---

