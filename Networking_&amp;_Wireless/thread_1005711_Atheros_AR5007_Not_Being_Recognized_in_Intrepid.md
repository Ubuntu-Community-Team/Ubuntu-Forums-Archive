---
title: "Atheros AR5007 Not Being Recognized in Intrepid"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by Mr_Mischif on 2008-12-08
Hello all,

as the title states, I am not able to find my Atheros AR5007 wireless card no matter what I do, and thusly cannot connect to any wireless networks.

In the beginning I was running Hardy, and with a couple MadWiFi drivers, everything was fine. Then I upgraded to Intrepid, and I noticed that I couldn't find NetworkManager; I had the applet in my toolbar, but when I tried to access it through System->Admin it wasn't there. I checked my main menu configuration to see if I moved it or hid it, but it's not there.

Then I decided NetworkManager was being wonky so I decided to use WiCD, which I was using when I was running Hardy, but when I was trying to find my wifi adaptor, I couldn't find it. I tried iwconfig, but all entries said no wireless extensions or something like that (I don't know what it is off the top of my head, I'm typing this in an Apple Store)

Finally I tried ifconfig to see what's going on, but it just gave me eth0 (my wired connection), loopback, and pan0 (I don't know what this; it says it uses etherned, but I know that's a lie since the computer only has one ethernet connection and it's not the same MAC address as my real ethernet card).

I've checked all hardware and software switches, and they're all on, so I don't know what else to do - it can't be just a general problem with the computer or networking because the card was working fine before I upgraded and the wired connection works like a dream. PLEASE HELP!

---

### Post by bl4hbl4hbl4h on 2008-12-08
Type in sudo lshw -C network in the terminal and post what comes up.

---

### Post by Mr_Mischif on 2008-12-08
> **bl4hbl4hbl4h said:**
> Type in sudo lshw -C network in the terminal and post what comes up.

Ok, I got this output:

```
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:37:17:28
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=yes module=r8169 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:54:64:ba:ad:9a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

But now I have a new problem: just so you know I restarted the computer, and now when I check ifconfig eth0 is gone, but something new called pan0:avahi has come up; eth0 still remains in iwconfig though

---

### Post by bl4hbl4hbl4h on 2008-12-08
Okay, so your wireless drivers are not installed, hence the "unclaimed" part.

Type this in the terminal without the spaces

sudo wget http:// snapshots.madwifi. org/ madwifi-hal-0.10.5.6-current.tar.gz (only the url without spaces, everything else needs the spaces)

then type in tar zxvf madwifi-hal-0.10.5.6-current.tar.gz

then type in cd madwifi-hal-0.10.5.6-r3879-20081204

and then sudo make

and sudo make install

that should solve your problem.

note that you may have to reboot

---

### Post by thewaytolite on 2009-01-06
These are the steps that worked for me..
C/O Reasoner

The device string displayed by lspci -v was as follows:

Code:

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

First under System/Administration/HarwareDrivers disable both the Atheros HAL and the Atheros wireless thing and then reboot.

The kernel headers and the compiler are needed to build this driver so I started by installing build-essential. In a terminal window (Applications/Accessories/Terminal) enter:

Code:

sudo apt-get install build-essential

The driver code will be downloaded with the subversion source code manager so I installed subversion:

Code:

sudo apt-get install subversion

I needed a place to put the driver source without mixing it up with other stuff so I changed directory to my home directory:

Code:

cd ~

Created a directory:

Code:

mkdir madwifi

And changed to the new dirctory:

Code:

cd madwifi

Use subversion to download (checkout) a copy of the code:

Code:

svn co [http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6](http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6)

After the driver code is downloaded by subversion, change to the directory, which should be madwifi-hal-0.10.5.6

Code:

cd madwifi-hal-0.10.5.6

Run the make script to have the compiler build the driver:

Code:

make

Install the driver

Code:

sudo make install

Add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding "ath_pci" (without the quotes) to the end of the /etc/modules file. I used the vi editor which I won't describe here. Gedit is probably easy to use so try:

Code:

sudo gedit /etc/modules

Now you can reboot and it should work. To get it working without a reboot you need to load the module manually:

Code:

sudo modprobe ath_pci

That should do it. The little wireless button seems to always stay lit orange. When I press it it seems to disable the wireless but it still stays lit orange. WPA works for me. I assume WEP will also. I haven't tried WPA2

---

### Post by Sleestack on 2009-01-16
Thanks to everyone who contributed to this thread. I'm using an Acer 4720Z laptop and Ubuntu 8.10 and the wireless was not being recognized. I originally Googled around and found there is a method to use a Windows wireless driver within Ubuntu (news to me...I had to locate and download the original Windows .INF file from the Acer web site,) but I got an error telling me "a configuration tool could not be found" during configuration. Maybe just an 8.10 bug. Googled more...found this thread. After trying the first solution without success, I carefully followed thewaytolite's and it worked perfectly for me. It was all new to me, never did a MAKE before. Thanks again for everyone's input.

---

### Post by NCSmokeEater on 2009-01-17
For anyone who needs the guidance, I found it a few weeks ago when I was going through what you guys are going through haha It was a pain. I followed the directions [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html") on UbuntuGeek. The article goes in detail of the easiest way to get the AR5007eg's and ar242x's working on Intrepid. After almost a month of no wireless, I found that and it worked like a charm.

Best of luck.

-John

---

### Post by darksideforge on 2009-01-19
I have yet to have any of these suggestions work for me...it's obviously a user problem if y'all are having success with it. Here are copies of my code:

```
~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1a:92:a9:bf:35
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 42:b1:fe:42:df:98
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
~$ sudo ifconfig
[sudo] password for darkside: 
eth0      Link encap:Ethernet  HWaddr 00:1a:92:a9:bf:35  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fea9:bf35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16908 (16.9 KB)  TX bytes:5259 (5.2 KB)
          Interrupt:16 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4856 (4.8 KB)  TX bytes:4856 (4.8 KB)

~$ sudo wget http://snapshots.madwifi-hal-0.10.5.6-current.tar.gz
--2009-01-19 11:27:45--  http://snapshots.madwifi-hal-0.10.5.6-current.tar.gz/
Resolving snapshots.madwifi-hal-0.10.5.6-current.tar.gz... 74.54.82.156
Connecting to snapshots.madwifi-hal-0.10.5.6-current.tar.gz|74.54.82.156|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 411 [text/html]
Saving to: `index.html'

100%[======================================>] 411         --.-K/s   in 0s      

2009-01-19 11:27:45 (23.5 MB/s) - `index.html' saved [411/411]

~$ tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
tar: madwifi-hal-0.10.5.6-current.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
~$ cd madwifi-hal-0.10.5.6-r3879-20081204
bash: cd: madwifi-hal-0.10.5.6-r3879-20081204: No such file or directory
~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ff680000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec00 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at ff640000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, fast devsel, latency 0
	Memory at ff580000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at ff63c000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: ff200000-ff2fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at e880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e480 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at e400 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ff63bc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=09, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: ff300000-ff3fffff
	Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7128
	Flags: fast devsel, IRQ 17
	Memory at ff2f0000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath_pci

05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at ff300000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
	Memory window 0: 40000000-43fff000 (prefetchable)
	Memory window 1: 44000000-47fff000
	I/O window 0: 0000d000-0000d0ff
	I/O window 1: 0000d400-0000d4ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at d800 [size=256]
	Memory at ff3ffc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139cp, 8139too
```

bl4hbl's suggestions bombed out on the *$ tar zkvf madwifi-...* line, when my lappy gave me an unrecoverable error

NCSmokeEater's suggestions bombed out (by following the link s/he provided when I followed ubuntugeek's suggestions and got to the

```
sudo tar -jxvf compat-wireless-2.6.tar.bz
```

What am I doing wrong? The bottom line is that my Atheros AR242x card is being recognized, but there aren't any drivers for it. I run a completely 100% Ubuntu 8.10 system, so using windows--or, to the best of my knowledge, windows drivers--is not an option.  Thanks for any advice, guidance, or direction.

---

### Post by gymophett on 2009-01-19
This worked for me..
Try this :)

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

### Post by kevdog on 2009-01-19
I'm not sure why this method is listed as not working:

Install linux-backports-modules-intrepid. This works but you would have to reload the driver every time you log on

Have to reload the driver every time you log on?  Thats exactly the same with madwifi!! What is this guy talking about??

---

