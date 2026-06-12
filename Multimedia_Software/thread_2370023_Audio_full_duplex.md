---
title: "Audio full duplex"
date: 2017-08-29
forum: Multimedia Software
---

### Post by 4l3x2 on 2017-08-29
Good evening.

I have a new question.....

I disabled the integrated audio card of my motherboard and installed a little usb device with Mic in and Phones out, it is correctly detected and installed.
Using the Pulse Audio Volume Control I enabled the out with the 100% vol, the mic with 30% vol (due to too high signal level) and the monitor with 100% vol.

If I start Audacity I can record my voice, but I can never hear it in full duplex, ie singing a song with PyKaraoke or using any app of any kind.

Is there a way to do this?

Thank you very much for your help, of course :)

---

### Post by Autodave on 2017-08-30
First off, are you sure that your external sound card IS a duplex sound card?  Did you enable *Play through *in Audacity?

---

### Post by 4l3x2 on 2017-08-30
I just did an attempt to enable Play through and I heard my voice in duplex, with a very small delay (but far smaller than with Win 7), so I tried to correct it with Pulse Audio Volume setting -20ms Latency.
When I reopened Audacity and tried to record I got an error on the device, so I set it back to 0.

---

### Post by Autodave on 2017-08-30
OK, so it is duplex. What version of Ubuntu are you running? Have you tried opening you karaoke program and then opening pavucontrol? Look for input devices and see if the USB is found and can you choose it.

---

### Post by 4l3x2 on 2017-08-30
XUbuntu 16.04.3
Under PyKaraoke there is no way to select any device, only the freq. sampling rate, bit depth and stereo or mono.
In Pavucontrol the usb device is always selected as active and the integrated sound card is turned off, as it is in the bios after I configured it in this way.
The only difference is that when I launch PyKaraoke I can see a new output device in Pavucontrol, a Python device with 100% volume, but no differences in hardware configuration.

---

