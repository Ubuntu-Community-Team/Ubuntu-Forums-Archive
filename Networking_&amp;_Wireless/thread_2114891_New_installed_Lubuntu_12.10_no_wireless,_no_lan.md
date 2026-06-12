---
title: "New installed Lubuntu 12.10 no wireless, no lan"
date: 2013-02-11
forum: Networking &amp; Wireless
---

### Post by Ian CPFC on 2013-02-11
Hi everyone,
I have a compaq mini netbook with windows xp. As it was becoming so slow lately I thought I should use a light software to use it during my travels.
I added a partition with Lubuntu 12.10.
It got installed easily and quickly.
I like the light OS and it's very quick on my netbook.
The problem is both the wireless AND LAN do not work, so that the netbook is now basically useless, since I cannot connect it in any way...
Just to give you some more info, it does work well with windows, both LAN and wireless, so those cards are not damaged nor disabled, they do work with Windows.
Any suggestion on how to solve this?
:confused:

---

### Post by Rex Bouwense on 2013-02-11
Don't be insulted, but have you enabled networking and wireless?  Just click on the icon in the lxpanel and check enable.

---

### Post by Ian CPFC on 2013-02-11
> **Rex Bouwense said:**
> Don't be insulted, but have you enabled networking and wireless?  Just click on the icon in the lxpanel and check enable.
No worries, I understand some users may even not do that :lolflag:
It is enabled.

Actually, when clicking on the relevant icon in the tray bar I have the following:

no network devices available (not possible to click on it)
VPN connections
Enable networking (and that is marked, so it's enabled)
information (not possible to click on it)
Edit

There is no wireless reference though.
And of course the wireless is working. I'm using it with a notebook with Ubuntu in this very moment.

---

### Post by Rex Bouwense on 2013-02-11
Next stupid question:  On my ASUS EeePC netbook there is an Fn key that starts wifi (in my case it is Fn F2). If you have one is it turned on because "no network devices detected".

---

### Post by Ian CPFC on 2013-02-11
> **Rex Bouwense said:**
> Next stupid question:  On my ASUS EeePC netbook there is an Fn key that starts wifi (in my case it is Fn F2). If you have one is it turned on because "no network devices detected".
Turned on as well ;)

---

### Post by Rex Bouwense on 2013-02-11
Ok.  No more stupid questions.  
Identify your network card.
```
lspci | grep -i ethernet
```

See [http://lxlinux.com/#16](http://lxlinux.com/#16)

---

### Post by Ian CPFC on 2013-02-11
> **Rex Bouwense said:**
> Ok.  No more stupid questions.  
Identify your network card.
```
lspci | grep -i ethernet
```See [http://lxlinux.com/#16](http://lxlinux.com/#16)
First of all allow me to thank you for your patience.
Anyway, there's no reply to that command.

---

### Post by Rex Bouwense on 2013-02-11
Excuse the wait.  I had to go buy some propane.  You got no response when you entered that into the terminal?  Try simply 
```
lspci
```
Make sure that you are entering small l not a 1.  Then hit enter.

---

### Post by Ian CPFC on 2013-02-11
> **Rex Bouwense said:**
> Excuse the wait.  I had to go buy some propane.  You got no response when you entered that into the terminal?  Try simply 
```
lspci
```Make sure that you are entering small l not a 1.  Then hit enter.
with that command only it replies. Here it is:

00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by Bucky Ball on 2013-02-11
*Thread moved to **Networking & Wireless**.*

Try:

```
sudo lshw -C network
```

More specific and more info. That wireless card does work but needs some tweaking. Think you need to install b43-fwcutter and firmware-b43-lpphy-installer then restart. You may need to blacklist something if that doesn't work but not too sure.

Can you get online with a cable and update? Is there anything for the wireless in Additional Drivers?

---

### Post by Ian CPFC on 2013-02-11
> **Bucky Ball said:**
> *Thread moved to **Networking & Wireless**.*

Try:

```
sudo lshw -C network
```More specific and more info. That wireless card does work but needs some tweaking. Think you need to install b43-fwcutter and firmware-b43-lpphy-installer then restart. You may need to blacklist something if that doesn't work but not too sure.

Can you get online with a cable and update? Is there anything for the wireless in Additional Drivers?
Cheers to you as well. Sorry for getting to the wrong section.
Anyway here's the reply:

ian@ian-Compaq-Mini:~$ sudo lshw -c network
[sudo] password for ian: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff

---

### Post by Rex Bouwense on 2013-02-11
I should have guessed that you have a Broadcom chip set.  See here:

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

I had the same problem when trying to activate on my old (really old) Dell Inspiron 1000.

---

### Post by Ian CPFC on 2013-02-11
Got it.
So mine is this:
14e4:4315 
   yes (2.6.33+) 
   BCM4312 
   b/g 
   LP (r1) 
   wl 

and I should install this:
[https://launchpad.net/ubuntu/+source/bcmwl](https://launchpad.net/ubuntu/+source/bcmwl)

correct?
Provided I can do it since I have no LAN as well...

---

### Post by Rex Bouwense on 2013-02-11
Just connect your computer to your router using an ethernet cable.  If you cannot do that you should be able to download the package(s) to a flash drive and get it off of that.

Here is the official Ubuntu wiki on installing broadcom chip set drivers

---

### Post by Ian CPFC on 2013-02-11
> **Rex Bouwense said:**
> Just connect your computer to your router using an ethernet cable.  If you cannot do that you should be able to download the package(s) to a flash drive and get it off of that.

Here is the official Ubuntu wiki on installing broadcom chip set drivers

Thank you very much for your help.
The problem with the ethernet cable is the fact that that doesn't work either...
I downloaded it to a flash drive, but could not find a way to install it.
I have the tar.gz file but I'm still not expert enough to install it from there.
Will study about it.
Cheers!

---

### Post by Rex Bouwense on 2013-02-12
It has been a while but I believe you right click the file and choose to extract it here.  Since there are many kinds look for the read me file.

---

### Post by Ian CPFC on 2013-02-12
> **Rex Bouwense said:**
> It has been a while but I believe you right click the file and choose to extract it here.  Since there are many kinds look for the read me file.
Thank you for your reply.
Unfortunately I didn't understand how to install it, so I'm still without connection at all.
I've extracted it, but there's no read me file.

---

### Post by Rex Bouwense on 2013-02-13
Finally got back to the forums and discovered that I didn't post the site with the instructions.  My error.  See here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

---

