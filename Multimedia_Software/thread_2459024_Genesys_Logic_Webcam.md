---
title: "Genesys Logic Webcam"
date: 2021-03-08
forum: Multimedia Software
---

### Post by grey1beard on 2021-03-08
This pretty cheap webcam works well on my 32 bit laptop running Ubuntu 16.04, with a plug and play set up.
I've just done a clean install of 16.04 on my 'new' 64 bit hp ProDesk SFF desktop, with only minor issues, but it doesn't want to run my webcam.
**lsusb** in Terminal identifies it as being present, but Cheese,  VLC, and Zoom are **'unable to open'** it.
I've hunted round for any hints, but so far nothing.
If it had been a different os, I would have suspected a driver issue, but does switching from a 32 bit version to a 64 bit one hold the clue ?

John
EDIT See below for new OS update

---

### Post by grey1beard on 2021-03-13
I've now completed a fresh install of Ubuntu 20.04, but still cannot get the web cam to work.
In Terminal

** lsusb **gives > Bus 003 Device 008: ID 05e3:0503 Genesys Logic, Inc. Webcam. 

**v4l2-ctl --list-devices** gives
> USB2.0 UVC PC Camera; USB2.0 UV (usb-0000:00:14.0-7):
/dev/video0   
/dev/video1

If I open Cheese, it shows a black screen - no image.

If I open VLC/Open Capture Device I get an error message

> Your input can't be opened:
VLC is unable to open the MRL 'v4I2:///dev/video0. Check the log for details.

Your input can't be opened:
VLC is unable to open the MRL 'v4I2:///dev/video1. Check the log for details.

I've searched the web, but not got any further.
Any help ?

---

### Post by grey1beard on 2021-03-15
I found the answer on Askubuntu. There seems to be a lot of enquiries re using snap to install vlc, and the suggestion was to remove it, and reinstall as follows.
> sudo snap remove vlc

sudo apt-add-repository universe
sudo apt-get update
sudo apt-get install vlc
As is often the case, I had to use the 'Capture Device' sequence twice, but then up came the image.

John

---

### Post by CelticWarrior on 2021-03-15
VLC snap can be used as well once we understand snaps confinement and permissions and act accordingly by enabling the required permission for a given snap.
Of course, many people don't like and don't want to understand how snaps work so that's exactly the knee-jerk reaction they always have: Uninstall snap, install deb.

It's great that you solved the problem that way and it's perfectly fine but for the future keep in mind that whenever installing a snap version of a given software you may need to enable additional permissions. In Ubuntu Software open the software's page and you'll see a bug red button "Permissions". Click it and enable what you need, all should be self-explanatory.

---

