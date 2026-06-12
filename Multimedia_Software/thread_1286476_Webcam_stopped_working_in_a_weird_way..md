---
title: "Webcam stopped working in a weird way."
date: 2009-10-09
forum: Multimedia Software
---

### Post by jpmelos on 2009-10-09
Hello, everyone.

I'm having problems with my webcam. Now, I can give you a lot of info, so you guys can help me figure this out.

The platform:

Sony Vaio VGN-FZ250AE, what means the webcam is the default Sony Vaio Motion Eye Ricoh. I know people use to have a lot of problems with it, but please keep reading. The webcam worked on Ubuntu for months. Keep reading.

Running Ubuntu 9.04 upgraded to date.

Here comes the situation number one:

I had Windows XP installed, just so I could use my webcam to talk to my parents, who live very far and I can only visit them once a year. Someday, I decided to give my webcam one more chance in Ubuntu, and I installed Cheese. I was not expecting a good result. But the webcam worked. Perfectly. I even installed Skype, and the webcam started working there as well (what makes me think that maybe Cheese driver worked for Skype as well?).

The next day, I rebooted and it did not work. I was like "Oh, well... I didn't expect much anyway". But, after a few days, I decided to go in the terminal and type "sudo mkdir /dev/video0/". And the webcam begun working after a reboot. Worked for months. I uninstalled Windows (I seriously only had it for the webcam!).

Current situation:

Today, I had to reinstall Ubuntu. Inserted to disk into the drive, booted, installed, just like everyone does everyday.

Upgrades, installation of applications, appearance changes and the whole new-OS-protocol. Then, I installed Cheese, and what a shame, the webcam did not work. I tried to reproduce the environment of before, trying to remember what packages I had installed, and I ended up installing even more stuff that what was there before, like the dependencies to compile Cheese, Camorama, GStreamer, I installed EVERYTHING that appeared on Google when you type anything related to /dev/video0 webcam vaio cheese video4linux2... Everything.

Now, technical info:

What is the output as I type "lsusb", you might ask?

```
Bus 005 Device 002: ID 046d:c50a Logitech, Inc. Cordless Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 005: ID 044e:3012 Alps Electric Co., Ltd 
Bus 007 Device 004: ID 044e:3013 Alps Electric Co., Ltd 
Bus 007 Device 003: ID 044e:3010 Alps Electric Co., Ltd 
Bus 007 Device 002: ID 044e:3011 Alps Electric Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

As you can see from the bold line there, the system is somehow detecting the device, and yet it cannot see it as a webcam!

And what about "ls -l /dev/video0"?

```
ls: cannot access /dev/video0: No such file or directory
```

But, what happens when you run Cheese, or Camorama?

For Cheese, the usual color bars, the buzzy screen on the lower-right corner, and the notice "No camera found!".

For Camorama, "Could not connect to video device (/dev/video0). Please check connection."

Well, I can assure you, without a single doubt, that it's not a connection problem. The webcam worked everytime for years in Windows without a failure, it worked for months in Ubuntu without a failure, and I used it yesterday, when the OS was exactly the same (Ubuntu 9.04 upgraded to date)! It has to be a very, very, VERY unlikely coincidente. I'm sure the connection is working perfectly.

What about "luvcview -L"?

```
luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
ERROR opening V4L interface: No such file or directory
```

Do you any other information that could help? Let me know, and I'll answer as soon as I can.

Can you guys help me out with this? If I have to install Windows again just to use the webcam, I'll be really unpleased. Thank you very much!

---

### Post by Dthdealer on 2009-10-09
Looks like v4linux isn't installed, which web-came programs such as cheese use.  I don't know which package to install however to alleviate your problems. What you can do is check if the cheese dependencies are met.
```
sudo apt-get check
```

---

