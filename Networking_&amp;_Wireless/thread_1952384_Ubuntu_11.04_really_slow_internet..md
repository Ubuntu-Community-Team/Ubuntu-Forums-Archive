---
title: "Ubuntu 11.04 really slow internet."
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by toobywedge on 2012-04-04
Hello,
I haven't used Ubuntu for a while but I decided to come back and try it for a bit. I am really liking it so far but the internet is almost unbearable. It is so slow. The speed test shows about 30kbps but when I run windows the speed is around 600kbps.
When entering "sudo iwconfig" I receive this:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 14:D6:4D:2D:B0:A2   
          Bit Rate=121.5 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:4887   Missed beacon:0
```

I need help asap. Sorry if I left any information out.
Thanks,

*EDIT* Sorry about the smiley faces in the result from "sudo iwconfig". Not sure how to fix that.

---

### Post by nothingspecial on 2012-04-06
> **toobywedge said:**
> 

*EDIT* Sorry about the smiley faces in the result from "sudo iwconfig". Not sure how to fix that.

Fixed :)

Moved to networking & wireless.

---

### Post by wildmanne39 on 2012-04-06
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by toobywedge on 2012-04-07
Read below.

---

### Post by toobywedge on 2012-04-07
Ok. When I enter what you said I receive this.
```
lachland@Lachys-PC:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux Lachys-PC 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
lachland@Lachys-PC:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave Device [1a3b:1089]
	Kernel driver in use: ath9k
--
08:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1820]
	Kernel driver in use: atl1c
lachland@Lachys-PC:~$ lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 001 Device 003: ID 13d3:5122 IMC Networks 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lachland@Lachys-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Wolngarin - Public Internet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 06:15:6D:F4:1E:62   
          Bit Rate=36 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:6927   Missed beacon:0

lachland@Lachys-PC:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
lachland@Lachys-PC:~$ lsmod

```

I am on holidays using free Wifi. Not sure if this will make a difference but I can do it again when I get home.

---

### Post by wildmanne39 on 2012-04-07
Hi, please do:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by toobywedge on 2012-04-09
Sorry about the late reply.
It went from about 20kbps to around 300kbps. Thank you so much!

---

### Post by wildmanne39 on 2012-04-15
Hi, I am glad it worked, please use thread tools at the top of the page to mark the thread solved.
Thanks

---

