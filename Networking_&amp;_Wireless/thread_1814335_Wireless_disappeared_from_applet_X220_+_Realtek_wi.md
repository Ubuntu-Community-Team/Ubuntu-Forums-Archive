---
title: "Wireless disappeared from applet X220 + Realtek wifi"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by substanceneil on 2011-07-29
I am having issues with wifi on my Lenovo X220.  What has occurred is that the network applet in the notification bar no longer shows me any wireless network options.  When I click on the applet, the drop down shows me: Wired network: disconnected (greyed out), VPN connections, Enable networking (checked), Connection information (greyed out), and Edit connections.  Missing is Wireless connections.  This occurred "out of the blue" in the middle of using the computer (i.e. NOT just after a reboot or new driver installation, etc.)

I have noted that:
1. Wired ethernet works just fine.
2. Wireless (wifi) works when I boot into Windows 7 or into a fresh Ubuntu USB Start up disk (implying that this is a software issue, not hardware).
3. The hardware led for wifi is OFF (whereas the Bluetooth light is on.)  In Windows or using a fresh ubuntu from USB, this light turns on normally.

This may be irrelevant, but the issue started yesterday when I noticed that the trackpoint scrolling that I had enabled using gpointing-device-settings was not working.  I ran that app and checked the settings, which were normal.  I then reset the computer, and found the trackpoint was working just fine, but I had no wifi.  A few resets later, the problem was not solved.

In case it helps, my lspci | grep Real shows:

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

I had installed updated Realtek drivers using this method

[http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html](http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html)

with great results for a few weeks until this problem happened.

Someone please help.  The obvious solution, since a fresh USB ubuntu works, is to reinstall.  But I'd rather not invest all that time and energy getting my machine back in order from a fresh installation.

I am running 11.04 32 bit.  (if i reinstall, should I try 64 bit?)

Thanks,
Neil

---

### Post by wildmanne39 on 2011-07-29
Hi, please run these commands in a terminal
```
lsmod | grep rt2
```
```
rfkill list all
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
and post th results here.
Thank you

---

### Post by substanceneil on 2011-07-29
@wildmanne39,

-----------
dngr@aleaiactaest:~$ lsmod | grep rt2
(no output)
-----------

-----------
dngr@aleaiactaest:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
-----------

----------
dngr@aleaiactaest:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
-----------

-----------
dngr@aleaiactaest:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.
-----------

thanks for helping.

---

### Post by wildmanne39 on 2011-07-29
Hi, please post the the results of
```
sudo lshw -C network
```
```
nm-tool
```
```
dmesg | grep wlan0
```
```
dmesg | grep eth0
```
```
dmesg | grep eth1
```
Thank you

---

### Post by substanceneil on 2011-07-29
----------------
dngr@aleaiactaest:~$ sudo lshw -C network
[sudo] password for dngr: 
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 04
       serial: f0:de:f1:5b:d6:63
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:40 memory:d2500000-d251ffff memory:d252b000-d252bfff ioport:6080(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:5000(size=256) memory:d2400000-d2403fff
------------

dngr@aleaiactaest:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:5B:D6:63

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
---------
dngr@aleaiactaest:~$ dmesg | grep wlan0
dngr@aleaiactaest:~$ dmesg | grep wlan
dngr@aleaiactaest:~$ dmesg | grep eth0
[    1.580806] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) f0:de:f1:5b:d6:63
[    1.580809] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.580874] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
[   22.042266] <30>udev[316]: renamed network interface eth0 to eth1
dngr@aleaiactaest:~$ dmesg | grep eth1
[   22.042266] <30>udev[316]: renamed network interface eth0 to eth1
[   23.639362] ADDRCONF(NETDEV_UP): eth1: link is not ready

---

### Post by wildmanne39 on 2011-07-30
Hi, you have no drivers being used for your wireless here is a link for installing them.
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667)
The last three posts on that page has the answer. If you need more help post back here.
Thank you

---

### Post by substanceneil on 2011-07-31
Interesting!

While rebooting to try to install new wifi drivers, I noticed that sometime along the way, a new set of GRUB2 entries had appeared:

Default:
2.6.38-10-generic-pae

Second choice:
2.6.38-8-generic-pae

Third choice: Windows 7
etc.

I am not sure how the 2.6.38-10 appeared, but when I booted into the 2.6.38-8 kernel, wifi was working perfectly.  I wonder if the wireless drivers I had installed somehow broke when the kernel was updated.

Does the kernel update automatically when I install updates?

Neil

---

### Post by bkratz on 2011-07-31
> **substanceneil said:**
> Interesting!

While rebooting to try to install new wifi drivers, I noticed that sometime along the way, a new set of GRUB2 entries had appeared:

Default:
2.6.38-10-generic-pae

Second choice:
2.6.38-8-generic-pae

Third choice: Windows 7
etc.

I am not sure how the 2.6.38-10 appeared, but when I booted into the 2.6.38-8 kernel, wifi was working perfectly.  I wonder if the wireless drivers I had installed somehow broke when the kernel was updated.

Does the kernel update automatically when I install updates?

Neil



since your kernel was updated the wireless drivers you previously installed would have had to be reinstalled, but the new kernel apparently has newer drivers available.

The new kernel would have shown up in the updates you selected for download.

---

### Post by wildmanne39 on 2011-07-31
Hi, that explains where your drivers went I am glad to know you had a kernel update, so you just need to reinstall your drivers in the new kernel and you should be good to go.
Thank you

---

### Post by substanceneil on 2011-07-31
Reinstalled the drivers and problem solved!  I am a newb and did not realise that drivers are installed "into" the kernel.  Frankly, I could recall that I had agreed to an update to the kernel at all.  I guess I just accept all the recommended updates without reviewing.  After recompiling the drivers and installing, I'm back in business.

---

### Post by wildmanne39 on 2011-07-31
Hi, I am glad you got it working.

The reason you had to recompile the drivers is because you had compiled them in the first place  and was not able to find one in synaptic or additional driver.

---

### Post by substanceneil on 2011-08-20
I am the original poster.  I recently updated my kernal to 2.6.38-11-generic (64bit 11.04).  I recompiled the realtek drivers as I had before to recover my wireless.  I followed the same steps as I had originally, from this post below.

[http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html](http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html)

I noticed in the comments of the above post that the newer Realtek drivers (26 July 2011) for rtl8188ce do compile and work under 11.04 64bit.  Can someone please walk me through the process of updating to the new driver?  I worry that I might break my installation if I just download and install without somehow disabling the older version.

Neil

---

### Post by substanceneil on 2011-11-18
I upgraded my X220 to 11.10.  The Realtek drivers that I had installed (see my original post) had solved the unreliable wireless issues in 11.04, but I am not sure I can follow the same tutorial for 11.10:

[http://www.chayx.net/2011/06/how-to-...atty-1104.html](http://www.chayx.net/2011/06/how-to-...atty-1104.html)

New version, new kernel...  I would hate to bork my system doing this again.  I cannot find any threads discussing this issue in 11.10.

My lspci | grep "Realtek":

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)


My uname -r:

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

---

### Post by substanceneil on 2011-11-18
I installed the newer Realtek 8188 CE drivers from Realtek's website.  Despite some trepidation, I followed the simple instructions in the readme to compile and install the drivers. 

After a reboot, everything seems to be working fine.  No dropped wireless.

Unlike the installation instructions I followed in 11.04 (link above), I didn't blacklist any drivers this time.  Is this okay?

---

