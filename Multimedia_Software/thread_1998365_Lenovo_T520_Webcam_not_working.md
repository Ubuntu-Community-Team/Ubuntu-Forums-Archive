---
title: "Lenovo T520 Webcam not working"
date: 2012-06-06
forum: Multimedia Software
---

### Post by IsmAvatar on 2012-06-06
I have a Lenovo ThinkPad T520 with Ubuntu 12.04 freshly installed. A webcam is integrated into the laptop.

I've been trying to follow the instructions on [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

I installed cheese, and when I run it, the camera area is just black, and the buttons below it are all grayed out.

I tried vlc:

```
$ ls /dev/video*
/dev/video0
$ vlc v412:///dev/video0
VLC media player 2.0.1 Twoflower (revision 2.0.1-0-gf432547)
[0x2031108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x7f1628000b78] main input error: open of `v412:///dev/video0' failed
$
```

Likewise, web applications don't pick up any video either.

Webcam works fine on Windows.

Is this a dead end webcam that will only work on Windows? Or can we get this working on Ubuntu?

---

### Post by zobcat on 2012-06-06
It seems it should work out of the box. [CERTIFIED]("http://www.ubuntu.com/certification/catalog/component/usb:04F2:B217-CAPTURE/")

---

### Post by IsmAvatar on 2012-06-06
Ok, that's promising. That's kind of what I figured too.

Then it's just a matter of figuring out why it doesn't work for me.

Like I said above, even Cheese doesn't give me any video, so something's wonked up. Anyone have any ideas? I'll need it for video conferences with my company, so it'd be great if we can get this working soon, so I don't have to put in a request for a separate cam or computer or something silly like that.

---

### Post by ammofreak on 2012-06-06
Hi ):P
Had same problem with my Logitech Pro 5000 webcam. As a workaround, I installed Google Chrome, then the Webcam Toy app from the Google store probably other webcam apps there too). Kind of a pain but it worked. Finally, I upgraded to 12.04 but Cheese did not work still. Did a *lsusb* on a terminal command line to see if the webcam was present. No webcam!. Plugged my webcam into another usb port. My webcam was present. Has been working ever since. Maybe this will help. I have to say though that I have always had problems with my webcam as far back as 9.04. But again, I am still using my Pro 5000. Cheers...:)

---

### Post by IsmAvatar on 2012-06-06
Google Chrome Webcam Toy app says "Sorry, no webcam found! Please check and try again", and then it provides me with an Adobe Flash Player Settings for Camera, which says "Cannot find camera".

Also, like I mentioned before, this is an integrated webcam, not a USB webcam, so I can't plug it into another usb port (nor should it show up in lsusb).

Any other ideas?

---

### Post by IsmAvatar on 2012-06-07
This problem seems to have resolved itself with a reboot. It may have been update related or something.

Thanks for your help anyways.

Solved.

---

### Post by Corpel on 2012-10-18
> **IsmAvatar said:**
> This problem seems to have resolved itself with a reboot. It may have been update related or something.

Thanks for your help anyways.

Solved.


I have the same problem. Reboot doesn't work here.
I don't know what to do !

---

