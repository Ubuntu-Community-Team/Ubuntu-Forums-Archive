---
title: "My Webcam (Acer Crystal Eye) is not being detected."
date: 2011-06-30
forum: Multimedia Software
---

### Post by Mildare on 2011-06-30
I've been having a few problems with it lately. I couldn't use it, but it was still being detected by hardinfo and when I typed up lsusb, it came up in the list of available devices. For some strange reason, Cheese couldn't use it, so I tried using luvcview instead, to find that the path /dev/video0 didn't exist. I changed the name of /dev/video1 to /dev/video0; thereupon, I could use my webcam with luvcview just fine, so I did a test call with Google Talk, and I could see myself fine, only it froze when I moved my screen. I did a second call, and a few seconds in, my image froze again, and my cam isn't being recognized by hardinfo or lsusb now. 

Any suggestions? Is my issue hardware originated, or do you think it might have had something to do with the fact that I changed /dev/video0 to video 1?

Also, I'm on Natty Narwhal 11.04.

EDIT: This is what I'm getting when I type "lsusb": 

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


My webcam used to be on Bus 005, so might there be a slight chance it's still being recognized?

EDIT 2: After doing "lsusb" several times I found that the webcam can be recognized on certain positions of the screen. Looks like my issue is hardware-related. Solved.

---

### Post by no2498 on 2011-07-01
in a terminal type dmesg click enter
just read it close to the bottom 
did it find the cam

---

