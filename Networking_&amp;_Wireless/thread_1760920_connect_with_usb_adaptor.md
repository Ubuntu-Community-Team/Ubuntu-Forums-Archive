---
title: "connect with usb adaptor"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by patnm on 2011-05-17
Can't connect to wireless router using netgear usb adaptor.  Works with windows xp.  Please help.
Thank you,
Pat

---

### Post by 3xp10r3r|X13 on 2011-05-17
Hello there,
I'm sorry to disappoint you, but I've got bad news for you.

1. The usb adaptor probably needs some driver you haven't installed on ubuntu(maybe because it just exists for windows.)

2. As you probably know, ubuntu doesn't have a "perfect" hardware support, so it might just be that it's not compatible (I made the experience, that it supports a lot of hardware and to be honest ubuntu never disappointed me, referring to this sort of topic)

Sorry, but that's just my opinion :)

---

### Post by chili555 on 2011-05-17
Please open a terminal and run and post:```
lsusb
```Let's see what you need.

---

### Post by patnm on 2011-05-18
Hello,
Sorry I don't know what that means.  Just installed Ubantu because I get so mad at windows and wanted something new....but would have to have internet access for it to do me any good.
Thank you,
Pat

---

### Post by patnm on 2011-05-18
Thank you for your reply,
Pat

---

### Post by gordintoronto on 2011-05-18
> **patnm said:**
> Hello,
Sorry I don't know what that means.  Just installed Ubantu because I get so mad at windows and wanted something new....but would have to have internet access for it to do me any good.
Thank you,
Pat

"Netgear USB wireless adapter" describes a large number of different products, and you might need to know which one in order to make it work.

Run Accessories/Terminal, and enter the command:
lsusb

It should produce several lines of output, one of which should say Netgear. The nine characters after "ID" are the useful information.

Which version of Ubuntu did you install? Is there a network icon on the top-right corner of your screen, near the volume control?

---

### Post by patnm on 2011-05-18
Hello,
It's a Netgear WNA3100, the nine characters after netgear "id" are 0846:9020 and I have Ubuntu 10.10 installed as a dual boot with Win XP on a Dell desktop.  yes, there is a network icon and it says "no network connection.
Thank you for your reply,
Pat

---

### Post by gordintoronto on 2011-05-18
This is pretty techie stuff. Might be easier to just get a supported adapter.
[http://reminiscenza.livejournal.com/2969.html](http://reminiscenza.livejournal.com/2969.html)

Before you start that, run System/Administration/Synaptic Package Manager and install build-essential.

---

