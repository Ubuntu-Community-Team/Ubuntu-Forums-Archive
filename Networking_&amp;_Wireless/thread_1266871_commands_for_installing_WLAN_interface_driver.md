---
title: "commands for installing WLAN interface driver"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by yanvolking on 2009-09-15
Hello Community,
 
I may finally have found a way to get my PC connected to the internet via WLAN with UBUNTU.  I should forget UBUNTU 8.04 and get 8.10 as it "[COLOR=#333333][FONT=Arial]provides full "out of the box" support for this device ([COLOR=#000000]D-Link USB)[/COLOR], using the [/FONT][/COLOR]**[COLOR=#333333]rt73usb[/COLOR]**[COLOR=#333333][FONT=Arial] driver".[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]The instructions for this are:[/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3]"After connecting the D-Link USB device, entering the command [/SIZE][/FONT]**lsusb**[FONT=Times New Roman][SIZE=3] at the shell prompt should return something like this:
[/SIZE][/FONT]Bus 001 Device 002: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]
[FONT=Times New Roman][SIZE=3]To check that the driver [/SIZE][/FONT]**rt73usb**[FONT=Times New Roman][SIZE=3] is loaded, enter the command [/SIZE][/FONT]**lsmod | grep rt73usb**[FONT=Times New Roman][SIZE=3] and check that the output includes a line starting with [/SIZE][/FONT]**rt73usb**[SIZE=3][FONT=Times New Roman] , which means that the driver is loaded."[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]**[SIZE=4]Question 1[/SIZE]** : what is the shell?, in other words where do I have to enter the command "lsusb"?  could this be simply after the prompt of the terminal?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][SIZE=4]**Question 2**[/SIZE] : then where do I enter the command "**[FONT=Courier New]lsmod | grep rt73usb"?[/FONT]**[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]Thanks[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]:confused:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman][/FONT][/SIZE] 
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]

---

### Post by siiib on 2009-09-15
you type these commands in by opening a terminal.. with some of these commands you may have to add the word sudo to the beginning or otherwise you won't have the admin privelidges to use this command (noone ever tells you this..)
the wireless seems particularly flakey in ubuntu compared to other distros:(
hth

---

### Post by yanvolking on 2009-09-15
Thanks

---

