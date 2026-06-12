---
title: "Xterasys, INPROCOMM IPN 2220 PCI card (Linksys WPC54G ver.4)"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by Vox754 on 2009-01-17
**1. History**

This thread is a follow-up to this thread [http://ubuntuforums.org/showthread.php?p=1927767](http://ubuntuforums.org/showthread.php?p=1927767) which is now in the read-only Forums Archive.

The archived thread was created: 2006-December-24, running Ubuntu 6.10
The archived thread was updated: 2007-sometime, running Ubuntu 7.04
The archived thread was updated: 2008-March-25, running Ubuntu 7.10

This thread was created: 2009-January-17, running Ubuntu 8.10

**2. The Inprocomm IPN 2220 chipset**

This thread describes my experience with the **Xterasys WPG2600 802.11g Wireless LAN PCI Card** with **Inprocomm IPN 2220** chipset.

[http://www.xterasys.com/product/wpg2600.htm](http://www.xterasys.com/product/wpg2600.htm)

This card is for a desktop PC, not a laptop. Nevertheless, the information contained here may be useful to those having a laptop with this same chipset.

I originally started the archived thread on **2006-December-24** while running **Ubuntu 6.10**. At that time, I thought my card was **Linksys WPC54G ver.4**, as reported by

```

lspci -v

```

```

00:09.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
        Subsystem: Linksys, A Division of Cisco Systems WPC54G ver. 4
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at e200 [size=32]
        Memory at f6001000 (32-bit, non-prefetchable) [size=32]
        Memory at f6002000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
```

Now I know that it is a fairly generic card with an **Inprocomm IPN 2220 chipset**, which is not very common.

```

00:09.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
	Subsystem: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at e200 [size=32]
	Memory at fa001000 (32-bit, non-prefetchable) [size=32]
	Memory at fa002000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ndiswrapper
```

**InProComm Inc. no longer exists as a company**; they only developed a couple of chips, so only few binary drivers were ever released for Windows. I don't know if 64-bit versions exist, as I have only used this device in 32-bit Windows XP and Ubuntu.
The last Windows drivers were released in 2005.

Since no source code is available, no free drivers have been developed, and this chipset only works with "**ndiswrapper**".

**3. Links**

More information on InProComm can be found at [http://en.wikipedia.org/wiki/Inprocomm](http://en.wikipedia.org/wiki/Inprocomm)

Some devices with Inprocomm chipsets can be found at [http://inprocomm.rapla.net/](http://inprocomm.rapla.net/)

Specific information on these chipsets in Ubuntu can be found at [https://help.ubuntu.com/community/WifiDocs/Device/ipn2220](https://help.ubuntu.com/community/WifiDocs/Device/ipn2220)

First, you should understand how ndiswrapper works. The Ubuntu community knowledge regarding ndiswrapper is found here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The "**ndiswrapper list**" shows which devices have been known to work with a specific version of ndiswrapper, in which Linux distribution, and with which drivers, [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

A "**comprehensive ndiswrapper troubleshooting guide**" is found in this thread [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
You should check it out.

The **ndiswrapper project page** at SourceForge.net is available here [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

**4. Ndiswrapper in Ubuntu**

Ubuntu has included the ndiswrapper kernel module "**ndiswrapper.ko**" as part of the Ubuntu Linux Kernel since **Ubuntu 6.06** (Dapper Drake).

In Ubuntu 8.10, the full path to the module is
```

/lib/modules/2.6.27-9-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko

```

In order to use ndiswrapper, the "userspace" utilities need to be installed. These utilities are generally found in a package named "**ndiswrapper-utils**", for instance, **ndiswrapper-utils-1.9**.

If you feel that you need to compile your own version of ndiswrapper you may remove any ndiswrapper packages and the kernel module without problem.
However, renaming "**ndiswrapper.ko**" to "**ndiswrapper.ko.original**" may be enough.

The source package "**ndiswrapper-x.y.tar.gz**" found at the project website includes both the kernel module and the utilities source code.

**5. Each Ubuntu distribution**

**Ubuntu 6.10 (Edgy Eft)**
Kernel version: 2.6.17-10-generic
ndiswrapper: 1.18
ndiswrapper-utils: 1.8.

This version did not work for me, so I compiled and installed ndiswrapper 1.37 from source.
I used the **inprocomm_ipn2220_v3.07.02.2005.zip** drivers attached to this thread.

I couldn't configure the wireless network through the graphical interface so I used the terminal, after which I didn't have any problems at all.
I only tested 64-bit WEP encyption.

```

iwlist wlan0 scan
sudo iwconfig wlan0 essid ESSID_NAME
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 key open xxxxxxxxxx

```

In subsequent releases a newer version of ndiswrapper was included in the kernel, which worked with the already installed drivers. I didn't need to do anything else.

**Ubuntu 7.04 (Feisty Fawn)**
Kernel version: 2.6.20-16-generic
ndiswrapper: 1.38
ndiswrapper-utils: 1.9

**Ubuntu 7.10 (Gutsy Gibbon)**
Kernel version: 2.6.22-14-generic
ndiswrapper: 1.45
ndiswrapper-utils: 1.9

**Ubuntu 8.04 (Hardy Heron)**
I did not test my wireless card with this distribution.

**Ubuntu 8.10 (Intrepid Ibex)**
Kernel version: 2.6.27-9-generic
ndiswrapper: 1.53
ndiswrapper-utils: 1.9

At first it didn't want to work with the drivers I had been using. The kernel logs showed
```

[ 38.859085] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 38.958858] ndiswrapper (check_nt_hdr:156): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
[ 38.958867] ndiswrapper (load_sys_files:206): couldn't prepare driver 'neti2220'
[ 38.959492] ndiswrapper (load_wrap_driver:10: couldn't load driver neti2220; check system log for messages from 'loadndisdriver'
[ 38.959584] usbcore: registered new interface driver ndiswrapper

```

I tried the **ipnworks.tar.gz** drivers found in a different web page and they worked.

I did some **md5 checksums** to verify that these files are in fact the same as the ones included in the other zip file, so I don't know why it didn't want to work the first time.

After installing the correct drivers, **NetworkManager Applet 0.7.0** was able to detect and configure my wireless connection without problem. Again, I have only tested 64-bit WEP encryption.

*Warning: if you try to compile ndiswrapper in Ubuntu 8.10, you'll notice that there are errors. You have to apply a patch to the ndiswrapper source as described in the **comprehensive ndiswrapper troubleshooting guide** in this thread [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)*


**6. Drivers used with the IPN 2220 chipset**

These drivers have worked for me, and I have attached them to this post:
[LIST=1]
[*]**inprocomm_ipn2220_v3.07.02.2005.zip** which I found in this thread [http://www.laptopvideo2go.com/forum/index.php?showtopic=7172](http://www.laptopvideo2go.com/forum/index.php?showtopic=7172)

[*]**ipnworks.tar.gz** which I found in this thread (in German) [http://forum.ubuntuusers.de/topic/hardy-heron-ndiswrapper-inprocomm-ipn-2220/](http://forum.ubuntuusers.de/topic/hardy-heron-ndiswrapper-inprocomm-ipn-2220/)
[/LIST]


Other drivers found on the net:
```

80211bg.zip
a802.zip
acerwlan.zip
WPC54G v4 driver rev 1.22.1.2004.zip

```

Some Acer laptops included this chipset, so a driver for it can be found on the driver CD, or downloaded from the vendor's website.

**7. Quick installation:**
In general, as long as you are using a recent ndiswrapper (>= 1.37), a 32-bit Ubuntu and 32-bit Windows XP drivers, this card should work.

For more detailed instructions, check out the Ubuntu community help [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

1a. If you compile ndiswrapper and the utilities from source
```

sudo make uninstall
make
sudo make install

```

1b. If you use the module included in the kernel and install the utilities from the repositories
```

sudo aptitude install ndiswrapper-utils-1.9

```

2. Extract the zip file or tarball with the Windows drivers.
```

unzip inprocomm_ipn2220_v3.07.02.2005.zip -d inprocomm_ipn2220_v3.07.02.2005

--- or ---

tar xvzf ipnworks.tar.gz

```

3. Change into the directory containing the driver; the *.inf and *.sys files must be present.

4. Install the driver with ndiswrapper
```

sudo ndiswrapper -i neti2220.inf

```

5. Check that it's been installed properly
```

ndiswrapper -l

neti2220 : driver installed
	device (17FE:2220) present

```

6. Load the ndiswrapper module
```

sudo modprobe ndiswrapper

```

7. Your device should be detected and you should be able to configure it with the **NetworkManager Applet**, or through the terminal using "**iwconfig**".

8. If everything is working correctly, you may set to load the "ndiswrapper" module at start up
```

sudo ndiswrapper -m

```

**8. Additional information**

Since I don't really need security in my network only 64-bit WEP encryption has been tested.

My motherboard is a Biostar K8M800-M7A

Sometimes I would lose association with my access point. I only needed to re-enable the connection to make it work.

From the terminal it is possible to run
```

sudo /etc/init.d/networking restart

```
to restart the network detection and renew the IP address from the access point.

**In general, I don't recommend this card at all.** The manufacturer doesn't exist any more and there are no free drivers. I have been lucky enough to use this card for the past two years with the help of ndiswrapper. Who knows when this card will become totally unusable, either because of changes in ndiswrapper or the kernel, which actually does the work.
Only use this old card if you have no choice. In other cases get one of the cards with free drivers.

---

### Post by pitoszek on 2009-02-07
Hi, i've got such a card WPC64Gv4. Since a few days I'm still trinig to connect via this card. The problem is that my laptop got only 128Mb and I've got only a few distro to choose. 
Thanks for informations, but even your files can't help me. 
May I have a kind request for ndiswrapper (in any well-worked version) with drivers for ipn2220? Is that possible?

---

### Post by Vox754 on 2010-04-19
> **pitoszek said:**
> Hi, i've got such a card WPC64Gv4. Since a few days I'm still trinig to connect via this card. The problem is that my laptop got only 128Mb and I've got only a few distro to choose. 
Thanks for informations, but even your files can't help me. 
May I have a kind request for ndiswrapper (in any well-worked version) with drivers for ipn2220? Is that possible?
I'm sorry I didn't answer before.

To anyone reading this, please note that the mentioned card **WPC64Gv4** is not the same one as **WPC54G ver.4** which I mentioned in the first post.

Also, please note that my card **is NOT** WPC54G ver.4. It was **originally** identified as WPC54G ver.4., but it is actually **INPROCOMM IPN 2220**. Therefore, this thread may not apply to you.

Also, note that with current Ubuntu distributions (Ubuntu 9.10), there is no need to manually compile "ndiswrapper", this kernel module is already included in the default system.

For Ubuntu 9.10:
```

user@dekstop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.31-20-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.55
vermagic:       2.6.31-20-generic SMP mod_unload modversions 586 

```

With ndiswrapper already installed, only the Windows driver (inprocomm_ipn2220_v3.07.02.2005.zip) is needed.

---

### Post by timsoft on 2011-01-21
another location for the windows drivers for the inprocomm 2220 device can be found at 
[http://support1.toshiba-tro.de/tedd-files2/0/wlesslan-20080722133341.zip](http://support1.toshiba-tro.de/tedd-files2/0/wlesslan-20080722133341.zip)  :)

---

