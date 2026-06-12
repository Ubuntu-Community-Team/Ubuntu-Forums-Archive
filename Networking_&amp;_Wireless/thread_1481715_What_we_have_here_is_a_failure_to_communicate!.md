---
title: "What we have here is a failure to communicate!"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by Nesaskewatch on 2010-05-12
Just another weary soul having trouble getting wireless on my laptop.  New Toshiba Satellite L500-00U, Dual Lucid/7 setup.  All Intel chipset and cpu.  Fresh 10.04 install today from a live dvd.  Here is the pertinent part of; 

```
lspci -knn
```

0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Kernel driver in use: r8169
	Kernel modules: r8169
14:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
	Kernel driver in use: rtl819xSE
	Kernel modules: r8192se_pci

Network manager applet is present.  I can "see" the network when I "connect to hidden wireless network", and the icon "ranges" like it normally does while connecting, but it never establishes the connection.  Eventually times out.  I see that there was(?) issues with the driver for my "card", and Realtek released a new Linux driver; r8101-1.016.00.tar.bz2 which the following link purports to address.  [CLICK ME]("http://en.alessiotreglia.com/articles/realteks-modules-new-version-has-been-released/#more-8/install")

My question is; Is that solution my best approach to this?  It seems as though the Lucid wireless driver is working, but something else is causing an issue here otherwise it wouldn't even detect the network.  ?

If the driver is indeed the trouble, are the instructions at that link good to follow?

Thanks for any ideas.

I just noticed that the wired connection is also at about 1/4 speed.  I guess maybe there is a problem with the driver.

---

### Post by chili555 on 2010-05-13
> Realtek released a new Linux driver; r8101-1.016.00.tar.bz2 which the following link purports to address. This is a driver for wired ethernet, not wireless. Let's see if the kernel has anything to report about your card and driver. Please post:```
dmesg | grep -e wlan -e 819
```Thanks.

---

### Post by Nesaskewatch on 2010-05-13
Here you go;

```
dmesg | grep -e wlan -e 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    9.567121] Adding 8193108k swap on /dev/sda7.  Priority:-1 extents:1 across:8193108k 
[    9.881593] Linux kernel driver for RTL8192 based WLAN cards
[    9.881699] rtl819xSE 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    9.881754] rtl819xSE 0000:14:00.0: setting latency timer to 64
[    9.899224] Adapter(8192SE) is found - DeviceID=8172
[   11.222939] rtl819xSE 0000:14:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   11.350897] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   11.361579] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.360068] ----------->rtl8192se_check_hw_scan()
[   18.361082] <-----------rtl8192se_check_hw_scan()
[   25.390043] ----------->rtl8192se_check_hw_scan()
[   25.391054] <-----------rtl8192se_check_hw_scan()
[   40.047730] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   47.050061] ----------->rtl8192se_check_hw_scan()
[   47.051074] <-----------rtl8192se_check_hw_scan()
[   70.049932] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   77.060076] ----------->rtl8192se_check_hw_scan()
[   77.061093] <-----------rtl8192se_check_hw_scan()

```

Boy.  You are a busy guy!  Your moniker is on a large number of the posts I have seen while searching for a clue.  Thanks very much for the help!

Cheers!

---

### Post by chili555 on 2010-05-13
It actually looks pretty normal. May we see:```
iwconfig
```> You are a busy guy! Your moniker is on a large number of the postsI like to keep the brain cells working. I learn a thing or two every day. When I get that great line, "It's working. Thanks," that's a wonderful payoff. I hope I'll get one here!

It's really kind of bad because I sometimes get called out right in the subject line of posts! There are plenty of other guys here who do excellent work.

---

### Post by Nesaskewatch on 2010-05-13
Sorry for the delay.  I got called away.  Here is the output of iwconfig;

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I will stand by this time.  Thanks very much!

Had to edit out the smilies!  lol

---

### Post by chili555 on 2010-05-13
> wlan0 802.11bgn Nickname:"rtl8191SEVA2"
Mode:Managed Frequency=2.457 GHz Access Point: Not-Associated
Bit Rate:300 Mb/s
Retry:on RTS thr:off Fragment thr:offStill looks healthy! If you have an ethernet cable attached, detach it, let the system notice a change of state and do:```
sudo ifconfig wlan0 up
iwlist wlan0 scan
```If you get no scan results, you might try:```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```If the flag is managed=false, change it to managed=true. Proofread, save and close gedit. After a reboot, can you click the Network Manager icon, see your network and connect?

---

### Post by Nesaskewatch on 2010-05-13
> **chili555 said:**
> see your network and connect?

A mighty try, but no go.  I *see* the network.  It is not listed at first, but after I select "connect to hidden network" it appears in the list as it scans.  If I select it, it flashes "wireless network disconnected", then scans until it times out.  That first code had no effect AFAIK.  It had managed=false in that line I changed in GEdit.  I just checked and it is managed=true now.

---

### Post by Nesaskewatch on 2010-05-13
Entering ```
sudo ifconfig wlan0 up
iwlist wlan0 scan
``` *now* shows; WLan0   No scan results

Cheers!

---

### Post by chili555 on 2010-05-13
Let's have a look at:```
lsmod | grep tosh
rfkill list
```Thanks.

---

### Post by Nesaskewatch on 2010-05-13
I tried those commands and got no result at all.  I tried both copying as is and separate lines.  Just returned to the command prompt.

---

### Post by Nesaskewatch on 2010-05-13
Well, I got it to work.  After trying just about everything I found by searching, I decided to set the router to broadcast the ssid et voila.  It spotted the network, then all I had to do was enter the passkey and the keyring password to connect.  Why won't it connect to a higher security hidden network anymore?  It did in Karmic.  Oh well...  Can't have everything I guess.


Thanks for your help Chili!

---

