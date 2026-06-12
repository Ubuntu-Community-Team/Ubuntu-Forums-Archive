---
title: "How to setting Up a second monitor? - Dual Monitors ?"
date: 2008-07-21
forum: Multimedia Software
---

### Post by ricardo072 on 2008-07-21
Hi all,

I've a deskTop, I working with NVidia driver version 173.14.09, and my video card is GeForce 6200/AGP/SSE2

1) My primary monitor is an Acer [ wideScreen 19", 1280x1024 ] everything works fine, but...

2) I have 32" Sony monitor, I have connected the HD-Cable between the HD-output video card of my desktop to the HD-In Sony monitor,... I'm aware that my Sony monitor supports 1024x768 resolution.

When I selected "Preferences -> Screen Resolution" to make changes, everything remains the same, I can't change anything.

How can I set up my second[Sony] monitor ? How can I set up my both monitors at the same time ? I no have idea....:confused:

Thanks in advance.

---

### Post by tamoneya on 2008-07-21
type:```
sudo nvidia-settings
```

---

### Post by ricardo072 on 2008-07-22
Oh sorry it didn't work.... I tryed to add the second monitor...

NVIDIA X Server Setting--> 
X Server Display Configuration --> [the second monitor is detected]
I clicked in the "Configure.." button...
and select.. 

1) "Separate X Screen".
2) Resolution 1024x768 - Auto
3) after this, I clicked "Apply" btn...

Inside the linux console, I got the following message:

richard@Home-WorkStation:~$ sudo nvidia-settings
[sudo] password for richard: 

(nvidia-settings:6154): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 0

I also got this error message:

Failed to set MetaMode (1) 'CRT-0: 1280x1024@60 @1280x1024 +0+0' (Mode 1280x1024, id: 0) on X screen 0

Would you like to remove this MetaMode?
Yes - No 

Any ideas ? Anybody can help me ?
I'm newbie in ubuntu... :confused:

---

