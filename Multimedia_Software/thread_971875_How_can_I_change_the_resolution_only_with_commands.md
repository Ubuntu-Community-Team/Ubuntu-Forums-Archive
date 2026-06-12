---
title: "How can I change the resolution only with commands on a terminal?"
date: 2008-11-05
forum: Multimedia Software
---

### Post by ljl16 on 2008-11-05
Hi, 
 A couple of days ago, I installed ubuntu 8.04 (on sunday). The fact is, that I changed resolution to 1440x900. Everything went fine at first, but after rebooting, everything was 640x480. I chose configuration, searched out my monitor, set up 1440x900 as resolution and booted the pc.
 Now, every time I start ubuntu, the display is all messed. It's like only 2/3 of the display monitor is used & the image is all segmented (you cant read anything, since the image is 3 times repeated, i.e. at every moment you see 3 mouse pointers & 3 of everything).

 That's why I would like to know a couple (or 1) command-phrases to change resolution. Is there not any "error-proof" mode like on windows? The only alternative of ubuntu at the startup on grub doesnt let me go into my desktop. Only to repair packages, write on a terminal & something related to X server.

Thanks in advance, hope there's a solution for this!

---

### Post by tuxxy on 2008-11-05
You could boot into recovery mode and try the xfix tool (hit ESC at GRUB boot and select recovery)

---

### Post by tangibleorange on 2008-11-05
> **ljl16 said:**
> Hi, 
 A couple of days ago, I installed ubuntu 8.04 (on sunday). The fact is, that I changed resolution to 1440x900. Everything went fine at first, but after rebooting, everything was 640x480. I chose configuration, searched out my monitor, set up 1440x900 as resolution and booted the pc.
 Now, every time I start ubuntu, the display is all messed. It's like only 2/3 of the display monitor is used & the image is all segmented (you cant read anything, since the image is 3 times repeated, i.e. at every moment you see 3 mouse pointers & 3 of everything).

 That's why I would like to know a couple (or 1) command-phrases to change resolution. Is there not any "error-proof" mode like on windows? The only alternative of ubuntu at the startup on grub doesnt let me go into my desktop. Only to repair packages, write on a terminal & something related to X server.

Thanks in advance, hope there's a solution for this!

like tuxxy suggested above, you can try fixing your xserver from recovery mode. if you want to change the resolution from the command line, look at the xrandr tool. for example:
```
xrandr -q
```
shows available resolutions and
```
xrandr -s 1440x900
```
sets to 1440x900. keep in mind the second command will only work if 1440x900 is listed as a possible resolution when you run the first command. if it does not show up, you may have messed up your driver.

---

### Post by tuxxy on 2008-11-05
Adding to tangible advice, if you can access and use a terminal you may save youself rebooting with 

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by goathunter on 2008-12-11
Hello. I had the same problem and fixed like you said> xrandr -q

.My question is how do i make this change permanent or better still restore it to default settings? At the moment everytime I reboot it loads with 512x384 when it should be 1024x768.
Any help would be appreciated.

---

