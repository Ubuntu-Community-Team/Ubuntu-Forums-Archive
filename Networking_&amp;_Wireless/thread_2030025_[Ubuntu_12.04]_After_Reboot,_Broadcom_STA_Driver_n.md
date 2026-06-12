---
title: "[Ubuntu 12.04] After Reboot, Broadcom STA Driver not working."
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by alanclick on 2012-07-20
Gone through many forums but nothing seems to have worked in my case.


I have Ubuntu 12.04 installed on my Dell Inspiron 1464 Laptop with Wubi. The other operating system being Windows 7.


The wireless on Windows is working perfectly fine but not on Ubuntu. Initially, in Ubuntu 12.04 the wireless used to work perfectly fine but not lately. (Note. I keep on updating my Ubuntu regularly. So, might be the case.)

The Exact Problem is: 

Everytime I restart my laptop, **the Additional Driver for "Broadcom STA wireless driver" says "This driver is activated but not currently in use"**. So, in order to make it work, I have to remove and re-activate the driver to make it work every time I boot.


I have **blacklisted bcma and brcm80211** as mentioned in this 
[thread]("http://ubuntuforums.org/showthread.php?t=1879096")... I have followed all the steps as mentioned in the thread but it hasn't worked in my case.



The Outputs of few Commands which may help the "Super Geeks" solve my problem. 

```
lspci -vvnn | grep 14e4

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

``````

sudo lshw -C network

  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f0403fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: b8:ac:6f:6c:e3:62
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:f0810000-f0810fff memory:f0800000-f080ffff memory:f0820000-f083ffff


```Presently, these are the packages installed in my laptop
```

1)bcmwl-kernel-source
2)broadcom-sta-common
3)broadcom-sta-source
4)firmware-b43-installer

```Guys, I am really frustrated cause of this, I have been trying occasionally, looking over the forums on internet and trying to fix it by myself. 

Thanks in advance.

Alan

---

### Post by matt_symes on 2012-07-20
Thread moved to **"Networking and Wireless**"

---

### Post by lJ9%3MR&gt;sa on 2012-07-20
Try opening Terminal and typing ```
sudo gedit /etc/modules
```. Type your root password to open up the text editor. At the bottom of the file put ```
b43
```. Press save and exit gedit. Reboot your computer. It should automatically load the broadcom wifi module to start your wireless card. :)
 
EDIT:
If you don't have gedit, open a Terminal and put ```
sudo apt-get install gedit
```.

---

### Post by chili555 on 2012-07-20
> Broadcom Corporation BCM4312 802.11b/g LP-PHY [[COLOR="Red"]14e4:4315[/COLOR]] (rev 01)With all due respect to my colleague faxmanloveswaffles, I believe wl is the correct driver for this device. I suggest you add wl to the file and not b43 and reboot.

---

### Post by alanclick on 2012-07-22
@faxmanloveswaffles

No, it did not worked after making the necessary change suggested by you.

Under Additional Drivers,

It still says, "This driver is activated but not currently in use."

But, there is one difference now, **Under Wireless Networks**:

It says, **"Device Not Ready (Firmware Missing)"**


PS: Pls Find Attachment.

---

### Post by alanclick on 2012-07-22
@chili555

Thank you so much Chili555. You have just saved a human life, you are too awesome, many many thanks brother!!!

Ladies and Gentleman, It is wwworking !!!

---

### Post by abelardopardo12 on 2012-12-19
> **chili555 said:**
> With all due respect to my colleague faxmanloveswaffles, I believe wl is the correct driver for this device. I suggest you add wl to the file and not b43 and reboot.
HI chili555

it works for me, thank you very much!! ^^

---

