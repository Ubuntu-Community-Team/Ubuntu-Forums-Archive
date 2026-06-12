---
title: "Can't capture video in Kino"
date: 2008-11-01
forum: Multimedia Software
---

### Post by DoctorBeaver on 2008-11-01
I'm trying to load a miniDV video from a video camera but when I click the capture button in Kino i gt this message:-

WARNING: raw1394 kernel module not loaded or failure to read/write dev/raw/1394!

I've checked and that directory doesn't exist.

Does anyone know what I have to do now?

---

### Post by xc3RnbFO8P on 2008-11-01
Ubuntu 8.04 (Hardy Heron)

The only reason that Kino cannot capture from Firewire in Hardy is that the software was compiled incorrectly. A correctly compiled version is available here: kino_1.3.0-2ubuntu0_i386.deb. This will not install on Ubuntu 8.10. 

[https://help.ubuntu.com/community/Firewire]("https://help.ubuntu.com/community/Firewire")

---

### Post by DoctorBeaver on 2008-11-02
Ringi - thanks for your help.

---

### Post by MakisM1 on 2009-07-02
New user with Jaunty. Got this one solved.

Kino gave me the same warning 'Module raw 1394 not loaded or /dev/raw 1394 needs permissions to read/write.

With file browser I went to /dev which I opened with Administrator rights' and found the file raw 1394. If you do a normal Open, you will not get the right to change permissions, as per below.

Right clicked on it and clicked on Properties

Selected the tab 'Properties' and selected Read and write for 'others'

Got out and Kino captured from my Sony Handycam DCR TRV33 fine.

Thought to save some newbies like me some trouble.

Best regards

MakisM

---

### Post by Yfrwlf on 2009-09-21
> **MakisM1 said:**
> New user with Jaunty. Got this one solved.

Kino gave me the same warning 'Module raw 1394 not loaded or /dev/raw 1394 needs permissions to read/write.

With file browser I went to /dev which I opened with Administrator rights' and found the file raw 1394. If you do a normal Open, you will not get the right to change permissions, as per below.

Right clicked on it and clicked on Properties

Selected the tab 'Properties' and selected Read and write for 'others'

Got out and Kino captured from my Sony Handycam DCR TRV33 fine.

Thought to save some newbies like me some trouble.

Best regards

MakisM

I hope this is fixed with Karmic Koala.  Users need easy out-of-the-box firewire support.  Anyone know if this problem has been solved yet?

I tried messing around in "authorizations" aka Policy Kit and tried adding my user to various devices under device-access like "video devices" and "firewire AVC devices" and other things and nothing I tried worked.  Either way of course is not ideal for a normal user.  At the very least, if this is some kind of real security issue, there should be some kind of prompt or mechanism in place to allow a user access to their firewire device when they need it of course.  Seems kind of silly to me though as you have access to USB devices...so how is firewire so different (aside from the fact that in a lot of ways it's better)?

---

### Post by bumanie on 2009-09-21
This is how I got kino going in both jaunty and karmic.

> sudo apt-get install kino
> sudo apt-get install dvgrab
> sudo apt-get install libraw1394-8
> sudo apt-get install libraw1394-dev
To start kino in terminal
> sudo kino
Initially, I could only get kino operating via opening as root. I have since tried changing ownership and I think it works OK.

---

### Post by Yfrwlf on 2009-09-23
> **bumanie said:**
> This is how I got kino going in both jaunty and karmic.





To start kino in terminal

Initially, I could only get kino operating via opening as root. I have since tried changing ownership and I think it works OK.

I've never had to install anything firewire-related, but perhaps I was just lucky and it was correctly detected on my system, but access to it simply wasn't granted.

---

### Post by bootdoc on 2009-10-17
I have been using Kino for a long time (ever since Dapper) and I have always had to run in terminal:

sudo chown *username* /dev/raw1394

to obtain the permissions for capturing.

---

