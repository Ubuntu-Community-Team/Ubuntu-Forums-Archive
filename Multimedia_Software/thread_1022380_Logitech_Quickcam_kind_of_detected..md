---
title: "Logitech Quickcam kind of detected."
date: 2008-12-26
forum: Multimedia Software
---

### Post by deathchimp on 2008-12-26
Been running linux on my dads computer for a while, he was getting too much spyware in windows, and everything has gone great. He can't even tell the difference. Problem is he likes to use his webcam to talk to friends overseas. 
We are running Ubuntu 8.10
He has a Logitech Quickcam Plus.
lsusb shows:

Bus 001 Device 002: ID 046d:08f6 Logitech, Inc. Quickcam Messenger Plus

but not a single program will detect the presence of the webcam. There isnt even a Video0 folder in /dev/. Ive looked around and though everyone seems to be having problems many people seem much farther along than me. Even the dimmest glimmer of hope would be appreciated as well as any information on how linux handles webcams as I am new at all this. This is the last sticking point for linux, if I can get this working I will never have to clean another virus off his machine.

---

### Post by wolfen69 on 2008-12-26
go [here]("http://ubuntuforums.org/showthread.php?t=191770") for the tutorial. then go [here]("http://home.mag.cx/messenger/source/") for the qc-usb-messenger-1.8.tar.gz driver.

---

### Post by xc3RnbFO8P on 2008-12-26
And read this:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/22070]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/22070")

---

