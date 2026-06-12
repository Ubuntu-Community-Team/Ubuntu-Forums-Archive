---
title: "How do I install Rosewill RNX-N180UB wireless Adapter"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by ReDRMo on 2010-06-10
Hi there,

I was wondering how to install the **Rosewill RNX-N180UB **wireless adapter?

[http://rosewill.com/products/1590/productDetail.htm](http://rosewill.com/products/1590/productDetail.htm)

It works on a XP PC, but not on my Ubuntu workdesk without playing with the code. I have downloaded the package, but since I'm a Noob: help would be really appreciated. (+ there's no computer shop that knows Linux around here...damn!)

Thanks!

---

### Post by musicman10489 on 2010-06-18
I am having the very same problem!
I found on the Rosewill website they have drivers for linux but the installation instructions do not seem to work for me. :[
Maybe you will have some different luck...
[http://www.rosewill.com/products/d_1590/productDetail.htm](http://www.rosewill.com/products/d_1590/productDetail.htm)

---

### Post by ReDRMo on 2010-06-21
No Luck yet... :(

If anyone knows how: would really appreciate the help!

---

### Post by musicman10489 on 2010-06-21
Same here :(
I'm afraid I just went out and bought the Netgear WG111 (v3) usb adapter....and it worked right out of the box....but I am still looking for a way to get the N180ub working on my other linux machine. Hopefully soon...

---

### Post by Anachronox on 2010-07-06
I'm having a problem with this too. I just installed 10.04 today and need to get internet set up so I can stop using Windows for a bit (I'm a linux noob). When I googled this problem all I got were multiple links to this thread. I have no idea how to get the driver from rosewill working and I tried ndiswrapper to no avail.

---

### Post by Ruuki on 2010-07-07
What's wrong with the installer? From first glance at the driver all you need to do is extract the tar and use the makefile method, and post the error please.

---

### Post by Anachronox on 2010-07-07
I'm pretty much completely new to Linux so I don't really know how to install it at all without the package manager deal, I don't know what the makefile method is. I tried to follow the instructions included with the driver but I couldn't really follow them. I saw a video on how to do the ndiswrapper thing but when I install the driver it just says something like unable to tell if the hardware is present. But on the installed driver list is says hardware is present. Any help is appreciated.

---

### Post by ReDRMo on 2010-07-23
Still need help! Don't know how this dumb network device install on Ubuntu... Have to work on Windows7 for now: until I know how to do this! 

Would really, but really appreciate a hand on this! 

Thanx in advance!

---

### Post by n.hinton on 2010-07-23
May have nothing to do with your issue, but installing linux-backports-modules-wireless-lucid-generic got my getnet USB Wireless Adaptor working.

---

### Post by r+9 on 2010-07-30
Same story, here is what I've learned.
{this part is all in the folder documents included in the linux driver tar file}
First: Rosewill drivers
For new folks to Linux, this is the scare part.
1. download the tar (its like a zip)
2. extract it (anyplace will do)
3. cd <extracted long name>/drivers
4. execute the command "make"
5. execute the command "./clean"
6. execute the command "sudo insmod 8712u.ko"
(what that command does is loads the modules to your kernel)
7a. execute the command "ifconfig -a" look for a wlan#
7b. execute the command "sudo ifconfig wlan# up" (mine fails here)

---

### Post by n.hinton on 2010-08-01
You are substituting the # in 7b with the wlan number you got from the results of 7a aren't you!

---

### Post by r+9 on 2010-08-10
Ha, yes I believe mine was wlan1, but it's hard to be specific without being too specific.

I'm going to take another crack at this tonight using ndiswrapper.  I'm only a white-belt in linux-fu so I'm not getting my hopes but, but I'll post if I find anything useful.

---

### Post by r+9 on 2010-08-11
No luck so far.  What's nuts is my wife has another rosewill wireless adapter that worked right out of the box.

---

### Post by tjktyler on 2010-08-12
I finally got my adapter to work, but it took a good deal of trial and error. For whatever reason, it seems that the adapter will not work unless the kernel module is loaded before it is inserted. 

Rosewill has a download package for the source of the Linux drivers, which included quick install documentation. I followed the instructions ```
make ; ./clean ; sudo insmod 8712u.ko ;
``` and then inserted the adapter. After many failed attempts, it became apparent that the "device [wasn't] ready" unless the module was loaded before insertion. 

To automatically load the driver at boot (which doesn't solve the load module before insertion; the adapter will need to be removed before or during shutdown), I added the 8712u.ko module to "/lib/modules/2.6.xx-xx/kernel/drivers/net/wireless" (replace 2.6.xx-xx with your complete kernel name) via ```
sudo mv [driver_location] /lib/modules/.../wireless
``` (replace driver_location with the complete path to the compiled driver and replace /lib/modules/.../wireless with the complete path to the ./wireless directory). I then added "8712u" to /etc/modules with ```
sudo nano /etc/modules
```

The adapter works, but it takes a good deal of effort to keep it that way.

---

### Post by r+9 on 2010-08-18
Does that mean don't insert the wireless adapter never-ever before loading the modules, or you will need to logout or reboot or 're-install linux'?

I have installed the modules before (and have rebooted since then), I just tried out your instructions and the mouse+keyboard froze up as soon as I inserted the wireless adapter.

I don't understand kernel-fu so I suppose more trial and error is necessary.

---

### Post by r+9 on 2010-09-24
during the make I get a lot errors:
warning: cast from pointer to integer of different sizerrors 

Which sounds like a 32v64 bit issue.  I'm not a C guy...

the interesting issue is my system appears to kernel panic when I install the device.

---

### Post by Anachronox on 2011-04-23
Been learning a little about Linux in school so I gave it another shot and was able to set this adapter up. It was a pain but in hindsight it wasn't that complicated. The driver installed fine following the provided instructions, my problem was setting up the connection. You can use the network manager gui. I was trying to do it in command line, after using the GUI I realized i put the encryption key in wrong. I'm on Linux right now, enjoying it.

---

