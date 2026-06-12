---
title: "Dell Inspiron 1545 Ethernet and Wireless Won't connect"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by pokeman89 on 2010-09-15
I posted this earlier in the general help section, but was pointed here. I've been having trouble connecting to the internet. The network manager says "Device not ready" for the wireless and ethernet says "Disconnected." I tried connecting an ethernet cable but it wasn't detected. I have a Dell Inspiron 1545. I also tried connecting in Studio and OpenSUSE with no luck. Can someone help me get connected please? I tried getting the drivers, but the drivers it came up with could not be installed because I obviously wasn't connected to the internet.

Machine specs: Dell Insprion 1545, Dell 1397 WLAN Mini-Card, Marvell Yukon 88e8040 PCI-E Fast Ethernet Controller, Verizon is the internet provider, WEP Shared Key connection, 128 bit encryption, 64-bit OS, Windows 7 installed alongside.

---

### Post by pokeman89 on 2010-09-17
Can anyone help me?

---

### Post by TBABill on 2010-09-17
I wish I could offer direct assistance. Does your system work via ethernet in Windows? I imagine you run it normally via wireless.
 
I have a 1545 as well. Intel Core i3-330m CPU and it has a Broadcom wireless card. First thing to fix must be your ethernet port because, once working, you'll need to connect via ethernet, download updates and then install your wireless driver. The machine should detect that hardware drivers are available and prompt you to install them...for your machine that should only be the wireless unless you have an additional graphics card besides the on-chip GPU (Intel). 
 
If you haven't experienced it before, any install of Ubuntu or derivative will need to be connected via ethernet to download the Broadcom wireless driver since it is proprietary (till they include it in kernel 2.6.37 and later). So it will be critical to have ethernet connectivity after install. Hopefully someone can come along to help you troubleshoot the ethernet portion since it should work out of the box on that machine.

---

### Post by pokeman89 on 2010-09-17
> **TBABill said:**
> I wish I could offer direct assistance. Does your system work via ethernet in Windows? I imagine you run it normally via wireless.
 
I have a 1545 as well. Intel Core i3-330m CPU and it has a Broadcom wireless card. First thing to fix must be your ethernet port because, once working, you'll need to connect via ethernet, download updates and then install your wireless driver. The machine should detect that hardware drivers are available and prompt you to install them...for your machine that should only be the wireless unless you have an additional graphics card besides the on-chip GPU (Intel). 
 
If you haven't experienced it before, any install of Ubuntu or derivative will need to be connected via ethernet to download the Broadcom wireless driver since it is proprietary (till they include it in kernel 2.6.37 and later). So it will be critical to have ethernet connectivity after install. Hopefully someone can come along to help you troubleshoot the ethernet portion since it should work out of the box on that machine.

Thank you for the reply. Unfortunately while the ethernet does work under windows, it does not work in ubuntu. I do not know why, it may be bios setting or even a hardware defect, but I assume there must be some way to download the driver needed under windows and then install it under Ubuntu. Since the port works under windows, Dell said they cannot service it under warranty and I would have to pay for it.

As for other drivers, I do have the radeon HD 4330 upgrade, but the graphics seem fine so I don't think I need a driver for it.

EDIT: I also have a netgear 802.11n USB adapter, model WN111 which I can use, but it doesn't seem to work out of the box either.

---

### Post by xircon on 2010-09-17
Maybe totally unrelated, but what does:
```
cat /var/lib/NetworkManager/NetworkManager.state
```
Return?

I have a Inspiron N5010 and I have a problem with this file, which I am going to post about later (if I can't bottom it myself).

:Edit: This might help, [http://ubuntuforums.org/showthread.php?t=1562766](http://ubuntuforums.org/showthread.php?t=1562766)

---

### Post by pokeman89 on 2010-09-17
The results came across true for all of them. I checked the bios and the wlan toggle switch is checked. The toggle switch works because when I use it in linux the network manager goes from disconnected to device not ready.

What if I installed ubuntu on my desktop pc, ran the updater to get the netgear's driver, and then copied that driver to my laptop. would that allow me to get a connection?

Edit: I can confirm that I have the broadcom bcm4315 chip.

---

### Post by mathia on 2010-09-17
Hi,
please install the following ethernet driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8040 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

have a lot of fun ...:razz:

---

### Post by pokeman89 on 2010-09-17
> **mathia said:**
> Hi,
please install the following ethernet driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8040 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices    Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

have a lot of fun ...:razz:


Yes! Thank you that worked, even though it did cause a slight bit of trouble for me. I'm still getting used to using the terminal, so I had to go back and forth for a while to figure out what commands to use to navigate to the right directory. Once that driver was loaded and the old one deactivated,  it was easy to get the Broadcom driver. I can't thank you enough for helping me fix this! ):P

---

### Post by mathia on 2010-09-17
Hi pokeman89,

you are welcome. I am very happy that I could help you to fix the problem. ;)

---

### Post by mathia on 2010-09-17
Hi pokeman89,
for your broadcom wieless card try this link...

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by pokeman89 on 2010-09-17
> **mathia said:**
> Hi pokeman89,
for your broadcom wieless card try this link...

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)


Thank you for the link however I used the Hardware Drivers panel in Administration to get that once I had an active internet connection. I appreciate the help though :)

---

