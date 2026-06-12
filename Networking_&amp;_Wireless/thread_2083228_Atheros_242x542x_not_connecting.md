---
title: "Atheros 242x/542x not connecting"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by ChristopherAdams on 2012-11-11
Recently, I installed the Ubuntu mini.iso on my Acer Aspire One, and I can't get the wireless function to work. Here are the specifics:

1. Machine make & model: Acer Aspire One

2. Wireless Brand, Model and Wireless Chipset:

The command 'lspci | grep 'Wireless Brand' ' returns nothing. 

'lspci' returns: Ethernet Controller [0200:] Atheros Communications, Inc., AR242x / AR542x Wireless Network Adapter (PCI-Express)

3. Result of 'iwconfig wlan0':

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit: 7   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: on

4. The command 'lsmod | grep 'wlan_module_name'' returns nothing. The command 'lsmod' returned the following lines:

Module 		Size  	Used By
ath5k		145127	0
aht		        19387	ath5k

5. The command 'dmesg | grep 'wlan' returns nothing.

6. The command 'lshw -C network' returns:
*-network DISABLED
	Description: Wireless Interface
	Product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
	Vendor: Atheros Communications, Inc.

7. The command 'iwlist scan wlan0' returns:
wlan0 Interface doesn't support scanning : Network is down.

8. The command 'lsb_release -d' returns:
Description: Ubuntu 12.04.1 LTS

9. The command 'uname -mr' returns:
3.2.0-32-generic-pae i686

10. The command 'sudo /etc/init.d/networking restart' returns:
Running etc/init.d/networking restart is deprecated because it may not enable again some interfaces.
* Reconfiguring network interfaces ...

After that, the command 'iwlist scan wlan0' still returns:
wlan0 Interface doesn't support scanning : Network is down.

-----------------------------------------------------------------------------

From all this I gather that Ubuntu recognizes the Wireless card as an Ethernet card, and therefore can't make any connections, thinking that the connection is simply down.

Any help would be appreciated. Thanks!

Chris Adams.

---

### Post by chili555 on 2012-11-11
> From all this I gather that Ubuntu recognizes the Wireless card as an Ethernet card, and therefore can't make any connections, thinking that the connection is simply down.Interesting, but probably not the case. Let's see:```
rfkill list all
```

---

### Post by ChristopherAdams on 2012-11-12
When I run the command 'rfkill list all', I get:

```
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
```

---

### Post by chili555 on 2012-11-12
No hardware switch problem....we then wonder why:> *-network [COLOR="Red"]DISABLED[/COLOR]
Description: Wireless Interface
Product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
Vendor: Atheros Communications, Inc.
Please detach the ethernet cable and reboot so we have a clean slate and run and post:```
dmesg | grep ath
```You may then reconnect with ethernet to post the result.

---

### Post by ChristopherAdams on 2012-11-12
chili555 wrote:

> Please detach the ethernet cable and reboot so we have a clean slate and run and post:

```
dmesg | grep ath
```

OK, here is the result:

```
[    8.345273] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.345303] ath5k 0000:03:00.0: setting latency timer to 64
[    8.345458] ath5k 0000:03:00.0: registered as 'phy0'
[    8.849231] ath: EEPROM regdomain: 0x65
[    8.849239] ath: EEPROM indicates we should expect a direct regpair map
[    8.849248] ath: Country alpha2 being used: 00
[    8.849252] ath: Regpair used: 0x65
[    8.903635] Registered led device: ath5k-phy0::rx
[    8.903734] Registered led device: ath5k-phy0::tx
[    8.903771] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
```

---

### Post by chili555 on 2012-11-13
Very interesting. There is nothing obviously wrong we can see to fix. Let's have a look at a few things. First, are all the dependencies loaded:```
lsmod | grep -e ath -e 80211
```Second, is a wireless interface created:```
iwconfig
```Next, is Network Manager in exclusive control:```
cat /etc/network/interfaces
```Now, is there a problem with the PCI bus to whick the card is attached:```
lspci -nn | grep 0280
```Part of the data retuned is the bus number; for example, from my machine:> chili@LAPTOP410:~$ lspci -nn | grep 0280
[COLOR="Red"]03:00.0[/COLOR] Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
We'd like you to find out the bus number and check dmesg for problems:```
dmesg | grep 03:00  [COLOR="Red"]<--substitute your finding here[/COLOR]
```Last, we wonder if there is an error or warning in dmesg that prevents your PCI device from starting:```
dmesg | grep -i -e warn -e error
```

---

### Post by ChristopherAdams on 2012-11-14
OK, here are my latest results:

1. lsmod | grep -e ath -e 80211
-------------------------------
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211

2. iwconfig
-----------
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
3. cat /etc/network/interfaces
------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

4. lspci -nn | grep 0280
------------------------
Returns nothing; but 'lspci -nn' returns:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GSE Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)

5. dmesg | grep -i -e warn -e error
-----------------------------------
[    0.383968] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
[    0.383995] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c25ca8), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.384043] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.399350] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
[    0.399375] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c25ca8), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.399626] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
[    0.399648] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c25ca8), AE_ALREADY_EXISTS (20110623/psparse-536)
[    1.064226] i8042: Warning: Keylock active
[    7.364166] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

---

### Post by chili555 on 2012-11-14
Yikes!

I saw this: [https://bbs.archlinux.org/viewtopic.php?id=117372](https://bbs.archlinux.org/viewtopic.php?id=117372)> Okay, so the fallback image works fine, but I still don't know what's wrong with the normal one so I don't know what to fix!Can you reboot and select a different kernel version, for example 3.2.0-21 or -22 or similar and boot into it? Then run:```
dmesg | grep -i -e warn -e error
```Do the errors disappear and does the wireless work? If you have no earlier kernel, I suggest you reinstall the current one:```
sudo apt-get install --reinstall linux-image-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~.> my machine is running fine for 2 weeks now with pcie_aspm=off boot option.If the reinstalled kernel doesn't help, we'll try this next.

---

### Post by ChristopherAdams on 2012-11-18
OK, replacing the kernel seemed like a pretty drastic step, so I decided to experiment a little before going there (especially since chili555 said "There is nothing obviously wrong we can see to fix."). I downloaded the package 'wicd-gtk' and that program was able to initiate a connection to my router. 

I should have mentioned earlier that I did not have a traditional desktop, but only the Openbox window manager. I'm used to relying on things like desktop widgets to connect to wireless networks automatically, so it didn't occur to me until recently that maybe I was missing a step in trying to establish a wireless connection. 'wicd-gtk' provided that missing step.

chili555, thanks so much for your help. I hope I haven't wasted too much of your time.

Christopher Adams.

---

