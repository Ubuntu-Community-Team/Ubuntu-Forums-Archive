---
title: "usb sound device problem"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by alan_daniel on 2006-12-20
Hey, I'm using Ubuntu Edgy on a Thinkpad T43, and because laptop sound cards are widely known as being sub-par, I decided to get an external USB sound device to be used as a sound card. It's a Philips PSC805 Aurilium. When I plugged it into the computer running Ubuntu, the system picked up a new sound card just fine, and it even opened up the sound preferences in gnome. I got a test sound to work from the headphones that were plugged into the sound device, but I can't get any other sound to work. After a reboot, too, I have lost the ability to get even the test sound.

The device is listed as a sound card for the computer, and the computer seems to be recognizing and integrating it just fine, with the only problem being that I can't seem to get anything to play with it.

Anyone know how to fix this?

---

### Post by userundefine on 2006-12-20
Did you disable the other card?

Do a

> **asoundconf list**

then after you see your USB card on the list, do

> **asoundconf set-default-card *USBNAME***

where *USBNAME* is the card as it showed up after **list** command.

You may have to preface those commands with **sudo**, I'm not sure if it requires root privileges or not right now.

---

### Post by alan_daniel on 2006-12-20
Yeah, I've set the card as default, but it still doesn't seem to want to work...Still plays music with mplayer (which uses default sound card) through the computer speakers, not the usb device.

Edit: Actually, after a reboot, I tried playing mplayer with a random song, and this is what I got> alsa-init: using device default
alsa-lib: pcm_hw.c:543: (snd_pcm_hw_prepare) SNDRV_PCM_IOCTL_PREPARE failed: Broken pipe
alsa-init: unable to set hw-parameters: Broken pipe
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
alsa-play: write error: File descriptor in bad state
alsa-play: trying to reset soundcard
alsa-lib: pcm_hw.c:543: (snd_pcm_hw_prepare) SNDRV_PCM_IOCTL_PREPARE failed: Broken pipe
alsa-play: pcm prepare error: Broken pipe
alsa-lib: pcm_hw.c:499: (snd_pcm_hw_delay) SNDRV_PCM_IOCTL_DELAY failed: File descriptor in bad state


---

### Post by ojgville on 2007-01-18
I have a similar problem but, my USB card is not listed. I can however get sound out of the head phones when playing a CD just not anything else. running 6.10 on a toshiba tecra9000 with a broken sound card.

---

### Post by staticsage on 2007-04-21
This is what seems to work best for me:

> sudo gedit /etc/modprobe.d/alsa-base

I changed the line (near the bottom) that says "options snd-usb-audio index=-2" to "options snd-usb-audio index=0". This forces asla to use your usb card as the default soundcard. This will also fix the issues where everything will play through your external soundcard, but things like quicktime or flash will come out of your laptop.

Hope this helps.

---

