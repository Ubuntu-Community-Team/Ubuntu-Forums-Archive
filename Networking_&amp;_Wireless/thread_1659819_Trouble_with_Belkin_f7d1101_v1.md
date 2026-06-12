---
title: "Trouble with Belkin f7d1101 v1"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by fliphkd23 on 2011-01-04
I bought the belkin f7d1101 usb wireless adapter months ago for windows, but recently I decided to finally give Ubuntu a try.  I installed 10.10 and very quickly realized that this is a terrible adapter to try use in linux.  

I tried ndiswrapper, compiling the driver given by realtek, along with a million other things.  I did however get it to work somewhat by using the guide given on the first post of this link [http://ubuntuforums.org/showthread.php?t=1522815](http://ubuntuforums.org/showthread.php?t=1522815).  

HOWEVER, for some reason the device only works about a quarter of the time I boot into Ubuntu.  Nothing changes between boots, but sometimes the device will power up and I can see/connect to wireless networks, and sometimes it just won't work at all.  I'm relatively new to linux, but I am fairly certain this is not a normal problem.  The only thing that I have noticed is it seems to work only after a hard reboot (power down by pressing and holding power button and not waiting for ubuntu to shut down properly). If anyone has any pointers, or insight into what is going on please help me out! This is driving me crazy!

A little info about my machine: gateway T-series laptop, dual booting with windows 7 (64-bit) and Ubuntu 10.10 (64-bit).

---

### Post by PatchesTheCaveman on 2011-01-04
Download the *rfkill* package by running this command on a terminal:
```
sudo apt-get install rfkill
```

Next time its not working, check to see if it's blocked:
```
sudo rfkill list
```

If it is, run this command to unblock it:
```
sudo rfkill unblock 0
```
Replace 0 with the number reported for your wireless adapter by the *rfkill list* command if its different.

Good luck!

---

### Post by fliphkd23 on 2011-01-05
Thanks for the tip, but unfortunately it didn't work. rfkill sees the device and reports that it is not blocked, but the usb adapter still isn't powered up or seeing any networks.  

Although, if I block the device and then unblock it, network manager goes from "wireless disconnected" to "device not ready". I'm not sure what this indicates (or if it has any relevance), but this is really starting to irritate me! It was upsetting that I had to hop on over to windows just to read and reply to your post, I was really getting to like Ubuntu....

---

### Post by fliphkd23 on 2011-01-05
Just for the heck of it I decided to try boot Ubuntu with an older kernel, 2.6.35-22 instead of 2.6.35-24, and I am pleased to say that the device appears to be cooperating much better. It seems that there is something about the 2.6.35-24 kernel that really does not want to play nice with this wireless usb adapter. Wonder what it could be...oh well it looks like the problem is solved for now!

---

### Post by PatchesTheCaveman on 2011-01-05
That version of the kernel breaks a lot of devices.  I have reported a bug to the kernel developers but they haven't fixed it yet.  To completely remove the broken kernel so you don't have to switch every time you boot and install the latest kernel that works properly, go to Applications > Accessories > Terminal and type each of the following commands in the black box that appears, pressing Enter after each one:
```
sudo apt-get remove linux-image-2.6.35-24-generic
sudo apt-get --reinstall install linux-image-2.6.35-23-generic
```

---

### Post by fliphkd23 on 2011-01-06
It now works without a hitch. Thanks for the help!

---

