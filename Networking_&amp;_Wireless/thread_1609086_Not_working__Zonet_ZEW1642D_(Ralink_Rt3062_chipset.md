---
title: "Not working:  Zonet ZEW1642D (Ralink Rt3062 chipset) in Ubuntu Studio"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by jis4joe on 2010-10-29
long time reading... 1st time posting... very new to all of this... appreciate any help offered

I've read and tried many different suggestions on these and other forums to get my Zonet ZEW1642D to work on my new install of Ubuntu Studio 10.10.  None of the how-tos I've found APPEAR to have worked although I guess I'm not entirely sure how I would know.  There is a pair of computers at the top right of my screen by the date/time.  When I right click there the following are all checked:
Enable Networking
Enable Wireless
Enable Notifications
but when I click Connection Information Auto eth0 is the only connection that comes up (which must be the wired connection I'm using to submit this)

Here are the things I've tried:

1)  README_STA included in the driver files downloaded from the Ralink website although I must admit this was a bit over my head
2)  [http://ubuntuforums.org/showthread.php?t=1045703](http://ubuntuforums.org/showthread.php?t=1045703)
3)  [http://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/](http://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/)

Based on many other posts I've read it appears that someone wanting to help may want to see:

maestro@studio:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:00.0 Network controller: RaLink Device 3062

maestro@studio:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
maestro@studio:~$ lspci | grep  -i network
05:00.0 Network controller: RaLink Device 3062
maestro@studio:~$ 

Thanks for any help you may be able to offer.

---

### Post by jis4joe on 2010-10-30
Update:  I found another WLAN card that works and I'm just going to use that for now.  Unfortunately it is only b/g so I won't get n speeds.  I did confirm that the ZONET card works in a Windows 7 machine so that's good to know.
 
It appears that the card is using the wrong driver.  When I run lspci -knn it find that the module being used is the rt2800sta but that the rt3652sta is there.  I just don't know how to force the kernel to use the other driver.

---

### Post by MooPi on 2010-10-30
You may need to blacklist rt2800 so that rt3562 functions.
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Add these lines at the end of the file
```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2800lib
```
You may also need to edit /etc/module as well by adding rt3562sta.ko
```
gksu gedit /etc/modules
```
Add to the end of that file ```
rt3562sta.ko
```
If after you've blacklisted and it still doesn't work try my post on the Ralink 3060/3062/3562 driver install
[http://ubuntuforums.org/showthread.php?t=1608095]("http://ubuntuforums.org/showthread.php?t=1608095")

---

### Post by jis4joe on 2010-10-31
Thanks MooPi.  I won't have a chance to try your suggestion until next weekend but am looking forward to trying it.  Just as I was reaching exhaustion I read something somewhere and wondered if blacklist was going to be the ticket but wasnt' sure exactly how to implement it.  Your suggestions look like they may be the ticket.
 
I really appreciate your help.

---

### Post by jis4joe on 2010-11-02
That was it!  I blacklisted the three files you suggested.  Rebooted and immediately connected to my wireless network.

Thank you for your help MooPi.

Here is what I'm getting now:

maestro@studio:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"dlink"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:E7:C9:8D:2A   
          Bit Rate=130 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-52 dBm  Noise level:-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

maestro@studio:~$ lspci |grep -i network
05:00.0 Network controller: RaLink Device 3062
maestro@studio:~$ 

Interesting that it appears to have chosen the 2860 driver though:

maestro@studio:~$ lspci -knn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a000] (rev 02)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a001] (rev 02)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: i915
    Kernel modules: i915
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:d618]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
    Subsystem: Intel Corporation Device [8086:4f4d]
    Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel modules: i2c-i801
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:d615]
    Kernel driver in use: r8169
    Kernel modules: r8169
05:00.0 Network controller [0280]: RaLink Device [1814:3062]
    Subsystem: RaLink Device [1814:3062]
    Kernel driver in use: rt2860
    Kernel modules: rt3562sta, rt2800pci

---

### Post by jis4joe on 2010-11-24
I just installed some updates from the UPDATE MANAGER and now it appears to have reverted back to the original rt2800 driver.  Wireless is dead again (sending this from another computer in the house) Grrr.

My blacklist.conf file still has the same lines I added to make it work originally, but it seems to be ignoring these now and loading the original driver anyway.

Help... Please.

---

### Post by chili555 on 2010-11-24
Please change your blacklists to:```
blacklist rt2800pci
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2800lib
```Reboot and let us have your report.

---

### Post by jis4joe on 2010-11-24
Thanks for your quick support.  I made the suggested changes using

sudo gedit /etc/modprobe.d/blacklist.conf

I verified that the changes were saved.  I then rebooted.  Still no wireless connection.  Here is what I get:

maestro@studio:~$ lspci -knn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a000] (rev 02)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a001] (rev 02)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: i915
    Kernel modules: i915
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:d618]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
    Subsystem: Intel Corporation Device [8086:4f4d]
    Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:4f4d]
    Kernel modules: i2c-i801
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Intel Corporation DeskTop Board D510MO [8086:d615]
    Kernel driver in use: r8169
    Kernel modules: r8169
05:00.0 Network controller [0280]: RaLink Device [1814:3062]
    Subsystem: RaLink Device [1814:3062]
    Kernel modules: rt2800pci
maestro@studio:~$

---

### Post by jis4joe on 2010-11-24
OK.  I got it working again.  I noticed as I was posting my last that there was no "driver in use"... just a reference to the rt2800pci module.  So I re-did everything ie...

sudo su
make && make install
modprobe rt3562sta

Once I typed the last line it immediately connected.

lspci -knn

now ends with 

05:00.0 Network controller [0280]: RaLink Device [1814:3062]
    Subsystem: RaLink Device [1814:3062]
    Kernel driver in use: rt2860
    Kernel modules: rt3562sta, rt2800pci

So is it common to have to re-do these things after updates are applied?  I'll keep this in mind next time... and my notes handy.

Thanks Chili555 for getting me started down the path.

---

### Post by chili555 on 2010-11-25
> So is it common to have to re-do these things after updates are applied? If the update is a newer linux-image, or kernel, then you must build the module against the newer running kernel. The correct process is:```
[COLOR="Red"]make clean[/COLOR]
make 
sudo make install
sudo modprobe rt3562sta
```sudo su is effective as well.

---

### Post by slimgrey on 2011-04-17
> **jis4joe said:**
> I just installed some updates from the UPDATE MANAGER and now it appears to have reverted back to the original rt2800 driver.  Wireless is dead again (sending this from another computer in the house) Grrr.

My blacklist.conf file still has the same lines I added to make it work originally, but it seems to be ignoring these now and loading the original driver anyway.

Help... Please.
I'm having the exact same problem as jis4joe, but I can't solve it using his solution.  I just updated the system, and the WIFI driver support went down exactly like in jis4joe's situation.  

I'm showing these drivers  in use:

[B]05:00.0 Network controller [0280]: RaLink Device [1814:3062]
    Subsystem: RaLink Device [1814:3062]
    Kernel driver in use: rt2860
    Kernel modules: rt3562sta, rt2800pci     [/B]

When I go to *System > Administration > Additional Drivers *It lists the **rt3562sta** driver and says ' This driver is activated and currently in use'

The system is acting like there is no driver in use though.

---

### Post by chili555 on 2011-04-17
Did you amend /etc/modprobe.d/blacklist.conf as outlined in post #7 above?

---

### Post by someitalian123 on 2012-01-15
I made a dkms package for this driver you can get it [here.]("http://www.mediafire.com/file/4q70p4skokwv74e/rt3562-dkms_2.4.1.1_all.deb") This way you shouldn't need to worry about recompiling when upgrading your kernel. 


Edit: NVM, I had tested it on fresh install and had worked when I  upgraded to 3.0.0-14, but then when I upgraded to ubuntu 12.04 and it  upgraded the kernel to 3.2 it didn't work. So I'm doing something wrong  with dkms I just don't know what it is.

---

### Post by someitalian123 on 2012-01-20
> **someitalian123 said:**
> I made a dkms package for this driver you can get it [here.]("http://www.mediafire.com/file/4q70p4skokwv74e/rt3562-dkms_2.4.1.1_all.deb") This way you shouldn't need to worry about recompiling when upgrading your kernel. 


Edit: NVM, I had tested it on fresh install and had worked when I  upgraded to 3.0.0-14, but then when I upgraded to ubuntu 12.04 and it  upgraded the kernel to 3.2 it didn't work. So I'm doing something wrong  with dkms I just don't know what it is.

O.K after a lot of googleing for answers and posting on forms I was able to fix the problem. Install this package then reboot, and you won't need to blacklist anything or recompile and reinstall every time you upgrade your kernel. It will automate the process.

[ATTACH]211271[/ATTACH]

Of course you'll need to have dkms installed to install this package, you can get dkms bellow, or if your able to connect to the internet without this driver you could use apt-get

[http://packages.ubuntu.com/oneiric/dkms](http://packages.ubuntu.com/oneiric/dkms)

Trying to setup a ppa but I'm having this issue 

```
Checking signature on .changes
gpg: WARNING: unsafe ownership on configuration file `/home/antoniu/.gnupg/gpg.conf'
gpg: no valid OpenPGP data found.
gpg: the signature could not be verified.
Please remember that the signature file (.sig or .asc)
should be the first file given on the command line.
No signature on /var/lib/dkms/rt3562/2.4.1.1/dsc/rt3562-dkms_2.4.1.1_source.changes.

```

---

### Post by someitalian123 on 2012-01-21
For some reason when packaging the driver the file permissions were changed on the script that blacklists the other 4 modules, this has been fixed. Also I started a ppa for this driver

[https://launchpad.net/~someitalian123/+archive/rt3562sta]("https://launchpad.net/%7Esomeitalian123/+archive/rt3562sta")

[ATTACH]211271[/ATTACH]

---

### Post by lewinb on 2012-04-17
I've been struggling with this for at least 7 hours, and am ready to put my head through the wall!

I had to reinstall my wireless drivers after allowing update manager to run. After hours of work, I FINALLY got the proper modules to load again:

```
02:01.0 Network controller [0280]: Ralink corp. Device [1814:3062]
	Subsystem: Ralink corp. Device [1814:3062]
	Kernel driver in use: rt2860
	Kernel modules: rt3562sta, rt2800pci

~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
~$


```

But there are still no wireless networks detected, and underneath the network menu-bar icon I have a greyed-out "device not ready" message, even though there is a checkmark by "wireless enabled". Do I need to specify to use ra0 instead of wlan0?

I also simultaneously get the message that the interface is *disabled*, 

```
~$ sudo lshw -c network
  *-network DISABLED      
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: ra0
       version: 00
       serial: c8:3a:35:c9:57:9e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.1.1 latency=66 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
       resources: irq:24 memory:fa400000-fa40ffff   
```


but trying to enable it gets me this:

```
~$ sudo ifconfig ra0 up
SIOCSIFFLAGS: Operation not permitted
```

On the other hand, if I try it this way:

```
~$ sudo ifup ra0
Ignoring unknown interface ra0=ra0,
```


ethernet works without any problems, but check this out. when I tried to disable ethernet:

```
~$ sudo ifdown eth0
[sudo] password for lewinb: 
Ignoring unknown interface eth0=eth0.
```

WTF?

I don't know what to do next at this point. I don't even know if I'm working in the right direction,
Help would be GREATLY appreciated!!

---

### Post by chili555 on 2012-04-17
> 02:01.0 Network controller [0280]: Ralink corp. Device [1814:3062]
	Subsystem: Ralink corp. Device [1814:3062]
	Kernel driver in use: rt2860
	Kernel modules: rt3562sta, rt2800pci
Let's make sure, first of all, that rt2800pci is not loaded. Please run:```
lsmod | grep rt2
```If it is loaded, remove and blacklist it:```
sudo su
modprobe -r rt2800pci
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```When you compiled the driver, did you make changes to os/linux/config.mk?> Where it says:
[QUOTE]# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Manager
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
Make sure that both lines have a "y" after them (by default they have an "n"), then save the file.
[/QUOTE]If not, please do so and recompile:```
cd Desktop/rt3562STAfile  <---or wherever you extracted the files
sudo su
make clean
make
make install
modprobe -r rt3562sta
modprobe rt3562sta
exit
```Post back if we need to dig deeper.

---

### Post by lewinb on 2012-04-17
H, thanks for the quick reply!

I went back and re-verified that each one of those was set properly, and the the rt2800 module is not loaded.

The last time I did this, I remember there being one last step to get the card to "turn on" but I can't remember what it is. I recall that I could tell immediately that it was "turned on" because the LEDs on the card lit as soon as I did it.

What should I try next?

---

### Post by chili555 on 2012-04-17
This is pretty mysterious to me:> ~$ sudo lshw -c network
  *-network [COLOR="Red"]DISABLED[/COLOR]      
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.May I see:```
rfkill list all
dmesg | grep 02:01
```What type of computer is this?

---

### Post by lewinb on 2012-04-17
Here's what I got:


```
~$ rfkill list all
lewinb@Xeon:~$ dmesg | grep 02:01
[    1.052587] pci 0000:02:01.0: [1814:3062] type 0 class 0x000280
[    1.052608] pci 0000:02:01.0: reg 10: [mem 0xfa400000-0xfa40ffff]
[   24.152885] rt2860 0000:02:01.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[   24.152952] 0000:02:01.0: at 0xfa400000, VA 0xffffc90010b40000, IRQ 24. ~$ 

```

This is a HP Workstation xw8200 with 2 dual core Xeon processors (socket 604, I *think*)

As I said, I have had this working before on this machine. And last time, it was a pretty straightforward process, once I stopped trying to install the 2860 drivers (since the card is 3060 chipset). It's just the last step, that is eluding me.

---

### Post by chili555 on 2012-04-17
This will be a bit long, but let me see:```
modinfo rt3562sta | grep 3062
lsmod
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by lewinb on 2012-04-17
```

~$ modinfo rt3562sta | grep 3062
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
$

```
```

~$ lsmod
Module                  Size  Used by
rt3562sta             986681  0 
nls_utf8               12557  1 
isofs                  40283  1 
binfmt_misc            17565  1 
nvidia              10709116  50 
snd_intel8x0           38272  2 
snd_ac97_codec        134270  1 snd_intel8x0
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96391  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  17113  0 
snd                    67382  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17606  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_intel8x0,snd_pcm
psmouse                73535  0 
serio_raw              13166  0 
e752x_edac             18139  0 
edac_core              53845  1 e752x_edac
parport_pc             36959  1 
shpchp                 37297  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
mptspi                 22738  0 
e1000                 111862  0 
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
mptscsih               44457  1 mptspi
crc_itu_t              12707  1 firewire_core
floppy                 74120  0 
mptbase               102904  2 mptspi,mptscsih
scsi_transport_spi     30630  1 mptspi
$

```

```

~$ dmesg | grep -e rt2 -e rt3
[   16.394648] rt3562sta: module license 'unspecified' taints kernel.
[   24.152848] ===> rt2860_probe
[   24.152885] rt2860 0000:02:01.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[   24.154841] @rt2860_probe MAC address: c8:3a:35:c9:57:9e
[   24.154845] <=== rt2860_probe
[   24.187787] !!! rt28xx Initialized fail !!!
[   24.187799] rt28xx_open return fail!
[   24.202564] !!! rt28xx Initialized fail !!!
[   24.202576] rt28xx_open return fail!
[  281.081823] rt28xx_get_wireless_stats --->
[  281.081829] <--- rt28xx_get_wireless_stats
[  701.997402] !!! rt28xx Initialized fail !!!
[  701.997417] rt28xx_open return fail!
[  702.014439] !!! rt28xx Initialized fail !!!
[  702.014454] rt28xx_open return fail!
[ 1308.709179] !!! rt28xx Initialized fail !!!
[ 1308.709194] rt28xx_open return fail!
[ 1881.090203] !!! rt28xx Initialized fail !!!
[ 1881.090218] rt28xx_open return fail!
[ 2066.368883] !!! rt28xx Initialized fail !!!
[ 2066.368897] rt28xx_open return fail!
[ 2640.724904] rt28xx_get_wireless_stats --->
[ 2640.724908] <--- rt28xx_get_wireless_stats
[ 2979.705905] rt28xx_get_wireless_stats --->
[ 2979.705908] <--- rt28xx_get_wireless_stats
[ 2979.732754] rt28xx_get_wireless_stats --->
[ 2979.732758] <--- rt28xx_get_wireless_stats
[ 2979.753592] rt28xx_get_wireless_stats --->
[ 2979.753597] <--- rt28xx_get_wireless_stats
[ 2979.770722] rt28xx_get_wireless_stats --->
[ 2979.770727] <--- rt28xx_get_wireless_stats
[ 3166.638096] rt28xx_get_wireless_stats --->
[ 3166.638105] <--- rt28xx_get_wireless_stats
[ 3166.670768] rt28xx_get_wireless_stats --->
[ 3166.670775] <--- rt28xx_get_wireless_stats
[ 3166.699279] rt28xx_get_wireless_stats --->
[ 3166.699284] <--- rt28xx_get_wireless_stats
[ 3166.722550] rt28xx_get_wireless_stats --->
[ 3166.722555] <--- rt28xx_get_wireless_stats
[ 3287.143615] rt28xx_get_wireless_stats --->
[ 3287.143620] <--- rt28xx_get_wireless_stats
[ 4187.735107] !!! rt28xx Initialized fail !!!
[ 4187.735123] rt28xx_open return fail!
[81439.463586] rt28xx_get_wireless_stats --->
[81439.463590] <--- rt28xx_get_wireless_stats
[81439.482451] rt28xx_get_wireless_stats --->
[81439.482456] <--- rt28xx_get_wireless_stats
[81439.499449] rt28xx_get_wireless_stats --->
[81439.499454] <--- rt28xx_get_wireless_stats
[81439.516538] rt28xx_get_wireless_stats --->
[81439.516541] <--- rt28xx_get_wireless_stats
[82969.903486] rt28xx_get_wireless_stats --->
[82969.903490] <--- rt28xx_get_wireless_stats
[84394.211931] ===> rt2860_suspend()
[84394.211978] rt2860 0000:02:01.0: PCI INT A disabled
[84394.230212] <=== rt2860_suspend()
[84395.952871] rt2860 0000:02:01.0: restoring config space at offset 0xf (was 0x4020100, writing 0x4020103)
[84395.952890] rt2860 0000:02:01.0: restoring config space at offset 0x4 (was 0xffff0000, writing 0xfa400000)
[84395.952896] rt2860 0000:02:01.0: restoring config space at offset 0x3 (was 0x0, writing 0x4210)
[84395.952903] rt2860 0000:02:01.0: restoring config space at offset 0x1 (was 0x4100000, writing 0x4100107)
[84395.958566] rt2860 0000:02:01.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[84395.958571] ===> rt2860_resume()
[84395.958574] <=== rt2860_resume()
[84422.293769] Modules linked in: nls_utf8 isofs binfmt_misc nvidia(P) snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device ppdev snd joydev soundcore snd_page_alloc psmouse serio_raw e752x_edac edac_core parport_pc shpchp rt3562sta(P) lp parport usbhid hid mptspi e1000 firewire_ohci firewire_core mptscsih crc_itu_t floppy mptbase scsi_transport_spi
[84422.827594] !!! rt28xx Initialized fail !!!
[84422.827609] rt28xx_open return fail!
[84422.846921] !!! rt28xx Initialized fail !!!
[84422.846938] rt28xx_open return fail!
[84585.580219] ===> rt2860_remove_one
[84593.088475] ===> rt2860_probe
[84593.099250] @rt2860_probe MAC address: c8:3a:35:c9:57:9e
[84593.099255] <=== rt2860_probe
[84593.196081] !!! rt28xx Initialized fail !!!
[84593.196096] rt28xx_open return fail!
[84593.215375] !!! rt28xx Initialized fail !!!
[84593.215392] rt28xx_open return fail!
[84628.865965] !!! rt28xx Initialized fail !!!
[84628.865980] rt28xx_open return fail!
[84628.887595] !!! rt28xx Initialized fail !!!
[84628.887611] rt28xx_open return fail!
~$
```

So, why does it appear that the kernal is still fooling around with 2860?

---

### Post by chili555 on 2012-04-18
rt2860 is the basis for this driver. It's referred to all over the package you compiled. I see nothing unusual there.

May I see:```
cat /etc/Wireless/RT2860STA/RT2860STA.dat
```Thanks.

---

### Post by lewinb on 2012-04-18
Here you go:

```
~$ cat /etc/Wireless/RT2860STA/RT2860STA.dat
cat: /etc/Wireless/RT2860STA/RT2860STA.dat: No such file or directory
~$
```

So even though all the instructions say to disable rt28xxsta, the 3062 drivers still rely on them somehow?

---

### Post by chili555 on 2012-04-18
> So even though all the instructions say to disable rt28xxsta, the 3062 drivers still rely on them somehow?Nope. As I said, Ralink used the driver for rt2860sta to write rt3562sta. There are still a lot of references to it in the source code for rt3562sta. Here is a tidbit from os/linux/Makefile.6:> cp $(RT28xx_DIR)/$(DAT_FILE_NAME) $(DAT_PATH)/.That means we are going to copy the DAT file on to your system at /etc/Wireless/. Here is what the file is named:> $ ls
chips   include           Makefile  README_STA_pci     [COLOR="Red"]**RT2860STA.dat**[/COLOR]  sta_ate_iwpriv_usage.txt
common  iwpriv_usage.txt  os        RT2860STACard.dat  sta            tools
So the file didn't get copied over for some reason. Let's do so and see if things improve. Please open a terminal and do:```
cd Desktop/RT3562file  <---or wherever you extracted the files
sudo su
mkdir /etc/Wireless/RT2860STA
cp RT2860STA.dat /etc/Wireless/RT2860STA
exit
```Now check:```
cat /etc/Wireless/RT2860STA/RT2860STA.dat
```You should get a nice long file like this redacted example:> #The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=Dennis2860AP
NetworkType=Infra
<snip>Reboot and let me have your report.

---

### Post by lewinb on 2012-04-18
VICTORY! It connected immediately. It topped out at slightly over 4 MB/sec over the course of a 700 MB file transfer. I consider that pretty good for wireless (at least, it's not any slower than it was prior to system update). 

Interesting: there was nothing in /etc/wirelesss/ before I entered your commands. 

It's almost worth it to make uninstall, just to see if it happens again.Almost.

You rock! Thanks so much for the help! I hope I'll be able to do the same for someone else at some point.

TO OTHERS READING THIS: CHECK THE CHIPSET OF YOUR CARD!... 

That's what cost me hours of time, **before** I even posted here. I just followed guides, assuming that my card used the drivers for the 2860 chipset. That's what all the guides listed, so I just went with what they said without checking.

---

### Post by someitalian123 on 2012-05-01
> **chili555 said:**
> Nope. As I said, Ralink used the driver for rt2860sta to write rt3562sta. There are still a lot of references to it in the source code for rt3562sta. Here is a tidbit from os/linux/Makefile.6:That means we are going to copy the DAT file on to your system at /etc/Wireless/. Here is what the file is named:So the file didn't get copied over for some reason. Let's do so and see if things improve. Please open a terminal and do:```
cd Desktop/RT3562file  <---or wherever you extracted the files
sudo su
mkdir /etc/Wireless/RT2860STA
cp RT2860STA.dat /etc/Wireless/RT2860STA
exit
```Now check:```
cat /etc/Wireless/RT2860STA/RT2860STA.dat
```You should get a nice long file like this redacted example:Reboot and let me have your report.

Thank you, I updated the package in the ppa to fix this problem on precise.

[https://launchpad.net/~someitalian123/+archive/rt3562sta]("https://launchpad.net/~someitalian123/+archive/rt3562sta")

---

### Post by someitalian123 on 2012-12-07
Ironically, it appears now that the offical driver is causing kernel panics in 64bit while the reverse engineered rt2800pci driver is working, slowly, but stably.

---

### Post by pullmoll on 2012-12-09
> **someitalian123 said:**
> Ironically, it appears now that the offical driver is causing kernel panics in 64bit while the reverse engineered rt2800pci driver is working, slowly, but stably.

The reason is most probably a buggy implementation of some OS abstraction macros in include/os/rt_linux.h for 64 bit Linux.
 I posted a description of how I fixed my issues with the driver: [http://ubuntuforums.org/showthread.php?t=2092888](http://ubuntuforums.org/showthread.php?t=2092888) 
Jürgen

---

