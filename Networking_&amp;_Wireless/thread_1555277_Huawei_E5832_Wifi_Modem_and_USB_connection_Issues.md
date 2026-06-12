---
title: "Huawei E5832 Wifi Modem and USB connection Issues"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by barefootmisty on 2010-08-17
Hi,

Running Ubuntu 10.04 installed from CD and I'm trying to get Australian Virgin Prepaid WIFI Modem Huawei E5832 to work through  USB connection.  

The system doesn't seem to recognise it at all.  The computer is charging the modem fine and the modem is connected and working wirelessly on another computer.

Unfortunately the computer I am trying to USB connect to is having issues with it's wireless, so that is not an option.

I am fairly new to ubuntu, but know the basics of using terminal.
Any help or advice, would be greatly appreciated.

---

### Post by barefootmisty on 2010-08-19
I tried following the instructions on [https://help.ubuntu.com/community/MobileWirelessBroadband](https://help.ubuntu.com/community/MobileWirelessBroadband)
as per a friends suggestion.  Eject or Safely Removing Drive didn't work and when I try  /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi  I get permission denied.  The other option returned No file or directory.

Any ideas?

---

### Post by varunendra on 2010-08-21
> **barefootmisty said:**
> when I try  /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi  I get permission denied.
Try (in terminal) ```
sudo cat /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```
If you need to edit it (I'd suggest to make a backup first), try ```
gksudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```


> **barefootmisty said:**
> The other option returned No file or directory.

What do you mean by 'other option'? If you mean "installing USB Modeswitch", you should be able to find this package in Synaptic from where you can easily install it. Open **System>Administration>Synaptic Package Manager** and type **usb modeswitch** in the search box. The **usb-modeswitch** package should get listed in the result packages (you may need to enable **'universe'** repository under 'Settings' menu in Synaptic). Mark it for installation and **Apply the changes** to install it.

---

