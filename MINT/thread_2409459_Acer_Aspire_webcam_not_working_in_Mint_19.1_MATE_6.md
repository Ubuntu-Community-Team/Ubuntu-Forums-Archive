---
title: "Acer Aspire webcam not working in Mint 19.1 MATE 64-bit?"
date: 2019-01-02
forum: MINT
---

### Post by RallyDarkstrike on 2019-01-02
Hi all - just did a fresh install of Mint 19.1 MATE 64-bit on an Acer  Aspire 5732Z laptop for an elderly lady. All is working perfectly except  Cheese, nor Skype nor VLC will show the webcam. Skype and Cheese just  say 'No Device Found'. There are no BIOS settings whatsoever for the  camera, so I know it's not disabled there. I don't see any keyboard  Function shortcuts that would enable or disable it either.

lsusb returns: ```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

``` 

  With no sign of anything that looks like the webcam.

lspci doesn't return anything that looks possibly like the camera either  unless I've missed it. The lady had Ubuntu 12.04 32-bit (ancient!) on  here before and it supposedly worked fine then. What's missing here?  Anybody have any suggestions they can give me so I can try to get it  working again for her...?

Cheers and thanks! [IMG]https://forums.linuxmint.com/images/smilies/icon_smile.gif[/IMG]

---

### Post by RallyDarkstrike on 2019-01-02
A bit more info - just checked in dmesg after a cold boot and I saw this:                            
   [[IMG]https://forums.linuxmint.com/download/file.php?id=46444&t=1[/IMG]]("https://forums.linuxmint.com/download/file.php?id=46444&mode=view")                                                 
  Could this be the webcam trying to be activated but failing? Any way to solve this?

I had read somewhere to try loading the uvcvideo module, so I ran: 
sudo modprobe uvcvideo


 Which seemed to complete without error - dmesg listed that it had registered a new interface driver uvcvideo.

Both Cheese and Skype still say 'no device detected'...?

---

### Post by RallyDarkstrike on 2019-01-02
Yet another update - I decided to unplug the webcam and plug it back in while the computer was running to see what I would get from dmesg:
(click the pic to enlarge it)
[ATTACH=CONFIG]282081[/ATTACH]

This seems like it could be a hardware failure...anybody else have any other ideas?

---

