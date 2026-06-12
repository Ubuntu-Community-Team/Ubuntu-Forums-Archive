---
title: "Downloading video from Sony DV camera"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by Anders J on 2008-04-10
I have found that most connected gear just works right out of box and prompts med for appropriate drivers and programs.

But plugging a Sony DV camera to the computer via Firewire produces no reaction form the computer whatsoever.

I would like to take the digital video from the camera an dstpre that on any standard format or record on DVD.

Anyone out there that has a non-Windoze solution?

---

### Post by xc3RnbFO8P on 2008-04-10
Install  [Kino]("http://www.getdeb.net/app/Kino")
and read this:
[http://ubuntuforums.org/showpost.php?p=4649034&postcount=4]("http://ubuntuforums.org/showpost.php?p=4649034&postcount=4")
Install [Devede]("http://www.getdeb.net/app/DeVeDe") to convert file from .dv to dvd iso or mpeg.

---

### Post by Anders J on 2008-04-11
Thanks.

As far as I can judge, I have done what You described.

As I start Kino and choose capture, there is a warning message saying "raw1394 kernel not loaded or failure to read/write /dev/raw1394!"

I have set myself as the owner of that file with all permissions and I checked that /etc/modules/ have the four *1394 lines.

Any ideas what to do next?

---

### Post by xc3RnbFO8P on 2008-04-11
Before you start Kino do:

sudo modprobe dv1394
sudo modprobe video1394
sudo modprobe raw1394
sudo modprobe ohci1394
and I forgot 
sudo chmod a+rw /dev/*1394

Then in Kino Edit> preferences> ieee1394, do you get any warnings there?

---

### Post by Anders J on 2008-04-11
Nope. Edit/Preferences/IEEE1394 only shows an empty field AV/C Device:    .

The warning text only shows as I press "Capture" on the right side of the screen.

---

### Post by xc3RnbFO8P on 2008-04-11
Do have more information about your camera, model?

---

### Post by Anders J on 2008-04-11
Sony Handycam DCR-HC44E.

Edit: It is not my camera, so if this cam is less prone to work with Kino, there is always the possibility to feed the casettes into another camera to get the transfer done.

---

### Post by xc3RnbFO8P on 2008-04-11
> **Anders J said:**
> Sony Handycam DCR-HC44E.

Edit: It is not my camera, so if this cam is less prone to work with Kino, there is always the possibility to feed the casettes into another camera to get the transfer done.

Yes try that.

---

### Post by Anders J on 2008-04-13
I am afraid it was not that simple.

This cam, as well as another Canon DV cam, produced the same (non-)result and they both invoked identical and expected actions when connected to a Windoze computer.

So I am pretty sure that something is wrong with my firewire setup and that this has nothing to do with the camera at all.

How do I trace down this problem?

---

### Post by xc3RnbFO8P on 2008-04-13
Connect the camera and in the Terminal:>  **lsmod**
Look for this lines: 
> ohci1394               36528  2 dv1394,video1394
ieee1394               96312  5 dv1394,video1394,raw1394,ohci1394

and show output of:
> sudo gedit /etc/modules 

---

### Post by Anders J on 2008-04-16
OK, had to borrow the cam again, here we go:

from lsmod response

```
dv1394                 20824  0 
video1394              19800  0 
ohci1394               36528  2 dv1394,video1394
raw1394                31096  0 
ieee1394               96312  4 dv1394,video1394,ohci1394,raw1394
```

and

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
fuse
raw1394
video1394
ohci1394
dv1394
```

Any ideas?

Edit: I have a computer which I bought as a complete unit with a number of USB, audio and card reader ports on the front panel. And also a firewire port. But it is clear from documentation from the manufacturer of the motherboard that there is no Firewire port on the M/B. This means that the information that I was given is probably correct and the problem is most probably my hardware. My sincere apologies for wasting Your time.

---

### Post by xc3RnbFO8P on 2008-04-16
Here is Hardware Compatibility List:
[http://www.linux1394.org/hcl.php?class_id=3]("http://www.linux1394.org/hcl.php?class_id=3")

---

### Post by Anders J on 2008-04-16
Thanks again. I hope You did read my edit in the previous post, my front panel Firewire port has no connection to the M/B since there is no FW interface on the M/B!

---

### Post by xc3RnbFO8P on 2008-04-16
That is OK, this thread will hopefully help someone :)

---

### Post by Anders J on 2008-06-11
Almost two months later, a tried it once again, this time with a firewire board in the computer and this time it all worked as described.

Thanks again!

---

