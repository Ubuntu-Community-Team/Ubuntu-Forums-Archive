---
title: "CME M-Key usb-midi keyboard (problems)"
date: 2007-12-29
forum: Multimedia Production
---

### Post by GorArn on 2007-12-29
Ubuntu Studio (7.10) does not recognize this keyboard on the usb port and does not set it up as it should. According to lsusb it is some Philips thing. 

Bus 001 Device 004: ID 0471:0010 Philips 

I have tried some suggestions found on the web bot without success. Anyone experiencing the same problem (and having a solution)?

---

### Post by kelnerv10 on 2008-01-03
Hello,

I have this same problem. Below is attached some /var/log/messages output:

Dec 31 12:31:27 localhost kernel: usb 2-4: new low speed USB device using ohci_hcd and address 3
Dec 31 12:31:28 localhost kernel: usb 2-4: configuration #1 chosen from 1 choice
Dec 31 12:31:28 localhost kernel: snd-usb-audio: probe of 2-4:1.0 failed with error -5
Dec 31 12:31:28 localhost kernel: snd-usb-audio: probe of 2-4:1.1 failed with error -5
Dec 31 12:31:28 localhost kernel: usbcore: registered new driver snd-usb-audio
Dec 31 12:35:00 localhost kernel: usb 2-4: USB disconnect, address 3
Dec 31 12:35:06 localhost kernel: ohci_hcd 0000:00:13.0: wakeup
Dec 31 12:35:06 localhost kernel: usb 1-3: new low speed USB device using ohci_hcd and address 2
Dec 31 12:35:06 localhost kernel: usb 1-3: configuration #1 chosen from 1 choice
Dec 31 12:35:06 localhost kernel: snd-usb-audio: probe of 1-3:1.0 failed with error -5
Dec 31 12:35:06 localhost kernel: snd-usb-audio: probe of 1-3:1.1 failed with error -5
Dec 31 12:35:46 localhost kernel: usb 1-3: USB disconnect, address 2
Dec 31 12:35:52 localhost kernel: ohci_hcd 0000:00:13.0: wakeup
Dec 31 12:35:53 localhost kernel: usb 1-3: new low speed USB device using ohci_hcd and address 3
Dec 31 12:35:53 localhost kernel: usb 1-3: configuration #1 chosen from 1 choice
Dec 31 12:35:53 localhost kernel: snd-usb-audio: probe of 1-3:1.0 failed with error -5
Dec 31 12:35:53 localhost kernel: snd-usb-audio: probe of 1-3:1.1 failed with error -5

---

### Post by GorArn on 2008-01-11
Hi, it feels comfortable to know that I'm not totally alone in this world. I tried another way around, i.e. use the midi out on the keyboard and connect it to the midi port of my soundcard (a SB Audigy 2 ZS). After a lot of trouble in getting cables and contacts this didn't work. I found out yesterday that the reason for this is that there is no support for the midi i/o on the sound card in ALSA. Back to square one...

I think I'll try to follow the USB route. Need to learn more about USB-devices...

---

### Post by GorArn on 2008-01-11
lsusb gives: Bus 002 Device 005: ID 0471:0010 Philips

The current list of usb units supported(?) by linux is found at

[http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)

There is no Philips device with device ID 0010 in that list but it is an interesting fact  that the CME devices listed by usb.ids are

7104  CME (Central Music Co.)
	2202  UF5/UF6/UF7/UF8 MIDI Master Keyboard

Although the M-KEY is not listed among those supported its interesting to note that the vendor ID 0471 is a permutation of 7104. Apparently the ID would be 7104:XXXX if the M-KEY was included in usb.ids (XXXX stands for the "would be" device number of the M-KEY). Is it possible to change the ID after connecting the device and will ALSA respond to that. The UFX are, as is the M-KEY,  said to be "usb midi class compliant" and should work on the spot.

Anyone with a suggestion?

---

### Post by GorArn on 2008-01-14
:) Solved! 

Got the info from an expert that low-speed USB is not supported (aalowed) by the present kernel (2.6.22) and ALSA (1.0.14) and that coming versions (2.6.23 ans 1.0.15) have a workaround. 

I'll wait...

---

### Post by dugald on 2008-03-07
I would like to add that users of the "U2MIDI" USB-MIDI device are in the same boat (same DMESG output etc).  Any idea when the kernel update is scheduled?  EDIT:  Okay, I see that 2.6.23 has been released but has to be built as a custom kernel for gutsy.  Has anyone tried the new kernel?  Does it support low speed usb-audio devices?

I will try it out iin a few days and post back.

---

### Post by dugald on 2008-03-09
Good News Everybody - I installed a 2.6.24.3 (latest) kernel and the midi interface works fine now.

I followed a giude to build the kernel.  It wasn't too tricky, but there are the usual problems with graphics, vmware etc.  Because you are installing a custom kernel, the restricted drivers package isn't available etc - you may wish just to wait for the next ubuntu release.

Really wasn't so painful though and certainly did the trick. :guitar:

---

