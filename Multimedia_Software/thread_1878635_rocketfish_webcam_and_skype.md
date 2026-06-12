---
title: "rocketfish webcam and skype"
date: 2011-11-10
forum: Multimedia Software
---

### Post by pierreu1 on 2011-11-10
I am running ubuntu 10.10 and had no issues whatsoever when I was running 10.04 with regards to Skype and the webcam Rocketfish.

The first issue that I was not able to get around was the issue of my camera not showing in Skype. It has been about a year and talking to my wife has been okay, but she would prefer seeing me once in a while! :)

So, I googled and searched and followed a few advices. One of them was to get rid of Cairo taskbar, which meant I had no taskbar at all. That was fun! Anyway, I finally figured out I could download unity 2D taskbar, which indicated initially that I had skype. I could click on the shortcut and it actually worked. But the camera didn't, as usual.

I might have followed a few advice, removed Skype and reinstaled it, thinking that might do. It didn't, if not I would not be writing this! :)

Anyway, there is a short cut on my desktop. No skype in the taskbar options/apps. ANd when I click the Skype shortcut, I get the atrached screenshot error message. 

UPDATE:

I finally was able to find the SKype file and make it work.

Still, rocketfish webscam is not working. lsusb returned this:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 2222:3085 MacAlly 
Bus 004 Device 002: ID 04a9:1086 Canon, Inc. i560
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:6288 Microdia PC Camera with Microphone (SN9C202 + OV9655)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I googled 2222:3085 and skype, and got 1 single post: 

EDIT: I should have googled 0c45:6288. SO SORRY!

[http://ubuntuforums.org/archive/index.php/t-1748952.html](http://ubuntuforums.org/archive/index.php/t-1748952.html)

But, I am unable to have the webcam work in Skype. It does work anywhere else!

I am at a loss as to what I should do! 

Please help!

---

### Post by coldraven on 2011-11-10
Make sure that no other program is using the web-cam
Is it being listed as a device in Skype when you go into Skype>Options>Video?
If so, is the Test Video showing anything. Try shining a bright light at the web-cam, sometimes it is actually working but very dark.
If it is just dark, quit Skype and install guvcview from the Software Centre.
Run guvcview and uncheck "Auto gain" if it is listed.
If not then increase the brightness control.
No need to save, just quit guvcview and try Skype.

---

