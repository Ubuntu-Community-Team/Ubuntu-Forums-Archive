---
title: "Webcam Hercules Classic - Help required"
date: 2006-12-08
forum: Multimedia &amp; Video
---

### Post by umuro on 2006-12-08
I need directions to install, in Edgy, a webcam - Hercules Classic. Is anybody using it?

---

### Post by loell on 2006-12-08
you can post your device id by doing

```
lsusb
```

---

### Post by umuro on 2006-12-08
I tried the instructions on [http://doc.ubuntu-fr.org/materiel/webcam_ov51x](http://doc.ubuntu-fr.org/materiel/webcam_ov51x)

And ended up getting

This is xawtv-3.95, running on Linux/i686 (2.6.17-10-386)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65

---

### Post by umuro on 2006-12-08
lsusb returns:

Bus 001 Device 003: ID 05a9:4519 OmniVision Technologies, Inc.

---

### Post by umuro on 2006-12-08
Ok. The cam works. And it has been working. The problem is in "xawtv". "xawtv" and the latest NVIDIA driver are not compatible anymore. "camorama" shows the webcam stream without any problems.

Instead of the french URL you can follow the same instructions in:

[http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall)

to install :Hercules Classic".

---

### Post by umuro on 2007-05-07
Well. all was successful until feisty.

Now the cam shows black&white and the image is tiled horizontally 3 times.

Heeelp

---

### Post by umuro on 2007-05-07
Well, using ekiga the cam is alright. It is "camorama" that has gone weird this time.

---

### Post by Hugolp on 2007-08-10
Hi

My Hercules classic webcam was working fine in Feisty with kernel 2.6.20-15-generic (camorama was giving me the three images but the rest of programs were fine). But when I upgraded to kernel 2.6.20-16-generic it stoped working. It still works if I load with kernel 2.6.20-15-generic. More here: [http://ubuntuforums.org/showthread.php?p=3165959#post3165959]("http://ubuntuforums.org/showthread.php?p=3165959#post3165959")

---

### Post by jazzgossen on 2008-01-03
Did you ever get the problem sorted out with the new kernel?

I want to get a webcam, and Hercules Classic looks like the perfect choice for me (high still resolution, low price, good looks).

---

