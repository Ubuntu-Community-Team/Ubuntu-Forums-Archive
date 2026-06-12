---
title: "k9copy wont work"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by eazyeh on 2007-04-22
Please help, i installed k9copy on feisty and sucessfully copied 2 dvd's then in trying to do some configuration I selected to use opengl and now k9copy wont open. is there any way to fix this, i have uninstalled and reinstalled several times to no avail. i really like this as it saved me from having to boot windoze:popcorn:

---

### Post by Foxmike on 2007-04-22
OpenGL seems to make it crash under Ubuntu (gnome).  To unselect it, may paste the following in a terminal:

```
gedit ~/.kde/share/config/K9Copy
```Then, find the line that looks like this

```
/options/useGL=1
```(in mine, line 15)

Then change the "1" for "0".

It should work.

---

### Post by chasmanian on 2007-04-22
i can't find that file. when i type in that command, i get a blank doc. any ideas?

---

### Post by Foxmike on 2007-04-22
Okay, this is strange... I thought that files would be installed at same places... You will have to look around in your /home/(username)/ directory (with the option "show hidden files" enabled to find the K9Copy configuration file.

However, I just tried dvd95 which seems to be pretty neat, and gnome based.  It may be a good option for you to get something working while you find a workaroud for K9Copy.

Good luck!
-FM

---

### Post by MepisReign on 2007-04-23
Done this and now is running like a charm, THX!!

MepisReign

---

### Post by lefty.crupps on 2007-04-27
>Done this and now is running like a charm, THX!!

Does it still work?  My K9Copy hasn't worked at all with my Feisty fresh install.  I'm going to try DVD95 now!

---

### Post by ninhobomba on 2007-05-02
Yay! Thanks... I got my k9copy back!!
Am Happy. 
:popcorn:

---

### Post by EnigMattic on 2007-05-15
Thank you SOOOO much!!! :-D

---

### Post by Bd0g on 2007-07-05
Yepp, thx from me too.. 

Love txt files with settings :)

---

### Post by sefs on 2007-07-10
I just installed K9Copy and it does not start.

I can start it from the command line though, just not from the menu.

the oput in the term i get is 

```

X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
find: /dev/bus/usb/.usbfs/007: Permission denied
find: /dev/bus/usb/.usbfs/006: Permission denied
find: /dev/bus/usb/.usbfs/005: Permission denied
find: /dev/bus/usb/.usbfs/004: Permission denied
find: /dev/bus/usb/.usbfs/003: Permission denied
find: /dev/bus/usb/.usbfs/002: Permission denied
find: /dev/bus/usb/.usbfs/001: Permission denied
find: /dev/bus/usb/.usbfs/007: Permission denied
find: /dev/bus/usb/.usbfs/006: Permission denied
find: /dev/bus/usb/.usbfs/005: Permission denied
find: /dev/bus/usb/.usbfs/004: Permission denied
find: /dev/bus/usb/.usbfs/003: Permission denied
find: /dev/bus/usb/.usbfs/002: Permission denied
find: /dev/bus/usb/.usbfs/001: Permission denied
configDlg::setProperty( "modal", value ) failed: property invalid, read-only or does not exist
configDlg::setProperty( "sizeGripEnabled", value ) failed: property invalid, read-only or does not exist
find: /dev/bus/usb/.usbfs/007: Permission denied
find: /dev/bus/usb/.usbfs/006: Permission denied
find: /dev/bus/usb/.usbfs/005: Permission denied
find: /dev/bus/usb/.usbfs/004: Permission denied
find: /dev/bus/usb/.usbfs/003: Permission denied
find: /dev/bus/usb/.usbfs/002: Permission denied
find: /dev/bus/usb/.usbfs/001: Permission denied
configDlg::setProperty( "modal", value ) failed: property invalid, read-only or does not exist
configDlg::setProperty( "sizeGripEnabled", value ) failed: property invalid, read-only or does not exist
find: /dev/bus/usb/.usbfs/007: Permission denied
find: /dev/bus/usb/.usbfs/006: Permission denied
find: /dev/bus/usb/.usbfs/005: Permission denied
find: /dev/bus/usb/.usbfs/004: Permission denied
find: /dev/bus/usb/.usbfs/003: Permission denied
find: /dev/bus/usb/.usbfs/002: Permission denied
find: /dev/bus/usb/.usbfs/001: Permission denied

```

What would keep it from starting...

---

### Post by jackmc on 2007-08-02
thanks, worked for me :)

---

### Post by blueb73 on 2007-08-03
how do these programs handle Arcoss?

---

### Post by rustybronco on 2007-08-06
Add me the satisfied with this list. Thank you.

---

### Post by SonicJMC on 2007-10-09
> **Foxmike said:**
> OpenGL seems to make it crash under Ubuntu (gnome).  To unselect it, may paste the following in a terminal:

```
gedit ~/.kde/share/config/K9Copy
```Then, find the line that looks like this

```
/options/useGL=1
```(in mine, line 15)

Then change the "1" for "0".

It should work.

Thank you, you saved me much hair pulling

---

### Post by NewLover on 2007-11-28
> **sefs said:**
> I just installed K9Copy and it does not start.

I can start it from the command line though, just not from the menu.

the oput in the term i get is 

```

X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
find: /dev/bus/usb/.usbfs/007: Permission denied
find: /dev/bus/usb/.usbfs/006: Permission denied
find: /dev/bus/usb/.usbfs/005: Permission denied
find: /dev/bus/usb/.usbfs/004: Permission denied
find: /dev/bus/usb/.usbfs/003: Permission denied
find: /dev/bus/usb/.usbfs/002: Permission denied
find: /dev/bus/usb/.usbfs/001: Permission denied
find: /dev/bus/usb/.usbfs/007: Permission denied
find: /dev/bus/usb/.usbfs/006: Permission denied
find: /dev/bus/usb/.usbfs/005: Permission denied
find: /dev/bus/usb/.usbfs/004: Permission denied
find: /dev/bus/usb/.usbfs/003: Permission denied
find: /dev/bus/usb/.usbfs/002: Permission denied
find: /dev/bus/usb/.usbfs/001: Permission denied
configDlg::setProperty( "modal", value ) failed: property invalid, read-only or does not exist
configDlg::setProperty( "sizeGripEnabled", value ) failed: property invalid, read-only or does not exist
find: /dev/bus/usb/.usbfs/007: Permission denied
find: /dev/bus/usb/.usbfs/006: Permission denied
find: /dev/bus/usb/.usbfs/005: Permission denied
find: /dev/bus/usb/.usbfs/004: Permission denied
find: /dev/bus/usb/.usbfs/003: Permission denied
find: /dev/bus/usb/.usbfs/002: Permission denied
find: /dev/bus/usb/.usbfs/001: Permission denied
configDlg::setProperty( "modal", value ) failed: property invalid, read-only or does not exist
configDlg::setProperty( "sizeGripEnabled", value ) failed: property invalid, read-only or does not exist
find: /dev/bus/usb/.usbfs/007: Permission denied
find: /dev/bus/usb/.usbfs/006: Permission denied
find: /dev/bus/usb/.usbfs/005: Permission denied
find: /dev/bus/usb/.usbfs/004: Permission denied
find: /dev/bus/usb/.usbfs/003: Permission denied
find: /dev/bus/usb/.usbfs/002: Permission denied
find: /dev/bus/usb/.usbfs/001: Permission denied

```

What would keep it from starting...

Hi,

I've just experienced the same issue. Have you got any solution on this??? I tried it with "sudo" too, but k9copy didn't start. More exactly, the GUI seems to start after roughly 1 minute but dies immediately....

regards 
jensen

---

### Post by Kimos on 2007-12-10
Big help. I was looking in ~/.kde/share/apps/ for the config file.

To add, I was having trouble with the OpenGL setting for preview:

```
[preview]
MplayerAout=0
MplayerVout=0
useGL=true
useMplayer=false
```

Had to set the GL setting here to false.

---

