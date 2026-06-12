---
title: "AE1000 installed but can't connect to router"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by ktam33 on 2011-01-05
Hello, 

I have managed to compile and install the driver for my linksys AE1000 adapter. I can scan and see my network (and several others) but can't seem to connect. I have read a few threads looking for clues but I can't seem to figure it out. My kernel is 2.6.35-24-generic and I am using the latest rt3572 driver (v2.5.0.0). 

Here are a couple of steps that I have taken:
1) The usb driver does work properly and connect on a Windows machine. 
2) Temporarily removed security from my router (uses WPA2). Still can't connect. 
3) Tried compiling and installing the previous version of the driver (2.4.0.2)

Any ideas? Thanks...

---

### Post by kennabec on 2011-02-08
Anybody have this combination working?  

Ubuntu 10.10 (2.6.35-25) plus Ralink rt3572usb driver 2.5.0.0 on x64?

Following directions found here ([http://www.fedoraforum.org/forum/showthread.php?t=244215](http://www.fedoraforum.org/forum/showthread.php?t=244215)) I was able to get this card working on a 32-bit setup (same as above just 32-bit).

On the x64 install, the drive appears to work ok, I can see the wireless networks.  I just can never connect.

Thanks

---

### Post by ericrichards420 on 2011-03-11
You say that the usb driver does work because it works on a windows machine? Are you trying to use the ndis-wrapper drivers for windows? that might be your problem because that will not work. do this step by step [http://ubuntuforums.org/showthread.php?t=1701471&highlight=ae1000](http://ubuntuforums.org/showthread.php?t=1701471&highlight=ae1000)

---

### Post by sixtyfourk on 2011-03-12
I have the exact same problem.  I can see networks but I cannot connect to them.

Did you get it to work?

---

### Post by bubba911 on 2011-03-18
I got rt3572USB 2.4.0.2 Workong on my Ubuntu 10.10

I could not get 2.5.0.0 working however, it would not let me connect, then give me a Kernel Error and freeze my Desktop.

Steps I personally took in setting up my Linksys AE1000.

1.) Plugged in old and dying Wireless-G card and downloaded
sudo apt-get install build-essential linux-headers-generic

2.) Unplug old card and open up the folder for your rt3572USB driver

3.)Open: /common/rtusb_dev_id.c - and add  
	{USB_DEVICE(0x13b1,0x002f)}, /* Linksys AE1000 */
inbetween #ifdef RT35xx and #endif // RT35xx //

4.)Open: /include/os/rt_linux.h - 
replace usb_buffer_free --> usb_free_coherent
replace usb_buffer_alloc --> usb_alloc_coherent
(leave rausb crap alone)

4.)Open: /os/linux/config.mk
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
HAS_QOS_DLS_SUPPORT=y

5.)Open Terminal window and go to the driver folder
6.) make
7.) sudo make install
8a.) if you device was already plugged in during make install process --> sudo modprobe rt3572sta
8b.) if your device wasn't plugged in during make install process --> Plug it in

9.) Hope this worked for you like it did me.




Funny thing is, is that I got the newest 2.5.0.0 drivers working on Fedora 14 x64 no problem. However Ubuntu either hates the driver, or hates all of us because I get the no connecting problem when I try using 2.5.0.0. However if I use 2.4.0.2 with my steps I can connect no problem.

Report success or miserable failure.

Going to try and attach my rt3572_2.4.0.2 folder with all changes made already....

```
http://www.megaupload.com/?d=LKXM31BD
```


I've used my method on the latest 3 kernel builds with success
current kernel: 2.6.35-27-generic
os: Ubuntu 10.10 x64


```
http://www.youtube.com/watch?v=cwMiHiaWtPI
```

---

### Post by ugmoe2000 on 2011-03-27
Thanks Bubba911! That did it for me... I'll be pointing folks over here for sure. Thanks too for taking the time to do a write-up/video on the process and providing the old drivers for download. You really went the extra mile here! :D

---

### Post by drewbeans on 2011-10-20
Sorry to bump this thread again but I have a question.

First off, thanks bubba for all the great information.  My issue comes about when I try preparing the driver so I can install it using your method:

I keep getting said error                                       make [2]" *** [/folder dir/os/linux/../../common/cmm_mac_usb.o] Error 1 followed by another error.

Did anyone else run into this issue using the v2.4.0.2 driver with Ubuntu 10.04.3 and linux headers updated to 2.6.32-29-generics?

I have been trying to figure it out for a while with no luck.

Thanks again

---

### Post by Turalyon on 2012-03-11
Hello Everyone,

I found a working solution that works perfectly on my computer.

I am using Ubuntu 11.10 (32 bit) and I am using the Linksys ae1000 wireless USB adapter. I am not 100% sure that it will work for every distro out there, but it worked perfectly for mine. All I had to do was open a terminal and then copy & paste the codes from the following link. There was no complicated procedures or steps to follow just simple copy & paste. I found it very useful considering the fact that the only terminal command I vaguely understand is "sudo apt-get install"

Here is the link

[http://blog.up-link.ro/ubuntu-how-to-build-and-install-linksys-ae1000-wireless-n-linux-driver-on-ubuntu-11-10/](http://blog.up-link.ro/ubuntu-how-to-build-and-install-linksys-ae1000-wireless-n-linux-driver-on-ubuntu-11-10/)

I hope this works for everyone else out there with the same issues I had, and good luck.

---

### Post by Turalyon on 2012-03-14
Sorry to repost so soon, sometimes I get a bit loopy with no sleep...

I thought it might be prudent to add the fact that I had to cnnect to a WIRED network in order for my above fix to work ^^^.

Cheers

---

### Post by Turalyon on 2012-05-06
Greetings Programs!!!

Here is a little update to my previous posts in this thread.

The fix I posted above ^^^ for the AE1000 in Ubuntu 11.10 (32 bit) also works perfectly in the new Ubuntu 12.04 (32bit). 

I did a clean wipe and install from 11.10 to 12.04 and had the same issues with the same wireless adapter, so I decided to try this fix and it worked perfectly, still no complicated procedures or codes to memorize. Just the same 'ol copy and paste.

I did have to connect to the internet with an ethernet cable the first time to make this work just like with Ubuntu 11.04, but once I finished the copy and pasting I unplugged the wire and the wireless AE1000 took over and worked perfectly.

Here is the link once again for quick reference.

[http://blog.up-link.ro/ubuntu-how-to-build-and-install-linksys-ae1000-wireless-n-linux-driver-on-ubuntu-11-10/](http://blog.up-link.ro/ubuntu-how-to-build-and-install-linksys-ae1000-wireless-n-linux-driver-on-ubuntu-11-10/)

---

