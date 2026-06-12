---
title: "Logitech Quickcam Chat in 8.10"
date: 2008-12-27
forum: Multimedia Software
---

### Post by freesitebuilder on 2008-12-27
I've got a Logitech Quickcam Chat, which works fine in XP, but in Ubuntu 8.10 I just get a black square whichever program I try. 


lsusb shows:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 05ac:1301 Apple, Inc. iPod Shuffle 2.Gen
Bus 004 Device 004: ID 046d:092e Logitech, Inc. QuickCam Chat
Bus 004 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 004 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Other info:
gspca_spca561          19328  0 
gspca_main             29312  1 gspca_spca561
videodev               41344  1 gspca_main
usbcore               148848  6 gspca_spca561,gspca_main,usbhid,uhci_hcd,ehci_hcd

I've been searching around, including this thread:
[http://ubuntuforums.org/showthread.php?t=984126&highlight=logitech+quickcam+chat](http://ubuntuforums.org/showthread.php?t=984126&highlight=logitech+quickcam+chat)

But before I start installing stuff that I don't really understand (I've only been using Ubuntu for a couple of years) I thought I'd ask for advice. I've read that the driver is preinstalled with 8.10, as the module info above seems to bear out, but I also got "Module gspca not found" when I followed some instructions on another thread to remove and reload the module.

An odd thing - when I boot, the light on the webcam comes on as it does in XP. But if I load a webcam program, such as Cheese, the light goes out - in XP it remains lit unless I unplug it.

I've also looked at this, and tried Camstream:
[https://answers.launchpad.net/ubuntu/+question/49739](https://answers.launchpad.net/ubuntu/+question/49739)
but the trace window just causes Camstream to close, and the light on the camera to go out. The main window is just black.

TIA for any advice.

---

### Post by itix on 2008-12-28
I had a logitech a while ago as well, but it was worthless, mostly due to the fact that the resolution was shitty and the light perception was useless, but also because it was not suported by Ubuntu... or actually, logitech didn't support linux at all.

That however does not seam to be your case since it's recognized by lsusb. It should be located at /dev/video0.

I'm not sure how to check if it works other than installing cheese (which is a webcam booth) and setting it to percieve /dev/video0.

I'm sure that there are a couple of cool commands for checking if /dev/video0 responds, but I don't know any such commands.

---

