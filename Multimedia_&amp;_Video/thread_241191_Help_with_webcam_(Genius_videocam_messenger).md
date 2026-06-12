---
title: "Help with webcam (Genius videocam messenger)"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by Emanuel Felipe on 2006-08-22
hi...

Ive just pluged my webcam and it works... but the image is so dark... in amsn I adjust the brightness to maximun, but still very dark...

maybe using wrong driver? something wrong with v4l? (dunno anything about it)

here is the webcam lsusb:

Bus 001 Device 005: ID 0c45:602e Microdia


if someone could help me.. tkz in advance...

---

### Post by Emanuel Felipe on 2006-08-22
bump

---

### Post by Emanuel Felipe on 2006-08-22
Dunno if it helps, but here [https://help.ubuntu.com/community/Spca5xx#head-abf4e347bdfd1f6955b8097f6541ddfe68eee51a](https://help.ubuntu.com/community/Spca5xx#head-abf4e347bdfd1f6955b8097f6541ddfe68eee51a) i found that my webcam is supported

> {USB_DEVICE(0x0c45, 0x602e)},       /* Genius VideoCam Messenger */

adn here [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) I got some infos that I cant understand exactly

> Genius 	142 	0x0c45 	0x602e 	NB350 	  	sn9c102 	OV7630 	Yes 	gbgr 	spca5xx 	****

Just remembering, the drivers seems to works fine.. but my image is very dark :( (in windows its fine).

---

### Post by macross3003 on 2006-12-08
same thing here using edgy

---

### Post by vir1980 on 2007-01-31
My image is the same, i see only dark pictures:confused: , but the camera is working fine:( , does anybody else have a camera like this and made it work a little more clear?  Im using edgy.

---

### Post by wxnker on 2007-02-12
I have the same problem with "Logitech Quickcam Communicate". The quality was great when I used Windows XP but in Ubuntu Edgy the picture is very dark and the quality is "so so"

I have not adjustet any settings. It worked when I installed Ubuntu, but the quality is poor and the image is very dark.

---

### Post by macross3003 on 2007-02-23
bumping

---

### Post by skimitar on 2007-04-01
Hi

You can try adjusting the gamma by passing a parameter when the gspca module loads.

With the webcam unplugged:

```
sudo nano /etc/modprobe.d/options
```

insert a line at the of the file:

```
options gspca gamma=4
```

save and then plug in the webcam. Open up your webcam viewer (e.g. Camorama)  If it is too bright (or too dark), then close the viewer and:

```
sudo rmmod gspca
```

change the gamma to another value and

```
sudo modprobe gspca
```

and have another look.

NOTE: I recompiled my webcam driver module so I am not sure if the default module is gspca or spca5xx. Either way, you can check what parameters you can pass to the module with:

```
sudo modinfo -p <INSERT MODULE NAME>
```

Cheers

---

