---
title: "Broadcom 4312 has stopped associating on Lucid."
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by QwUo173Hy on 2010-11-21
The wireless stopped associating on my mothers Lucid machine. I can only assume an update caused this to happen, but the wireless in Windows doesn't work either now! I then installed Maverick, but the symptoms were the same. Now I've put Lucid back on and didn't run update manager but I still have the same problem. I'm going away in a month and I don't want to leave her without internet so any help is very appreciated!

** Basically:**
I can see all the networks, but can't connect to any of them. The 'scanning' icon just gives up and asks me for the password again. I've installed the STA driver as well as b43-fwcutter.

** Here is all the info requested in the sticky:**
Ubuntu 10.04 LTS (no updates)
Dell Inspiron 1750
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

**ifconfig**
eth1      Link encap:Ethernet  HWaddr 0c:60:76:0d:14:b0  
          inet6 addr: fe80::e60:76ff:fe0d:14b0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:21
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

**iwconfig**
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

**lsmod**
The wl module is installed

** sudo lshw -C network**
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 0c:60:76:0d:14:b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff


** iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

Thanks,
Jarlath

---

### Post by QwUo173Hy on 2010-11-26
Bump - I really need help here. I'm even willing to install Windows if someone can tell me that it will get the wifi working for her again. I tried uninstalling and reinstalling the driver from windows too, hoping that it would fix any potential firmware problem, but still no luck. i really am desperate here.

Would Canonicals paid support be able to help me here? I don't mind spending the 100 or so euro for a years support.

---

### Post by QwUo173Hy on 2010-11-28
Anybody?

---

### Post by bkratz on 2010-11-28
Don't know if it would be any help to you, but you might read the readme at the following:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Apparently, a new release was made for your STA driver on 11/12 which is not in the repos' yet.

---

### Post by QwUo173Hy on 2010-11-28
Thanks bkratz, I tried it - but I'll give it another go just to be sure.

---

### Post by QwUo173Hy on 2010-11-28
This might be a silly question - but is it possible that the drivers aren't the problem? Could it be the firmware?

---

### Post by QwUo173Hy on 2010-11-28
From the document: "Some distros (Ubuntu and Fedora at the least) already have a version of
this driver in their repositories precompiled, tested and ready to go.
You just use the package manager to install the proper package.  If
its available for your distro, this is usually an easier solution. See
the end of this document for further discussion."

So it seems we already have this driver. I wonder if that's the problem...

---

### Post by bkratz on 2010-11-28
> **jarlath said:**
> From the document: "Some distros (Ubuntu and Fedora at the least) already have a version of
this driver in their repositories precompiled, tested and ready to go.
You just use the package manager to install the proper package.  If
its available for your distro, this is usually an easier solution. See
the end of this document for further discussion."

So it seems we already have this driver. I wonder if that's the problem...

Well you do already have a version of this driver install per your first post

```
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]driver=wl0 driverversion=5.60.48.36[/COLOR] latency=0 multicast=yes wireless=IEEE 802.11bg
resources: irq:17 memory:f69fc000-f69fffff
```


The version listed in my last post is 

[COLOR="Red"]Version: 5.60.246.6[/COLOR]

It also has directions showing anything that needs "blacklisting"

---

### Post by uncaspi on 2010-11-28
I compiled the STA driver from Broadcom site. The file is named

hybrid-portsrc_x86-32_v5.60.246.6.tar.gz 

It works a once if you type depmod -a after make install.
This is an Acer Timeline brand new laptop. lspci -nn shoved [14e4:4357]
but I seem to remember that the Broadcom product ID are 43225.
So thank you bkratz;)

---

### Post by TBABill on 2010-11-28
Could have been an update to the driver, not sure. Try to ```
sudo rfkill list
``` If either soft blocked or hard blocked are marked YES, then ```
sudo rfkill unblock all
```

---

### Post by QwUo173Hy on 2010-11-28
Thanks bkratz, I missed that. I'll try it in the morning.

tbabill, I got a 'no' on both counts there. I find it strange that the networks can be seen but not connected to. I assume this means that there is not a driver conflict, correct? Meaning that blacklisting won't be a part of the plan here (but I'll follow whatever instructions bkratz has linked to)

---

### Post by QwUo173Hy on 2010-11-29
I followed the instructions to the letter and removed all other drivers - but still no change. I can see the networks but can't authenticate.

I think this issue might go beyond the driver since the problem is the same in Windows too, but I have no idea what else is involved. I have heard of people in the past have Ubuntu make their card stop working for other OSes.

I'm thinking that if I made a Windows restore disc and reinstalled Windows - I should have a working system again right? (unless it's the actual hardware that's faulty)

---

### Post by QwUo173Hy on 2010-11-29
I now have working internet - thank you everyone!

After I updated the driver and rebooted - I had the same problem. I then shutdown, but also reset the router. Now it's working, with WEP and with the same ptassword.

I can't understand it. My folks came back from holidays saying the laptop wouldn't connect to anything - so I never suspected the router. Also, all other devices in the house authenticate to it fine.

So either the second reboot did the trick, or resetting the router did it. Windows now authenticates again too.

Thanks again everyone, I was getting worried there.

---

