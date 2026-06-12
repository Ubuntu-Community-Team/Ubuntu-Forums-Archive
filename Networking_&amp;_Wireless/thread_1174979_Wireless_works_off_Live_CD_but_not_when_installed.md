---
title: "Wireless works off Live CD but not when installed"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by don_diego on 2009-05-31
Yesterday morning I ran 9.04 off the Live CD for a while and then decided to install it. Much to my surprise after the installation I no longer had access to my wireless LAN. (For the moment I am resorting to a wired connection to post here.) 

Since then I have followed the troubleshooting procedure provided in Ubuntu help, read numerous threads yet I still am without a wireless connection. All I have learned so far is that it helps to post as much info for those who are willing to help solve a problem. For a start, here is the output from lshw -C network:

```

  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:7c:d8:cd
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.106 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5a:2e:8b:9f:3e:ea
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```I will be forever grateful to whoever can help me out since I am at the end of my wits.
TIA

---

### Post by chili555 on 2009-05-31
I believe this is supposed to use the module *iwlagn*. Please open a terminal and do:```
sudo modprobe iwlagn
```Note and post here any errors. If there are no errors, hopefully, see if you can click the Network Manager icon and connect. If, upon reboot, it doesn't load automagically, then do:```
sudo nano /etc/modules
```Add a new item on its own line:```
iwlagn
```Proofread, save and close.

---

### Post by don_diego on 2009-05-31
Hi Chili, here's the output I get from modprobe iwlagn:
```
lutz@lutz-laptop:~$ sudo modprobe iwlagn
[sudo] password for lutz: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
lutz@lutz-laptop:~$ 
```Having only joined the Ubuntu community very recently (yes I'm a real newbie), I have no idea how to proceed. Hope you can get me through this.

---

### Post by -tr on 2009-05-31
I've encountered the exact same problem (I think). It starts up and I go to connect to the network through the network manager and it does the loading thing and during that time the WLAN LED on the front of my laptop flashes ~3 times and then it disconnects (though it never really connects). Then back to the CD and everything's working fine again.

It seems that many people are having similar problems yet I have yet to see a guaranteed fix. Does anybody have recommendations as to alternatives for in the mean time as I too am a complete Ubuntu noob and need to get this going..

---

### Post by chili555 on 2009-05-31
> **don_diego said:**
> Hi Chili, here's the output I get from modprobe iwlagn:
```
lutz@lutz-laptop:~$ sudo modprobe iwlagn
[sudo] password for lutz: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
lutz@lutz-laptop:~$ 
```Having only joined the Ubuntu community very recently (yes I'm a real newbie), I have no idea how to proceed. Hope you can get me through this.The module was loaded without error. When you do:```
sudo lshw -C network
```Does your wireless interface still show as 'Unclaimed'? Can you click the Network Manager icon, see your network and connect?

---

### Post by don_diego on 2009-06-01
Thanks for your reply Chili. Here's the info you need:
> **chili555 said:**
> The module was loaded without error. When you do:```
sudo lshw -C network
```Does your wireless interface still show as 'Unclaimed'?
Yes, it's still  the same:
```
 *-network UNCLAIMED
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```>  Can you click the Network Manager icon, see your network and connect?No, that too is unchanged. I am using the wired connection to post here and wireless networks isn't shown as a choice. Could it possibly be that the problem is due to the fact that* iwlagn* is only the alternate driver and the primary driver isn't working? ```
lutz@lutz-laptop:~$ sudo ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netw5x32 : driver installed
    device (8086:4232) present (alternate driver: iwlagn)

```Thanks again, hope we can get this solved, I noticed that many people seem to have trouble with there wireless setups.

---

### Post by chili555 on 2009-06-01
If you do:```
sudo rmmod -f iwlagn
sudo modprobe ndiswrapper
```Are there any errors? Does you interface still show as 'Unclaimed'?

By the way, this temporary experiment will probably not survive a reboot, so if it works, we will need to make a couple of changes to make it permanent.

---

### Post by don_diego on 2009-06-01
> **chili555 said:**
> If you do:```
sudo rmmod -f iwlagn
sudo modprobe ndiswrapper
```Are there any errors? Does you interface still show as 'Unclaimed'?

By the way, this temporary experiment will probably not survive a reboot, so if it works, we will need to make a couple of changes to make it permanent.
I executed both of those without encountering any errors. But there's been no change in the Network Manager's behaviour either. 

If it helps any, in the meantime I booted JJ once again from the Live CD (because that way wireless works) and looked at the output friom * lshw -C network.* The wireless network is claimed and this is what its configuration line looks like:

```
configuration: broadcast=yes driver=iwlagn ip=192.168.1.102 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
```Quite a difference compared to the present contents of just* latency=0.* So you are correct, iwlagn is the driver to use. Question is how?

I hope you will come up with an answer, thanks.

---

### Post by chili555 on 2009-06-01
> iwlagn is the driver to use. Question is how?Well, it's a coin toss. Either iwlagn or ndiswrapper ought to work, but neither works! Usually, when you see this:> netw5x32 : driver installed
    device (8086:4232) present ([COLOR="Red"]alternate driver: iwlagn[/COLOR])it suggests that there is a conflict between the ndiswrapper driver and the native driver, iwlagn, in this case. Generally, when ndiswrapper is installed, the native driver is blacklisted. Maybe it didn't work so well, in this case. Please do:```
sudo rmmod -f iwlagn
sudo modprobe ndiswrapper
sudo ndiswrapper -l
```*Now *is it 'Unclaimed'? If that makes no difference in the health of your wireless card, then I think we can conclude that ndiswrapper is not going to work for us and I suggest you remove it through Synaptic.

Then, I'd like to look through dmesg to see what is not happening correctly. Please do:```
dmesg > dmesg_diego.txt
```A text file will be created in your home directory. Right-click it and select 'Create Archive.' Select .zip. Post back and attach *dmesg_diego.txt.zip*.

Finally, as long as you have the ethernet cable attached and running, please do:```
sudo apt-get install linux-backports-modules-jaunty-generic
```There is a newer iwlagn in there.

---

### Post by don_diego on 2009-06-01
> **chili555 said:**
> 
```
sudo rmmod -f iwlagn
sudo modprobe ndiswrapper
sudo ndiswrapper -l
```*Now *is it 'Unclaimed'? If that makes no difference in the health of your wireless card, then I think we can conclude that ndiswrapper is not going to work for us and I suggest you remove it through Synaptic. I did them all, there were no errors and the network remains UNCLAIMED. I have removed ndiswrapper as you suggested.
> Then, I'd like to look through dmesg to see what is not happening correctly. Please do:```
dmesg > dmesg_diego.txt
```A text file will be created in your home directory. Right-click it and select 'Create Archive.' Select .zip. Post back and attach *dmesg_diego.txt.zip*.Done, at least I hope so. (I only tried to attach a file once before and it didn't work.)
>  Finally, as long as you have the ethernet cable attached and running, please do:```
sudo apt-get install linux-backports-modules-jaunty-generic
```There is a newer iwlagn in there.Done. No errors occured. I'll get this reply on its way and reboot. If I notice a change I'll post again right away, if not then things remained the same.

In the meantime, many thanks.

---

### Post by chili555 on 2009-06-01
Your dmesg came through fine. There are some interesting errors concerning ndiswrapper, however, for now, we have removed it. This is quite interesting about iwlagn:> iwlagn 0000:03:00.0: PCI INT A disabledThis is what my own dmesg says about the same subject:> iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17Ater a night's sleep, I will be googling.

---

### Post by don_diego on 2009-06-01
> **chili555 said:**
> Your dmesg came through fine. There are some interesting errors concerning ndiswrapper, however, for now, we have removed it. This is quite interesting about iwlagn
Indeed, I looked at that dmesg file and, while nothing in there meant anything to me, I figured that last line had to mean trouble.
> After a night's sleep, I will be googling.I am sorry to cause you so much work, I really do, and wish there was some way I could reciprocate other than just saying thank you!

---

### Post by chili555 on 2009-06-02
> wish there was some way I could reciprocate My reward will be when you tell us its all working now and you are loving Ubuntu.

Was this dmesg done after you removed ndiswrapper? I am mystified that there are numerous ndiswrapper errors in there. Please do:```
sudo nano /etc/modules
```Make sure that iwlagn is listed and ndiswrapper is not. Remove ndiswrapper, if it's there, save and close nano. Next, please do:```
sudo rm /etc/modprobe.d/ndiswrapper
```Next, please do:```
sudo nano /etc/modprobe.d/blacklist.conf
```Make sure iwlagn is not there; remove it if it is and save and close nano. To be on the safe side, reboot and see if your wireless is 'Unclaimed.' Post back with hopefully good news. If you have bad news, please give us another dmesg as outlined above.

---

### Post by don_diego on 2009-06-02
> **chili555 said:**
> My reward will be when you tell us its all working now and you are loving Ubuntu.
Don't worry, I don't let a small detail like wireless not working deter me. I DO love Ubuntu and with your help I am sure that detail will soon be ironed out so I can eventually disconnect this laptop from its umbilical cord and take it with me. 

To keep this brief, I executed all the commands you had listed and there was no trace of *ndiswrapper* to be found anywhwere, *iwlagn* appeared in /etc/modules and but was not blacklisted in blacklist.conf. 

However, after rebooting I see that my wireless is no longer UNCLAIMED, it is now DISABLED! I am attaching a new dmesg in the hope you can figure out what has happened. This file was made after the reboot.

BTW, this is probably totally unrelated but when I boot up a line is displayed as follows:

[CENTER][LEFT][FONT=Courier New]**[1.0985650] pci 0000:02:00:00 unsupported PM cap regs version (7)**[/FONT]
[/LEFT]
 
[LEFT]This causes a 20 second delay in the bootup process and that's the reason I can quote it completely.
[/LEFT]
 [/CENTER]

---

### Post by chili555 on 2009-06-02
> [1.0985650] pci 0000:[COLOR="Red"]02:00:00[/COLOR] unsupported PM cap regs version (7)Please run:```
lspci
```Let's see what device has that PCI bus and we can troubleshoot that.> However, after rebooting I see that my wireless is no longer UNCLAIMED, it is now DISABLED!'Disabled' usually, not always, means that the device is turned off by the wireless switch or key combination. This will be confirmed with:```
sudo cat /var/log/messages | grep -i kill
```It may also be disabled in the computer's BIOS.

I strongly feel we are getting closer!

PS- I think the 02:00:00 device is your ethernet device. I am googling and temporarily stumped.

---

### Post by don_diego on 2009-06-02
> **chili555 said:**
> Please run:```
lspci
```Let's see what device has that PCI bus and we can troubleshoot that]/quote 
Here's the output from *lspci*:
```
lutz@lutz-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
```> 'Disabled' usually, not always, means that the device is turned off by the wireless switch or key combination. This will be confirmed with:```
sudo cat /var/log/messages | grep -i kill
```It may also be disabled in the computer's BIOS.I think we can safely assume that the labtop's wifi is working because I've never turned it off and its LED is on, it also worked when I ran JJ from the Live CD and I have not made any changes in the BIOS. BTW, *sudo cat /var/log/messages | grep -i kill* did NOT provide any kind of output.


[quote]I strongly feel we are getting closer!I thought you were going to say you feel like you are leading a blind man down a dark tunnel. But maybe that bright spot at the end is getting bigger!

> PS- I think the 02:00:00 device is your ethernet device. I am googling and temporarily stumped. Speaking of googling, I did some of that, too, and found an interesting Ubuntu website (Ubuntuusers.de) where I saw an interesting thread abou iwlagn and the Intel wifi 5100 chipset. I had no trouble reading the German text but unfortunately the LINUX speak was Greek to me.

---

