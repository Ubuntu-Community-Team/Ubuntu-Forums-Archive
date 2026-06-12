---
title: "webcam and tv card, is it one or another??"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by gaspar on 2007-01-18
Hi there.
I'm using Edgy, and some days ago, I finally got my TV Card working, it's a Brookthree hardware-based. Today, I finally got my webcam working, following the how-to ([http://ubuntuforums.org/showthread.php?t=303330&highlight=webcam)](http://ubuntuforums.org/showthread.php?t=303330&highlight=webcam)). 
But now, the TV card is gone, I have no idea why. TV time says it can't open /dev/video0 (the tv card itself).
Should I try to reinstall the TV Card and risk lose my webcam? Or I'm stuck in a circle here? ](*,)

Edit: sorry, it did not make my webcam work. Instead, it only changed the dev, and now the TV card is /dev/video1

Man, it's getting very very boring make it work...

---

### Post by Stemp on 2007-01-19
I had the same problem, webcam and tv card switching from video0 to video1.
Boring... so I created a /dev/webcam and a /dev/tv
But you can also use the /dev/vbi0 for your tv card (eg tvtime -d /dev/vbi0)

---

### Post by gaspar on 2007-01-22
Thanks, Stemp, I will try it. BTW, how did you make your webcam work?
Mine uses the spca5xx driver, but no succes trying to make it work, in anyway...

---

### Post by Stemp on 2007-01-22
> **gaspar said:**
> Thanks, Stemp, I will try it. BTW, how did you make your webcam work?
Mine uses the spca5xx driver, but no succes trying to make it work, in anyway...

If your webcam use the spca5xx driver (or the new gspca driver) it should work just out of the box !
Did you try with camorama ? or with mplayer (mplayer tv:// -tv device=/dev/video1:driver=v4l) ?

---

### Post by gaspar on 2007-01-22
Yep, I tried camorama, mplayer, amsn, xawtv, even cat /dev/videoX, but none worked. 
My webcam is a Braview 315MP; after a lot of searching, found it is compatible with the spca5xx.
what is the difference between the gspca and the spca?
The problem here is, when I use lsusb, looks like my cam was detected, but I can´t make it work under any app.
When I get home, I´ll post the output.
And, btw, thanks for your help, Stemp :-)

---

### Post by Stemp on 2007-01-22
> what is the difference between the gspca and the spca?

I think it's just a name change.

try this command to find the idVendor and idProduct of your webcam :
```
lsusb
```

by example the line of my webcam is :
```
Bus 001 Device 003: ID **046d**:**08a2** Logitech, Inc. Labtec WebCam Pro
```

---

### Post by gaspar on 2007-01-22
Ok, here's the output for lsusb:
[B]
Bus 002 Device 002: ID 102c:6151 Etoms Electronics Corp. [/B]
Bus 002 Device 003: ID 0079:0006  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

and, for dmesg (if it helps):

[B][17179590.380000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: USB Etx61xx51 camera found.Qcam Sangha Et61x151+Pas 106 
[17179590.380000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_probe:5480] Camera type GBRG 
[17179590.380000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_getcapability:1765] maxw 352 maxh 288 minw 160 minh 120
[17179590.380000] usbcore: registered new driver spca5xx
[17179590.380000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered
[17179590.444000] et61x251: V4L2 driver for ET61X[12]51 PC Camera Controllers v1:1.02[/B]

So, it's that Etoms E.C. does taht mean the spca5xx is working?

---

### Post by gaspar on 2007-01-23
So, after googling more last night, I found the driver is not the spca5xx, it´s the et61x251.
Ok, downloaded, trying to compile - nope, I need the latest stable kernel. 
I´ll try again tonite, and post the results...

---

### Post by Stemp on 2007-01-23
```
[17179590.444000] et61x251: V4L2 driver for ET61X[12]51 PC Camera Controllers v1:1.02
```

You are allready using the et61x251 driver. So your webcam is recognized.
But it seems to be a V4L2 driver only (no camorama but example : V4L only).

Try this command to try it using mplayer :

```
mplayer tv:// -tv device=/dev/video0:driver=v4l2
```

or 

```
mplayer tv:// -tv device=/dev/video1:driver=v4l2
```

---

### Post by koshimazaki on 2007-01-23
Hi Stemp,
i'm thinking about getting the labtec webcam pro so i'd like to ask a few questions:

Is your camera the one marketed as labtec webcam pro:
[http://www.labtec.com/index.cfm/gear/details/EUR/EN,crid=30,contentid=675](http://www.labtec.com/index.cfm/gear/details/EUR/EN,crid=30,contentid=675)
?

Did it work out of the box on edgy?

Did you try it with wengophone or ekiga?

Is the driver V4L or V4L2?

Do you know if it works with USB1.1?

Thanks : )

Oh, and hello, this is my first post on ubuntuforums : )

---

### Post by Stemp on 2007-01-23
> Is your camera the one marketed as labtec webcam pro:
[http://www.labtec.com/index.cfm/gear...,contentid=675](http://www.labtec.com/index.cfm/gear...,contentid=675)
?
Yes that's mine

> Did it work out of the box on edgy?
Yes no problems

> Did you try it with wengophone or ekiga?
Didn't try Wengophone, but work with Ekiga.
Don't forget this card is a basic one. 

> Is the driver V4L or V4L2?
V4L

> Do you know if it works with USB1.1?
I'm not sure , but I think so.

> Thanks : )
You're welcome

> Oh, and hello, this is my first post on ubuntuforums : )
Hello and congratulations.... Champagne !! :D

---

