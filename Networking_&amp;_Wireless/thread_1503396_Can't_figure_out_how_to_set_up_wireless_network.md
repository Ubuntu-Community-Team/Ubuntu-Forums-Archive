---
title: "Can't figure out how to set up wireless network"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by Sonic42 on 2010-06-06
I'm running ubuntu 10.04 side-by-side with Windows XP. I'm having no luck at all with my Linksys Wireless-N WMP300 Network. When I click on the network indicator on the status bar, it opens a drop down that only mentions a wired network. I've been searching threads, Wikis, and guides all day but can't find an answer. It seems like everything I read is extremely vague. 

So what am I doing wrong?

---

### Post by 666f6f on 2010-06-06
If you don't see any wireless network then probably your Wifi adapter isn't detected. Do you have the option to install restricted drivers? (System > Administration > Hardware Drivers)

Also, can you post the command output of the following command? ```
lshw -c network
```

---

### Post by Jurgen Oscar on 2010-06-06
> **Sonic42 said:**
> I'm running ubuntu 10.04 side-by-side with Windows XP. I'm having no luck at all with my Linksys Wireless-N WMP300 Network. When I click on the network indicator on the status bar, it opens a drop down that only mentions a wired network. I've been searching threads, Wikis, and guides all day but can't find an answer. It seems like everything I read is extremely vague. 

So what am I doing wrong?

Hello Sonic42,

I am no expert here, and I am trying hard to make my WUSB11 (linksys) usb card working
for weeks and still CANNOT make it works.

But maybe, you could check on the syslog (System > Administration > Log file viewer),
and check for the atmel*.bin file that is probably missing.

HTH.

J.O.

---

### Post by marcoftheknight on 2010-06-06
Ok so what we have is 
this :
Dignostic Step 1: Does linux recognize my hardware fully ?

To see this we need to out put our hardware info because it's a usb this might be  a little different lest start with the basic info:
go to the terminal applications --> accesories--> terminal
type this code: sudo lshw -C network
copy pas information
Next peice of information

Type this code: lsusb

**3.2.2. USB Wireless Adapter**

 
[LIST=1]
[*]Open a Terminal (**Applications** | **Accessories**  | **Terminal**), type lsusb and press the  return/enter key. 
[*]Look through the output of the lsusb command  for an entry for your wireless adapter. 
[*]Once you have  identified your adapter, note down the contents of the chipset ID, this  will be in the form *104c:8400*
[/LIST]
Google is theres a driver for linux and a installation method or maybe you already have the driver isntall and your network settings arent correct also try plugin your wireless device into different usb ports to see if somehting pops up about getting a driver or driver in use or anything.

Thats kinda of a start  Ive never gotten my wireless working perfectly for me the speed isnt fast enough but I think its because of the stupid WPA security I have doesnt work well ubuntu mentions my chipset as having occasional slowness which it does and beyond my capcity to fix.


cools

---

