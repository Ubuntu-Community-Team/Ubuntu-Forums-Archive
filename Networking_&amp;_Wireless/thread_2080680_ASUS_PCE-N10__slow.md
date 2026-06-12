---
title: "ASUS PCE-N10  slow"
date: 2012-11-04
forum: Networking &amp; Wireless
---

### Post by mike acker on 2012-11-04
my  ASUS PCE-N10   running WPA2-PSK is slow..... I'm getting 10Mb/sec where both of my Win7 computers are getting 40 Mb/sec  ( the connection is supposed to be 30 Mb/sec but it does a bit better that the SLA ) .

I hunted around for solutions but didn't find anything--

any know solution to this ( I hope )

---

### Post by mike acker on 2012-11-05
this morning I installed the RJ45 setup cable to my CICSO wireless router

this gives 100 Mb/sec

the network test is now showing 35 Mb/sec -- same rate as for Windows (wireless) systems

something is wrong in the Ubuntu driver for the wireless cards: there seem to be a lot of hits on this topic on the net.

it isn't the AppArmor I applied to my Firefox: that is still in effect.

amendment
this may be my error ( not again )
here's the system info on the card:
```

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 8505
    Flags: bus master, fast devsel, latency 0, IRQ 48
    I/O ports at e800 [size=256]
    Memory at fdfff000 (64-bit, prefetchable) [size=4K]
    Memory at fdff8000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: r8169
    Kernel modules: r8169


```yep it's a PCI/Express card, and that's not on the supported list

if this is a know problem i'll look into getting a different card

i have this one on order:
[EDIMAX EW-7128Gn PCI Wireless Adapter for PC and Mac]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833315096")

I think this one will be ok.  It does the WPA2 security that i use, 802.11b|g\n  ( i use 802.11n and WPA2-PSK)
and the details sheet lists Linux

---

### Post by chili555 on 2012-11-05
You may wish to try the r8168 driver here: [http://ubuntuforums.org/showthread.php?t=1958899](http://ubuntuforums.org/showthread.php?t=1958899) 

I suggest the process at post #4 and following.

---

### Post by mike acker on 2012-11-05
> **chili555 said:**
> You may wish to try the r8168 driver here: [http://ubuntuforums.org/showthread.php?t=1958899](http://ubuntuforums.org/showthread.php?t=1958899) 

I suggest the process at post #4 and following.

thanks; I'll make a note here but it will be easier to change the wireless card.

---

### Post by chili555 on 2012-11-05
> it will be easier to change the wireless card.Really? You and I could install r8168 in about ten minutes, if you wish.

---

### Post by mike acker on 2012-11-05
> **chili555 said:**
> Really? You and I could install r8168 in about ten minutes, if you wish.

I'm willing to try it but I'm reluctant because I don't understand all those sudo commands

is this a known problem in 12.04 LTS ? not supporting 802.11 in PCI Express  slots ?

if I was a betting man I'd wager Ubuntu is using a generic driver because it doesn't recognize the ASUS PCE-N10 which it then sets to the old 10Mb/sec standard rate

is this software from the official library ?

I note most of the 802.11 cards being sold by NewEgg are PCI Express. it seems a shame to waste the PCI slot on the WiFi card   (M5A88-M has 1 PCI slot, 2 express )

I was wanting to stick with the ASUS product line

---

### Post by chili555 on 2012-11-05
> I'm willing to try it but I'm reluctant because I don't understand all those sudo commandsThe partial purpose of the forum is to ask someone that does. I'm pretty sure I do.> is this a known problem in 12.04 LTS ? not supporting 802.11 in PCI Express slots ?Not at all. What *IS* a known problem is that some card and driver combinations do N very well, some not at all. As far as I know, there is no such thing as a 'generic' wireless driver. They are all quite specific. Some are well done and some not.> 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 8505
    <snip>
    Kernel driver in use: r8169
    Kernel modules: r8169You got me! Ouch. You asked about wireless and then asserted these are the details. Here I come, answering posts, eating lunch, and watching financial news and I believed you! This is not a wireless device, it's a wired ethernet. Let's see what you *really* have:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by mike acker on 2012-11-05
yuk! sorry! it says PCI Express and references ASUS -- which is did put an ASUS wifi card in the top PCI Express slot

> **chili555 said:**
> This is not a wireless device, it's a wired ethernet. Let's see what you *really* have:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

ok, here's what it came out with:

```

:~$ lspci -nm | grep 0280
02:00.0 "0280" "10ec" "8176" -r01 "1043" "84b5"
:~$ 


```what are we grepping for ?  the motherboard is ASUS M5A88-M

---

### Post by chili555 on 2012-11-05
It was actually lspci -n[COLOR="Red"]n[/COLOR] | grep 0280. However, we got the pci.id of 10ec:8176. It uses the tricky rtl8192ce. You can check:```
lsmod | grep rtl
```We can also look at what's going on under the hood:```
dmesg | grep -e wlan -e rtl
```Thanks.

---

### Post by mike acker on 2012-11-05
> **chili555 said:**
> It was actually lspci -n[COLOR=Red]n[/COLOR] | grep 0280. However, we got the pci.id of 10ec:8176. It uses the tricky rtl8192ce. You can check:```
lsmod | grep rtl
```We can also look at what's going on under the hood:```
dmesg | grep -e wlan -e rtl
```Thanks.

ok, here's what it said:  sorry about the nm nn error :-(

```

:~$ lspci -nn |grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
:~$ lsmod |grep rtl
rtl8192ce              84826  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce
mac80211              506816  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              205544  2 rtlwifi,mac80211
:~$ dmesg | grep -e wlan -e rtl
:~$ 

```

---

### Post by chili555 on 2012-11-05
> :~$ dmesg | grep -e wlan -e rtl
:~$Interesting. Please try:```
sudo cat /var/log/syslog | grep -e wlan -e rtl
```

---

### Post by mike acker on 2012-11-05
> **chili555 said:**
> Interesting. Please try:```
sudo cat /var/log/syslog | grep -e wlan -e rtl
```

ok:
```

T4:~$ sudo cat /var/log/syslog | grep -e wlan e rtl
grep: e: No such file or directory
grep: rtl: No such file or directory
[sudo] password for bill: 
T4:~$ cd /var
T4:/var$ cd log
T4:/var/log$ cd syslog
bash: cd: syslog: Not a directory
T4:/var/log$ ls
alternatives.log    dist-upgrade     lastlog             syslog.3.gz
alternatives.log.1  dmesg            lightdm             syslog.4.gz
apparmor            dmesg.0          mail.err            syslog.5.gz
apport.log          dmesg.1.gz       mail.log            syslog.6.gz
apport.log.1        dmesg.2.gz       mysql               syslog.7.gz
apport.log.2.gz     dmesg.3.gz       mysql.err           udev
apport.log.3.gz     dmesg.4.gz       mysql.log           ufw.log
apport.log.4.gz     dpkg.log         mysql.log.1.gz      ufw.log.1
apport.log.5.gz     dpkg.log.1       mysql.log.2.gz      ufw.log.2.gz
apport.log.6.gz     faillog          mysql.log.3.gz      ufw.log.3.gz
apport.log.7.gz     fontconfig.log   mysql.log.4.gz      unattended-upgrades
apt                 fsck             mysql.log.5.gz      upstart
auth.log            hp               mysql.log.6.gz      wtmp
auth.log.1          installer        mysql.log.7.gz      wtmp.1
auth.log.2.gz       jockey.log       news                Xorg.0.log
auth.log.3.gz       jockey.log.1     pm-powersave.log    Xorg.0.log.old
auth.log.4.gz       jockey.log.2.gz  pm-powersave.log.1  Xorg.1.log
boot                jockey.log.3.gz  pm-suspend.log      Xorg.1.log.old
boot.log            jockey.log.4.gz  pm-suspend.log.1    Xorg.2.log
bootstrap.log       kern.log         samba               Xorg.2.log.old
btmp                kern.log.1       speech-dispatcher   Xorg.3.log
btmp.1              kern.log.2.gz    syslog              Xorg.3.log.old
ConsoleKit          kern.log.3.gz    syslog.1            Xorg.4.log
cups                kern.log.4.gz    syslog.2.gz         Xorg.4.log.old
T4:/var/log$ cd /etc/apparmor.d

```remember: this system is on RJ45 setup right now; wireless is off, out of service, not in use

it lets me tail syslog ...
```

T4:/var/log$ sudo cat syslog |grep -e wlan e rtl
grep: e: No such file or directory
grep: rtl: No such file or directory
T4:/var/log$ 

```


**** break **** back around 1900 EST

---

### Post by chili555 on 2012-11-05
> T4:~$ sudo cat /var/log/syslog | grep -e wlan e rtl
grep: e: No such file or directoryIt is actually:```
T4:~$ sudo cat /var/log/syslog | grep -e wlan [COLOR="Red"]**-**[/COLOR]e rtl
```Neatness and punctuation counts.

---

### Post by mike acker on 2012-11-06
> **chili555 said:**
> It is actually:```
T4:~$ sudo cat /var/log/syslog | grep -e wlan [COLOR=Red]**-**[/COLOR]e rtl
```Neatness and punctuation counts.

i always have a bad time with command line, i'll try to do better
```

ackerwaa@acker4:~$ sudo cat /var/log/syslog | grep -e wlan -e rtl
[sudo] password for ackerwaa: 
Nov  6 06:03:10 acker4 NetworkManager[1028]: <info> (wlan0): bringing up device.
Nov  6 06:03:10 acker4 kernel: [ 1256.619670] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
Nov  6 06:03:10 acker4 kernel: [ 1256.959650] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  6 06:03:10 acker4 NetworkManager[1028]: <info> (wlan0): supplicant interface state: starting -> ready
Nov  6 06:03:10 acker4 NetworkManager[1028]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Nov  6 06:03:10 acker4 NetworkManager[1028]: <info> (wlan0): supplicant interface state: ready -> inactive
Nov  6 06:03:12 acker4 NetworkManager[1028]: <info> Activation (wlan0) starting connection 'ackerNET'
Nov  6 06:03:12 acker4 NetworkManager[1028]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov  6 06:03:12 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  6 06:03:12 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  6 06:03:12 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  6 06:03:12 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  6 06:03:12 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  6 06:03:12 acker4 NetworkManager[1028]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  6 06:03:12 acker4 NetworkManager[1028]: <info> (wlan0): preparing device.
Nov  6 06:03:12 acker4 NetworkManager[1028]: <info> Activation (wlan0/wireless): connection 'ackerNET' has security, and secrets exist.  No new secrets needed.
Nov  6 06:03:12 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  6 06:03:12 acker4 NetworkManager[1028]: <info> (wlan0): supplicant interface state: inactive -> scanning
Nov  6 06:03:13 acker4 NetworkManager[1028]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov  6 06:03:13 acker4 kernel: [ 1259.666289] wlan0: authenticate with 20:aa:4b:11:85:f3 (try 1)
Nov  6 06:03:13 acker4 kernel: [ 1259.667839] wlan0: authenticated
Nov  6 06:03:13 acker4 kernel: [ 1259.668153] wlan0: associate with 20:aa:4b:11:85:f3 (try 1)
Nov  6 06:03:13 acker4 kernel: [ 1259.671361] wlan0: RX AssocResp from 20:aa:4b:11:85:f3 (capab=0x411 status=0 aid=2)
Nov  6 06:03:13 acker4 kernel: [ 1259.671370] wlan0: associated
Nov  6 06:03:13 acker4 NetworkManager[1028]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov  6 06:03:13 acker4 kernel: [ 1259.686772] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov  6 06:03:13 acker4 NetworkManager[1028]: <info> (wlan0): supplicant interface state: associating -> associated
Nov  6 06:03:13 acker4 NetworkManager[1028]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Nov  6 06:03:13 acker4 NetworkManager[1028]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Nov  6 06:03:13 acker4 NetworkManager[1028]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ackerNET'.
Nov  6 06:03:13 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  6 06:03:13 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov  6 06:03:13 acker4 NetworkManager[1028]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov  6 06:03:13 acker4 NetworkManager[1028]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov  6 06:03:13 acker4 NetworkManager[1028]: <info> Activation (wlan0) Beginning IP6 addrconf.
Nov  6 06:03:13 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov  6 06:03:13 acker4 NetworkManager[1028]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov  6 06:03:13 acker4 dhclient: Listening on LPF/wlan0/10:bf:48:fb:aa:5b
Nov  6 06:03:13 acker4 dhclient: Sending on   LPF/wlan0/10:bf:48:fb:aa:5b
Nov  6 06:03:13 acker4 dhclient: DHCPREQUEST of 192.168.1.117 on wlan0 to 255.255.255.255 port 67
Nov  6 06:03:15 acker4 avahi-daemon[1062]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::12bf:48ff:fefb:aa5b.
Nov  6 06:03:15 acker4 avahi-daemon[1062]: New relevant interface wlan0.IPv6 for mDNS.
Nov  6 06:03:15 acker4 avahi-daemon[1062]: Registering new address record for fe80::12bf:48ff:fefb:aa5b on wlan0.*.
Nov  6 06:03:16 acker4 avahi-daemon[1062]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::12bf:48ff:fefb:aa5b.
Nov  6 06:03:16 acker4 avahi-daemon[1062]: Joining mDNS multicast group on interface wlan0.IPv6 with address fd96:6e68:888b:0:9555:a438:b322:f878.
Nov  6 06:03:16 acker4 avahi-daemon[1062]: Registering new address record for fd96:6e68:888b:0:9555:a438:b322:f878 on wlan0.*.
Nov  6 06:03:16 acker4 avahi-daemon[1062]: Withdrawing address record for fe80::12bf:48ff:fefb:aa5b on wlan0.
Nov  6 06:03:16 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) starting DHCPv6 as requested by IPv6 router...
Nov  6 06:03:16 acker4 NetworkManager[1028]: <info> Activation (wlan0) Beginning DHCPv6 transaction (timeout in 45 seconds)
Nov  6 06:03:16 acker4 dhclient: Listening on Socket/wlan0
Nov  6 06:03:16 acker4 dhclient: Sending on   Socket/wlan0
Nov  6 06:03:16 acker4 dhclient: DHCPREQUEST of 192.168.1.117 on wlan0 to 255.255.255.255 port 67
Nov  6 06:03:16 acker4 NetworkManager[1028]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Nov  6 06:03:16 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov  6 06:03:16 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Nov  6 06:03:16 acker4 avahi-daemon[1062]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.117.
Nov  6 06:03:16 acker4 avahi-daemon[1062]: New relevant interface wlan0.IPv4 for mDNS.
Nov  6 06:03:16 acker4 avahi-daemon[1062]: Registering new address record for 192.168.1.117 on wlan0.IPv4.
Nov  6 06:03:16 acker4 avahi-daemon[1062]: Registering new address record for fd96:6e68:888b:0:12bf:48ff:fefb:aa5b on wlan0.*.
Nov  6 06:03:16 acker4 dhclient: XMT: Info-Request on wlan0, interval 930ms.
Nov  6 06:03:17 acker4 NetworkManager[1028]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov  6 06:03:17 acker4 NetworkManager[1028]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov  6 06:03:17 acker4 NetworkManager[1028]: <info> Policy set 'ackerNET' (wlan0) as default for IPv4 routing and DNS.
Nov  6 06:03:17 acker4 NetworkManager[1028]: <info> Activation (wlan0) successful, device activated.
Nov  6 06:03:17 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov  6 06:03:17 acker4 dhclient: XMT: Info-Request on wlan0, interval 1800ms.
Nov  6 06:03:18 acker4 NetworkManager[1028]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov  6 06:03:18 acker4 NetworkManager[1028]: <info> Policy set 'ackerNET' (wlan0) as default for IPv4 routing and DNS.
Nov  6 06:03:18 acker4 NetworkManager[1028]: <error> [1352199798.361271] [nm-system.c:1121] nm_system_replace_default_ip6_route(): (wlan0): failed to set IPv6 default route: -7
Nov  6 06:03:18 acker4 NetworkManager[1028]: <info> Policy set 'ackerNET' (wlan0) as default for IPv6 routing and DNS.
Nov  6 06:03:19 acker4 dhclient: XMT: Info-Request on wlan0, interval 3510ms.
Nov  6 06:03:23 acker4 dhclient: XMT: Info-Request on wlan0, interval 7250ms.
Nov  6 06:03:30 acker4 dhclient: XMT: Info-Request on wlan0, interval 14940ms.
Nov  6 06:03:45 acker4 dhclient: XMT: Info-Request on wlan0, interval 30240ms.
Nov  6 06:04:00 acker4 NetworkManager[1028]: <warn> (wlan0): DHCPv6 request timed out.
Nov  6 06:04:01 acker4 NetworkManager[1028]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 5757
Nov  6 06:04:01 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov  6 06:04:01 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov  6 06:04:01 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov  6 06:04:26 acker4 kernel: [ 1332.204276] [UFW BLOCK] IN=wlan0 OUT= MAC=10:bf:48:fb:aa:5b:20:aa:4b:11:85:f1:08:00 SRC=66.189.0.100 DST=192.168.1.117 LEN=62 TOS=0x00 PREC=0x00 TTL=244 ID=39897 DF PROTO=UDP SPT=53 DPT=57124 LEN=42 
Nov  6 06:04:26 acker4 kernel: [ 1332.205198] [UFW BLOCK] IN=wlan0 OUT= MAC=10:bf:48:fb:aa:5b:20:aa:4b:11:85:f1:08:00 SRC=24.178.162.3 DST=192.168.1.117 LEN=62 TOS=0x00 PREC=0x00 TTL=242 ID=21027 DF PROTO=UDP SPT=53 DPT=57124 LEN=42 
Nov  6 06:04:36 acker4 kernel: [ 1342.243713] [UFW BLOCK] IN=wlan0 OUT= MAC=10:bf:48:fb:aa:5b:20:aa:4b:11:85:f1:08:00 SRC=24.247.15.53 DST=192.168.1.117 LEN=62 TOS=0x00 PREC=0x00 TTL=249 ID=27465 DF PROTO=UDP SPT=53 DPT=59912 LEN=42 
Nov  6 06:04:36 acker4 kernel: [ 1342.288060] [UFW BLOCK] IN=wlan0 OUT= MAC=10:bf:48:fb:aa:5b:20:aa:4b:11:85:f1:08:00 SRC=24.178.162.3 DST=192.168.1.117 LEN=62 TOS=0x00 PREC=0x00 TTL=242 ID=27347 DF PROTO=UDP SPT=53 DPT=59912 LEN=42 
Nov  6 06:04:46 acker4 kernel: [ 1352.339883] [UFW BLOCK] IN=wlan0 OUT= MAC=10:bf:48:fb:aa:5b:20:aa:4b:11:85:f1:08:00 SRC=24.178.162.3 DST=192.168.1.117 LEN=62 TOS=0x00 PREC=0x00 TTL=242 ID=7019 DF PROTO=UDP SPT=53 DPT=29650 LEN=42 
Nov  6 06:04:46 acker4 kernel: [ 1352.482575] [UFW BLOCK] IN=wlan0 OUT= MAC=10:bf:48:fb:aa:5b:20:aa:4b:11:85:f1:08:00 SRC=66.189.0.100 DST=192.168.1.117 LEN=62 TOS=0x00 PREC=0x00 TTL=244 ID=11011 DF PROTO=UDP SPT=53 DPT=29650 LEN=42 
ackerwaa@acker4:~$ 

```

notes: there were 19 updates this morning which i installed

i switched the system back to the wireless card for this test

---

### Post by chili555 on 2012-11-06
Interesting for what's there and not there! We see nothing unusual; that is, fixable here. I am fascinated to see that you appear to have received an IPv6 address!> Joining mDNS multicast group on interface wlan0.IPv6 with address fd96:6e68:888b:0:9555:a438:b322:f878.We so far have little experience with IPv6. We don't know if Network Manager, wpa_supplicant, the driver and hardware all work correctly together. Just as a temporary experiment, click the Network Manager icon and disconnect from ackerNET. Right-click the Network Manager icon and Edit Connections. Edit Wireless and select IPv6 Settings and select Ignore. Save and close. Now connect again. 

Is there any improvement? Let's see:```
sudo cat /var/log/syslog | grep wlan | tail -n15
```It may take a reboot.

I have a suspicion but not a clear understanding. Please see attached.

---

### Post by mike acker on 2012-11-06
> **chili555 said:**
> Interesting for what's there and not there! We see nothing unusual; that is, fixable here. I am fascinated to see that you appear to have received an IPv6 address!We so far have little experience with IPv6. We don't know if Network Manager, wpa_supplicant, the driver and hardware all work correctly together. Just as a temporary experiment, click the Network Manager icon and disconnect from ackerNET. Right-click the Network Manager icon and Edit Connections. Edit Wireless and select IPv6 Settings and select Ignore. Save and close. Now connect again. 

Is there any improvement? Let's see:```
sudo cat /var/log/syslog | grep wlan | tail -n15
```It may take a reboot.

I have a suspicion but not a clear understanding. Please see attached.

ok,-- here's what we get:
```

bill@acker4:~$ sudo cat /var/log/syslog | grep wlan | tail -n15
[sudo] password for bill: 
Nov  6 08:39:04 acker4 avahi-daemon[1062]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.117.
Nov  6 08:39:04 acker4 avahi-daemon[1062]: New relevant interface wlan0.IPv4 for mDNS.
Nov  6 08:39:04 acker4 avahi-daemon[1062]: Registering new address record for 192.168.1.117 on wlan0.IPv4.
Nov  6 08:39:04 acker4 avahi-daemon[1062]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::12bf:48ff:fefb:aa5b.
Nov  6 08:39:04 acker4 avahi-daemon[1062]: Joining mDNS multicast group on interface wlan0.IPv6 with address fd96:6e68:888b:0:12bf:48ff:fefb:aa5b.
Nov  6 08:39:04 acker4 avahi-daemon[1062]: Registering new address record for fd96:6e68:888b:0:12bf:48ff:fefb:aa5b on wlan0.*.
Nov  6 08:39:04 acker4 avahi-daemon[1062]: Withdrawing address record for fe80::12bf:48ff:fefb:aa5b on wlan0.
Nov  6 08:39:05 acker4 avahi-daemon[1062]: Registering new address record for fd96:6e68:888b:0:9555:a438:b322:f878 on wlan0.*.
Nov  6 08:39:05 acker4 NetworkManager[1028]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov  6 08:39:05 acker4 NetworkManager[1028]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov  6 08:39:05 acker4 NetworkManager[1028]: <info> Policy set 'ackerNET' (wlan0) as default for IPv4 routing and DNS.
Nov  6 08:39:05 acker4 NetworkManager[1028]: <info> Activation (wlan0) successful, device activated.
Nov  6 08:39:05 acker4 NetworkManager[1028]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov  6 08:40:15 acker4 kernel: [10681.234462] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:20:aa:4b:11:85:f1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Nov  6 08:40:17 acker4 kernel: [10683.728179] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:20:aa:4b:11:85:f1:08:00 SRC=192.168.1.1 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
bill@acker4:~$ 

```Interesting: speed test showed 17+ Mb/sec  -- it never read that high earlier. i'll test several times in this as the test result is never quite the same

using : [http://www.speedtest.net/](http://www.speedtest.net/)

the SLA here (Charter) specifies 30Mb/sec

```

bill@acker4:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ackerNET"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 20:AA:4B:11:85:F3   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:28   Missed beacon:0

eth0      no wireless extensions.

bill@acker4:~$ ^C
bill@acker4:~$ 

```

I am using a CISCO LINKSYS E900 router

---

### Post by chili555 on 2012-11-06
It looks like you still got an IPv6 address. Did you reboot?

---

### Post by mike acker on 2012-11-06
> **chili555 said:**
> It looks like you still got an IPv6 address. Did you reboot?

ok, after the reboot:
```

bill@acker4:~$ sudo cat /var/log/syslog | grep wlan | tail -n15
[sudo] password for bill: 
Nov  6 08:58:26 acker4 avahi-daemon[1015]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.117.
Nov  6 08:58:26 acker4 avahi-daemon[1015]: New relevant interface wlan0.IPv4 for mDNS.
Nov  6 08:58:26 acker4 avahi-daemon[1015]: Registering new address record for 192.168.1.117 on wlan0.IPv4.
Nov  6 08:58:27 acker4 NetworkManager[1103]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov  6 08:58:27 acker4 NetworkManager[1103]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov  6 08:58:27 acker4 NetworkManager[1103]: <info> Activation (wlan0) successful, device activated.
Nov  6 08:58:27 acker4 NetworkManager[1103]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov  6 08:58:28 acker4 avahi-daemon[1015]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::12bf:48ff:fefb:aa5b.
Nov  6 08:58:28 acker4 avahi-daemon[1015]: Joining mDNS multicast group on interface wlan0.IPv6 with address fd96:6e68:888b:0:7467:5da8:c72d:72e5.
Nov  6 08:58:28 acker4 avahi-daemon[1015]: Registering new address record for fd96:6e68:888b:0:7467:5da8:c72d:72e5 on wlan0.*.
Nov  6 08:58:28 acker4 avahi-daemon[1015]: Withdrawing address record for fe80::12bf:48ff:fefb:aa5b on wlan0.
Nov  6 08:58:28 acker4 avahi-daemon[1015]: Registering new address record for fd96:6e68:888b:0:12bf:48ff:fefb:aa5b on wlan0.*.
Nov  6 09:00:04 acker4 NetworkManager[1103]: <info> Policy set 'ackerNET' (wlan0) as default for IPv4 routing and DNS.
Nov  6 09:00:04 acker4 NetworkManager[1103]: <info> Policy set 'ackerNET' (wlan0) as default for IPv4 routing and DNS.
Nov  6 09:01:15 acker4 kernel: [  191.311085] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:20:aa:4b:11:85:f1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
bill@acker4:~$ 

```note: the system selected the RJ45 interface after re-boot.  I switched that off and turned on the wireless.

the RJ45 interface is testing at 35Mb/sec this morning (1 test ) last 802 test was 6Mb/sec

I remember running into serious problems working at the hospital with computers having "dual stack" network protocols,...... TCP/IP + Novell -- was a probable recipie for trouble

---

### Post by chili555 on 2012-11-06
It appears you _still_ got an IPv6 address! i guess there is no stopping progress. Can you confirm the change you made stuck; i.e. that your NM settings look as my previous attachment? Is there a setting in the router to turn off IPv6, just so we can test and rule possibilities in and out?

Please also try:```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce swenc=1
```When you remove the module, your connection will drop and it will come back when you reload it with a driver parameter. Is there any improvement?

What speeds does your router advertise?```
nm-tool
```Please disguise the MAC address, something like: xx:13:10:62:8D:xx.

---

### Post by mike acker on 2012-11-06
> **chili555 said:**
> It appears you _still_ got an IPv6 address! i guess there is no stopping progress. Can you confirm the change you made stuck; i.e. that your NM settings look as my previous attachment? Is there a setting in the router to turn off IPv6, just so we can test and rule possibilities in and out?

Please also try:```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce swenc=1
```When you remove the module, your connection will drop and it will come back when you reload it with a driver parameter. Is there any improvement?

What speeds does your router advertise?```
nm-tool
```Please disguise the MAC address, something like: xx:13:10:62:8D:xx.

sorry for the delay. I've not done any math for 50 years and I'm trying to help my daughter get thru a college math class :(

here's the nm-tool output
```

bill@acker4:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             disconnected
  Default:           no
  HW Address:        []

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0  [ackerNET] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        []

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *ackerNET:      Infra, 20:AA:4B:11:85:F3, Freq 2412 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.117
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             24.247.15.53
    DNS:             66.189.0.100
    DNS:             24.178.162.3


bill@acker4:~$ 

```it is still set to ignore IPV6.

I'll have to try to dig into the router

if i modprobe -r that module is the module gone for good or just until i re-boot ?

more: the mod probe: 

```

T4:~$ sudo modprobe -r rtl8192ce
[sudo] password for bill: 
T4:~$ sudo modprobe rtl8192ce swenc=1
T4:~$ 

```

speed test remains ~10Mb/sec

---

### Post by mike acker on 2012-11-06
> **chili555 said:**
> It looks like you still got an IPv6 address. Did you reboot?

ok i got into the CISCO E900 and disabled IPV6

here is iwconfig

```

bill@acker4:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ackerNET"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 20:AA:4B:11:85:F3   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

eth0      no wireless extensions.

bill@acker4:~$ 

```

speed is still testing at ~10 Mb/sec

---

### Post by chili555 on 2012-11-06
> if i modprobe -r that module is the module gone for good or just until i re-boot ?It is gone for about 3 seconds until you reload it with the very next command:```
sudo modprobe rtl8192ce swenc=1
```More later; time to vote.

---

### Post by chili555 on 2012-11-07
I am mystified about this:> wlan0     IEEE 802.11bgn  ESSID:"ackerNET"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 20:AA:4B:11:85:F3   
          [COLOR="Red"]Bit Rate=72.2 Mb/s[/COLOR]   Tx-Power=20 dBm   That suggests the wireless card and the router have agreed to connect at 72 Mb/s. However:> speed is still testing at ~10 Mb/sec Let's see if we can pin down the difficulty a bit more; first the computer to router:```
ping -c3 192.168.1.1
```Now, the computer to router, bypassing the assigned DNS nameserver:```
ping -c3 8.8.8.8
```Now through the ISP assigned nameservers:```
ping -c3 www.google.com
```

---

### Post by mike acker on 2012-11-07
> **chili555 said:**
> I am mystified about this:That suggests the wireless card and the router have agreed to connect at 72 Mb/s. However:Let's see if we can pin down the difficulty a bit more; first the computer to router:```
ping -c3 192.168.1.1
```

result: wired first; wireless 2d result:

```

bill@acker4:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=0.650 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=0.540 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=0.541 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.540/0.577/0.650/0.051 ms
bill@acker4:~$ 

bill@acker4:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=1.53 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=1.92 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=1.99 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.535/1.820/1.996/0.203 ms
bill@acker4:~$ 

```> Now, the computer to router, bypassing the assigned DNS nameserver:```
ping -c3 8.8.8.8
```result: wired first; wireless 2d result:

```

bill@acker4:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=46 time=25.0 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=46 time=26.1 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=46 time=26.0 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 25.068/25.740/26.113/0.511 ms
bill@acker4:~$ 

bill@acker4:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=46 time=41.6 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=46 time=68.1 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=46 time=40.8 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 40.885/50.244/68.158/12.672 ms
bill@acker4:~$ 

```> Now through the ISP assigned nameservers:```
ping -c3 www.google.com
```result: wired first; wireless 2d result:

```

bill@acker4:~$ ping -c3 www.google.com
PING www.google.com (74.125.225.210) 56(84) bytes of data.
64 bytes from den03s06-in-f18.1e100.net (74.125.225.210): icmp_req=1 ttl=50 time=49.2 ms
64 bytes from den03s06-in-f18.1e100.net (74.125.225.210): icmp_req=2 ttl=49 time=59.7 ms
64 bytes from den03s06-in-f18.1e100.net (74.125.225.210): icmp_req=3 ttl=48 time=78.8 ms

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 49.287/62.643/78.848/12.235 ms
bill@acker4:~$ 


bill@acker4:~$ ping -c3 www.google.com
PING www.google.com (74.125.225.209) 56(84) bytes of data.
64 bytes from den03s06-in-f17.1e100.net (74.125.225.209): icmp_req=1 ttl=49 time=298 ms
64 bytes from den03s06-in-f17.1e100.net (74.125.225.209): icmp_req=2 ttl=50 time=48.3 ms
64 bytes from den03s06-in-f17.1e100.net (74.125.225.209): icmp_req=3 ttl=49 time=59.9 ms

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 48.317/135.689/298.810/115.441 ms
bill@acker4:~$ 


```"FWIW" I still think the kernel recognizes the device as a wireless card but can't id the specifics.... and uses a generic setting

this is really my error,-- for not checking the list of supported cards before ordering a PCI/Express card

it would really be good to suppoort the ASUS express cards though,-- ASUS is pretty cool stuff,-- I think!!

---

### Post by chili555 on 2012-11-07
The kernel identifies the card perfectly well:> 02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)And assigns a specific driver:> :~$ lsmod |grep rtl
rtl8192ce              84826  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce
mac80211              506816  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              205544  2 rtlwifi,mac80211```
$ modinfo rtl8192ce
filename:       /lib/modules/3.5.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    [COLOR="Red"]Realtek 8192C/8188C 802.11n PCI wireless[/COLOR]
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     40628D8F1554C378D140D79
<snip>
```

---

### Post by mike acker on 2012-11-07
> **chili555 said:**
> The kernel identifies the card perfectly well:And assigns a specific driver...{snip}

apparently the card is mfg by Realtek and re-sold by ASUS then.  

I'm still worried: the card is a PCI/Express card, not a PCI card.

the card came with a CD which also states system requirements: WINDOWS. so i discarded the CD. the instructions do call for installation of a driver but this works from a windows autorun file

the replacement card [ EDIMAX EW-7128Gn R ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833315096") states it has Linux support . card should be here tw; it was transferred to USPS/Des Plains this morning . it is PCI not PCI-E which is unfortunate: my M5A88-M has only one PCI slot.

---

### Post by mike acker on 2012-11-09
> **mike acker said:**
> 

the replacement card [ EDIMAX EW-7128Gn R ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833315096") states it has Linux support . card should be here tw; it was transferred to USPS/Des Plains this morning . it is PCI not PCI-E which is unfortunate: my M5A88-M has only one PCI slot.

well, i got the replacement card today

and I looked thru the installation procedure.

I have one comment: You must be joking.

I will run the RJ-45 and just put up with the wire.

END

---

### Post by chili555 on 2012-11-09
Would you care to share it? There may be a better way.

---

### Post by mike acker on 2012-11-09
> **chili555 said:**
> Would you care to share it? There may be a better way.

by all means!!  I thought I was beat!!!!

Looking at the new wirless card I looked thru the CD and found the LINUX directory.  On a hunch I looked at the CD that came with the ASUS PCE N10  ( PCI Express )

sure enough: it has a LINUX section

here are the contents:
```

T4:~/Downloads/PCE_N10$ ll     { renamed copy from CD -- was just "Linux" }
total 1200
drwxrwxr-x 6 bill bill    4096 Jan  3  2012 ./
drwxr-xr-x 5 bill bill    4096 Nov  9 16:11 ../
drwxrwxr-x 3 bill bill    4096 Jan  3  2012 firmware/
drwxrwxr-x 3 bill bill    4096 Jan  3  2012 HAL/
-r-------- 1 bill bill    4024 Jun 23  2011 Makefile
-r-------- 1 bill bill    8058 Jun 23  2011 readme.txt
drwxrwxr-x 2 bill bill    4096 Jan  3  2012 realtek/
-r-------- 1 bill bill    1734 Jun 23  2011 release_note
drwxrwxr-x 2 bill bill    4096 Jan  3  2012 rtllib/
-r-------- 1 bill bill     489 Jun 23  2011 runwpa
-r-------- 1 bill bill     337 Jun 23  2011 wpa1.conf
-r-------- 1 bill bill 1178238 Jun 23  2011 wpa_supplicant-0.6.9.tar.gz
bill@ALBERT4:~/Downloads/PCE_N10$ 

```here is the first part of the readme
```

========================================================================================
                I. Component 
========================================================================================
The driver is composed of several parts:
    1. Firmare to make nic work
           1.1 firmare/RTL8192CE

    2. Module source code
       2.1 rtllib 
       2.2 HAL/rtl8192
    
    3. Script to build the modules
       3.1 Makefile 

    4. Example of supplicant configuration file:
       4.1 wpa1.conf

    5. Script to run wpa_supplicant
       5.1 runwpa

========================================================================================
                II. Compile & Installation & uninstall
========================================================================================
You can enter top-level directory of driver and execute follwing command to
Compile, Installation, or uninstall the driver:

        1. Change to Super User
       sudo su

    2. Compile driver from the source code 
       make

    3. Install the driver to the kernel
           make install
           reboot

    4. uninstall driver
       make uninstall

========================================================================================
                III. Start Up Wireless
========================================================================================
You can use two methord to start up wireless:

    1. Install driver like II. and reboot OS, Wireless will be brought 
       up by GUI, such as NetworkManager

```I am familiar with "make",-- it instructs  the C compiler to compile anything that needs compiling from the list of instructions ( the "make" file ) and then to link and produce an executable.... in this case I expect a .bin -- the needed driver....

```

T4:~/Downloads/PCE_N10$ sudo su
[sudo] password for bill: 
root@T4:/home/bill/Downloads/PCE_N10# make Makefile
make: Nothing to be done for `Makefile'.
root@T4:/home/bill/Downloads/PCE_N10# exit
exit
bill@T4:~/Downloads/PCE_N10$ 

```

should I try the install ?  was everything delivered compiled?

---

### Post by chili555 on 2012-11-09
> RTL8192CEThe module rtl8192ce is already built in to 12.04 LTS, I do believe. Find out with:```
modinfo rtl8192ce
```It will either return 'not found' or all the module information. If you have it, I'd swap out the wireless cards and see if you can connect.

From my 12.10 install:> chili@LAPTOP410:~$ modinfo rtl8192ce
filename:       /lib/modules/3.5.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
etc., etc.You could also check for the presence of the firmware:```
ls /lib/firmware/rtlwifi
```You couldn't build the driver because you'd need build tools; *make*, for instance, and kernel headers. It is quite likely that the version in 12.04 LTS is newer anyway.

---

### Post by mike acker on 2012-11-10
> **chili555 said:**
> The module rtl8192ce is already built in to 12.04 LTS, I do believe. Find out with:```
modinfo rtl8192ce
```It will either return 'not found' or all the module information. If you have it, I'd swap out the wireless cards and see if you can connect.

From my 12.10 install:You could also check for the presence of the firmware:```
ls /lib/firmware/rtlwifi
```You couldn't build the driver because you'd need build tools; *make*, for instance, and kernel headers. It is quite likely that the version in 12.04 LTS is newer anyway.

ok, I tried out the EDiMAX card.  It's worse: 4 Mb/sec .   the CD for this card also wants me to MAKE the driver.  I can understand why that could be needed in the LINUX environment -- to a point:  what kernel is UBUNTU 12.04 LTS built on ?  I would think the driver would need to be for that kernel.  Given that,-- the PCI Express slot should be an IEEE standard arrangement and the motherboard should deal with that OK.  Next up is the CPU -- AMD Phenom II x4 .  so, in the end there could be some set-up parms in the whole thing that have to be adjusted for the particular combination of the card, slot, motherboard and CPU -- .  Given that though I would expect to be able to execute the install stuff off the CD...

I really like the ASUS PCE N-10 card better: it fits in a PCI/Express slot.  I like that.

I put the PC back together without a wireless card.

hopefully we have some sort of Wireless Card news here so that whenever this gets sorted out I can put my wireless card back.

---

### Post by chili555 on 2012-11-10
> to a point: what kernel is UBUNTU 12.04 LTS built on ?Kernel version 3.2.0-xx; confirm:```
uname -r
```>  I would think the driver would need to be for that kernel.It already is!> chili@LAPTOP410:~$ modinfo rtl8192ce
filename:       /lib/modules/3.5.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
That's from my 12.10 system, running 3.5.0-xx. Please check your system:```
modinfo rtl8192ce
```Isn't the driver built for your kernel?> I would expect to be able to execute the install stuff off the CD...You can't for a number of reasons, including security and that build tools are required. In almost every case, compiling from source code is not required and so build tools are not installed by default.

By the way, did you notice that the new card and the old card apparently use the *same* driver???

If you insist on replacing the newer, optimized for Ubuntu rtl8192ce with an older, jack-of-all-trades-master-of-none driver, I will reluctantly assist you.

[RANT]The fact that one can insert a CD, DVD or USB key and an autorun installs software, virii, trojans, et al immediately is, at once, convenient and a ***huge*** security flaw.[/RANT]

---

### Post by mike acker on 2012-11-10
> **chili555 said:**
> Kernel version 3.2.0-xx; confirm:```
uname -r
```It already is!That's from my 12.10 system, running 3.5.0-xx. Please check your system:```
modinfo rtl8192ce
```Isn't the driver built for your kernel?You can't for a number of reasons, including security and that build tools are required. In almost every case, compiling from source code is not required and so build tools are not installed by default.

By the way, did you notice that the new card and the old card apparently use the *same* driver???

If you insist on replacing the newer, optimized for Ubuntu rtl8192ce with an older, jack-of-all-trades-master-of-none driver, I will reluctantly assist you.

[RANT]The fact that one can insert a CD, DVD or USB key and an autorun installs software, virii, trojans, et al immediately is, at once, convenient and a ***huge*** security flaw.[/RANT]

that's a GOOD RANT. Autorun was utilized a lot by hackers.

here's the info you asked for:
```

bill@acker4:~$ uname -r
3.2.0-32-generic
bill@acker4:~$ modinfo rtl8192ce
filename:       /lib/modules/3.2.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     216E9AAB4459E49C3C6B69A
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.2.0-32-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
bill@acker4:~$ 

```I would dearly love to solve this but i think we are missing some key info. for some reason it isn't negotiating the proper rate
amendment
googling against rtl8192ce suggests there may be a problem with rtl8192ce when signal strength is low
see [https://bugzilla.redhat.com/show_bug.cgi?id=847875](https://bugzilla.redhat.com/show_bug.cgi?id=847875)

later today i might try some tests related to this. unfortunatly i have no way to read signal strength on my nix box

---

### Post by mike acker on 2012-11-10
RF Signal Level

based on this report
[https://bugzilla.redhat.com/show_bug.cgi?id=847875](https://bugzilla.redhat.com/show_bug.cgi?id=847875)

i determined to try a Big Experiment

The EDiMAX card came with a "Witch's Hat" cone shape antenna on about 2M antenna cable

I re-installed the ASUS PCE-N10 and connected the Witch's Hat antenna in place of the little buck-horn that came with the PCE-N10

Bingo!

the Speed Test
[http://www.speedtest.net/](http://www.speedtest.net/)

is now registering 44 Mb/sec and correspondingly the Ubox performance meter reads a bit over 4 MB/sec

I can page thru my favorites on FLICKR without getting the focusing delay...

the results of this test point at the antenna change as having resolved the  problem. The inference then being that signal strength was the actual problem.

I have fought many bugs in my day and this one is similar to some of the worst in one particular way: the device did not provide any feedback regarding whatever issues it was encountering.  the wireless indicator:
[IMG]http://napfn.com/ubuntu_wireless_indicator.jpeg[/IMG]

looked EXACTLY the same: top bar dim. we are used to this being a field strength indicator

the Network box from the System Settings thing -- looks exactly the same. It just sez: "connected 72 Mb/sec" 

where is the diagnostic info ?????

~~~
RANT: DO;
I had one like this earlier.  In a MSFT application.  The App kept failing with a message "xxxxx.dll - not found"

we called the vendor. repeatedly. and he tried to easter egg the problem, having us move the .dll to every place he could think of

the actual outcome?

the app found that .dll every time.  but it was the WRONG VERSION.  And so it reported "not found" when it should have reported c:\windows32\xxxxx.dll -- wrong version
END RANT;

well, Chilli has encouraged me to stick with this and I'm glad we did.  Thanks Chilli, I would not have got it without ya!!

but anyway, Chilli allowed himself a short rant so I got me one too.

---

### Post by chili555 on 2012-11-10
Awesome. I'm very glad it's working!

---

