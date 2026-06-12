---
title: "How to dial USB modem from ubuntu?"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by cerebrosus on 2009-08-29
Hello people,

I've dual boot computer (ubuntu 8.10 & XP) and i use HUAWEI E1550 USB modem to connect to the Internet. the following happends to me as I'm trying to connect :-

1- I connect to the internet through the USB modem succefully only when i connect to the internet from windows first (I mean: i've to boot from windows first and dial the USB modem then restart the computer and boot from ubuntu to find my self connected automatically) otherwise i wont be able to connect (if i booted from ubuntu first)

Please, help

---

### Post by GeorgeVita on 2009-08-29
Hi **cerebrosus**, most possible description for 'what is going on':

When powering up modem (Huawei E1550) is identified as the internal virtual CDROM (with windows drivers) and must be switched to modem state to be used by Ubuntu. You have not installed/used/managed the modem state to appear at Ubuntu. As windows can do it and when rebooting to Ubuntu the 'modem state' is already there and can be used.

You can check above doing: ```
lsusb | grep 12d1
``` booting Ubuntu directly and after windows.
If system shows different product IDs then you should try:
[http://ubuntuforums.org/showthread.php?t=1211787](http://ubuntuforums.org/showthread.php?t=1211787)

Post here or there any progress to follow up (including output of lsusb).

Regards,
George

---

### Post by cerebrosus on 2009-09-01
Thanks GeorgeVita. I installed udev-extras then added the custom udev rule 
for Huawei E1550 > echo 'SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"' | sudo tee  /etc/udev/rules.d/45-huawei1550.rulesand it worked very fine very stable. 

Now Huawei E1550 works on UBUNTU easier than on Windows. 


Many thanks GeorgeVita :D

---

### Post by KL-7 on 2009-10-12
Hi
I have almost the same problem (dual boot USB modem which starts correctly only after Windows and then Ubuntu booting), but I use Thomson, Inc. DCM245 Cable Modem.
How should I configure udev rules or smth else to get my modem working properly?

Thanks in advance.

---

