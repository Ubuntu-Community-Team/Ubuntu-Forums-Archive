---
title: "Logitech USB Desktop Microphone"
date: 2006-02-01
forum: Multimedia &amp; Video
---

### Post by advoss on 2006-02-01
Im looking for some help in getting my USB microphone to work.  Both Sound Recorder and Recording Level Monitor show no input.

The only information about getting it to run on Linux that i have found is [here](http://www.daniel-lemire.com/blog/archives/2005/10/12/logitech-usb-desktop-microphone-under-linux/)

I got as far as the dmesg and found it does say ```
[4303538.218000] usb 3-2: new full speed USB device using uhci_hcd and address 7
```

From there on I havent been able to find equivalents of the steps the writer used.

---

### Post by advoss on 2006-02-08
Please offer some advice, please.  It is kind of an important piece for me.  Do I have to recompile the Kernel to fix this?

---

### Post by advoss on 2006-02-19
Ok despite the second part of the thing not showing up, It does show up in mixer as a microphone, however i cant get it to recored from there.  When disable the microphone on the soundcard (by pressing the microphone button so an X appears by) in both OSS and ALSA it still doest get audio from the USB microphone, and the levels on the Recording Level Monitor seem to move when ever the system makes a sound.

If the second part thing is my problem then i can switch to Debian because i know that it automatily does the second thing if thats important, but if Mixer sees it is a microphone, why cant i record to it, is there some other way i should set the computer to use the USB instead of the soundcard for the microphone?

Please move this to Newbie Forum if that will help be get replies, because i really need to make this work inorder to switch to linux.

---

### Post by mandragor on 2006-03-14
Make sure "snd_usb_audio" is loaded:

lsmod | grep snd_usb_audio

If you get no output you need to write the following:

modprobe snd_usb_audio

Then it should work - in theory. It still won't work in Audacity for example
though, some programs just don't let you choose to use /dev/dsp1.*sigh*

---

