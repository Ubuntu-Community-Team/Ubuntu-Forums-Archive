---
title: "Mouse stopped working after plugging in Flash stick"
date: 2011-02-25
forum: Multimedia Software
---

### Post by davethewave83 on 2011-02-25
I plugged a cruzer 2.0gb flash stick into the PC running Ubuntu 10.10 and the mouse stopped working, it also did not mount the USB drive. Keyboard still works, I can navigate with the keyboard. I tried to do a bit of research but it's difficult with just a keyboard because I have been spoiled all my life with the convenience of a mouse, during the research I found someone who said to gedit /etc/modprobe.d/blacklist.conf and comment out usbmouse and usbkbd so I have done so, but it did not fix anything even after a reboot. 

I have disconnected the USB mouse and memory stick, rebooted, plugged them back in, tried different ports nothing is working and there is an error in the ALT+F# command-line screens "hub 2-0:1.0:Connect-debounce failed, port 1" "Connect-debounce failed, port 2" which repeats over and over and over... 

all this just from plugging in a memory stick, I'm not quite sure how to fix this. 

In synaptic I also re-installed anything I could find that was installed that had to do with "mouse" but that did nothing either. I really wish Ubuntu had a "System restore" as I am dead in the water here, with only a keyboard to try to fix things with. 

If anyone can tell me how to fix this I would appreciate it. This is actually my sister's PC, I convinced her to install Ubuntu and abandon windows because I never personally experience many issues with Ubuntu. It's a lot more embarrassing when it was my idea to give her Ubuntu and this happens :P, she will probably just want Windows back if I cannot fix this.

Windows is easy to fix this kind of problem on for me, just go to device manager and uninstall/reinstall the device and presto. I'm not sure how to do that on Ubuntu.

---

### Post by Yellow Pasque on 2011-02-26
Sounds like a bad USB controller issue or some other hardware issue. Maybe there is a BIOS fix..

First, make sure your id's are updated:
```
sudo update-usbids
sudo update-pciids
```
See if running lsusb before and after plugging the device shows any difference.Also, post lspci output so we know what hardware you have.
```
sudo lsusb -vv
sudo lscpi -vv
```

---

### Post by davethewave83 on 2011-02-26
solved

---

