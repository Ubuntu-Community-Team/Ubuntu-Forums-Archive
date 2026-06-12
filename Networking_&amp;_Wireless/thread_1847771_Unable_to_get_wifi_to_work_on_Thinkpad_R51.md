---
title: "Unable to get wifi to work on Thinkpad R51"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by klov on 2011-09-21
I installed **Ubuntu Server 10.04** on my IBM Thinkpad R51 . I have  been trying to get it to work for past 2 days with no luck. I followed  many posts here on forum with no luck , except once when iwconfig gave  eth1 with values 802 .... rather than 'unassociated'. I would appreciate  any guidance on this.


lspci | grep Network
```

02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

```nm-tool
```

State: connected
---Device: eth1 ----------------------------
Type:    802.11 WiFi
 Driver:  ipw2200
 State:   disconnected
 Default: no
 HW Address: 00:13:CE:87:4Z:DB

Capabilities:
 Wireless Properties
   WPA Encryption: yes
  WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points
 list of all points including my router. 

```lshw -C network
```

*-network:0
     description: Wireless interface
     product: PRO/Wireless 2200BG [Calexico2] Network COnnection
     vendor : Intel Corporation
     physical id: 2
  bus info: pci@00000:02:02.0
  logical name: eth1
 version : 05
 serial: 00:12:de:........
 width: 32 bits
 clock: 33MHz
 capabilities: pm bus_master cap_list ethernet physical wireless
 Configuratio:  broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq  firmware=ABG:9.0.5.27 (Dec 12 2007 ) latency=64 link=no maxlatency=24  mingnt=3 multicast=yes wireless=unassociated
  resources : irq:11 memory:d00200000-d020000fff

```I am not sure if the driver is installed here or not. 
iwlist eth1 scan .. gives me results. 
No matter what , eth1 is unassociated.
Also , I am not using any GUI as my goal is to emulate the production server environment .


Appreciate any help or input. 
Thank you

---

### Post by praseodym on 2011-09-21
Please show:

```
ifconfig -a
iwconfig
lsmod
dmesg | grep iwl
rfkill list
```
The driver can be updated (via cable) with the backport-modules:

```
sudo apt-get install linux-backports-modules-wireless-lucid-server
```

and reboot.

---

### Post by klov on 2011-09-21
Thank you Praseodym for prompt reply

I tried 

sudo apt-get install linux-backports-modules-wireless-lucid-serverbut the output I get is 
The following packages have unmet dependencies:2.6.
linux-backports-modules-wireless-lucid-server: Dependends: linux-backports-modules-wireless-2.6.34-2.6.32-28-server but it is not installable
E: Broken packages

The following are the outputs for 
ifconfig -a

eth1 Link encap: Ethernet HWaddr 00:13:......
inet6 addr: fe80::213 .... Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 error:0 dropped:0 overruns:0 frame:0
TX packets:1 errors:0 
dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes: 84 (84.0 B)
Interrupt:11 base address:0xc000 Memory: ....

iwconfig:
eth1    unassociated ESSID:"DevWifi"
        Mode: Managed Channel=0 Acess PointL Not-Associated
        Bit Rate: 0 kb/s Tx-Power=20 dbm Sensitivity = 8/0
        Retry Limit: 7  RTS thr:off fragment thr: off
Power Management: off
 Link QualityL 0 , signal level, noise level, Rx invalid nwid, Rx invalid
 crypt , Rx invalid frag, Tx excessive retries, Invalid misc,
Missed beacon .. are all 0.
------
lsmod  | grep 2200
  ipw2200 135216 0
  libipw   39896 1 ipw2200
  lib80211  5046 3 lib80211_crypt_wep,ipw2200, libipw

------
dmesg | grep iwl
 No output
------
rfkill list
no output

Sorry to have missed these outputs before.

---

### Post by klov on 2011-09-21
sorry for delayed response. I am typing all the values from the other computer :)

---

### Post by praseodym on 2011-09-21
Which kernel is installed?

```
uname -a
```please

---

### Post by klov on 2011-09-21
Thanks again :)

Linux servername 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux

---

### Post by praseodym on 2011-09-21
So it has to be

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

---

### Post by klov on 2011-09-21
Thanks :)  That worked 
Now iwcconfig finally shows
, but Ping [www.ubuntu.com](www.ubuntu.com) says ping: unknown host [www.ubuntu.com](www.ubuntu.com).


eth1 IEEE 802.11bg ESSID: "DevWifi"
Mode: Managed Channel=0 Acess PointL Not-Associated
        Bit Rate: 0 kb/s Tx-Power=20 dbm Sensitivity = 8/0
        Retry Limit: 7  RTS thr : off fragment thr: off
Power Management: off
 Link QualityL 0 , signal level, noise level, Rx invalid nwid, Rx invalid
 crypt , Rx invalid frag, Tx excessive retries, Invalid misc,
Missed beacon .. are all 0.

Also the wireless light isn't blinking.

---

### Post by praseodym on 2011-09-21
Did you reboot? Check also

```
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by klov on 2011-09-21
tried sudo ip link set eth1 up

But it gives output:

RTNETLINK answers: Unknown error 132

But thanks a zillion for helping me get rid of '**unmanaged**' :)

---

### Post by klov on 2011-09-21
did sudo rfkill unblock all
 rfkill kist all
0: phy0: wireless LAN
 Soft blocked : no
 hard blocked : no

cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkEnabled=true
WirelessEnabled=true
WWANEnabled=true
And rebooted again. 
But wireless not working. Will try to set the essid and key again and see if that helps.

---

### Post by klov on 2011-09-21
Tried to rest the essid and key. Wifi light is not blinking anymore.
iwlist eth1 scan gives result.
tried ip link set eth1 up 
doesn't give me error anymore, but still no wifi light.

---

### Post by praseodym on 2011-09-21
Do you use the network-manager-GUI? 

```
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
ifconfig -a
cat /etc/NetworkManager/nm-system-settings.conf
iwconfig
```

---

