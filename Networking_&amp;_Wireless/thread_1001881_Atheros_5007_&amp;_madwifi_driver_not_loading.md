---
title: "Atheros 5007 &amp; madwifi driver not loading"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by andy_t9566 on 2008-12-04
...I've Googled to nausea, but can't find an answer, so I'm hoping for some help.

I'm running Ubuntu v8.10 and I'm trying to get a Belkin F5D7010Hv8 (ath_5007 chip) card working.  'lspci' sees the card (see below).  However, 'iwconfig'  does not. (see below).  I have madwifi v.9.3.3, which I've tried to install, but I'm not exactly sure how to verify the install.  I checked /etc/modprobe.d/madwifi to see if 'ath5k' was blacklisted. It was, so I commented it out, and rebooted without success.  I've also tried to run 'rmmod ath_pci ath_hal', then 'insmod ath5k'. The insmod produces the error, 'ath5k': No such file or directory.  I've run 'find' for ath5k.ko, but it's not anywhere, so I'm suspecting that's the cause but not sure how to resolve. 'modprobe' shows "ath_hal.ko", "ath_pci.ko", and "ath9k.ko", but not "ath5k.ko" (see below).

WHAT AM I MISSING???????

I've verified the card is working using Windows-XP, so it's not a hw issue.

========================= lspci output ===================
#sudo lspci -vv
04:00.0 Ethernet controller: Atheros Communications Inc. AR5007G Wireless Network Adapter (rev 01)
	Subsystem: Belkin Device 721b
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at 8c000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath_pci

======================== iwconfig output ===================
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

============================== modprobe output =========================
#$ modprobe -l | grep ath
/lib/modules/2.6.27-9-generic/volatile/ath_hal.ko
/lib/modules/2.6.27-9-generic/volatile/ath_pci.ko
/lib/modules/2.6.27-9-generic/volatile/ath_rate_amrr.ko
/lib/modules/2.6.27-9-generic/volatile/ath_rate_minstrel.ko
/lib/modules/2.6.27-9-generic/volatile/ath_rate_onoe.ko
/lib/modules/2.6.27-9-generic/volatile/ath_rate_sample.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/md/dm-multipath.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/md/multipath.ko

---

### Post by andy_t9566 on 2008-12-04
..update

I went ahead and installed "linux-backports-modules-intrepid-generic", so I now have the "ath5k.ko" file in /lib/modules/2.6.27-9-generic/updates. 'modprobe' show it's loaded, but it still doesn't show up in 'lwconfig', nor are there any LED's.....  The other thing I don't understand, is why modprobe shows ath_hal & ath_pci, but if I try to unload them 'rmmod' reports them as not being in /proc/modules (see below)

$ modprobe -l | grep ath
/lib/modules/2.6.27-9-generic/volatile/ath_hal.ko
/lib/modules/2.6.27-9-generic/volatile/ath_pci.ko
/lib/modules/2.6.27-9-generic/volatile/ath_rate_amrr.ko
/lib/modules/2.6.27-9-generic/volatile/ath_rate_minstrel.ko
/lib/modules/2.6.27-9-generic/volatile/ath_rate_onoe.ko
/lib/modules/2.6.27-9-generic/volatile/ath_rate_sample.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/md/dm-multipath.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.27-9-generic/updates/ath9k.ko
/lib/modules/2.6.27-9-generic/updates/ath5k.ko

$ sudo rmmod ath_hal ath_pci
ERROR: Module ath_hal does not exist in /proc/modules
ERROR: Module ath_pci does not exist in /proc/modules

---

### Post by acreech on 2008-12-09
Go to this post and try it

[http://ubuntuforums.org/showthread.php?p=6201697#post6201697]("http://ubuntuforums.org/showthread.php?p=6201697#post6201697")

This is what works for me I have that same chip. I can use it in Hardy and Intrepid.

---

### Post by thewaytolite on 2009-01-06
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

