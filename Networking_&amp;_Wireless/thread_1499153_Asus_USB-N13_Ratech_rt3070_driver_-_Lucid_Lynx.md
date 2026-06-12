---
title: "Asus USB-N13 Ratech rt3070 driver - Lucid Lynx"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by jlh97214 on 2010-06-01
I was given the following information to help in getting my wireless driver to work.
 
 
"I think post #32 here will, with a slight modification, have your device working in a few moments." - Chili555
 
[http://ubuntuforums.org/showthread.php?t=1419504&highlight=USB-N13&page=4](http://ubuntuforums.org/showthread.php?t=1419504&highlight=USB-N13&page=4)
 
 
I have created the files in gedit and saved them.
 
I am unable to create the folders as instructed. Even in properties-permissions, the access is shaded out and I cannot use the file - create folder function as it is shaded out as well.
 
How do I get permission to add the folders?  obviously, I'm a 'newbie' so I will need baby step assistance - I learn fast, however.

---

### Post by chili555 on 2010-06-01
Let's create those files with the text editor gedit. We will use the terminal to open gedit as the super user. Super user privileges are needed to modify or create system files. Please remove the device and then open Applications > Accessories > Terminal and do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules 
```Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta"

```Notice we changed the driver to rt2870sta. Proofread carefully, save and close gedit. Now do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long line:```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread carefully, save and close gedit.

Now reinsert the device and see if you see networks when you click the Network Manager icon.

---

### Post by jlh97214 on 2010-06-02
Holy Lucid Lynx, Batman, it is working, four bars, even!!!!
 
Are we done or is there some fine tuning for the 3070 driver?
 
And, additionally, this process taught me how to access the root directory to make changes.
 
Thank you.
 
PS - Now I have a desire to get my D-Link DWA-142 wireless adapter functioning on my other computer using NDISWrapper (I have the AMD64 drivers). I couldn't get it functioning. New Link??

---

### Post by chili555 on 2010-06-02
> Are we done or is there some fine tuning for the 3070 driver?Not any fine-tuning that I know of. We are actually using the rt2870sta driver, but it's virtually the same as rt3070sta:```
$ modinfo rt2870sta
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
[COLOR="Red"]alias:          rt3070sta[/COLOR]
version:        2.0.1.0
license:        GPL
--- snip ---
```> I couldn't get it functioning. New Link?? Please, and PM me the link if I don't catch it in a couple of hours.

Glad it's working for you! Wasn't that easy? Be very careful with your newly found 'sudo' powers. With power comes responsibility.

---

### Post by jlh97214 on 2010-06-02
What would have happened if we had left the "3070" instead of inserting the "2870"?  Curiosity.

---

### Post by chili555 on 2010-06-02
> **jlh97214 said:**
> What would have happened if we had left the "3070" instead of inserting the "2870"?  Curiosity.It simply would not have worked, because there is no rt3070sta in Lucid, unless you compiled one from source. Had you tried to load rt3070sta when there is none, the process would have errored out with a message buried in the syslog. Your wireless certainly would not be working.

---

### Post by roydrager on 2010-07-17
Just an update to the much appreciated solution from Chili555.  I managed to get his solution working in 10.04 lucid lynx 32 bit with the latest usb-n13 driver from the Asus site, version 2.3.0.2 dated April 22 2010 (zip file attached to this post, and here is also the Asus official link):

[http://support.asus.com/download/download.aspx?modelname=USB-N13&SLanguage=en-us](http://support.asus.com/download/download.aspx?modelname=USB-N13&SLanguage=en-us)

(Of course Chili555's solution also works with the driver he attached in post #17 of the main thread:

[http://ubuntuforums.org/showthread.php?t=1419504&highlight=USB-N13&page=2](http://ubuntuforums.org/showthread.php?t=1419504&highlight=USB-N13&page=2)

)

The steps I followed were:

tar -xvzf DPO_RT3070_LinuxSTA_V2.3.0.2_20100422.tgz
cd DPO_RT3070_LinuxSTA_V2.3.0.2_20100422
sudo make 
make install

At this point, there was an error "error 1" with the new driver's makefile where it's looking for the file /DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat .  However the actual file is named RT2870STA.dat .  Here is the terminal output of the error:

```
make -C /home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat /etc/Wireless/RT3070STA/.
**cp: cannot stat `/home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat': No such file or directory**
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
make: *** [install] Error 2
```

The solution is to edit the os/linux/Makefile.6 file:

sudo gedit os/linux/Makefile.6

There is a line near the top:

```
DAT_FILE_NAME = RT$(CHIPSET)STA.dat
```Change this line to:

```
DAT_FILE_NAME = RT2870STA.dat
```Save, exit, then: 

sudo make install

The makefile should install without errors now.  Then create the two files in /etc/modprobe.d/ and /etc/udev/rules.d/ exactly as Chili555 wrote them:

[http://ubuntuforums.org/showpost.php?p=9395844&postcount=2](http://ubuntuforums.org/showpost.php?p=9395844&postcount=2)

Then physically insert the usb-n13 device in the usb port.  At this point ubuntu recognized the hardware, I didn't need to restart.  This new driver seems to give me better speed than the older version.

---

### Post by Tonyr63 on 2010-07-22
> **chili555 said:**
> It simply would not have worked, because there is no rt3070sta in Lucid, unless you compiled one from source. Had you tried to load rt3070sta when there is none, the process would have errored out with a message buried in the syslog. Your wireless certainly would not be working.
Hi
 
 
i have the very same problem however the process explained by Chili555 has not worked for me even though i have done the make and make install and added the rules and config files.
 
Here is some output that might assist.
 
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
#iface eth0 inet dhcp
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2776] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
02:00.0 Ethernet controller [0200]: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) [8086:108c] (rev 03)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
H/W path Device Class Description
======================================================
                               system 9210DM1
/0 bus IBM
/0/0 memory 111KiB BIOS
/0/4 processor Intel(R) Pentium(R) D CPU 3.40GHz
/0/4/5 memory 16KiB L1 cache
/0/4/6 memory 2MiB L2 cache
/0/4/0.1 processor Logical CPU
/0/4/0.2 processor Logical CPU
/0/22 memory 1GiB System Memory
/0/22/0 memory 1GiB DIMM DDR Synchronous 400 MHz (2.
/0/22/1 memory DIMM DDR Synchronous 400 MHz (2.5 ns)
/0/22/2 memory DIMM DDR Synchronous 400 MHz (2.5 ns)
/0/22/3 memory DIMM DDR Synchronous 400 MHz (2.5 ns)
/0/1 processor
/0/1/0.1 processor Logical CPU
/0/1/0.2 processor Logical CPU
/0/100 bridge 82945G/GZ/P/PL Memory Controller Hub
/0/100/2 display 82945G/GZ Integrated Graphics Control
/0/100/2.1 display 82945G/GZ Integrated Graphics Control
/0/100/1b multimedia N10/ICH 7 Family High Definition Audi
/0/100/1c bridge N10/ICH 7 Family PCI Express Port 1
/0/100/1c/0 eth0 network 82573E Gigabit Ethernet Controller (C
/0/100/1c.1 bridge N10/ICH 7 Family PCI Express Port 2
/0/100/1d bus N10/ICH7 Family USB UHCI Controller #
/0/100/1d.1 bus N10/ICH 7 Family USB UHCI Controller
/0/100/1d.2 bus N10/ICH 7 Family USB UHCI Controller
/0/100/1d.3 bus N10/ICH 7 Family USB UHCI Controller
/0/100/1d.7 bus N10/ICH 7 Family USB2 EHCI Controller
/0/100/1e bridge 82801 PCI Bridge
/0/100/1f bridge 82801GB/GR (ICH7 Family) LPC Interfac
/0/100/1f.2 scsi0 storage N10/ICH7 Family SATA IDE Controller
/0/100/1f.2/0 /dev/sda disk 160GB ST3160828AS
/0/100/1f.2/0/1 /dev/sda1 volume 146GiB EXT4 volume
/0/100/1f.2/0/2 /dev/sda2 volume 2903MiB Extended partition
/0/100/1f.2/0/2/5 /dev/sda5 volume 2903MiB Linux swap / Solaris partitio
/0/100/1f.2/1 /dev/cdrom disk DVDRAM_GSA-H10N
/0/100/1f.3 bus N10/ICH 7 Family SMBus Controller
Linux TeleUbuntu 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
[ 0.000000] found SMP MP-table at [c00f6670] f6670
[ 0.172711] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub with MMCONFIG support.
[ 0.244934] ACPI: No dock devices found.
[ 0.246302] ACPI Warning for \_SB_.PCI0._OSC: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
[ 0.396446] pnp: PnP ACPI: found 16 devices
[ 0.634021] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[ 0.651889] hub 1-0:1.0: USB hub found
[ 0.652236] hub 2-0:1.0: USB hub found
[ 0.652522] hub 3-0:1.0: USB hub found
[ 0.652813] hub 4-0:1.0: USB hub found
[ 0.653099] hub 5-0:1.0: USB hub found
[ 0.655662] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 0.658211] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 0.827478] isapnp: No Plug & Play device found
[ 11.550458] lp: driver loaded but no devices found
[ 1.109756] 0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:16:41:6a:5b:ce
[ 1.109760] 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[ 1.109774] 0000:02:00.0: eth0: MAC: 2, PHY: 2, PBA No: ffffff-0ff
[ 12.116766] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 14.054524] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 14.054528] 0000:02:00.0: eth0: 10/100 speed: disabling TSO
[ 14.054738] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 24.420008] eth0: no IPv6 routers present
[ 141.820451] e1000e: eth0 NIC Link is Down
[ 143.819341] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 143.819345] 0000:02:00.0: eth0: 10/100 speed: disabling TSO
[ 378.004456] e1000e: eth0 NIC Link is Down
[ 382.826684] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 382.826689] 0000:02:00.0: eth0: 10/100 speed: disabling TSO
[ 389.004450] e1000e: eth0 NIC Link is Down
[ 395.002519] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 395.002524] 0000:02:00.0: eth0: 10/100 speed: disabling TSO
[ 0.655659] device-mapper: multipath: version 1.1.0 loaded
[ 0.655662] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 0.344182] Switching to clocksource tsc
[ 11.931192] Console: switching to colour frame buffer device 128x48
lo no wireless extensions.
eth0 no wireless extensions.
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist-watchdog.conf:blacklist twl4030_wdt
sudo: hwinfo: command not found
 * Reconfiguring network interfaces... Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth0=eth0.
 
 
I also tried added 3 lines to the Blacklist file for RA28000 from advise on another post.
 
Do i have to restart using the process advised by RoyDrager?

---

### Post by Tonyr63 on 2010-07-22
> **roydrager said:**
> Just an update to the much appreciated solution from Chili555. I managed to get his solution working in 10.04 lucid lynx 32 bit with the latest usb-n13 driver from the Asus site, version 2.3.0.2 dated April 22 2010 (zip file attached to this post, and here is also the Asus official link):
 
[http://support.asus.com/download/download.aspx?modelname=USB-N13&SLanguage=en-us](http://support.asus.com/download/download.aspx?modelname=USB-N13&SLanguage=en-us)
 
(Of course Chili555's solution also works with the driver he attached in post #17 of the main thread:
 
[http://ubuntuforums.org/showthread.php?t=1419504&highlight=USB-N13&page=2](http://ubuntuforums.org/showthread.php?t=1419504&highlight=USB-N13&page=2)
 
)
 
The steps I followed were:
 
tar -xvzf DPO_RT3070_LinuxSTA_V2.3.0.2_20100422.tgz
cd DPO_RT3070_LinuxSTA_V2.3.0.2_20100422
sudo make 
make install
 
At this point, there was an error "error 1" with the new driver's makefile where it's looking for the file /DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat . However the actual file is named RT2870STA.dat . Here is the terminal output of the error:
 
```
make -C /home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat /etc/Wireless/RT3070STA/.
**cp: cannot stat `/home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat': No such file or directory**
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
make: *** [install] Error 2
```
 
The solution is to edit the os/linux/Makefile.6 file:
 
sudo gedit os/linux/Makefile.6
 
There is a line near the top:
 
```
DAT_FILE_NAME = RT$(CHIPSET)STA.dat
```Change this line to:
 
```
DAT_FILE_NAME = RT2870STA.dat
```Save, exit, then: 
 
sudo make install
 
The makefile should install without errors now. Then create the two files in /etc/modprobe.d/ and /etc/udev/rules.d/ exactly as Chili555 wrote them:
 
[http://ubuntuforums.org/showpost.php?p=9395844&postcount=2](http://ubuntuforums.org/showpost.php?p=9395844&postcount=2)
 
Then physically insert the usb-n13 device in the usb port. At this point ubuntu recognized the hardware, I didn't need to restart. This new driver seems to give me better speed than the older version.
 
 
Hi
 
 
Where is the os/linux folder as I cant find it in my filesystem?
 
If I run sudo gedit os/linux/Makefile.6 Gedit open an empty file?
 
Cheers
 
 
Anthony

---

### Post by misterspider on 2010-08-14
> **Tonyr63 said:**
> Hi
 
 
Where is the os/linux folder as I cant find it in my filesystem?
 
If I run sudo gedit os/linux/Makefile.6 Gedit open an empty file?
 
Cheers
 
 
Anthony

This is the Makefile for the asus driver, so it will be located wherever you saved and unzipped the driver on your system.

---

### Post by lukeiamyourfather on 2011-10-22
> **chili555 said:**
> Let's create those files with the text editor gedit. We will use the terminal to open gedit as the super user. Super user privileges are needed to modify or create system files. Please remove the device and then open Applications > Accessories > Terminal and do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules 
```Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta"

```Notice we changed the driver to rt2870sta. Proofread carefully, save and close gedit. Now do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long line:```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread carefully, save and close gedit.

Now reinsert the device and see if you see networks when you click the Network Manager icon.

I realize this was an old post, but man... You just made my day. Bought an Asus USB-N13 and it has been giving me trouble. Compiling the driver finished but then the adapter didn't work. After that stuff, it works. The box of the adapter says "Linux Support" which I figured meant the kernel already had drivers. Nope! Again, thanks for that!

---

