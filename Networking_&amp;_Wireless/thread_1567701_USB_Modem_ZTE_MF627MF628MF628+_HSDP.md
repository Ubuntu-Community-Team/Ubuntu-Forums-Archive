---
title: "USB Modem ZTE MF627/MF628/MF628+ HSDP"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by Sisophon2001 on 2010-09-04
Hi,

NOTE: The original post was mostly rubbish, an example of me trying to find patterns in seemingly random events and coming up with the wrong conclusions. I have therefore deleted the full text, and am starting over again.

There were two problems using this modem in UNR 10.04 that I have identified to date:
1. I had USB_ModeSwitch installed, and this interfered with ubuntu which already knows how to switch the modem. I needed to un-install USB_ModeSwitch to get it to work.
2. The modem registered four /dev/ttyUSBx ports, one of which was for SMS messages and this was incorrectly being identified as the modem port. I had to add this entry to /lib/udev/rules.d/77-mm-zte-port-types.rules or sometimes the network manager connects to the AUX port.

ATTRS{idProduct}=="2003", ENV{.MM_USBIFNUM}=="03", ENV{ID_MM_ZTE_PORT_TYPE_MODEM}="1"
ATTRS{idProduct}=="2003", ENV{.MM_USBIFNUM}=="01", ENV{ID_MM_ZTE_PORT_TYPE_AUX}="1"

I am now able to connect reliably. :)

Garvan

---

### Post by caloy230 on 2011-06-14
im a newbie...i can't get my smartbro wm66a zte mf627 to work..ubuntu 11.04 cant even detect it despite having usb modeswitch and usb modeswitch data pre installed...help please....tnx

---

### Post by eisanchez on 2011-09-23
Hi Garvan!

In ATTRS{idProduct}=="2003", ENV{.MM_USBIFNUM}=="01", ENV{ID_MM_ZTE_PORT_TYPE_AUX}="1"

How did you know "01" is the AUX port?

Thanks a lot


> **Sisophon2001 said:**
> Hi,

NOTE: The original post was mostly rubbish, an example of me trying to find patterns in seemingly random events and coming up with the wrong conclusions. I have therefore deleted the full text, and am starting over again.

There were two problems using this modem in UNR 10.04 that I have identified to date:
1. I had USB_ModeSwitch installed, and this interfered with ubuntu which already knows how to switch the modem. I needed to un-install USB_ModeSwitch to get it to work.
2. The modem registered four /dev/ttyUSBx ports, one of which was for SMS messages and this was incorrectly being identified as the modem port. I had to add this entry to /lib/udev/rules.d/77-mm-zte-port-types.rules or sometimes the network manager connects to the AUX port.

ATTRS{idProduct}=="2003", ENV{.MM_USBIFNUM}=="03", ENV{ID_MM_ZTE_PORT_TYPE_MODEM}="1"
ATTRS{idProduct}=="2003", ENV{.MM_USBIFNUM}=="01", ENV{ID_MM_ZTE_PORT_TYPE_AUX}="1"

I am now able to connect reliably. :)

Garvan

---

