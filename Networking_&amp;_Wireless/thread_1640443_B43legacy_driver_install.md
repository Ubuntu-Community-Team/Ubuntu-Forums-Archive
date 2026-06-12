---
title: "B43legacy driver install"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by campb.andrew on 2010-12-07
Goodnight all,

I'm having trouble getting my Broadcom wireless card to work with my new ubuntu 10.04 installation. I'm new to linux on a whole, so i know nothing about "sudo commads" and terminal and so forth as i've read in other posts.

My computer is a HP Compaq Presario 2100 currently running a 32-bit Windows XP Home Edition, System Pack 3 and i have 192MB Ram as well as an AMD Processor. I've installed Ubuntu 10.04 as i indicated above, but i cant seem to get the wireless adapter to pick up any signals. My ethernet port doesnt work, so this is my only method of connecting to the net. I would really love to get it working as Ubuntu runs faster than XP. :cry: 

I've already downloaded the b43-fwcutter thingy as i've seen indicated in many forums. But i dont know where to find the driver exactly. Most of the other forums are so confusing with the folder names, and directories and what not....sigh...Is it possible to take it from the drivers folder in windows rather than download it, and then transfer it to ubuntu? Or is there another way?

Please help :sad:

Thank you in advance. :KS

---

### Post by chili555 on 2010-12-07
Let's make sure what you have and then we'll decide what you need and how to install it. Please open Applications > Accessories > Terminal and type, exactly as I have it here:```
lspci -nn | grep -i 14e4
```Press Enter. It will spit out some details about your Broadcom wireless card. Jot them down and post all the details here.

For your information, b43-fwcutter goes out on the internet and locates a firmware package, downloads it and installs it in the correct location on your computer. Without internet access, usually through your ethernet connection, it's of little use. Save it, however; we may have a use for it later.

Do you have a USB key, if we need to transfer files?

---

### Post by kerry_s on 2010-12-07
connect to the internet via ethernet cable, then click system-> aministration-> additional drivers

kick back let it do it's thing, it'll find all the drivers you need.

sorry, my bag, missed the part about broken ethernet. ;)

---

### Post by campb.andrew on 2010-12-07
I have a usb key. I'll be back in a few mins. Thank you for your help by the way. :-)

---

### Post by campb.andrew on 2010-12-07
> **kerry_s said:**
> connect to the internet via ethernet cable, then click system-> aministration-> additional drivers

kick back let it do it's thing, it'll find all the drivers you need.

My ethernet port doesnt work. :-(

---

### Post by kerry_s on 2010-12-07
> **campb.andrew said:**
> My ethernet port doesnt work. :-(

yeah, i just saw that, sorry.

do you have the windows driver? cause ndiswrapper & ndisgtk is on the installer disk, you can use the windows driver to get it going, then replace it with the linux drivers once connected.

---

### Post by bkratz on 2010-12-07
Should you find the information Chili555 is asking for (bad English!) here is the link to get the files from the installation (live) CD.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

---

### Post by campb.andrew on 2010-12-07
Hey all, thanks for the help so far. I'm actually posting this via ubuntu. I tried the ethernet port again....and it worked. :-D..

Should i still use the terminal commands though?

---

### Post by chili555 on 2010-12-07
> **campb.andrew said:**
> Hey all, thanks for the help so far. I'm actually posting this via ubuntu. I tried the ethernet port again....and it worked. :-D..

Should i still use the terminal commands though?If the ethernet is working, you only need to follow the suggestion in post #3.

---

### Post by campb.andrew on 2010-12-07
Ok. Thank you. I'm going to update and then let you know how it goes...

Thank you once again for your help everyone.

---

### Post by bkratz on 2010-12-07
> **campb.andrew said:**
> Ok. Thank you. I'm going to update and then let you know how it goes...

Thank you once again for your help everyone.

Good Luck! Hope it turns out ok and remember to return and mark the thread as solved in the tools above, if it is, in case it helps someone else.

---

