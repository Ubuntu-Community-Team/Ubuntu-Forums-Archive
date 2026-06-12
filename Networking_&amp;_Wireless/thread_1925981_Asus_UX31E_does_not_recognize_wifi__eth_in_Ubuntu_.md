---
title: "Asus UX31E does not recognize wifi / eth in Ubuntu 11.10"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by narunas on 2012-02-15
Just got the laptop - set up dual boot with w7.
Wifi/eth is fine on the w7.
No joy at all in Ubuntu 11.00
" device is not ready " - in wifi connection display top right.

Kernel is 3.0.0-12-generic #20-Ubuntu  SMP.

It seems no one is having these issues.
Tried the next distro - not working

Went through several threads here about the issues with the ath9k driver - since I have no connection - could not even attempt to recompile a new kernel 

Need help
Narunas

---

### Post by chili555 on 2012-02-16
Let's see what wireless card you have. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboad on the same key with \.

You mention ath9k; let's see what is happening under the hood:```
dmesg | grep ath
```Thanks.

---

### Post by narunas on 2012-02-16
Thanks for responding - here is the output:



narunas@narunas-UX31E:~$ lspci -nn | grep 
0280
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)








narunas@narunas-UX31E:~$ dmesg | grep ath

[    2.482967] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17

[    2.482979] ath9k 0000:02:00.0: setting latency timer to 64

[    2.491266] ath: EEPROM regdomain: 0x60

[    2.491269] ath: EEPROM indicates we should expect a direct regpair map

[    2.491272] ath: Country alpha2 being used: 00

[    2.491274] ath: Regpair used: 0x60

[    2.518971] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'

[    2.520269] Registered led device: ath9k-phy0

---

### Post by chili555 on 2012-02-16
Looks very good so far! That card does, indeed, use ath9k. As we can tell by the timestamp, it is automatically loading early in the boot process. Is a wireless interface created?```
iwconfig
```What is Network Manager doing all this time?```
sudo cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by narunas on 2012-02-16
trying to cut and paste from a wifi-less side of us31x..... 



narunas@narunas-UX31E:~$ iwconfig


lo        no wireless extensions.



wlan0     
IEEE 802.11bgn  
ESSID:off/any  
          
Mode:Managed  
Access Point: Not-Associated 
Tx-Power=0 dBm   
         
Retry  long limit:7   
RTS thr:off   
Fragment thr:off
          
Power Management:off











narunas@narunas-UX31E:~$ sudo cat /var/log/syslog | grep etwork | tail -n20

[sudo] password for narunas: 

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> WiFi enabled by radio killswitch; enabled by state file

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> WWAN enabled by radio killswitch; enabled by state file

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> WiMAX enabled by radio killswitch; enabled by state file

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> Networking is enabled by state file

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <error> [1329321300.66204] [nm-device-wifi.c:3081] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 0)

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 2)

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> (wlan0): now managed

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> (wlan0): bringing up device.

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> (wlan0): deactivating device (reason 'managed') [2]

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> modem-manager is now available

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> wpa_supplicant started

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <error> [1329321300.75359] [nm-supplicant-interface.c:570] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <info> (wlan0): supplicant interface state: starting -> down

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <warn> Trying to remove a non-existant call id.

Feb 15 10:55:00 narunas-UX31E NetworkManager[761]: <warn> bluez error getting default adapter: No such adapter

---

### Post by chili555 on 2012-02-16
> <info> (wlan0): deactivating device (reason 'managed') [2]Let's have a look at:```
cat /etc/network/interfaces
cat /etc/NetworkManager/nm-system-settings.conf
```Thanks.

---

### Post by narunas on 2012-02-16
... here you go!

narunas@narunas-UX31E:~$ cat /etc/network/interfaces

auto lo 
iface 
lo inet loopback

narunas@narunas-UX31E:~$ cat /etc/NetworkManager/nm-system-settings.conf

cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory



thanks for your efforts,
Narunas

---

### Post by chili555 on 2012-02-16
Oops! Let's try this:```
cat /etc/NetworkManager/NetworkManager.conf 
```If that also comes up missing, let's see:```
ls /etc/NetworkManager/
```> auto lo
iface
lo inet loopbackAm I safe to assume this is actually formatted as:```
auto lo
iface lo inet loopback
```Thanks.

---

### Post by narunas on 2012-02-16
the current output:

narunas@narunas-UX31E:~$ ls /etc/NetworkManager
dispatcher.d  NetworkManager.conf  system-connections  VPN




narunas@narunas-UX31E:~$ cat /etc/NetworkManager/NetworkManager.conf

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


.......................
sorry about the formatting issues.... have to move around from the two sides - .txt files are not read correctly on windows

---

### Post by emramca on 2012-02-19
I had exactly the same problem with my new UX31E (the Japanese ry256s model) that I bought yesterday. I found a relatively clean solution, which at least fixed the issue of the disabled wifi adapter. The problem (whatever it is) is fixed in the kernel version 3.0.0-16. You just need to update the kernel offline. I followed the method described on this thread: [http://ubuntuforums.org/showthread.php?p=10856515#post10856515](http://ubuntuforums.org/showthread.php?p=10856515#post10856515)

You need another computer which has no network driver problems with ubuntu 11.10. I used the same USB stick with which I installed Ubuntu on the zenbook, to boot my old laptop. Then, during the live session, you can download the updates (although linuux-generic meta package is sufficient). There are other problems though (which I will start dealing with today), for instance, the ethernet dongle. For these, the following wiki page seems to be a good place to start:

[https://help.ubuntu.com/community/AsusZenbook](https://help.ubuntu.com/community/AsusZenbook)

---

### Post by narunas on 2012-02-19
Thanks everyone,
I suspected that the kernel itself would need to be hacked into a new 11.10 install  - the trick above worked - 
I am using Unity so the instructions to add the packages manually did not apply. Installed the latest kernel using 

dpkg -i <your latest and greatest kernel image>.deb

a bit tricky to find the one package that starts the upgrade.

Wifi now works!
will follow the thread here if there is a good solution for the ethernet adapter.

narunas

---

### Post by chili555 on 2012-02-20
> Wifi now works!
will follow the thread here if there is a good solution for the ethernet adapter.Excellent! Let's work on the ethernet. Please post:```
lspci -nn | grep 0200
```Thanks.

---

### Post by narunas on 2012-02-21
lspci -nn | grep 0200
..... no output

just lspci:

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation QS67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
03:00.0 USB Controller: Fresco Logic Device 1009 (rev 02)

if it helps!
BTW - just plugged in the ethernet adapter - connects immediately and switches seamlessly back to wifi once unplugged 
I say this issue is solved - thanks everyone for all the help.


Will tackle other "minor" issues listed in other threads - firs would be mutitouch support for mouse pad.

narunas

---

### Post by narunas on 2012-02-21
OK - the bluetooth does not discover my mouse - anyone got it to work on this laptop?
Again W7 side appears fine

narunas

---

