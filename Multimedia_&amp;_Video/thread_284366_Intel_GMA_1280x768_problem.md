---
title: "Intel GMA 1280x768 problem"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by Yako on 2006-10-25
I have a laptop: a HP Pavilion dv1668ea. It has an integrated graphics chip: the Intel GMA 945.
I am using Edgy Eft, and it all worked fine for me. I used 915resolution to get my 1280x768 resolution working, no problems.
Today I decided to install some v4l upgrade and the uvc kernel module to get my webcam working. It didnt succeed, but anyway, now the Xserver refuses to use the 1280x768 resolution, and falls back to 640x480.

In the Xorg.0.log it says this:
"(II) I810(0): Not using mode "1280x768" (no mode of this name)"
while there actually is a 1280x768 mode present in the video bios.

Could anybody tell me what the problem is?

---

### Post by Yako on 2006-10-28
I solved the issue by installing the xserver-xorg-driver-intel package, and used the 'intel' driver instead of the 'i810' one. This solved the problem. I think it was a driver issue, but I'm still puzzled by the fact that it used to work before, with the same configuration...

---

### Post by luvdemheels on 2006-10-29
What did you do after the install?? Just reboot or another command?

---

### Post by Yako on 2006-10-29
After installing the 'intel' driver, I did a sudo dpkg-reconfigure xserver-xorg, then I rebooted, and it worked out of the box.

---

