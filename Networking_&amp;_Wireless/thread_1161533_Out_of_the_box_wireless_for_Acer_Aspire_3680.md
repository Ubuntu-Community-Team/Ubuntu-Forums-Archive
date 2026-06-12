---
title: "Out of the box wireless for Acer Aspire 3680??"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by redcrystalmoon on 2009-05-16
Hi, I've been working for the past few days on trying to get my mothers Acer Aspire 3680-2472 working with Ubuntu. I have been testing out Hardy Heron (because I think it's probably the most stable and also has longterm support for her) with a usb stick... She really wants to tell windows where to go, but I haven't been able to get her wireless working. As wireless is the only way she has to get online, if I can't get it working then her computer is basically useless.

I am thinking that I probably have to actually install ubuntu to test things out because I am told I have to reboot after some changes to enable them to work but rebooting while I'm working from a fob just wipes out all the changes I've made.

Oh did I mention I'm a complete newbie??

I have an acer aspire one netbook runing Jaunty and pretty much everything worked out of the box for me there so I didn't have to fool around too much with it. (Except the darn right slot card reader, but that's a whole other thread...)

So, the info for the wireless card in the acer 3680 is:  BCM4311 802.11b/g WLAN [14e4.4311]

I've tried to get ndiswrapper working but a lot of it is over my head and apparently I have that "Hardy bug" or whaever where I get 
modprobe - ssd instead of 
modprobe - ndiswrapper 
and when I ran the commands I found to fix it, it didn't work....

Anyway my question is, Does anyone know of a distro that WILL work out of the box for this machine because I do really want to get her computer running on Linux but I'm getting burnt out and I just don't have the knowhow to work around all this stuff.....

or, can anyone lay out an easy guide to getting this driver to work?

Ok, so also, when I go into system-> Hardware Drivers, it shows two drivers, none of which are enabled. they say this:
1) Broadcom B43 wireless driver (when I put my mouse oer it it says: "While this driver is free software, it relys on proprietary firmware which cannot be legally shipped with the operating system. Your hardware will not function without the firmware") 
When I click o enable this driver, nothing happens.
2)Broadcom STA wireless driver  (When I put my mouse over this one it says: "This driver is necessary to support the hardware, there is no free/open alternative. If this driver is not eabled, the hardware will not function"
When I click to enable this driver it says I need to resart my computer for the change to take effect, and again I can't really do that because I'm booted from a Fob and if I reboot it will just start fresh....

I'm very hesitant to install before getting the wifi to work from the fob because if it doesn't work then I have essentially bricked her system, but I'm begining to doubt if I can get it to work without actually installing...
I can get access to a wired line though (I've been fiddling with it for hours here at a friends place)

I only have a 2GB flash drive and I apparently don't have enough room on there to do all the upgrades and such even...

Ahh I'm just getting frustrated with reading tutorials and not understanding half of them and trying things that seem to get me nowhere so I thought I'd come on here and hope that someone can help me out with some answers...
So, Thanks and hopefully someone can assist me in this process...

---

### Post by yanvolking on 2009-09-15
Hi fellow newbie,
 
You probably found the solution to your problem since your last post.  But in case you have not, let me tell you I am in a similar fix as you.  I recently bought a new PC which came without an operation system because I wanted to run it on UBUNTU.  I already had a CD of UBUNTU 8.04 which[FONT=Arial][SIZE=1][COLOR=black] I installed.  I have a [COLOR=#333333][FONT=Arial]D-Link DWL-G122 USB Wireless device for connecting to Internet but the drivers that came on its installation CD are for windows only.  I can only connect to Internet through a WLAN so no possibility of connecting via cable.  I am a complete newby to Linux but have begun to understand that UBUNTU unconnected to Internet does not go very far software installation functions such as NDISWRAPPER and SINAPTIC need internet connection to function.  So how can I find and install a driver for my WLAN interface which works with UBUNTU without connecting to Internet?[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=1][COLOR=black][COLOR=#333333][FONT=Arial][/FONT][/COLOR][/COLOR][/SIZE][/FONT] 
[FONT=Arial][SIZE=1][COLOR=black][COLOR=#333333][FONT=Arial]I may have found the solution :[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=1][COLOR=black][COLOR=#333333][FONT=Arial][/FONT][/COLOR][/COLOR][/SIZE][/FONT] 
[FONT=Arial][SIZE=1][COLOR=black][COLOR=#333333][FONT=Arial][SIZE=3][COLOR=#000000][FONT=Times New Roman]**Ubuntu 8.10** provides full "out of the box" support for this device, using the [/FONT][/COLOR][/SIZE][COLOR=#000000]**rt73usb**[FONT=Times New Roman][SIZE=3] driver. In this case, there is no need to use ndiswrapper at all and there is no need to make any changes to the default [/SIZE][/FONT]**/etc/modprobe.d/blacklist**[FONT=Times New Roman][SIZE=3] file. After connecting the D-Link USB device, entering the command [/SIZE][/FONT]**lsusb**[/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=3] at the shell prompt should return something like this:
[/SIZE][/FONT]Bus 001 Device 002: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73][/COLOR]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]To check that the driver [/COLOR][/SIZE][/FONT][COLOR=#000000]**rt73usb**[FONT=Times New Roman][SIZE=3] is loaded, enter the command [/SIZE][/FONT]**lsmod | grep rt73usb**[FONT=Times New Roman][SIZE=3] and check that the output includes a line starting with [/SIZE][/FONT]**rt73usb**[SIZE=3][FONT=Times New Roman] , which means that the driver is loaded. [/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=3][FONT=Times New Roman]I've managed to make a UBUNTU 8.10 CD last night.  Tonight I will install it and try out the above proceedures. [/FONT][/SIZE][/COLOR]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]Interested in the result?[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT] 
[/FONT][/COLOR][/COLOR][/SIZE][/FONT]

---

### Post by yanvolking on 2009-09-16
I solved my problem by using one of my older WLAN interfaces (**D-Link airplus G DWL-G122)**:

Get UBUNTU 8.10 and install it as your Operating System with your **D-Link airplus G DWL-G122 **WLAN interface connected to one of the USB ports. the UBUNTU 8.10 CD comes with driver software that will recognise the interface and activate itself during the installation. This is all done without needing any internet interaction.

PROBLEM SOLVED!

I didn't try this out using the RTL8187_Wireless_LAN_Adapter (WISACOM), but I suppose that UBUNTU 8.10 has more inherent driver software than just for the D-link interface. If your particular WLAN device's required driver is not inherent in UBUNTU 8.10, try doing this with 9.04. As it it more recent, I am sure that it has even more driver software already installed.

---

### Post by Cuba71 on 2009-09-16
redcrystalmoon:

Broadcom provides Linux drivers for the BCM4311.  Visit the following link

   [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

