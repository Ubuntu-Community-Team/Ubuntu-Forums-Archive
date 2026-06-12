---
title: "Need help"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by jetbangdink on 2011-04-26
ok i have decided to install my cisco ae1000 there is a thread i am going to paste here and i need someone to walk me through it because i dont understand how to do somethings and i need to know if i have to be hardwired in a router for this to work

---

### Post by jetbangdink on 2011-04-26
**How to Install AE1000 rt2870 on xubuntu or ubuntu** 
Alright yall, I just got my wireless usb device to work on ubuntu 10.10. I did alot of searching and I finally figured it out. this is what I did.

1.Download the linux drivers from this post, its called Ralink_RT3572USB_drv2400.zip

2.Extract them to a directory.

3.Make sure you have *build-essential* installed on your computer. you can do this by opening a terminal
and typing Code:
 sudo apt-get install *build-essential *
4.Now install linux headers so that you can compile the drivers.
Code:
 sudo apt-get install linux-headers-$(uname -r)
5.Now in your terminal goto where you extracted the Ralink_RT3572USB_drv2400 files.
once in that directory type Code:
 sed -ir -e 's/^HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/' -e 's/^HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/' ./os/linux/config.mk
6.and then Code:
 sed -ir -e 's!^#endif // RT2870 //!        {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE 1000 */\n#endif // RT2870 //!' ./common/rtusb_dev_id.c
7.Now then goto the directory where you extracted the Ralink_RT3572USB_drv2400 files and goto Ralink_RT3572USB_drv2400/include/os "NOTE your directory may be differnt!!!" just make sure your find the file called rt_linux.h and open it with a text editor.

8.Now that we have rt_linux.h opened goto line 1077 or search for string **usb_buffer_alloc** change this to [B]usb_alloc_coherent

[/B]9.Now on line 1078 change** usb_buffer_free **to** usb_free_coherent** and and save that file.

10.Now you are ready to install the drivers. open your terminal and goto the directory where you extracted the drivers earlyer. and type 
Code:
 make && sudo make install
11. restart your computer and make sure that your adapter is plugged in.

These instructions are for xubuntu, and ubuntu 10.10 and newer. if you are using ubuntu 10.04 or older then do this process skipping step 7. and 8.
I'm using the ae1000 on a 550 mhz computer with 256 megs of ram using xbuntu. I have an up to date computer as well, this one was just for the a project.

---

