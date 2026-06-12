---
title: "Genius Webcam works on a 32-bit laptop, but doesn't on a 64-bit"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by Gustavo Narea on 2007-11-25
Hello, people.

I have:
[LIST]
[*]A Genius Webcam ([COLOR="Navy"]VideoCam Messenger sn9c101 Ov76[/COLOR])
[*]A Dell Inspiron 6400 laptop ([COLOR="navy"]Linux valencia 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux[/COLOR]). It's completely up-to-date and runs Kubuntu Gutsy 32-bit.
[*]And, a Dell Inspiron 1501 laptop ([COLOR="navy"]Linux venezuela 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux[/COLOR]). It's completely up-to-date and runs Kubuntu Gutsy 64-bit.
[/LIST]

The webcam barely works on the 32-bit laptop (only Kopete recognizes it), but on the 64-bit laptop no program can read from the webcam.

Output of the following commands under the 32-bit laptop (when the webcam is plugged in):
```

gustavo@valencia:~$ caminfo
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "VideoCam Messenger sn9c101 Ov76"
Minimum size     : 160x120
Current size     : 0x0
Maximum size     : 640x480
Video inputs     : 1
 Input 0
  Name             : "SN9C102"
  Type             : Camera
  Audio            : no
  Tuners           : 0
Audio inputs     : 0

gustavo@valencia:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 003: ID 0c45:602e Microdia
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0458:0007 KYE Systems Corp. (Mouse Systems)
Bus 001 Device 001: ID 0000:0000

```

Output of the following commands under the 64-bit laptop (when the webcam is plugged in):
```

maribel@venezuela:~$ caminfo
CVideoDevice::CVideoDevice() could not query capabilities; is this really a video device?
CVideoDevice::ResetImagesRGB()
CVideoDevice::ResetImagesYUV()
Detected 0 Video4Linux devices.

maribel@venezuela:~$ lsusb
Bus 006 Device 001: ID 0000:0000
Bus 002 Device 003: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 003: ID 0c45:602e Microdia
Bus 004 Device 001: ID 0000:0000

```

Thanks in advance!

---

### Post by gerstrong on 2008-02-06
Hola Gustavo,

I use the same driver and had the same problem, until I compiled the driver and installed it.

Maybe it is not necessary to do that.

What you can do and helped me finally out of this, were the following commands.

sudo rmmod gspca
sudo rmmod sn9c102

hope it helps you too. Even on my 64-bit Ubuntu gusty I can use Skype with webcam!

I Wish you a lot of success!

---

### Post by Gustavo Narea on 2008-02-06
> **gerstrong said:**
> Hola Gustavo,

I use the same driver and had the same problem, until I compiled the driver and installed it.

Maybe it is not necessary to do that.

What you can do and helped me finally out of this, were the following commands.

sudo rmmod gspca
sudo rmmod sn9c102

hope it helps you too. Even on my 64-bit Ubuntu gusty I can use Skype with webcam!

I Wish you a lot of success!

Hello, gerstrong.

Thanks for your help! Unfortunately, it didn't work for me because those modules don't exist in /proc/modules.

Cheers!

---

### Post by itaBannet on 2008-02-26
> **Gustavo Narea said:**
> Hello, gerstrong.

Thanks for your help! Unfortunately, it didn't work for me because those modules don't exist in /proc/modules.

Cheers!

same problem for me! i've only found x86 drivers for SN9C102!

---

### Post by gerstrong on 2008-04-01
Sorry, i've forgot something

When you executed both commands, plug out the camera and then plug it in.

The light should go off, and you can use it!

That worked for me, even with Ubuntu hardy 64-bit beta

Greetz

---

### Post by gerstrong on 2008-04-01
itaBannet : If the drivers are not there, try to download and compile them.

search for gspca under google and download the source code, then compile it.

sn9c102 is included in the gspca package

Good Luck!

---

