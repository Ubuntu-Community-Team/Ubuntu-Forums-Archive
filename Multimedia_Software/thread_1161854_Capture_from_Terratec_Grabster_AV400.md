---
title: "Capture from Terratec Grabster AV400"
date: 2009-05-17
forum: Multimedia Software
---

### Post by mbeccaria on 2009-05-17
Hi there all, 
I have used this device (Terratec Grabster AV400) for a long time on Windows for video capture.

Now I wonder if there's any application under ubuntu (currently I am still on "intrepid ibex") to capture (via USB) from this device a stream and save it in AVI/MPG format on my hard disk.

Does anybody know for example if Kino fits for this purpose ? It seems it is able to capture only from DV (e.g. camcorder) and not from USB.

thanks

---

### Post by xc3RnbFO8P on 2009-05-17
In Terminal show the output of **lsusb**

---

### Post by mbeccaria on 2009-05-17
> **Ringi said:**
> In Terminal show the output of **lsusb**
here it is

massi@massi-laptop:~$ lsusb
Bus 007 Device 009: ID 0ccd:0039 TerraTec Electronic GmbH Grabster AV 400
Bus 007 Device 006: ID 0d49:7410 Maxtor 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 006 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:3012 Dell Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by xc3RnbFO8P on 2009-05-17
And now the output of **dmesg **

---

### Post by mbeccaria on 2009-05-17
see attached file

---

### Post by xc3RnbFO8P on 2009-05-17
This is what I found:
[http://www.isely.net/pipermail/pvrusb2/2007-March/001447.html]("http://www.isely.net/pipermail/pvrusb2/2007-March/001447.html")

---

### Post by mbeccaria on 2009-05-17
> **Ringi said:**
> This is what I found:
[http://www.isely.net/pipermail/pvrusb2/2007-March/001447.html]("http://www.isely.net/pipermail/pvrusb2/2007-March/001447.html")

OK Thanks for the link
But before starting compiling and installing a new driver (is it a straightforward task ??) maybe someone already solved the issue on Ubuntu distro...

---

### Post by Yanai on 2009-05-22
Hi mbeccaria,

I just got my AV400 to work under Jaunty. Download the latest pvrusb2 drivers from [http://www.isely.net/pvrusb2/download.html](http://www.isely.net/pvrusb2/download.html), decompress the file, and within the *driver* directory do **make**, **sudo make install** and **sudo depmod -a**. After that, plug in your AV400 and the power LED should go green ^_^ You should now have a new device */dev/video0* (or with a higher number, if you already have some other video device installed), which you can stream into a .mpg file. For informations about selecting the right input port, please read the complete thread Ringi has mentioned, e.g. [http://www.isely.net/pipermail/pvrusb2/2007-March/001454.html](http://www.isely.net/pipermail/pvrusb2/2007-March/001454.html)

If this does not work, please check if you can find the files *v4l-cx2341x-enc.fw*, *v4l-cx25840.fw* and *v4l-pvrusb2-24xxx-01.fw* in your directory */lib/firmware/*. Otherwise you have to download the ivtv firmware from [http://dl.ivtvdriver.org/ivtv/firmware/](http://dl.ivtvdriver.org/ivtv/firmware/) and copy that files to */lib/firmware/*.

---

### Post by mbeccaria on 2009-05-27
> **Yanai said:**
> Hi mbeccaria,

I just got my AV400 to work under Jaunty. Download the latest pvrusb2 drivers from [http://www.isely.net/pvrusb2/download.html](http://www.isely.net/pvrusb2/download.html), decompress the file, and within the *driver* directory do **make**, **sudo make install** and **sudo depmod -a**. After that, plug in your AV400 and the power LED should go green ^_^ You should now have a new device */dev/video0* (or with a higher number, if you already have some other video device installed), which you can stream into a .mpg file. For informations about selecting the right input port, please read the complete thread Ringi has mentioned, e.g. [http://www.isely.net/pipermail/pvrusb2/2007-March/001454.html](http://www.isely.net/pipermail/pvrusb2/2007-March/001454.html)

If this does not work, please check if you can find the files *v4l-cx2341x-enc.fw*, *v4l-cx25840.fw* and *v4l-pvrusb2-24xxx-01.fw* in your directory */lib/firmware/*. Otherwise you have to download the ivtv firmware from [http://dl.ivtvdriver.org/ivtv/firmware/](http://dl.ivtvdriver.org/ivtv/firmware/) and copy that files to */lib/firmware/*.
Hi Yanai
everything was done according to your indications. 
When I plug-in the AV400, i see the /dev/video0 device. I can "cat" it on a file to display the mpg just after the vlc. Every firmware file  is in /lib/firmware.
**BUT**, there's one strange issue: the audio is bad, in the sense that is seems slowed-down/distorced.
Do you know if there's some setting to be done after the installation ?
Any help ??

P.S: my ubuntu is intrepid (8.10) and not jaunty.

---

### Post by mbeccaria on 2009-05-28
> **mbeccaria said:**
> Hi Yanai
everything was done according to your indications. 
When I plug-in the AV400, i see the /dev/video0 device. I can "cat" it on a file to display the mpg just after the vlc. Every firmware file  is in /lib/firmware.
**BUT**, there's one strange issue: the audio is bad, in the sense that is seems slowed-down/distorced.
Do you know if there's some setting to be done after the installation ?
Any help ??

P.S: my ubuntu is intrepid (8.10) and not jaunty.

I have attached my dmesg output in case someone could dig into it...

---

### Post by Yanai on 2009-05-31
> **mbeccaria said:**
> **BUT**, there's one strange issue: the audio is bad, in the sense that is seems slowed-down/distorced.
Do you know if there's some setting to be done after the installation ?
Any help ??


Hi mbeccaria,  unfortunately I have the same problem, I just did not watch the captured files to see that. In my case the sound is too high and too fast, by about 150%, but also the file runtime is decreased accordingly. If I change the audio sample rate to 44.1kHz instead of 48kHz, then the sound is too slow. You can check your sample rate by ```
cat /sys/class/pvrusb2/unit-a/ctl_srate/cur_val
``` and change it by e.g. ```
echo 44.1 kHz > /sys/class/pvrusb2/unit-a/ctl_srate/cur_val
``` To get all possible values do ```
cat /sys/class/pvrusb2/unit-a/ctl_srate/enum_val
``` I don't know what the problem is, if I use the AV400 under Windows everything is right. I tried several settings to solve it, but to no avail. As soon as I have more time I will try to find a solution, but at the moment I have no possibility.

---

