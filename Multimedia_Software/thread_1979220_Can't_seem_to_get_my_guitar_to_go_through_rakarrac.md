---
title: "Can't seem to get my guitar to go through rakarrack"
date: 2012-05-13
forum: Multimedia Software
---

### Post by nwhitt30 on 2012-05-13
Hello everyone,

I found rakarrack last week and as soon as I did I ordered a guitar USB linkup so that I can start using what looks like an awesome piece of software. 

here's the hardware i bought:

[http://www.newegg.com/Product/Product.aspx?Item=9SIA0U008J0861](http://www.newegg.com/Product/Product.aspx?Item=9SIA0U008J0861)

So i plugged it in today, and nothing happened, so I figured maybe I needed the drivers for the USB to work correctly. But when I started googling, I found that i could type into the terminal aplay -l and arecord -l. 

Here are the results: 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I came to the conclusion that the USB Audio CODEC was my guitar link USB cable. 

I saw other people requesting help as well, and I tried to follow instructions other people were given on other forums, and i got lost and confused. Maybe someone on here could help me?

I realize that in order to get it to work, I need to use Jack to properly route the signal through the proper channels so rakarrack would understand where to grab the guitar sound from, I'm just not sure how to go about getting that. 

At the moment I've got Jack Audio Connection Kit, Rakarrack, and my USB all hooked up, I'm just not sure how to properly configure them to work correctly... any help would be greatly appreciated..

Edit: I got the guitar to go through rakarrack, I can see the lines bounce when I strum my guitar, but I can't quite manage to hear the sound yet, what is the appropriate output that I need if I want to listen through the USB jack that is part of the guitar link?

Thanks!

---

### Post by reteo on 2012-05-14
> **nwhitt30 said:**
> Hello everyone,

Edit: I got the guitar to go through rakarrack, I can see the lines  bounce when I strum my guitar, but I can't quite manage to hear the  sound yet, what is the appropriate output that I need if I want to  listen through the USB jack that is part of the guitar link?

Thanks!

This might help:


Guitar line -> Rakarrack in_1
Guitar line -> Rakarrack in_2 (the signal can be split by connecting the guitar to each one)

Rakarrack out_1 -> Left Speaker
Rakarrack out_2 -> Right Speaker.

If your Guitar interface does not have speaker or headphone jacks, then  you will need to add your main sound device to the Jack graph.

This can be done using the following command:

```
/usr/bin/alsa_out -j "Speakers" -d default -q 1
```Once the "Speakers" outputs show up in the Jack graph, you can then use the Rakarrack outs to the new speakers.

I hope that helps!

I cover the multiple-device angle in a blog post at [http://www.penguinproducer.com/2011/11/using-multiple-devices-with-jack/](http://www.penguinproducer.com/2011/11/using-multiple-devices-with-jack/)

---

