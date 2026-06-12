---
title: "TL-WN821N &quot;Atheros&quot; revert to ubuntu driver"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by psycho5 on 2010-06-20
Hi

I need some help, my wirless usb card which is a TP-Link TL-WN821N card was working fine, except that it would drop the connection once in a while.

I got the windows XP driver and used the graphical ndiswrapper tool to install it, and "Hardware Present = Yes" showed up next to the driver. 

So I followed the guide and edited my blacklist.conf to add the the atheros and any other conflicting drivers.

After that, I rebooted, but iwconfig and ifconfig doesn't show my wireless card anymore.

lsusb shows that the card is detected, I can also tell cause the activity light is constantly on instead of it blinking. 

I decided to uninstall the windows wireless driver from the graphical tool, and hash out the blacklist entries and reboot the pc. But still my wireless card is not working.

I just want to revert to ubuntu's own driver, how do I do that now?

---

### Post by psycho5 on 2010-06-21
*bump*

Any help please? Using Atheros chipset with driver ar9170usb. 

I can't browse the net, and I can't use an ethernet connection either. I can go online with the live cd, so how do I get Ubuntu to use back the old driver?

Using Ubuntu 10.04 32bit.

*edit*

Ok I manage to get the wireless card to start back up:

```

oj@oj-desktop:~$ sudo modprobe -r ar9170usb
[sudo] password for oj: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
oj@oj-desktop:~$ sudo modprobe ar9170usb
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
oj@oj-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"BRAINEVANS"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: D8:5D:4C:AF:AC:D2   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

oj@oj-desktop:~$ 

```

---

### Post by GrandTheft on 2010-07-24
Hi,

Works out-of-the-box for me. With current standard kernel only at g speed, with 2.6.35 kernel (mainline) at N speed. 

Are you using network-manager? 

Over here the process was

- pluggin in 
- entering details in network-manager
- works (speed depending on running kernel)

From your iwconfig-output it looks as if it should work fine. But note that it says "bg" there. If your router might be running at N speed only, the device cant connect. 

If you are configuring the stick from the command line using wpa_supplicant, I would have a look at the arch linux wiki, they have amazing descriptions on how to get wlan working.

Best regards,
GT

---

### Post by min_max9000 on 2011-01-11
I've been struggling with this this device as well. I'm installing this on my server and I'm able to set everything up over a wired connection via ssh with wpa_supplicant but then as soon as I disconnect the wired connection, the wireless connection stops and drops the access point.

The same is true on reboot. I can't seem to get the settings to stick.

Thoughts?

---

### Post by PatchesTheCaveman on 2011-01-11
Is there a GUI installed on the target machine?  The default NetworkManager network configuration program will override manually configured settings after awhile.  Remove it with this command to allow it to be completely configured via the command line:
```
sudo apt-get remove network-manager
```

If you continue to have trouble, please follow the instructions in this post to provide us with diagnostic information so we can look into your problem:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

