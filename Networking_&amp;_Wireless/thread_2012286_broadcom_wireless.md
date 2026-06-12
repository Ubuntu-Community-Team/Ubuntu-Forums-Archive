---
title: "broadcom wireless"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by toddkramer on 2012-06-28
here's my configs





-network UNCLAIMED      
        description: Network controller  
        product: BCM4311 802.11b/g WLAN  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:06:00.0  
        version: 01  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list  
        configuration: latency=0  
        resources: memory:30000000-30003fff

---

### Post by wildmanne39 on 2012-06-28
Hi, welcome to the forum! Please open a terminal ctrl+alt+t
Then copy and paste the following commands for accuracy:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source bcmwl
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
unplug wired connection then reboot.
Thanks

---

### Post by toddkramer on 2012-06-28
Building dependency tree       
Reading state information... Done
E: Unable to locate package broadcom-stasource
E: Unable to locate package bcmwl
albert@albert-Presario-V5000-EZ427UA-ABA:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 263 not upgraded.
Need to get 3,947 kB of archives.
After this operation, 8,962 kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates/multiverse linux-firmware-nonfree all 1.11ubuntu1 [3,947 kB]
Fetched 3,947 kB in 6s (570 kB/s)                                              
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 142194 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.11ubuntu1_all.deb) ...
Setting up linux-firmware-nonfree (1.11ubuntu1) ...
albert@albert-Presario-V5000-EZ427UA-ABA:~$

---

### Post by toddkramer on 2012-06-28
still no wireless connections available.

---

### Post by wildmanne39 on 2012-06-28
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
nm-tool
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by toddkramer on 2012-06-28
here you go:




albert@albert-Presario-V5000-EZ427UA-ABA:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux albert-Presario-V5000-EZ427UA-ABA 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux
albert@albert-Presario-V5000-EZ427UA-ABA:~$ lspci -nnk | grep -iA2 net
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel modules: wl, ssb
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:30a5]
    Kernel driver in use: e100
albert@albert-Presario-V5000-EZ427UA-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

albert@albert-Presario-V5000-EZ427UA-ABA:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:16:D4:3B:D7:EC

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.195
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


albert@albert-Presario-V5000-EZ427UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
albert@albert-Presario-V5000-EZ427UA-ABA:~$ lsmod

---

### Post by chili555 on 2012-06-28
Hey, Todd, please unload and reload the driver first:```
sudo modprobe -r b43
sudo modprobe b43
```Any improvement?

---

### Post by toddkramer on 2012-06-28
Well, can I do a test without uplugging the wired connection?

---

### Post by chili555 on 2012-06-28
> 0: hp-wifi: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]Is the wireless switch turned off on that HP? Please flip it on.

---

### Post by chili555 on 2012-06-28
> **toddkramer said:**
> Well, can I do a test without uplugging the wired connection?If it's working correctly, even with the ethernet connected, you should be able to scan:```
sudo iwlist wlan0 scan
```Flip that switch, please.

---

### Post by toddkramer on 2012-06-28
So when I right-click on the network tab at the top, I should see an option for a wireless connection, right? Well there's not even a "wireless connection" option there.

---

### Post by chili555 on 2012-06-28
I don't doubt it. Please see post #9.

---

### Post by toddkramer on 2012-06-28
Well, I thought I was pretty smart, this is not my computer and I did not know I had to turn on wireless with a freakin button. 


Thanks for your help guys.


YEAH  IT WORKS

---

### Post by chili555 on 2012-06-28
> **toddkramer said:**
> Well, I thought I was pretty smart, this is not my computer and I did not know I had to turn on wireless with a freakin button. 


Thanks for your help guys.


YEAH  IT WORKSHey, we're just glad it's working no matter what the method. Welcome to the Ubuntu community!

Please use thread tools at the top and mark Solved.

Have fun!

---

### Post by toddkramer on 2012-06-29
Update, the following morning. I shut the computer down over night, when I turned it on this morning I figured all was well. Just needed to push the "wireless" hard button. Well it did not light up. So I "unloaded" and "reloaded" the drivers with the

sudo modprobe -r b43 sudo modprobe b43command and sure enough it began working. I think there may be an issue with this machines hardware. If anyone has more diagnosis for this issue please leave a post here.

Thanks

Todd

---

### Post by chili555 on 2012-06-29
Please try this:```
sudo gedit /etc/rc.local
```Just above the exit 0 line, add these two lines:```
rfkill unblock all
modprobe b43
```Proofread, save and close gedit. When you boot up tomorrow, don't touch the wireless button and tell us if it's working.

---

### Post by toddkramer on 2012-06-29
So the final result is: IT WORKS. If anyone has the same Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware 

and you are using a COMPAQ PRESARIO with the "hardset" button for wireless connection
and you are having trouble getting the settings to stay, follow the threads and do exactly the same commands. I have a feeling you may only need to add the script that is posted above.

If you have questions you may ask me and I will try to answer. I am, by no means, an expert at Linux but if you can follow directions then this fix is pretty simple. I would like to thank the Ubuntu Community and Forum for the help.

Todd:guitar:

---

