---
title: "Dell Latitude D830 (Intel 3945ABG) WiFi Issue"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by kOna on 2010-05-29
Hey :)

After having mixed success with 9.10 a while back I decided to give 10.04 a try and see if everything "Just worked"; on first boot everything was OK but after rebooting my WiFi doesn't work. Sometimes when I reboot it does work, most of the time I get "Wireless is disabled" in NetworkManager even when the WiFi switch is enabled, usually I need to reboot ~5 times before Wireless will work again.

Have any of you knowledgeable lot got any idea's on how to fix this?

Cheers,

Kona

---

### Post by kOna on 2010-06-05
Well I've spent a few hours this week trying to solve this problem but I just can't for the life of me figure out what's wrong. Is there any way to re-install the iwlwifi driver, or force it to load when I log in?

Cheers!

---

### Post by kOna on 2010-06-05
I've just done some further digging and it appears that the card is detected, it's just disabled (the WiFi switch on the laptop is turned ON)

**rfkill list**
```
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.
```**lshw -c network**
```
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:7b:c7:69
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:f1fff000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:a1:12:cd
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5755m-v3.29 ip=192.168.1.121 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:31 memory:f1bf0000-f1bfffff
```

Is there any way to over-ride Ubuntu thinking the wireless is disabled?

Cheers.

---

### Post by chili555 on 2010-06-05
Please try:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
rfkill list all
```If this works, we will amend one file to make it permanent.

---

### Post by kOna on 2010-06-06
> **chili555 said:**
> Please try:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
rfkill list all
```If this works, we will amend one file to make it permanent.

That worked a treat, thanks :)

Which file should I amend to make this permanent?

Cheers,

Kona

---

### Post by chili555 on 2010-06-06
We will add dell-laptop to the file of modules that are not to be loaded, even if the system thinks it's needed. Open a terminal and do:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Hereafter, the module is banned.

---

### Post by jharv117 on 2010-11-12
hey guys, 

i have a dell D830 laptop running 10.04 LTS as well as kona, and i seem to be having the same problem, i tried the solution that was posted that worked for kona, but did not work for me, wireless is still disabled and a separate but related issue, the "wifi" light usually lights up when i turn on the laptop doesn't light up, but the bluetooth light right next to it does

any help would be greatly appreciated, as i am a relatively new ubuntu user, and i am out of ideas at this point

thanks 

Jeremy

---

