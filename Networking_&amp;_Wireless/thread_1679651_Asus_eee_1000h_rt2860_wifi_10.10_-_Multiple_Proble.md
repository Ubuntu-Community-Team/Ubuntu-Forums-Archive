---
title: "Asus eee 1000h rt2860 wifi 10.10 - Multiple Problems Fixed"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by nevdelap on 2011-02-01
At some point in the last couple of months my wifi started being unreliable. It could be something to do with moving and needing to connect to a different wifi router, or maybe it was an update. I don't know. But I had the following problems...

- Difficulty connecting in the first place. (WPA/WPA2/tkip/aes/tkip+aes - all combinations)
- Refusal to reconnect after disconnecting.
- Disconnecting many times per hour.
- Needing to restart to reconnect.
- Wifi not functioning after resume.
- Hanging on resume.

It is an Asus 1000H with an rt2860 wifi adaptor running Ubuntu 10.10.

This is how I solved all these problems, and now my wifi is absolutely rock solid, even with a 15% signal! It's never been so good.

(1 - 4 fix problems connecting, dropouts, and problems reconnecting by replacing the unreliable rt2860 driver with the Windows version running using ndiswrapper)

1. Install ndiswapper and ndisgtk using Synaptic or apt-get.

2. Blacklist all the wifi drivers in /etc/modprobe.d/. This is the end of mine...

```
# Nev's mods.
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
blacklist rt2400pci
blacklist rt2500pci
blacklist rt2500usb
blacklist rt2800lib
blacklist rt2800pci
blacklist rt2800usb
blacklist rt61pci
blacklist rt73usb
blacklist rt2600
blacklist rt2860 # Asus eee 1000H has an rt2860. To be loaded by ndiswrapper.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist r8192s_usb
```

3. Download comm_driver_gigabyte_mimobility_v.1.3.1.0.15.zip.

4. Use ndisgtk (System > Administration > Windows Wireless Drivers) to install the w2kxp driver contained within drivers/GN-WI30N_WP30N_WS30N_WS30HN_WS31N/WINXP2k.

(5 - 8 fix not connecting after resume by setting some kernel options)

5. sudo gedit /etc/default/grub

6. Edit the line with GRUB_CMDLINE_LINUX_DEFAULT and change it to:

GRUB_CMDLINE_LINUX_DEFAULT="pciehp.pciehp_force=1 pciehp.pciehp_poll=1 quiet splash"

7. sudo update-grub2

8. Restart the system.

(9 fixes the hanging on resume by unloading ndiswrapper before suspend and reloading it after resume)

9. Put the following in "/etc/pm/sleep.d/ndiswrapper" and chmod it +x.

```
#!/bin/bash
case "$1" in
    hibernate|suspend)
        sudo rmmod ndiswrapper
        ;;
    thaw|resume)
        sudo modprobe ndiswrapper
        ;;
    *)
        ;;
esac
exit $?
```

---

### Post by ObscureAngel on 2011-07-28
I am a newbie on Linux..
So How do i blacklist the drivers if the .conf files are read only?
I try to change the permission in options but it was blocked only for root!

How do i edit through console?
Thanks a lot..

---

### Post by chili555 on 2011-07-28
Open a terminal and gain root permissions with sudo:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Proofread carefully, save and close gedit.

Be careful!

---

### Post by ObscureAngel on 2011-07-28
The curious thing is that i dont have the ndiswrapper on step 9.

located at sleep.d!

Well anyway!
I will test a few days if this fix works!
Cause this one of the main reasons that bring me back to microsoft windows many many many times!

I am forcing my self to use Ubuntu!
So if i upgrade or clean Install the ubuntu 11.10 when its released, am i need to do this fixes again?

Thanks a lot!
I apreciate a lot your knowledge!

---

