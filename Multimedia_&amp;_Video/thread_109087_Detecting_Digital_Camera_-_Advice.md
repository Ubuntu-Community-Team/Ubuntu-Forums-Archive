---
title: "Detecting Digital Camera - Advice?"
date: 2005-12-27
forum: Multimedia &amp; Video
---

### Post by jensbrown on 2005-12-27
Any suggestions on best methods to detect my digital camera (Olympus D-520) via USB?

My unbuntu install was detecting this camera two weeks ago, but now I 'gtkam' does not scan/detect the camera. The camera is connected via USB, directly.

SOme background, I have removed and reinstalled gtkam in an effort to troubleshoot. This has not worked.

Any advice, I'm exhausted my meager nubie unbuntu skills.....:confused:

Post or email me back please - [email]jensbrown@gmail.com[/email]

---

### Post by lrmall01 on 2005-12-27
If you open a terminal and type: lsusb, do you see the camera?

---

### Post by Zimmer on 2005-12-27
[QUOTE=jensbrown]Any suggestions on best methods to detect my digital camera (Olympus D-520) via USB?

Any advice, I'm exhausted my meager nubie unbuntu skills.....:confused:

Post or email me back please - [email]jensbrown@gmail.com[/email][/QUOTE]
Hello..
Some SERIOUS advice...buy a card reader and use that to unload material from the camera's memory card. I have a Trust 16-1 USB 2.0 card reader and it   recognises the Compact flash fine. Do not format the flash cards using the computer, though, best doing that in the camera to avoid problems. I have a Minolta and wouldn't dream of connecting it directly because of potential mount/umount issues should the batteries give out in the process (even on XP!).

Regards

---

### Post by anil_robo on 2005-12-27
It once happend with my camera too. Ubuntu simply won't detect it. I tried several things, none of which worked. I rebooted, and it started working again!

At a later date, something else happened. Ubuntu was able to detect the camera, but it won't download photos from it. Reboots didn't work. I rebooted to windows, which said the files on the SD card of camera were corrupt. So I unplugged the camera, used the "erase all" command within the camera itself, and then it started working again in Ubuntu.

The fault was not with Ubuntu. The fault was with me - I must have switched off the camera while it was still writing the images to SD card.

I think you can also try to reconfigure your gtkam package.
```
sudo dpkg-reconfigure gtkam
```

Let us know! :) Good luck!

---

