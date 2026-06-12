---
title: "How to get old camera to work?"
date: 2008-06-03
forum: Multimedia Software
---

### Post by Thanh-BKK on 2008-06-03
Hello again.

Another question. I recently discovered that i still had an old camera lurking in a box, popped a couple of batteries in int and was surprised - it still works :)

It is a "CalComp Keter Eye-on" digital still camera that can also be used as a webcam, in fact under XP it WAS my webcam. 

So as an experiment i plugged it into the USB socket to see if Ubuntu can do anything with it (Vista could NOT). Well, Ubuntu can't, either.

However the device is detected when i do the "lsusb". 

So how can i make Ubuntu do *something* with it, either read what's inside it's memory (some pictures) or even enable it as a webcam?

Would be lovely if i would not have to chuck it back into the box under the bed and forget about it again - as i will never install XP again, THAT's for sure :)

With best regards.....

Thanh

---

### Post by prshah on 2008-06-03
> **Thanh-BKK said:**
> Hello again.

Another question. I recently discovered that i still had an old camera lurking in a box, popped a couple of batteries in int and was surprised - it still works :)



I have a similar one, only it's a mercury; holds about 26 hi-q digital pictures (VGA res) and a couple of mins of video;

I first saw it as detected in SANE; does it work in sane for you?

---

### Post by Thanh-BKK on 2008-06-03
> **prshah said:**
> 

I first saw it as detected in SANE; does it work in sane for you?

Hi :)

Thank you very much for that! I haven't tried that yet, but you know what? Under Vista, the cam also worked in my "scanner" program! And that was the only place it worked, and also only to "acquire" the pictures in it.

I will certainly give that a try once i am back at home (now at the office) and see if it works. 

I only know that, in "lsusb", the cam showed up as "Tek...." something, but i didn't know what to do with that device, as normally devices with some kind of memory in them are mounted as "drives" (like both the Sony digicams i have as well as just about every mobile phone, minus one of my Samsungs which also refuses to be detected at all) but that cam didn't mount as anything. 

It doesn't have a removable memory card tough, just something built-in, i think it, too, can hold around 20-ish VGA sized pictures or about 2 minutes video. 

Maybe we have very similar cams? Mine is the size of a pack of ciggies, but slimmer - small LCD display in the back that shows battery state and number of pictures in memory (or "USB" when connected to a computer), optical viewfinder, just a shutter button on top and a lens with a black ring around it that can be set to three positions - far, normal, macro (of which only "normal" works normal, both others are blurry). It runs on a couple of AAA batteries. 

(edit) found a (tiny) picture of it, and a description - here: [http://www.thaitechno.net/productdetails.php?id=1183&uid=3390](http://www.thaitechno.net/productdetails.php?id=1183&uid=3390)

I will let you know if i got it to work in Sane :)

Best regards.....

Thanh

---

### Post by prshah on 2008-06-03
> **Thanh-BKK said:**
> 
Maybe we have very similar cams? Mine is the size of a pack of ciggies, but slimmer - small LCD display in the back that shows battery state and number of pictures in memory (or "USB" when connected to a computer), optical viewfinder, just a shutter button on top and a lens with a black ring around it that can be set to three positions - far, normal, macro (of which only "normal" works normal, both others are blurry). It runs on a couple of AAA batteries. 


:lolflag: Yes similar cams.. these were very popular in India about 4 years back, when they were the cheap new entrants; they were (at that time) about 1/4th the cost of webcams and digital cameras! I had bought about 2 dozen of them over a period of 6 months!

Now they were just gathering dust, until chance and a desperate attempt to get an Epson scanner working made me realise it's alive!

---

### Post by Thanh-BKK on 2008-06-03
Hello again :)

Unfortunately, for me, Sane (or what i think is Sane - an application called "Xsane") does not detect the camera at all, it says "no device found".

I checked in Synaptic for other things with "Sane" and i installed subsequently "Sane" and "Sane-utils" however none of them shows up anywhere, and typing that into a terminbal also doesn't start any application.

I did what i did with my scanner, i.e. opened Gimp and went to "acquire" (which, with the scanner, opened Sane) but - nothing. 

And i was wrong with the listing in "lsusb" - the cam shows up as "Bus 003 Device 008: ID 03e8:2060 EndPoints, Inc.", that entry disappears if i unplug the cam. 

Hmm if you don't mind - what did YOU do to get your cam to work in Sane? I have meantime checked out yours, it is pretty much the same as mine but yours has a flash which mine doesn't. Everything else is identical (except for the looks, mine look different).

With kind regards......

Thanh

---

### Post by wolfen69 on 2008-06-03
the app "gthumb" seems to work well with digital cams.
```
sudo apt-get install gthumb
```
then go file>import photos

---

### Post by prshah on 2008-06-03
> **Thanh-BKK said:**
> Hello again :)

Unfortunately, for me, Sane (or what i think is Sane - an application called "Xsane") does not detect the camera at all, it says "no device found".

Yes, Xsane is the correct application.
> 
Hmm if you don't mind - what did YOU do to get your cam to work in Sane? 


I didn't do anything at all; it was just recognized. That was in Gutsy. In hardy, it shows up as a v4l (video for linux) device when plugged in, and is also available in Xsane.

Here's what I'll do; I'll plug it in and post the relevant lsusb and lsmod entries, along with a pic of the cam. I don't have the particular (non-standard) usb cable for it right now, I'll have to hunt around for it; just a couple of days max.

---

### Post by prshah on 2008-06-03
> **prshah said:**
> 
Here's what I'll do; I'll plug it in and post the relevant lsusb and lsmod entries, along with a pic of the cam. I don't have the particular (non-standard) usb cable for it right now, I'll have to hunt around for it; just a couple of days max.

In typical murphy's law fashion, found the cable within 2 mins of this post.

Anyway: ```

lsusb
Bus 005 Device 003: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
**Bus 002 Device 011: ID 0553:0202 STMicroelectronics Imaging Division (VLSI Vision) Aiptek PenCam 1**
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 0000:0000  

```
```

Tue Jun 03 23:27:14 ~:$ msgs
Jun  3 23:21:01 ubuntu kernel: [ 2330.955654] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv_init:376] STV(i): QVGA is supported
Jun  3 23:21:01 ubuntu kernel: [ 2330.967309] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv_init:392] STV(i): Camera has 0 pictures.
Jun  3 23:22:49 ubuntu kernel: [ 2438.921518] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [usb_stv680_remove_disconnected:1502] STV(i): STV0680 disconnected
Jun  3 23:26:37 ubuntu kernel: [ 2666.837119] usb 2-2: USB disconnect, address 10
Jun  3 23:27:04 ubuntu kernel: [ 2693.270836] usb 2-2: new full speed USB device using uhci_hcd and address 11
Jun  3 23:27:04 ubuntu kernel: [ 2693.554920] usb 2-2: configuration #1 chosen from 1 choice
Jun  3 23:27:04 ubuntu kernel: [ 2693.563070] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv680_probe:1425] STV(i): STV0680 camera found.
Jun  3 23:27:04 ubuntu kernel: [ 2693.563115] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv680_probe:1465] STV(i): registered new video device: video1
Jun  3 23:27:04 ubuntu kernel: [ 2693.696729] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv_init:376] STV(i): QVGA is supported
Jun  3 23:27:04 ubuntu kernel: [ 2693.707731] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv_init:392] STV(i): Camera has 0 pictures.
```

As soon as I plug it in, F-Spot pops up an import pics dialog; if I dismiss this dialog, the camera is immediately disconnected. If I leave this dialog open, I can see it in Xsane, and also as a v4l /dev/video1 device.

No extra modules, init, modprobe, anything. As you can see from the pictures, it's very much like what you described, even no flash. I think your camera _should_ work; maybe the cable is bad?

---

### Post by Thanh-BKK on 2008-06-04
Hello :)

Thanks again for all replies. Unfortunately today in the morning i didn't get to any experiments as i had to work on my motorbike :) When i'm back home in the evening i will try that "gthunmb", let's see what that does.

I am positive as the cam is detected as *something* at least, and as far as i know, if Linux sees that some device has been connected, it is possible to make Linux use that device. 

I tried F-Spot, too, however it says "no camera found" or something to that tune, so - no luck there.

The cable is definitely ok, because after installing the driver on my boyfriends (XP) laptop, the cam works fine there.

I don't necessarily NEED that camera to work, it's just that i am new to Linux and would like to try to get vaious devices to work - that cam, my Nokia phone (which is detected but it, too, can't be accessed), one of my Samsung phones (which isn't even detected), the USB-IrDA dongle (which is correctly detected but i have not yet found out how to send/receive files thru it) and the other IR thing that belongs to my old Casio "Wrist Camera" watch - a watch with a built-in camera which uses IR (non-IrDA compliant!) to transfer the pictures to/from a computer. The device is called "WQV-Link" and is of the serial variant. That didn't work under Vista either :)

With best regards.....

Thanh

---

### Post by Thanh-BKK on 2008-06-04
Hello once more.

Sadly, Gthumbs also says "No camera detected"......... i guess i really need to forget about this camera.

:sad:

Best regards....

Thanh

---

### Post by prshah on 2008-06-18
> **Thanh-BKK said:**
> 
Sadly, Gthumbs also says "No camera detected"......... i guess i really need to forget about this camera.


Stumbled across something new; with the camera unplugged, try ```
sudo apt-get install xserver-xorg-input-aiptek
``` then restart (to be on the safe side) and plug the camera in. Any joy?

---

### Post by Thanh-BKK on 2008-06-18
Hello :)

I just tried that.... still no joy. The camera shows up in lsusb as "EndPoints Inc" and has a device ID, but that's it - no program detects it as a camera or as anything else for that matter, even after installing the Aiptek thingy and rebooting.

Best regards.....

Thanh

---

