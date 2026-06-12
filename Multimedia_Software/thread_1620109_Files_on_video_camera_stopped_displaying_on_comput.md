---
title: "Files on video camera stopped displaying on computer"
date: 2010-11-12
forum: Multimedia Software
---

### Post by greymoose58 on 2010-11-12
I'm not sure if this is an Ubuntu issue or not but I'm new to using a digital video camera and this seemed the logical place to start.
 
We've bought a cheap video camera for our son to make a movie. Files are stored on a 16Gb SD disk. When we first used it a week ago I was able to connect the camera via USB and copy the files to my laptop. Today I went to clear some more files to make room for shooting the movie and nothing shows up when the camera is attached to the laptop. I can view the files on the camera so they do exist.

I have tried: [LIST]
[*]Using different usb ports
[*]Using a different computer
[*]Using an SD Card Reader on both computers
[*]Investigating permissions via terminal (the camera seems to be set to RWX --- ---)
[*]Checking that no one has played with the settings on the camera
[/LIST]

Nothing has changed on the camera or the laptop as far as I can see and yet the files are not showing up.

Camera Model: HD-C2 2.7" LCD 12MP
Ubuntu Version: 9.10 Karmic Koala

Any suggestions would be greatly appreciated.

Thanks.

---

### Post by no2498 on 2010-11-13
more of a ?
can you sign in as a diff name

---

### Post by greymoose58 on 2010-11-13
Thanks for your reply.

My question is: Does anyone have any idea why the files on the camera have stopped showing up without any changes being made?

I have just tried logging in as a different user with the same result. My user has more permissions than any other on the machine and the one I just tried has less than any other. The camera only shows up in the active user, the other one is unable to mount it. Thanks for the suggestion, by the way - I didn't think of that.

I have also just tried to connect to the camera via a Virtual windows Box that I use for previewing websites. The camera doesn't even show up. That may be a setting in Virtual Box of course.

Other ideas anyone?

---

### Post by owise1 on 2010-11-13
can you post the output of dmesg after you plug in the camera

Also how did you disconnect the camera the last time you used it?

---

### Post by no2498 on 2010-11-15
owise1

had this happen to me
Also how did you disconnect the camera the last time you used it?


also look for dust in all connections of the cable

---

