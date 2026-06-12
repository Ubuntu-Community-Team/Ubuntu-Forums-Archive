---
title: "Issue with USB Modem"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by JesCed on 2006-01-13
Hello, all.

I'd like to know if there is any way to get Ubuntu to connect to the Internet using a USB RYGE modem. I've read on another thread that this will be practically impossible to do.

However, I don't know if this will help, but my modem actually ships with Linux drivers on the installation CD. The drivers are for the 2.4 kernel, but I suppose that won't be a major issue (I hope I'm not wrong).

The problem is that, being new to Linux, I have no idea how to even try and see if the driver will work or not. Inside the 'Linux 2.4 Driver' folder I find the following files:

usbendpoint1.7.spec
USBENDPOINT-1.7-2.i386.rpm
USBENDPOINT-1.7-2.src.rpm
USBNET_E2_LINUX_110502_REL11a_E.tar.gz

Does anyone have any ideas as to what I can do with these? Is trying any of this going to give me a chance to get this working?

I'd really appreciate the input

---

### Post by Mr_Grieves on 2006-01-13
Does the modem come with a manual? Does the modem manufacturer have a homepage where they have install instructions? Is there any kind soul out there on the Internet ( hint: [http://www.google.com](http://www.google.com) ) that has put together install instructions for Linux?

What happens if you extract the USBNET_E2_LINUX_110502_REL11a_E.tar.gz file? Is there a README/INSTALL file there with instructions?

..and what kind of modem is it? Dial up?

---

### Post by mips on 2006-01-15
What model number is your Ryge modem, we need to identify it.

---

### Post by JesCed on 2006-01-17
Hello, and thanks for reading.

I haven't been able to find the exact model number, because it's not printed on the modem, box or manual. However, I CAN say that it's an ADSL modem, with USB and ethernet ports, which can function simultaneously (this is actually part of the issue... I've got two computers, and am trying to connect both of them to the Internet at the same time, so I'd like to connect one through USB and another through LAN (I've got the Ethernet connection running OK).

As to another one of the replies, I unpacked the tar.gz file, and found instructions for installation. Following them, I went to the folder and typed 'make'. The bash reply was make: command not found.

What else can I try?

---

### Post by mips on 2006-01-18
Are both pc's running linux ?

If one is running windows I recommend connecting the win pc via  USB and the ubuntu pc via ethernet and then use straight forward dhcp.

---

### Post by JesCed on 2006-01-25
Well, bot h PCs are actualle configured for dual boot under Ubuntu and Windows XP, but I'd like to be able to connect to tne internet from both computers at the same time, independently of the OS running at the moment.

---

### Post by mips on 2006-01-26
Well the ethernet part should be breeze, just use dhcp or static ip config depending on what your Ryge is setup for.

We'll have to do a google on your Ryge setup. You should be able to get the model number & stuff like that by accessing it's management interface via a web browser, there should be a section that gives you all the hardware details (Model, version, chipset etc), maybe you can find that and paste it here

---

### Post by JesCed on 2006-01-26
Well, configuring the access through ethernet WAS a breeze. I had actualle been ablo to set that up before ever posting for the first time... the connection was actually configured during install, so when I logged in for the first time, one of the first things I saw was a notification from the update manager.

However, even though I understand what you mean about accessing information through a web interface, I don't know where or how to do that. Any help on this?

---

### Post by mips on 2006-01-26
You need to know the modem/routers ip address. The route -n command in Ubuntu will give that to you or you can get it from a windows machine described as default gateway (ensure the connection is via ethernet) when you enter ipconfig /all.

Once you have the ip address you simply put it in your web browsers address field and hit enter. It will now try and connect to your router and you will most likely be prompted for a username & password which you either know or must get from your ISP.

The easiest way do do this is to probably buy a small 4-port hub/switch and connect that to the modem/router and then connect all the PC's via ethernet to the hub/switch.

---

### Post by mips on 2006-01-26
Double post

---

### Post by Ptero-4 on 2006-01-26
The archive you unpacked have the sources for the driver, which means you're very luvky b/c having the sources means that you'll be able to build a version of the drivers custom made for ubuntu. But first you'll need to boot one of your computers into ubuntu and while on the internet type "sudo apt-get install build-essential kernel-headers kernel-sources" (w/o quotes) in a terminal window and put your admin passwod when asked for it, that will give you the tools and headers/libraries necesary to build the driver. Once apt finishes installing everything go back and follow the drivers instructions you tried before.

---

### Post by cracker on 2006-01-26
As mips said, the best way to do this would be to get a 4-port router, switch, or hub, and create a LAN between all the devices. You would also gain the file and print sharing abilites of LANs in the home, and become OS independent. A router is the best choice, because it offers a hardware firewall from the internet, but a switch or hub would be much cheaper. If you live in the US, I suggest you look on newegg.com, as it will be cheaper than in a store and most other sites.

---

### Post by JesCed on 2006-01-28
Hello.

Well, I tried using the web interface to find out the information for my modem, and got as far as the address for my default gateway, but everytime I type the address into my browser, all I get is a timeout, so I can't find the information you've asked for (Why does my gateway time out, I wonder?).

Ive also jus found out another thing... apparently the ethernet on one of my computers (the one I've always connected through the USB) just isn't working. I've tried to connect through it from both ubuntu and windows, and it just doesn't work, so either i'll have to buy another ethernet card just to be able to configure the USB connection and use it again who knows when, ar am just stuck with the USB. For starters, assume I'm stuck with the USB.

I also read that using the CD I can build a customized driver for ubuntu. That sounds great, but I have a question at this point. Obviously, I can only get the required packages from the internet at the computer that's already connected. After I buid the driver, is it possible for me to copy it to the other PC? If so, how do I do that?

---

