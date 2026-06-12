---
title: "Webcam not working after system upgrade"
date: 2014-06-10
forum: Multimedia Software
---

### Post by rdh61 on 2014-06-10
Hi,

My Nilox USB webcam is not working with Skype or Cheese. When I try to open Video4Linux Control Panel, I am told:

"Unable to open file /dev/video0 No such file or directory".

(Yes, the webcam is plugged in!)

Before upgrading from Lubuntu 13.10 to 14.04 the webcam worked normally.

Any help gratefully received.

Many thanks.

---

### Post by dannyboy79 on 2014-06-10
what type of webcam is it? what does 
```
lsusb
```
return

---

### Post by rdh61 on 2014-06-10
The brand is "Nilox". I have no further info about it.

```
robert@robert-P4i65GV:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by dannyboy79 on 2014-06-10
is it a usb webcam cause if it is, it's not plugged in. right now it's only showing your HP printer

---

### Post by rdh61 on 2014-06-10
Thanks for your reply. As I stated in my first post, yes it is a USB webcam.

Yes, I can see that lsusb only shows my HP printer, but even so, you are mistaken, it* is* plugged in, again as stated in my first post.

---

### Post by dannyboy79 on 2014-06-10
if it's unplugged, then type in
```
dmesg
```
then plug it in and again issue
```
dmesg
```
paste back what the additional info is after you plug it in

---

### Post by rdh61 on 2014-06-11
As far as I can ascertain, the outputs of dmesg are the same whether the webcam is plugged in or not. I suppose the webcam may have a fault. I will try it on another computer and another operating system.

---

