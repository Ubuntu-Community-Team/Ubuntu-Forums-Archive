---
title: "Sony Handycam question"
date: 2010-08-11
forum: Multimedia Software
---

### Post by MrStill on 2010-08-11
I have a Sony DCR-TRV480 which records video to digital-8 tape. It has USB, Firewire, and av(RCA) out. It has USB stream capability. The camera is five years old now. I am trying to get video from the tapes to my laptop. My laptop, running Lucid, has only USB inputs.

Does anyone have any suggestions?

---

### Post by ronnielsen1 on 2010-08-11
I don't see too much googling. Does Ubuntu recognize the device? Plug it into your usb and post the output of lsusb (from terminal)

---

### Post by MrStill on 2010-08-11
> **ronnielsen1 said:**
> I don't see too much googling. Does Ubuntu recognize the device? Plug it into your usb and post the output of lsusb (from terminal)

Thanks for the reply,

I guess I had some luck; the camera's information is listed in lsusb output.

```

Bus 007 Device 003: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer
Bus 007 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 002: ID 054c:00c0 Sony Corp. Handycam DCR-30

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a104 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Though, I am not sure what step to take next.

---

### Post by no2498 on 2010-08-11
plug the cam in then turn it on
you may need to look in the cam's setting/setup to set it to computer

hope this helps

---

### Post by MrStill on 2010-08-11
Laptop is an HP tx2z and no such luck with just plugging it in.

I checked the /dev directory and noticed three extra entries when the camera is plugged in:

```

audio1
dsp1
mixer1

```

I guess my next step is to see how to collect information from these devices and see what I get.

---

### Post by ronnielsen1 on 2010-08-12
From googling it looks like the camera will work in kino. 
>  But I have heard that it works fine with
Firewire. Its USB that creates a problem. 

Do you have a firewire port you can try?
[http://list.digital-copyright.ca/pipermail/ilug-cal-discuss/2007-July/001496.html](http://list.digital-copyright.ca/pipermail/ilug-cal-discuss/2007-July/001496.html)

> luvcview is a camera viewer for UVC based webcams. It includes an mjpeg
decoder and is able to save the video stream as an AVI file.

From synaptic. Try to install luvcview and see how that works

---

### Post by MrStill on 2010-08-12
No luck on luvcview or firewire port on my box. I figure I will spend a good part of the weekend reading about about /dev/dsp devices, as I suspect that is where the information is being sent. Maybe I will find a solution there.

---

### Post by no2498 on 2010-08-12
with the cam plugged in in a terminal lsusb and now unplug it do the same

does show a diff ?

---

### Post by MrStill on 2010-08-13
> **no2498 said:**
> with the cam plugged in in a terminal lsusb and now unplug it do the same

does show a diff ?

Yes I notice a difference in the lsusb output and the devices shown in the /dev directory. 

lsusb shows make and model information about my camera when it is plugged in. But, there is no /dev/video1 (/dev/video0 is my laptop webcam). I am assuming that the information from the camera is going into /dev/dsp1. I am still looking into it.

---

### Post by curioussquid on 2011-03-08
MrStill,

Did you make any progress? My wife decided to give her aged sony camcorder (DCR-TRV245e) to her friend for our wedding. I am now left with the job of getting the data back off it, but it doesn't seem to play ball in either windows or linux land. I have tried the firewire route but no luck. I have also recorded the video when output on the S-video connector, but the digital->analogue->digital conversion results in very poor quality.

I was hoping to use the usb connection some how. The camcorder is listed as the same device under lsusb as yours;

```

Bus 003 Device 007: ID 054c:00c0 Sony Corp. Handycam DCR-30

```

Any tips?

Cheers

---

