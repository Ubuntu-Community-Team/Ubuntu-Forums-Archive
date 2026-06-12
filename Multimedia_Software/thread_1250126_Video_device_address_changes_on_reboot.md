---
title: "Video device address changes on reboot"
date: 2009-08-26
forum: Multimedia Software
---

### Post by peterthebike on 2009-08-26
Back in March 2008 I had a problem where a webcam and video capture card did not keep the same address after a reboot. The solution [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=730132") used the udev command.

Is there a way to solve the problem under Jaunty?

---

### Post by eldragon on 2009-08-26
is that solution not working?

a little history.

before udev came along, linux users had to create the /dev files manually (or statically during boot), which made things really user unfriendly.

then udev came along, this ensures that when a new device is found, the appropiate /dev file is created. this means that during boot, your video devices are being detected and added sequentially, but the order of detection is not guaranteed. this is why you need to force udev to asign a special name to each device.

now, what that solution provides, is a static link to the automatically created /dev/video? node. so you should make your program access that link instead /dev/video? and you should be good to go.

im not sure if i made myself clear enough, or if i muddied the waters but the bottom line is that solution should work for you under jaunty too.

---

### Post by peterthebike on 2009-08-26
> **eldragon said:**
> im not sure if i made myself clear enough, or if i muddied the waters but the bottom line is that solution should work for you under jaunty too.

Can I first own up to being embarrassed by what I have done. I was using Skype to confirm my webcam was working OK, but could not see the device listed. After using a Fedora Live CD to see if it worked OK I noticed a USB cable loose by my USB hub. Then I remembered unplugging the webcam because it caused a problem with another piece of software!:oops: Plug the cable in and the webcam works.

I do still have a problem with my TV card as it needs to be known as NestboxCam. The file 11-video.rules used to have the contents:
```
KERNEL=="video?", BUS=="pci", SYSFS{subsystem_device}=="0x13eb",SYSFS{subsystem_vendor}=="0x0070", SYMLINK+="NestboxCam"
```

So in answer to your quote above, you have not muddied the waters, but I have no idea how to create the required static link!:-k

---

### Post by eldragon on 2009-08-26
> **peterthebike said:**
> Can I first own up to being embarrassed by what I have done. I was using Skype to confirm my webcam was working OK, but could not see the device listed. After using a Fedora Live CD to see if it worked OK I noticed a USB cable loose by my USB hub. Then I remembered unplugging the webcam because it caused a problem with another piece of software!:oops: Plug the cable in and the webcam works.

I do still have a problem with my TV card as it needs to be known as NestboxCam. The file 11-video.rules used to have the contents:
```
KERNEL=="video?", BUS=="pci", SYSFS{subsystem_device}=="0x13eb",SYSFS{subsystem_vendor}=="0x0070", SYMLINK+="NestboxCam"
```

So in answer to your quote above, you have not muddied the waters, but I have no idea how to create the required static link!:-k

that line above should do it (if its set up correctly), are you sure the subsystem_device and subsystem_vendor ids match?

if they do, check if the following file exists

```

/dev/NestboxCam

```

---

### Post by peterthebike on 2009-08-26
Dumb question coming - should I put a copy of the old 11-video.rules in the current /etc/udev/rules.d ?

---

### Post by eldragon on 2009-08-26
> **peterthebike said:**
> Dumb question coming - should I put a copy of the old 11-video.rules in the current /etc/udev/rules.d ?

let me see if i understand correctly..

you had a previous version of ubuntu, you created a custom udev rule to fix your name changing issue...

you upgraded to 9.04, and now the udev rule you created got removed? (ubuntu is known to do this during updates...)

if this is the case, then yes, you should place a copy under /etc/udev/rules.d

if you want to learn more about udev and how it works, i suggest the man pages..
```

man udev

```

---

### Post by peterthebike on 2009-08-26
> **peterthebike said:**
> Dumb question coming - should I put a copy of the old 11-video.rules in the current /etc/udev/rules.d ?

I thought "what the heck" and copied the file into rules.d. 

Guess what - it is working! (probably no surprise to you **eldragon**!)

Thanks for your help though.

---

