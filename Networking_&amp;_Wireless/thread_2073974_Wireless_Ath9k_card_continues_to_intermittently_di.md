---
title: "Wireless Ath9k card continues to intermittently disconnect after upgrade 12.04"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by kodb on 2012-10-20
All,
I have spent the last 8 frustrating hours trying to troubleshoot this issue: was running 10.04 with no problems.  Upgraded to 12.04.01 this past week and since have been unable to have my wireless connect and stay connected. 
The behavior is as follows:  the wireless gets connected and shows that it is connected.  I am able to pull up the net.  About every 10 to 15 seconds, however, it disconnects then reconnects itself.  This cycle continues indefinitely.  I see multiple heterogeneous reports of this type of problem on the forum and via google but no definite fix.  Does anyone know if this is a bug in 12.04/a driver issue/etc?
I have already tried a bunch of stuff including disabling IPv6/rfkill unblock/modprobe/ etcetera etcetera:  no joy!

Hardware:   Acer Aspire One A532H
Wireless card Atheros with output from lshw as follows:

 *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 90:4c:e5:5c:f0:59
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.2.0-32-generic firmware=N/A ip=192.168.4.84 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:56000000-5600ffff

I have also found this using : rfkill list all
bob@bob-acer532h:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

I have already tried everything I can find on the forum and google so am hoping somebody has an idea which might help-this is making the system essentially unuseable for me.

Thanks,
Bob

---

### Post by uncaspi on 2012-10-20
Have a look at this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/945379](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/945379)

---

### Post by kodb on 2012-10-20
Thanks uncaspi for pointing me there.

I also found another bug report and the fix there was blacklisting the acer-wmi.
I did this and it has eliminated any further disconnects since rebooting it.

I found the instructions in a roundabout fashion but here is the original thread right here on our forums (and it had eluded me despite 8hours of searching LOL)
[http://http://ubuntuforums.org/showthread.php?t=1527048](http://http://ubuntuforums.org/showthread.php?t=1527048)

The gist of what I did is:
```
sudo nano /etc/modprobe.d/blacklist.conf
```
then add the following entry into the file at the bottom as the last entry
```
#entry to blacklist acer-wmi and avoid disconnects
blacklist acer-wmi 
```
save this file and then
```
sudo shutdown -r now
```
And it should be good

HTH anyone else pulling out their hair!
Bob

---

### Post by schnelle on 2012-12-21
> **kodb said:**
> Thanks uncaspi for pointing me there.

I also found another bug report and the fix there was blacklisting the acer-wmi.
I did this and it has eliminated any further disconnects since rebooting it.

I found the instructions in a roundabout fashion but here is the original thread right here on our forums (and it had eluded me despite 8hours of searching LOL)
[http://http://ubuntuforums.org/showthread.php?t=1527048](http://http://ubuntuforums.org/showthread.php?t=1527048)

The gist of what I did is:
```
sudo nano /etc/modprobe.d/blacklist.conf
```
then add the following entry into the file at the bottom as the last entry
```
#entry to blacklist acer-wmi and avoid disconnects
blacklist acer-wmi 
```
save this file and then
```
sudo shutdown -r now
```
And it should be good

HTH anyone else pulling out their hair!
Bob

On my Acer laptop I had to blacklist acer-wmi plus I had to do this:

```
sudo nano /etc/modprobe.d/ath9k.conf
```

and add this line:

```
options ath9k nohwcrypt=1
```

Save and reboot.

---

### Post by Pjotr123 on 2012-12-21
It's acer_wmi, not acer-wmi. When misspelled, it won't do anything.... :)

Furthermore, you might benefit from disabling power management for your wireless chipset:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card)
(item 2.1, right column)

---

