---
title: "No wireless on Aspire One AR242x 802.11abg"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by damendieta on 2009-07-14
Hi everyone,

I have a problem with my wireless (not working, ja ja ja) here the information:

OS: UBUNTU 9.04

It looks like it is DISABLED, but I have it enabled on networkmanager. I don't know how to enable it.

[COLOR="Blue"]lshw -C network[/COLOR]
  > 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:50:8b:2d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.15 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2b:1f:67:37
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:9a:40:d3:b4:2d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

[COLOR="Blue"]iwconfig[/COLOR]

> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Encryption key: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by ddrichardson on 2009-07-14
On 9.04 you may need to blacklist acer_wmi

Check if its loaded by opening a terminal and typing:```
sudo modprobe|grep acer_wmi
```If it is then remove it using```
sudo rmmod acer_wmi
```
Then you can add it to /etc/modprobe.d/blacklist-network.conf:```
blacklist acer_wmi
```

---

### Post by damendieta on 2009-07-14
I got my wireless working but it can't conect to any wireless network, I can see y wan, my wireless is on, but it just can't connect. 

This are the steps I followed to get my wireless enabled:

Step 1: Open Terminal from "Applications->Accessories->
Terminal"

Step 2: Run the following commands (copy-paste each line into the Terminal, press <enter> after each line)

> sudo aptitude update
sudo aptitude install build-essential subversion
cd ~
wget [http://snapshots.madwifi-project.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-trunk-current.tar.gz)
tar xvf madwifi-trunk-current.tar.gz

You have to check wich version you have, so is better if just write 

> cd  madwifi-trunk

Then press tab to get the folder name (autocomplete)

Then press enter and you will be at the folder of your version of madwifi

> make
sudo make install
sudo gedit /etc/modules


# Now add the Atheros kernel module ath_pci to the list of modules to be automatically loaded at boot. Go to gedit (the windows wich opens) and add this line:

> ath_pci

Save and close.

Go to the terminal again and write:

> sudo gedit /etc/modprobe.d/blacklist.conf

Add this to the blacklist.com file, (the new window again).

> blacklist ath5k_pci
blacklist ATL1E
blacklist ath5k

Now you can reboot and it should work.

---

### Post by damendieta on 2009-07-14
> **ddrichardson said:**
> On 9.04 you may need to blacklist acer_wmi

Check if its loaded by opening a terminal and typing:```
sudo modprobe|grep acer_wmi
```If it is then remove it using```
sudo rmmod acer_wmi
```
Then you can add it to /etc/modprobe.d/blacklist-network.conf:```
blacklist acer_wmi
```

I did it and my wireless now works fine.

Thanks.

---

### Post by ddrichardson on 2009-07-14
I'm going to go and add it to the community documentation because it keeps coming up, I'd hoped it would have been addressed - the most recent kernel doesn't have this problem and acer_wmi doesn't interfere with it (I've got an Arch system running on my Aspire One now and I've had _zero_ problems, even the WiFi LED works).

---

### Post by Quarkangel7 on 2009-09-30
You have gotten me further then anyone. Thankyou!!! You dont know how much grief you have saved me. God Bless

---

### Post by Quarkangel7 on 2009-09-30
Madwifi trunk download worked with a compiler in terminal. The Led doesnt work but meh thats not that important. I am even doing find with higher encryption forms then WEP. You must have most recent BIOS and you must get the madwifi trunk download if you want any hope of wireless on acer aspire one 150.

It detects all networks just fine without the wifi catcher, so i dont need it anyway.

Never tried Arch linux, but I seriously doubt that its problem free. Ubuntu isnt problem free, None of them are. But for now i prefer ubuntu, it has the most support and its friendly to beginners in linux, I may move on to Gentoo, or even Arch, but for now im pretty happy with Ubuntu.

---

