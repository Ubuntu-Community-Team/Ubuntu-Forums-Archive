---
title: "Logitech QuickCam Chat"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by xSauronx on 2007-01-27
Ive got a Quickcam Chat that i think should work, but am having some problems. 

Ive tried installing the spca5xx driver

Ive tried the qc-usb driver before that (though after that, and reading a bit, the spca seems more likely to be whats necessary)

I searched the forums for the output I got from lsusb:

Bus 001 Device 004: ID 046d:092c Logitech, Inc.

Using just the ID, i found 3 threads. Going through them I found a link to [ubuntu support page]("https://help.ubuntu.com/community/Spca5xx#head-7920e06984703f735918572ba8c0352d5a447b1d") to try troubleshooting the driver

When I modprobe i get this:

FATAL: Error inserting spca5xx (/lib/modules/2.6.17-10-generic/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

this page:
[supported camera list]("http://mxhaard.free.fr/spca5xx.html") would indicate the camera is supported

but im rather new to linux and am not sure what should be my next step. if anyone has any ideas, or if theres more information i should supply to get an idea of what i can try next, thatd be great. 

Im using xubuntu 6.10 on an inspiron 1000

before i forget, when i add the camera, i get a link in /dev/ for video and video0
but aMSN and camorama arent giving me anything but basic errors that theres nothing there :/

i feel like im most of the way there and with a pointer or two may be able to get this figured out

---

### Post by handband2 on 2007-01-27
xSauronx,

This worked perfectly for me.

Go here:  [http://www.ubuntuforums.org/showpost.php?p=1909921&postcount=1]("http://www.ubuntuforums.org/showpost.php?p=1909921&postcount=1")

The file to be downloaded brings an error because it was upgrade.  Here is the new one to download:  [http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz]("http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz")

---

### Post by xSauronx on 2007-01-27
> **handband2 said:**
> xSauronx,

This worked perfectly for me.

Go here:  [http://www.ubuntuforums.org/showpost.php?p=1909921&postcount=1]("http://www.ubuntuforums.org/showpost.php?p=1909921&postcount=1")

The file to be downloaded brings an error because it was upgrade.  Here is the new one to download:  [http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz]("http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz")

awesome, that *did* work perfectly!

thanks :D

---

### Post by Doug11 on 2007-01-27
After much screwin around,,this finally did it for me too.

---

### Post by Gsyman on 2007-03-11
Whilst trying to install Logitech Quickcam Chat on Edgy I tried to install Camorama. Apt-get gives error 'could find package camorama'

---

### Post by Mrs Twaddle on 2007-03-12
That worked for me, but i'm a funny blue colour. 
I had a more obscure webcam, and stupidly assumed the blue was because of that... 
So off i trotted to get a new more poular webcam, and i am still blue!! woohoo
Any suggestions much appreciated, though a quick search shows me blue is how it's gotta be.
Sorry for hijacking the thread

---

