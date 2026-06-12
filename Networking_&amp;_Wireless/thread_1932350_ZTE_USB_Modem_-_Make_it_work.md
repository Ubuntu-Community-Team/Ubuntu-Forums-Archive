---
title: "ZTE USB Modem - Make it work"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by Kenyan-Newbie on 2012-02-27
I have Ubuntu 11.10. I have 2 USB Modems. 

The Huawei E160 was 'picked-up' plag-n-play into my machine, the 'Safaricom' interface installed and I'm able to access internet; both via interface and through Network Manager. It's a GSM network/sim.

The problem is the black ZTE MF192 modem. It's not 'picked-up' by my computer. Network Manager doesn't recognize a wireless device has been connected. I fiddled with the 'Orange' interface software in the modem and managed to install it. Both, directly to Ubuntu and the Windows-version via Wine. Both softwares will load, but neither makes the USB Modem work. It's a CDMA network/sim and works perfectly in Windows 7.

What do I do to make it work?

---

### Post by raja.genupula on 2012-02-27
is it a 3G modem ? open software center and install modeswitch 
and try again . 

all the best .

---

### Post by clausrei on 2012-02-27
Modeswitch is already part of the new Oneric Ocelot 11.10 by standard. If it is not mistakenly recognized as a storage device, than the error must be somewhere else ! 

The device has no driver !

Try to find out if the chipset of your device is supported.

First step:
```

lsusb

```

Write down the _device number (001-005) _and maybe the Name of the Company who produced it.

Step two:
```

lsusb -v -s 03

```
( 03 is the example device number. you have to take away the first 0. Your device number will be different.) 

Look in the list of the above produced code for the id Vender and the id Product. Your id Product is your chip id. Try to find out in a search engine, whether or not this chip is supported in the Linux Kernal Drive. Possibly not ! Maybe you have to compile a driver.

---

### Post by Kenyan-Newbie on 2012-03-08
Vendor=19d2
Product=1518

I googled as directed and came across a few sites, one of which is 

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=5215&sid=f254c9cf4d2e1dfbc4fde37d424f7f33](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=5215&sid=f254c9cf4d2e1dfbc4fde37d424f7f33)

and the dongle does have installation software in it, including a directory 'driver' with a file 'se'.

PS: I'm a novice, much as I google 'PATCH', 'SWITCH' going about them confuses me even more. Please simply the process ie Do this, Then type this, Then.. etc

---

### Post by Jackalyn on 2012-07-16
> **Kenyan-Newbie said:**
> Vendor=19d2
Product=1518

I googled as directed and came across a few sites, one of which is 

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=5215&sid=f254c9cf4d2e1dfbc4fde37d424f7f33](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=5215&sid=f254c9cf4d2e1dfbc4fde37d424f7f33)

and the dongle does have installation software in it, including a directory 'driver' with a file 'se'.

PS: I'm a novice, much as I google 'PATCH', 'SWITCH' going about them confuses me even more. Please simply the process ie Do this, Then type this, Then.. etc

Is the answer to this to install Sakis? I find Sakis is working well with 3 modems.

---

### Post by Kenyan-Newbie on 2012-07-17
So sorry... I should have updated how I got it to work.

The dongle had a few files it it. One was 'Linux'... In 'Linux' was 'Tools'.. The trick was to first install each and everyone of those tools, some co-dependent, before installing the 'Orange' User Interface.

Once I tried that, it worked like a charm.

---

### Post by mungatsuma on 2012-11-10
That usually works, another method if you have internet connection is install libqt, basically any will do libqt3 or qt4 will do and wvdial. For Safaricom beware, it removes the Sudo password prompt, hence making your system vulnerable. The Modem on offer did that to my machine severally on precise and later on Quantal.
To fix this type in terminal
```
sudo visudo
```then comment out the last line that says
> ALL ALL=(ALL) NOPASSWD:ALLto look like this

> #ALL ALL=(ALL) NOPASSWD:ALLThe whole file should look like this

> #
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        mail_badpass
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:$

# Host alias specification

# User alias specification

# Cmnd alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
#ALL ALL=(ALL) NOPASSWD:ALL
Or delete the last line altogether after includedir /etc/sudoers.d

I dont know how safaricom does it, will go through the installation script. 

Kenyans beware.

---

