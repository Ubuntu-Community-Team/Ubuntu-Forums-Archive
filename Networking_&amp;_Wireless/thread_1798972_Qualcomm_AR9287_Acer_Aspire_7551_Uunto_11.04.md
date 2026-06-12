---
title: "Qualcomm AR9287/ Acer Aspire 7551/ Uunto 11.04"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by haloxiv on 2011-07-06
Just installed ubunto 1104 and I cannot connect wirelesly to my router. When I go through the trouble shooting the recommendation is to got to the device drivers page but the link does not take me anywhere. Here is the info from the terminal.

*-network DISABLED
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: ec:55:f9:60:8e:87
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless

06:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
 Looking for advice. 
Thanks 
Duke

---

### Post by chili555 on 2011-07-07
Oooh! Fun!

Please run and post:```
sudo modprobe ath9k
rfkill list all
dmesg | grep -e ath -e wlan
```Thanks.

---

### Post by haloxiv on 2011-07-07
[B]Hey chill, here it is 

Thanks
[/B]

duke@ubuntu:~$ sudo modprobe ath9k
duke@ubuntu:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
duke@ubuntu:~$ dmesg | grep -e ath -e wlan
[    0.492289]  [<c104f912>] ? warn_slowpath_common+0x72/0xa0
[    0.492298]  [<c104f9e3>] ? warn_slowpath_fmt+0x33/0x40
[    1.335353] device-mapper: multipath: version 1.2.0 loaded
[    1.335357] device-mapper: multipath round-robin: version 1.0.0 loaded
[   14.082025] ath9k 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.082035] ath9k 0000:06:00.0: setting latency timer to 64
[   14.172627] ath: EEPROM regdomain: 0x65
[   14.172631] ath: EEPROM indicates we should expect a direct regpair map
[   14.172635] ath: Country alpha2 being used: 00
[   14.172637] ath: Regpair used: 0x65
[   14.184775] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.185440] Registered led device: ath9k-phy0::radio
[   14.185466] Registered led device: ath9k-phy0::assoc
[   14.185487] Registered led device: ath9k-phy0::tx
[   14.185505] Registered led device: ath9k-phy0::rx
[   15.274897] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by haloxiv on 2011-07-07
Err, sorry chili

---

### Post by chili555 on 2011-07-07
> 0: acer-wireless: Wireless LAN
Soft blocked: yesDr. Chili doesn't like this at all, but I think we can fix it. Please do:```
sudo rmmod -f acer-wmi
```Does your wireless spring to life? If so, let's banish acer-wmi forever:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```If that doesn't do it, post back and we'll dig deeper.

---

### Post by haloxiv on 2011-07-07
Dr, thx that fixed it and both sections done and done. I have never touch anything but windows on a comp and want to lean this so I can install it on an old laptop for the kids and be able to do a little trouble shooting for them.

Duke

---

### Post by chili555 on 2011-07-07
Awesome, Duke! Although, when I read "...Acer...wireless not working..." I was 90% sure I already knew the answer. It's always good to get a confirmation, though.

Post back if we can help you further and you might use Thread Tools at the top to Mark Solved. I wish they were all this easy!

---

### Post by mtrethowan on 2011-08-27
This one helped me too. Just got an Acer Aspire 7551 and am setting it up for Linux/android/beagleboard development.

Thanks.:guitar:

---

### Post by nymusicman on 2011-09-29
Doc, you are awesome and a life saver. Same issue, same resolution. Thanks a lot.

---

