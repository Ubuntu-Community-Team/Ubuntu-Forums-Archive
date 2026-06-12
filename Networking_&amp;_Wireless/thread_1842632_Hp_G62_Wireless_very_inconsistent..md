---
title: "Hp G62 Wireless very inconsistent."
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by yungballla6 on 2011-09-11
Hi i have a Hp g62 laptop running ubuntu 11.04. I can connect to wireless but after about 5 minutes or so I no longer can surf the internet or download anything. It still says that i am connected but it seems like im not. If anyone can help i would gladly appreciate it as i am a student and need internet to complete assignments. 

Thank you, 

Louie

---

### Post by garvinrick4 on 2011-09-11
Are you running an Intel card with iwlagn driver? Post results here I have same machine
running intel iwlagn driver if same can help you.
```
lspci -k
```Copy and paste the Network card with driver here even if not Intel with iwlagn driver, have good users in Networking and wireless.

---

### Post by yungballla6 on 2011-09-11
> **garvinrick4 said:**
> Are you running an Intel card with iwlagn driver? Post results here I have same machine
running intel iwlagn driver if same can help you.
```
lspci -k
```Copy and paste the Network card with driver here even if not Intel with iwlagn driver, have good users in Networking and wireless.

Thank you very much here is:

lspci -k
```
louie@louie-HP-G62-Notebook-PC:~$ lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel driver in use: i915
	Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 1484
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel driver in use: uhci_hcd
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel driver in use: uhci_hcd
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel modules: i2c-i801
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
	Subsystem: Hewlett-Packard Company Device 1467
	Kernel driver in use: rtl819xSE
	Kernel modules: r8192se_pci
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 1484
	Kernel driver in use: r8169
	Kernel modules: r8169
louie@louie-HP-G62-Notebook-PC:~$ 

```

---

### Post by garvinrick4 on 2011-09-11
#This below is the card and driver we are interested in: I have read some threads where
upgrading the kernel to 3.0 and up will do the trick which is very easy to do.

#First we will bump this up to the front and see if any user knows the driver
and what the fix is, in case there is one. 


02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)     Subsystem: Hewlett-Packard Company Device 1467     
Kernel driver in use: rtl819xSE     Kernel modules: r8192se_pci

If any user out there knows this card and driver running Natty please jump in.

---

### Post by garvinrick4 on 2011-09-11
yungballla6,
 We will give this a good hour or so to see if a user pops in knowing your card and driver.
IN the mean time if you need to stop and start network without rebooting use below.
```
sudo service network-manager stop
``````
sudo service network-manager start
```Use the above two pieces of code in a terminal to stop and start network-manager
if any problem can also use below to restart network-manager:
```
sudo /etc/init.d/network-manager restart
```

---

### Post by yungballla6 on 2011-09-11
> **garvinrick4 said:**
> yungballla6,
 We will give this a good hour or so to see if a user pops in knowing your card and driver.
IN the mean time if you need to stop and start network without rebooting use below.
```
sudo service network-manager stop
``````
sudo service network-manager start
```Use the above two pieces of code in a terminal to stop and start network-manager
if any problem can also use below to restart network-manager:
```
sudo /etc/init.d/network-manager restart
```
My wireless dropped before i could read your last comment so i rebooted (because this brings wireless back for about 5-30mins before its lost again). I did what you said by starting and stopping NM. Usually when my wireless stops working I try to disconnect and reconnect but I can never reconnect after disconnecting. This is only after my wirless stops.

---

### Post by garvinrick4 on 2011-09-11
> I try to disconnect and reconnect but I can never reconnect after disconnecting. This is only after my wirless stops.
Hopefully we get this fixed I see from looking around you have had this problem a while.
Try these 3 if you cannot stop then start network manager with code I gave you.
```
sudo service network-manager stop
```
```
sudo rm /var/lib/NetworkManager/NetworkManager.state
```
```
sudo service network-manager start
```
That is all I got on starting and stopping network-manager: 

#Let us see if anyone has got anything on your card and driver.

---

### Post by yungballla6 on 2011-09-11
Off to bed, class in the morning. I appreciate all your help. Ill be back to the forums tomorrow to try to fix my problem. Thanks again.

---

### Post by garvinrick4 on 2011-09-11
O.K. will be around, there will be a way to fix this. I see you have been trying since May of
this year.

---

### Post by yungballla6 on 2011-09-12
Yes, I thought I found a fix for my problem by updating the realtekdriver, but the problem still persists. Someone must have a fix.

---

### Post by garvinrick4 on 2011-09-12
Download 4 items already in .deb so just have to click on and will install thru Ubuntu Software center.
Here is link to module-init-tools 3.13
Under Builds choose your 32 or 64 bit whichever you use. And then in lower
left hand corner of next page will see a .deb download it.
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1)

Now next I have a link below for kernel 3.0.1 choose;
all.deb
headers in your 32 or 64 bit
image in your 32 or 64 bit
Download them and then click on them in that order after download and Ubuntu software
center will install them. 
Now reboot into 3.0.1 kernel and hopefully kernel driver will work for your card.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.1-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0.1-oneiric/")

#If have any trouble with installing let me know and then of course let us know if it works fine. There
will be a lot of users could use a fix for this Card and Driver.
#You have your other kernels still installed as fallback kernels but I do have 3 installs of
Natty using this kernel so I am in practice here not in Theory.

---

### Post by yungballla6 on 2011-09-12
> **garvinrick4 said:**
> Download 4 items already in .deb so just have to click on and will install thru Ubuntu Software center.
Here is link to module-init-tools 3.13
Under Builds choose your 32 or 64 bit whichever you use. And then in lower
left hand corner of next page will see a .deb download it.
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1)

Now next I have a link below for kernel 3.0.1 choose;
all.deb
headers in your 32 or 64 bit
image in your 32 or 64 bit
Download them and then click on them in that order after download and Ubuntu software
center will install them. 
Now reboot into 3.0.1 kernel and hopefully kernel driver will work for your card.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.1-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0.1-oneiric/")

#If have any trouble with installing let me know and then of course let us know if it works fine. There
will be a lot of users could use a fix for this Card and Driver.
#You have your other kernels still installed as fallback kernels but I do have 3 installs of
Natty using this kernel so I am in practice here not in Theory.
I did exactly what you said and i am now on kernel 3. Every thing seems fine for now. I will post back with results of browsing web for a few hours. 

I truely appreciate your help. You are truely awesome. I know you didnt have to help me, im so grateful. Thank you again.

---

### Post by garvinrick4 on 2011-09-12
Yunballla6
If all stays well please marked as Solved in Thread tools so others may benefit.
Hopefully the 3.0.1 kernel has done the trick, we will know soon. Enjoy your Ubuntu.

---

### Post by Supertramp93 on 2012-06-17
I've done all of these but when I open my laptop, there is a "devian" icon in lower right corner and options to begine like : old ubuntu version, etc and I have to choose one to begin. I don't know much about linux so please help me.

---

### Post by Supertramp93 on 2012-06-17
The problem with the wireless also, is still here.

---

### Post by sffvba[e0rt on 2012-06-17
> **Supertramp93 said:**
> The problem with the wireless also, is still here.

This is an old thread with outdated info.

I would suggest starting a new thread and giving as much info as possible (describe the problem, attach screenshots if possible and also state version of Ubuntu etc.)

*Thread **closed**.*


404

---

