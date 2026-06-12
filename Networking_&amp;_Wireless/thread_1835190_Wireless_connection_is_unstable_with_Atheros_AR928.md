---
title: "Wireless connection is unstable with Atheros AR9287"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by kr0n1x on 2011-08-28
Hi, my laptop is an Acer Aspire 5742ZG.
I've always had problems with wireless connection.
The wireless works fine on Windows 7 (64bit).

I'm using Ubuntu 11.04 (64bit) but also Debian 6.0 got the same problem.

Some informations:

lspci -k output:
```
03:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Foxconn International, Inc. Device e034
	Kernel driver in use: ath9k
	Kernel modules: ath9k
```

My problem is that sometimes I completely loose connectivity to my router (or just having it, but with high packet loss, like 25%+), but my NetworkManager applet doesn't see it. The signal power is very high, but still, if I want my connection back, I have to click the icon and then click on my wireless connection name to reload my connection.

dmesg just after the problem happens (while the connectivity is alredy lost): [http://pastebin.com/YABGattr](http://pastebin.com/YABGattr)

dmesg after i reloaded my connection: [http://pastebin.com/1499V9BM](http://pastebin.com/1499V9BM)

the ping is like a joke... sometimes it's very stable like this:
```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=2.51 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=2.41 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=1.75 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=1.63 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=2.73 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=64 time=1.44 ms
64 bytes from 192.168.1.1: icmp_req=7 ttl=64 time=1.47 ms
64 bytes from 192.168.1.1: icmp_req=8 ttl=64 time=1.43 ms
64 bytes from 192.168.1.1: icmp_req=9 ttl=64 time=1.53 ms
64 bytes from 192.168.1.1: icmp_req=10 ttl=64 time=1.43 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9014ms
rtt min/avg/max/mdev = 1.436/1.838/2.738/0.484 ms
```

and sometimes it's unstable like 10ms to 300ms, sometimes also with packet loss.

I've found these useful links about my wireless chipset:
[https://bugs.edge.launchpad.net/ubuntu/+bugs?field.searchtext=ath9k&orderby=-importance](https://bugs.edge.launchpad.net/ubuntu/+bugs?field.searchtext=ath9k&orderby=-importance)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/378156](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/378156)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761176](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761176)

Some people say to put a ath9k.conf (or ath9.conf) file in /etc/modprobe.d/ with a particular line but it didn't help me.

I also installed compat-wireless (or atleast I've tried) by installing these two packages:
linux-backports-modules-cw-2.6.39-2.6.38-11-generic (2.6.38-11.7)
linux-backports-modules-cw-2.6.39-natty-generic (2.6.38.11.26)

but I'm not sure if them are active at the moment.

I didn't try updating my kernel to version 2.6.39, that will be my last try i think... I see people complaining about this issue since 2009 and I don't believe that a 2years later version of the kernel is the REAL and ONLY solution to this problem. But I'll do that if I will not have better solutions.:P

Can you help me? Tell me if you need more informations!

Thanks!

EDIT #1:
uname -a:
```
Linux 5742zg 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by wildmanne39 on 2011-08-29
Hi, I am on my way to bed but I did a search and I found the same bug and the same solutions.

That is all I have found so far, I will look more tomorrow.

---

### Post by kr0n1x on 2011-08-29
> **wildmanne39 said:**
> Hi, I am on my way to bed but I did a search and I found the same bug and the same solutions.

That is all I have found so far, I will look more tomorrow.

Thanks :D

edit: example of a (not-very) unstable ping on my machine, it can be way worse sometimes, like 25%+ packet loss:
```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=2.16 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=2.12 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=2.14 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=401 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=204 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=64 time=2.16 ms
64 bytes from 192.168.1.1: icmp_req=7 ttl=64 time=2.15 ms
64 bytes from 192.168.1.1: icmp_req=9 ttl=64 time=399 ms
64 bytes from 192.168.1.1: icmp_req=10 ttl=64 time=114 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 9 received, 10% packet loss, time 9009ms
rtt min/avg/max/mdev = 2.121/125.586/401.170/161.043 ms
```

---

### Post by wildmanne39 on 2011-08-29
Hi, post the results of this commands please do we can see what kernel you are currently using.
```
uname -a
``` 
Thank you

---

### Post by kr0n1x on 2011-08-29
Sure, here's my uname -a:
```
Linux 5742zg 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

I had just clicked on my "reply to this topic" link... in my email notification... and I just had to reload my connection because the packet loss went to 60%:

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=3.56 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=3.02 ms
64 bytes from 192.168.1.1: icmp_req=7 ttl=64 time=2.65 ms
64 bytes from 192.168.1.1: icmp_req=10 ttl=64 time=1.95 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 4 received, 60% packet loss, time 9038ms
rtt min/avg/max/mdev = 1.955/2.800/3.561/0.585 ms
```

Here's the dmesg:
[http://pastebin.com/HLVYpxws](http://pastebin.com/HLVYpxws)

I took that dmesg right after I got the connection back, by clicking the connection name in the NetworkManager applet.

---

### Post by wildmanne39 on 2011-08-29
Hi, I would update your kernel to kernel to version 2.6.39rc1 as recommended in the bug report, then we can go from there.
Thank you

---

### Post by praseodym on 2011-08-29
Package loss normaly means that the nameserver resolution doesnt work properly or you are using the wrong mtu-value. Can you show

```
ifconfig -a
route -n
cat /etc/resolv.conf
iwconfig
sudo iwlist scan
```
You may add the nameservers of your provider (or the google public ns 8.8.8.8 and 8.8.4.4, they are fast & stable) in the NM applet.

->IPv4-settings->"Automatic (DHCP), addresses only" and restart your connection:

```
sudo service network-manager restart
```
The nm makes problems with mixed WPA/WPA2-encryption, better use WPA2-AES instead if possible.

The mtu-value of your provider should replace "automatic" in the applet.

---

### Post by kr0n1x on 2011-08-29
> **wildmanne39 said:**
> Hi, I would update your kernel to kernel to version 2.6.39rc1 as recommended in the bug report, then we can go from there.
Thank you

I tried doing:
```
sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update && sudo apt-get dist-upgrade -y
```

but it doesn't install anything.

What's the best way to upgrade to 2.6.39? I got natty-proposed and natty-backports disabled. Do have I to enable them?

---

### Post by wildmanne39 on 2011-08-29
Hi, here is a link for installing the latest kernel and also further down the page there are directions for installing 2.6.39rc4 kernel.
[http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal](http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal)

Also you can try what praseodym mentions if you like first, I am not sure it will work since this is a bug, but he is very good with networking issues.
Thank you

---

### Post by kr0n1x on 2011-08-29
> **praseodym said:**
> Package loss normaly means that the nameserver resolution doesnt work properly or you are using the wrong mtu-value. Can you show

```
ifconfig -a
route -n
cat /etc/resolv.conf
iwconfig
sudo iwlist scan
```
You may add the nameservers of your provider (or the google public ns 8.8.8.8 and 8.8.4.4, they are fast & stable) in the NM applet.

->IPv4-settings->"Automatic (DHCP), addresses only" and restart your connection:

```
sudo service network-manager restart
```
The nm makes problems with mixed WPA/WPA2-encryption, better use WPA2-AES instead if possible.

The mtu-value of your provider should replace "automatic" in the applet.

all the commands outputs:
```
pasquale@5742zg:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:74:ae:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:559 errors:0 dropped:0 overruns:0 frame:0
          TX packets:559 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:44498 (44.4 KB)  Byte TX:44498 (44.4 KB)

wlan0     Link encap:Ethernet  HWaddr c4:46:19:38:ce:c8  
          indirizzo inet:192.168.1.4  Bcast:192.168.1.255  Maschera:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37063 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37491 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:37970892 (37.9 MB)  Byte TX:5476395 (5.4 MB)

pasquale@5742zg:~$ route -n
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
pasquale@5742zg:~$ cat /etc/resolv.conf 
# Generated by NetworkManager
nameserver 192.168.1.1
pasquale@5742zg:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TeleTu90"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 02:10:18:01:00:05   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:19   Missed beacon:0

pasquale@5742zg:~$ sudo iwlist scan
[sudo] password for pasquale: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 02:10:18:01:00:05
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"TeleTu90"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000044c15c320
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000854656C6554753930
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180202F5

pasquale@5742zg:~$
```

Should I hide the mac address? Or is it safe to spam those outputs here? :lolflag: (me n00b)
Anyway I think I'm already using WPA2-AES only... not mixed.
I'm using OpenDNS instead of google public ns.

---

### Post by praseodym on 2011-08-29
No, dont enable the proposed or backports. These sources contain "beta" packages in development, your system may get unstable or you may reach [dependency hell]("http://en.wikipedia.org/wiki/Dependency_hell").

Download the kernel packages manually, the PPA is empty, delete it (and install neccessary packages) via:

```
sudo apt-get install --reinstall ppa-purge build-essential dkms
sudo ppa-purge ppa:kernel-ppa/ppa
sudo apt-get update
```

The [Mainline-kernel-archive]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") lists a lot more kernels to install, e.g. [2.6.39-4]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/"). You need both amd64 and the all.deb packages.

For my first post: Did you try the tipps? Module ath9k often needs additionally a module parameter:

```
sudo modprobe -rf ath9k
sudo modprobe -v ath9k nohwcrypt=1
sudo service network-manager restart
```

If this works, make it permanent:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

[COLOR="Red"]Edit[/COLOR]: too slow ;-)

---

### Post by kr0n1x on 2011-08-29
At the moment I've only done the tips you said in your previous post (it means, I only added my opendns to addresses in networkmanager applet).

I restarted NetworkManager and now I'm downloading Ubuntu with .torrent.

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=1.57 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=2.51 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=4.92 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=1.69 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=1.45 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=64 time=2.93 ms
64 bytes from 192.168.1.1: icmp_req=7 ttl=64 time=2.04 ms
64 bytes from 192.168.1.1: icmp_req=8 ttl=64 time=1.46 ms
64 bytes from 192.168.1.1: icmp_req=9 ttl=64 time=1.92 ms
64 bytes from 192.168.1.1: icmp_req=10 ttl=64 time=1.43 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9009ms
rtt min/avg/max/mdev = 1.433/2.196/4.927/1.025 ms
```

It seems very stable for a connection that is downloading from a torrent.

Can that only modification solve my problem? :| I don't want to believe that xD If I only had to add the DNS...

If I will have some problems again, I will follow the last post (kernel upgrade and ath9k hacks)

---

### Post by wildmanne39 on 2011-08-29
Hi, keep us informed, that suggestion was not in the bug reports I read.

---

### Post by praseodym on 2011-08-29
See [here]("http://translate.google.de/translate?hl=de&sl=de&tl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FDNS-Probleme"). Google-Translator just translated all relevant stuff, but not all, you may translate the missing parts yourself.

---

### Post by wildmanne39 on 2011-08-29
Hi, thank you that is very useful information.

---

### Post by kr0n1x on 2011-08-29
My connection is still ok. :guitar:

Also, I made a screenshot of my router's advanced settings page and of dns servers page (both in attachment).

**Rate:** it can be set to automatic, or from 1 to 54 Mbps.

**Multicast rate:** same as above.

**Basic rate:** default, all, 1 & 2 Mbps, 1 & 2 & 5.5 & 6 & 11 & 12 & 24 Mbps.

**Acceleration:** MAXg (125 Mbps), 54g+ (XPress), None.

**54g mode:** automatic, 54g Performance, 54g LRS, 802.11b Only.

**54g protection:** automatic, disabled.

**Regulatory mode:** Disabled, 802.11h, 802.11d.

Until now, I only changed the 54g mode from automatic to 54g Performance, Since I don't use any 802.11b device (I changed it 30 minutes ago, it has been set to Automatic since always).

Are the other settings ok? Especially the one that I really don't know like Fragmentation threshold, RTS threshold, DTIM interval, Beacon interval.

The devices that use the wireless in my house are: laptops (all support 802.11g), iPhone 3GS (I think it supports 802.11g too... It's not mine, shame if else :D ahah), PlayStation 3.

---

### Post by wildmanne39 on 2011-08-29
Hi, the other setting look good to me, if it continues to work,  would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by kr0n1x on 2011-08-29
> **wildmanne39 said:**
> Hi, the other setting look good to me, if it continues to work,  would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

I'll do that when I'm sure the problems is gone. After rebooting my Ubuntu it seems the ping is unstable again.
I went to the NetworkManager and set the MTU to 1500 (instead of Automatic) and now I see how it goes.

Downloading from torrents seems unstable again.

Well... It still needs some testing!

At least, I have to see if the connection loss happens again, or the high packet loss for example (I got 1 packet loss out of 20 in a ping test to my router).

See you soon :)

---

### Post by kr0n1x on 2011-08-29
I confirm the fact that the problem is still present.

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=13 ttl=64 time=1.52 ms
64 bytes from 192.168.1.1: icmp_req=14 ttl=64 time=227 ms
64 bytes from 192.168.1.1: icmp_req=15 ttl=64 time=42.1 ms
64 bytes from 192.168.1.1: icmp_req=16 ttl=64 time=200 ms
64 bytes from 192.168.1.1: icmp_req=17 ttl=64 time=217 ms
64 bytes from 192.168.1.1: icmp_req=18 ttl=64 time=628 ms
64 bytes from 192.168.1.1: icmp_req=19 ttl=64 time=29.0 ms
64 bytes from 192.168.1.1: icmp_req=20 ttl=64 time=167 ms
64 bytes from 192.168.1.1: icmp_req=21 ttl=64 time=320 ms
64 bytes from 192.168.1.1: icmp_req=22 ttl=64 time=241 ms
64 bytes from 192.168.1.1: icmp_req=23 ttl=64 time=162 ms
64 bytes from 192.168.1.1: icmp_req=24 ttl=64 time=35.2 ms
64 bytes from 192.168.1.1: icmp_req=25 ttl=64 time=68.8 ms
64 bytes from 192.168.1.1: icmp_req=26 ttl=64 time=231 ms
^C
--- 192.168.1.1 ping statistics ---
27 packets transmitted, 14 received, 48% packet loss, time 26016ms
rtt min/avg/max/mdev = 1.523/183.876/628.099/155.431 ms
```

I'm going to follow the #11 post (upgrading kernel + eth9k hacks).

First I try by just doing the hacks and then, if problems persist, I'll upgrade.

---

### Post by kr0n1x on 2011-08-29
Hack done.

```
pasquale@5742zg:~$ sudo modprobe -rf ath9k
[sudo] password for pasquale: 
pasquale@5742zg:~$ sudo modprobe -v ath9k nohwcrypt=1
insmod /lib/modules/2.6.38-11-generic/updates/cw-2.6.39/cfg80211.ko 
insmod /lib/modules/2.6.38-11-generic/updates/cw-2.6.39/ath.ko 
insmod /lib/modules/2.6.38-11-generic/updates/cw-2.6.39/ath9k_hw.ko 
insmod /lib/modules/2.6.38-11-generic/updates/cw-2.6.39/ath9k_common.ko 
insmod /lib/modules/2.6.38-11-generic/updates/cw-2.6.39/mac80211.ko 
insmod /lib/modules/2.6.38-11-generic/updates/cw-2.6.39/ath9k.ko nohwcrypt=1 nohwcrypt=1
pasquale@5742zg:~$ sudo service network-manager restart
network-manager start/running, process 3351
pasquale@5742zg:~$ ping 192.168.1.1 -c10
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=1.46 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=1.59 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=1.47 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=1.43 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=2.26 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=64 time=1.43 ms
64 bytes from 192.168.1.1: icmp_req=7 ttl=64 time=1.40 ms
64 bytes from 192.168.1.1: icmp_req=8 ttl=64 time=2.02 ms
64 bytes from 192.168.1.1: icmp_req=9 ttl=64 time=1.43 ms
64 bytes from 192.168.1.1: icmp_req=10 ttl=64 time=1.44 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9005ms
rtt min/avg/max/mdev = 1.402/1.596/2.269/0.288 ms
pasquale@5742zg:~$
```

Now I have to check if the improvement is made thanks to the hack, or thanks to the restart of the service only. Many times, right after a restart, it gets back working correctly. Testing is needed.

I'll keep you up to date!! The 2.6.39 kernel is already in download.

---

### Post by wildmanne39 on 2011-08-29
Hi, ok I am keeping a check on you, good luck!!!

---

### Post by kr0n1x on 2011-08-29
The problems were still present after the ath9k hack.

I upgraded to 2.6.39, and I still have ping stability problem + packet loss.

```
pasquale@5742zg:~$ uname -a
Linux 5742zg 2.6.39-02063904-generic #201108040905 SMP Thu Aug 4 09:10:06 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
pasquale@5742zg:~$ ping 192.168.1.1 -c10
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=16.9 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=40.2 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=63.4 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=86.4 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=6.77 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=64 time=336 ms
64 bytes from 192.168.1.1: icmp_req=7 ttl=64 time=1.44 ms
64 bytes from 192.168.1.1: icmp_req=8 ttl=64 time=75.2 ms
64 bytes from 192.168.1.1: icmp_req=9 ttl=64 time=98.6 ms
64 bytes from 192.168.1.1: icmp_req=10 ttl=64 time=121 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 1.441/84.729/336.694/92.276 ms
pasquale@5742zg:~$ ping maya.ngi.it
PING maya.ngi.it (88.149.128.3) 56(84) bytes of data.
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=1 ttl=51 time=71.7 ms
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=2 ttl=51 time=189 ms
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=3 ttl=51 time=112 ms
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=4 ttl=51 time=133 ms
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=5 ttl=51 time=159 ms
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=6 ttl=51 time=79.6 ms
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=7 ttl=51 time=412 ms
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=8 ttl=51 time=128 ms
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=9 ttl=51 time=70.9 ms
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=10 ttl=51 time=73.5 ms
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=11 ttl=51 time=95.7 ms
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=12 ttl=51 time=223 ms
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=13 ttl=51 time=247 ms
64 bytes from maya.ngi.it (88.149.128.3): icmp_req=14 ttl=51 time=69.8 ms
^C
--- maya.ngi.it ping statistics ---
15 packets transmitted, 14 received, 6% packet loss, time 14010ms
rtt min/avg/max/mdev = 69.887/147.745/412.351/92.579 ms
pasquale@5742zg:~$
```

I really don't know what to do now :( All the things we've been trying haven't solved the problem.

Maybe we're trying to solve a different problem... maybe the problem is present in another thing... I really don't know since I don't have the needed knowleadge.

Any idea? :confused:

---

### Post by wildmanne39 on 2011-08-29
Hi, there are some people with your card that we can help them fix there problems and some we cant, I believe you fall into  the later category, if you have tried everything the the bug reports suggest, I am afraid I am out of ideas.

I am sorry.

---

### Post by kr0n1x on 2011-08-29
It is clear that the problem is software-side.

I should try another completely different software base... like Kubuntu for example, and Xubuntu.

What do you think? Maybe I could solve the problem.

Anyway, could you tell me a good wireless card completely supported by linux?? I mean... one without this kind of bugs! I could buy it and plug it in my laptop... or an usb one! That's the only solution if, even with other distributions, I will still have this problem!

---

### Post by wildmanne39 on 2011-08-29
Hi, kubuntu and xubuntu are run on top of ubuntu so the problem will most likely persist.

This is a list of certified hardware.
[http://www.ubuntu.com/certification/catalog](http://www.ubuntu.com/certification/catalog)
This is my usb card that came with my desktop and it worked out of the box with 11.04.
> 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device

---

### Post by kr0n1x on 2011-08-30
I tried booting Xubuntu from a Live-CD, I tried pinging the router, stability problem again :(

Now I added another disto to my system, Arch Linux.

I Installed it from the net image, and then I installed Xfce4.8 (Arch doesn't have a default Desktop Environment).

After 1 day of testing... it doesn't seem to have any problem with wireless. I'm using wicd. On Ubuntu I had problems even with wicd (yeh I also did the test, in past, removing the network-applet and having only wicd instead, without any success).

If the situation will remain positive, I think I will try installing Gnome and reporting here if I will have this stability problem again.

The bad thing is that now I have to learn a completely different distro :( which motto isn't "the automatic way" xD it is very "manual", everything takes to touch configuration files.

Well, more knowleadge doesn't hurt, thanks for the support!

PS: the problem was present also on Debian. I write this so maybe some developers can find it useful. The problem should be present in something related to both Debian and Ubuntu (yeh... I know Ubuntu is Debian-derivate!)

Thanks again, see you!

---

### Post by wildmanne39 on 2011-08-30
Hi, it is possible that it is a problem with the natty kernels,did you try your wireless card on an earlier version of ubuntu?

---

### Post by kr0n1x on 2011-08-30
> **wildmanne39 said:**
> Hi, it is possible that it is a problem with the natty kernels,did you try your wireless card on an earlier version of ubuntu?

I used Ubuntu with 10.10 and 11.04. Honestly I don't remember if I had this problem during 10.10.

debian uses an older kernel, 2.6.32-5, but the problem is present anyway.

On Arch I got 3.0.3 kernel version.

---

### Post by wildmanne39 on 2011-08-30
Hi, ok I hope you get use to Arch for now, I am sorry it did not work in ubuntu.

---

### Post by flanagan on 2011-09-05
Having almost the exact same symptoms, and having exhausted all the other suggestions from the bug report (and this thread), what worked for me was to use the link in wildmanne39's post #9 to upgrade to 2.6.39rc4 kernel:
```
Linux Aspire5552 2.6.39-020639rc4-generic #201104191410 SMP Tue Apr 19 14:19:01 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
One should be aware that the .deb file linux-headers-2.6.39-rc4-amd64.deb identifies itself incorrectly as being targeted for X86, but it does work on my amd64.

My Atheros AR9287 used to be dog slow (reminiscent of the dial-up days), had low signal strength and packet loss, and would cut out completely on anything sizable. Now it is stable (so far), fast, and full strength with no packet loss.
So, for me, it was definitely a problem with the 2.6.38-11-generic kernel. I will post back if I have any other problems with the rc4 kernel.

---

### Post by wildmanne39 on 2011-09-05
Hi, thats great I am glad I could help, if you need it we will be glad to help you.

Also if you want to would you click on my ubuntu member application in my signature to support me for membership.
Thank you

---

### Post by SpaceQuadrant on 2011-09-07
> **flanagan said:**
> Having almost the exact same symptoms, and having exhausted all the other suggestions from the bug report (and this thread), what worked for me was to use the link in wildmanne39's post #9 to upgrade to 2.6.39rc4 kernel:
```
Linux Aspire5552 2.6.39-020639rc4-generic #201104191410 SMP Tue Apr 19 14:19:01 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```One should be aware that the .deb file linux-headers-2.6.39-rc4-amd64.deb identifies itself incorrectly as being targeted for X86, but it does work on my amd64.

My Atheros AR9287 used to be dog slow (reminiscent of the dial-up days), had low signal strength and packet loss, and would cut out completely on anything sizable. Now it is stable (so far), fast, and full strength with no packet loss.
So, for me, it was definitely a problem with the 2.6.38-11-generic kernel. I will post back if I have any other problems with the rc4 kernel.

Hello , I also have an Acer Aspire 5552. I have been trying for 8 hours solid to get my wireless working. It will not connect to a Wireless Network that consists of a WPA security type at all. I upgraded my Kernel to 2.6.38-11-generic but nothing had changed so I tried with the very latest kernel 3.1.0-0301rc4-generic just for fun and it still does not work. My ethernet port also has a very weird issue, I have to do this process:

```
sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether <MAC>
sudo ifconfig eth0 hw up
sudo dhclient eth0
```to get my wired connection to work. With all other versions of Ubuntu in the last 3 years I've never had such trouble getting my wireless to work; What is wrong with this version?
```

dmesg | grep -e ath -e wlan
```returns

```
[  147.682410] wlan0: authenticate with 06:8b:5d:7e:37:72 (try 1)
[  147.684708] wlan0: authenticated
[  147.684748] wlan0: associate with 06:8b:5d:7e:37:72 (try 1)
[  147.688227] wlan0: RX AssocResp from 06:8b:5d:7e:37:72 (capab=0x421 status=0 aid=1)
[  147.688238] wlan0: associated
[  150.258996] wlan0: deauthenticating from 06:8b:5d:7e:37:72 by local choice (reason=3)
```I think there is something wrong with WPA_supplicant though I am not sure. 

Here is the syslog

```
sudo tail -n100 /var/log/syslog
```

```
Sep  7 04:56:58 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  7 04:56:59 Default wpa_supplicant[1032]: Trying to associate with 00:8b:5d:7e:37:72 (SSID='ET0020000F3528' freq=2447 MHz)
Sep  7 04:56:59 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  7 04:56:59 Default kernel: [  911.011363] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 1/3)
Sep  7 04:56:59 Default kernel: [  911.210221] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 2/3)
Sep  7 04:56:59 Default kernel: [  911.410211] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 3/3)
Sep  7 04:57:00 Default kernel: [  911.610204] wlan0: direct probe to 00:8b:5d:7e:37:72 timed out
Sep  7 04:57:09 Default wpa_supplicant[1032]: Authentication with 00:8b:5d:7e:37:72 timed out.
Sep  7 04:57:09 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Sep  7 04:57:09 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  7 04:57:10 Default wpa_supplicant[1032]: Trying to associate with 00:8b:5d:7e:37:72 (SSID='ET0020000F3528' freq=2447 MHz)
Sep  7 04:57:10 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  7 04:57:10 Default kernel: [  921.991375] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 1/3)
Sep  7 04:57:10 Default kernel: [  922.190266] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 2/3)
Sep  7 04:57:10 Default kernel: [  922.390200] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 3/3)
Sep  7 04:57:11 Default kernel: [  922.590250] wlan0: direct probe to 00:8b:5d:7e:37:72 timed out
Sep  7 04:57:14 Default NetworkManager[855]: <warn> Activation (wlan0/wireless): association took too long.
Sep  7 04:57:14 Default NetworkManager[855]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Sep  7 04:57:14 Default NetworkManager[855]: <warn> Activation (wlan0/wireless): asking for new secrets
Sep  7 04:57:14 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Sep  7 04:57:20 Default NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep  7 04:57:20 Default NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep  7 04:57:20 Default NetworkManager[855]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Sep  7 04:57:20 Default NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep  7 04:57:20 Default NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep  7 04:57:20 Default NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep  7 04:57:20 Default NetworkManager[855]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Sep  7 04:57:20 Default NetworkManager[855]: <info> Activation (wlan0/wireless): connection 'ET0020000F3528' has security, and secrets exist.  No new secrets needed.
Sep  7 04:57:20 Default NetworkManager[855]: <info> Config: added 'ssid' value 'ET0020000F3528'
Sep  7 04:57:20 Default NetworkManager[855]: <info> Config: added 'scan_ssid' value '1'
Sep  7 04:57:20 Default NetworkManager[855]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep  7 04:57:20 Default NetworkManager[855]: <info> Config: added 'psk' value '<omitted>'
Sep  7 04:57:20 Default NetworkManager[855]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  7 04:57:20 Default NetworkManager[855]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  7 04:57:20 Default NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep  7 04:57:20 Default NetworkManager[855]: <info> Config: set interface ap_scan to 1
Sep  7 04:57:20 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  7 04:57:21 Default wpa_supplicant[1032]: Trying to associate with 00:8b:5d:7e:37:72 (SSID='ET0020000F3528' freq=2447 MHz)
Sep  7 04:57:21 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  7 04:57:21 Default kernel: [  932.731531] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 1/3)
Sep  7 04:57:21 Default kernel: [  932.930214] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 2/3)
Sep  7 04:57:21 Default kernel: [  933.130213] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 3/3)
Sep  7 04:57:21 Default kernel: [  933.330211] wlan0: direct probe to 00:8b:5d:7e:37:72 timed out
Sep  7 04:57:31 Default wpa_supplicant[1032]: Authentication with 00:8b:5d:7e:37:72 timed out.
Sep  7 04:57:31 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Sep  7 04:57:31 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  7 04:57:32 Default wpa_supplicant[1032]: Trying to associate with 00:8b:5d:7e:37:72 (SSID='ET0020000F3528' freq=2447 MHz)
Sep  7 04:57:32 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  7 04:57:32 Default kernel: [  943.691427] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 1/3)
Sep  7 04:57:32 Default kernel: [  943.890226] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 2/3)
Sep  7 04:57:32 Default kernel: [  944.090213] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 3/3)
Sep  7 04:57:32 Default kernel: [  944.290207] wlan0: direct probe to 00:8b:5d:7e:37:72 timed out
Sep  7 04:57:42 Default wpa_supplicant[1032]: Authentication with 00:8b:5d:7e:37:72 timed out.
Sep  7 04:57:42 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Sep  7 04:57:42 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  7 04:57:43 Default wpa_supplicant[1032]: Trying to associate with 00:8b:5d:7e:37:72 (SSID='ET0020000F3528' freq=2447 MHz)
Sep  7 04:57:43 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  7 04:57:43 Default kernel: [  954.671522] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 1/3)
Sep  7 04:57:43 Default kernel: [  954.870225] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 2/3)
Sep  7 04:57:43 Default kernel: [  955.070222] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 3/3)
Sep  7 04:57:43 Default kernel: [  955.270224] wlan0: direct probe to 00:8b:5d:7e:37:72 timed out
Sep  7 04:57:53 Default wpa_supplicant[1032]: Authentication with 00:8b:5d:7e:37:72 timed out.
Sep  7 04:57:53 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Sep  7 04:57:53 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  7 04:57:54 Default wpa_supplicant[1032]: Trying to associate with 00:8b:5d:7e:37:72 (SSID='ET0020000F3528' freq=2447 MHz)
Sep  7 04:57:54 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  7 04:57:54 Default kernel: [  965.641397] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 1/3)
Sep  7 04:57:54 Default kernel: [  965.840237] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 2/3)
Sep  7 04:57:54 Default kernel: [  966.040225] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 3/3)
Sep  7 04:57:54 Default kernel: [  966.240217] wlan0: direct probe to 00:8b:5d:7e:37:72 timed out
Sep  7 04:58:01 Default NetworkManager[855]: <warn> (wlan0): link timed out.
Sep  7 04:58:04 Default wpa_supplicant[1032]: Authentication with 00:8b:5d:7e:37:72 timed out.
Sep  7 04:58:04 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Sep  7 04:58:04 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  7 04:58:05 Default wpa_supplicant[1032]: Trying to associate with 00:8b:5d:7e:37:72 (SSID='ET0020000F3528' freq=2447 MHz)
Sep  7 04:58:05 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  7 04:58:05 Default kernel: [  976.631710] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 1/3)
Sep  7 04:58:05 Default kernel: [  976.830100] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 2/3)
Sep  7 04:58:05 Default kernel: [  977.030211] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 3/3)
Sep  7 04:58:05 Default kernel: [  977.230207] wlan0: direct probe to 00:8b:5d:7e:37:72 timed out
Sep  7 04:58:15 Default wpa_supplicant[1032]: Authentication with 00:8b:5d:7e:37:72 timed out.
Sep  7 04:58:15 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Sep  7 04:58:15 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  7 04:58:16 Default wpa_supplicant[1032]: Trying to associate with 00:8b:5d:7e:37:72 (SSID='ET0020000F3528' freq=2447 MHz)
Sep  7 04:58:16 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  7 04:58:16 Default kernel: [  987.631478] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 1/3)
Sep  7 04:58:16 Default kernel: [  987.830137] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 2/3)
Sep  7 04:58:16 Default kernel: [  988.030220] wlan0: direct probe to 00:8b:5d:7e:37:72 (try 3/3)
Sep  7 04:58:16 Default kernel: [  988.240195] wlan0: direct probe to 00:8b:5d:7e:37:72 timed out
Sep  7 04:58:20 Default NetworkManager[855]: <warn> Activation (wlan0/wireless): association took too long.
Sep  7 04:58:20 Default NetworkManager[855]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Sep  7 04:58:20 Default NetworkManager[855]: <warn> Activation (wlan0/wireless): asking for new secrets
Sep  7 04:58:20 Default NetworkManager[855]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Sep  7 04:58:22 Default NetworkManager[855]: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Sep  7 04:58:22 Default NetworkManager[855]: <warn> Activation (wlan0) failed for access point (ET0020000F3528)
Sep  7 04:58:22 Default NetworkManager[855]: <info> Marking connection 'ET0020000F3528' invalid.
Sep  7 04:58:22 Default NetworkManager[855]: <warn> Activation (wlan0) failed.
Sep  7 04:58:22 Default NetworkManager[855]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Sep  7 04:58:22 Default NetworkManager[855]: <info> (wlan0): deactivating device (reason: 0).
Sep  7 04:58:22 Default NetworkManager[855]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
```

```

iwconfig wlan0

``````
wlan0     IEEE 802.11bgn  ESSID:"ET0020000F3528"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```
[COLOR=DarkOrange][B]

[MORE]
[/B][/COLOR]
I have also tried the following:

```

sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1

```this has not worked.

I have updated network manager from the PPA

```
sudo apt-get add-repository ppa:network-manager/ppa
```and ran a

```

sudo apt-get update 
sudo apt-get upgrade

```Still no wireless with WPA working and my ethernet is still not working.

I have even compiled from:
[http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

and installed and still nothing is working. I am perhaps going to see if madwifi functions, I don't know what the differences are between linuxwireless and madwifi if wpa_supplicant is the issue though.

---

### Post by wildmanne39 on 2011-09-07
Hi, I am about to get off here for tonight and I will be out of town part of the day tomorrow but post the results of these commands here and as soon as I get back I will check on you.
```
nm-tool
```
```
sudo iwlist scan
```
make sure your router is set to wpa2 and not wpa or mixed mode.
Thank you

---

### Post by SpaceQuadrant on 2011-09-07
> **wildmanne39 said:**
> Hi, I am about to get off here for tonight and I will be out of town part of the day tomorrow but post the results of these commands here and as soon as I get back I will check on you.
```
nm-tool
``````
sudo iwlist scan
```make sure your router is set to wpa2 and not wpa or mixed mode.
Thank you

I tried madwifi and did nothing as I should and probably did expect.

Erm as for the data you requested, here you go and thank you very much!

```

nm-tool

```

```


NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        88:AE:1D:A6:10:40

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.77
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        4C:0F:6E:6B:78:1C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ET0020000F3528:  Infra, 00:8B:5D:7E:37:72, Freq 2447 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    BTOpenzone:      Infra, 06:8B:5D:7E:37:72, Freq 2447 MHz, Rate 54 Mb/s, Strength 70
    BTFON:           Infra, 0A:8B:5D:7E:37:72, Freq 2447 MHz, Rate 54 Mb/s, Strength 72
    SKY58006:        Infra, 00:18:4D:5C:98:50, Freq 2462 MHz, Rate 54 Mb/s, Strength 38 WPA
    SKY61016:        Infra, 00:22:3F:48:DA:6C, Freq 2412 MHz, Rate 54 Mb/s, Strength 38 WPA
    SKY47131:        Infra, E8:BE:81:77:B8:1C, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA
    SKY92116:        Infra, F0:7D:68:71:01:88, Freq 2462 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2
    SKY88619:        Infra, 00:18:4D:05:E0:1E, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA
    Dee:             Infra, 00:24:01:9F:E8:39, Freq 2412 MHz, Rate 54 Mb/s, Strength 87 WPA2

```

```
sudo iwlist scan
```
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:8B:5D:7E:37:72
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"ET0020000F3528"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001380df180
                    Extra: Last beacon: 50ms ago
                    IE: Unknown: 000E4554303032303030304633353238
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:24:01:9F:E8:39
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"Dee"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a3b4fdc7c
                    Extra: Last beacon: 880ms ago
                    IE: Unknown: 0003446565
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: 0A:8B:5D:7E:37:72
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001380df180
                    Extra: Last beacon: 30ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: 06:8B:5D:7E:37:72
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000013807b180
                    Extra: Last beacon: 410ms ago
                    IE: Unknown: 000A42544F70656E7A6F6E65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: 00:18:4D:05:E0:1E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"SKY88619"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000391aa64f4f
                    Extra: Last beacon: 520ms ago
                    IE: Unknown: 0008534B593838363139
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010035FF7F
          Cell 06 - Address: F0:7D:68:71:01:88
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"SKY92116"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000922efb585e2
                    Extra: Last beacon: 290ms ago
                    IE: Unknown: 0008534B593932313136
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: 00:22:3F:48:DA:6C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"SKY61016"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b01e09ba4a
                    Extra: Last beacon: 890ms ago
                    IE: Unknown: 0008534B593631303136
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

```

I am trying my router on WPA2 and not WPA&WPA2

---

### Post by SpaceQuadrant on 2011-09-07
No change concerning the MadWifi driver, attempting to use ath9k

```
dmesg
``````

[  594.431274] wlan0: authenticate with 00:8b:5d:7e:37:72 (try 1)
[  594.433558] wlan0: authenticated
[  594.456593] wlan0: associate with 00:8b:5d:7e:37:72 (try 1)
[  594.460230] wlan0: RX AssocResp from 00:8b:5d:7e:37:72 (capab=0x431 status=0 aid=2)
[  594.460242] wlan0: associated
[  640.217282] wlan0: deauthenticating from 00:8b:5d:7e:37:72 by local choice (reason=3)
[  640.518520] cfg80211: All devices are disconnected, going to restore regulatory settings
[  640.518534] cfg80211: Restoring regulatory settings
[  640.518552] cfg80211: Calling CRDA to update world regulatory domain
[  640.526391] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  640.526401] cfg80211: World regulatory domain updated:
[  640.526406] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  640.526415] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  640.526422] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  640.526429] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  640.526435] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  640.526441] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```

Also not working for ath9k

trying to use just WPA now

No Luck!

Latest Dmesg

```

[   12.020941] ath9k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.020952] ath9k 0000:08:00.0: setting latency timer to 64
[   12.109487] ath: EEPROM regdomain: 0x65
[   12.109489] ath: EEPROM indicates we should expect a direct regpair map
[   12.109494] ath: Country alpha2 being used: 00
[   12.109495] ath: Regpair used: 0x65
[   12.157315] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.157992] Registered led device: ath9k-phy0
[   16.590254] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  176.619650] wlan0: authenticate with 00:8b:5d:7e:37:72 (try 1)
[  176.622018] wlan0: authenticated
[  176.645166] wlan0: associate with 00:8b:5d:7e:37:72 (try 1)
[  176.648814] wlan0: RX AssocResp from 00:8b:5d:7e:37:72 (capab=0x431 status=0 aid=2)
[  176.648824] wlan0: associated
[  176.659175] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  187.650166] wlan0: no IPv6 routers present
[  222.213941] wlan0: deauthenticating from 00:8b:5d:7e:37:72 by local choice (reason=3)
[  386.171401] wlan0: authenticate with 00:8b:5d:7e:37:72 (try 1)
[  386.173645] wlan0: authenticated
[  386.196638] wlan0: associate with 00:8b:5d:7e:37:72 (try 1)
[  386.202987] wlan0: RX AssocResp from 00:8b:5d:7e:37:72 (capab=0x431 status=0 aid=1)
[  386.202994] wlan0: associated


```


Latest Syslog

```

Sep  7 05:49:11 Default NetworkManager[925]: <info> Activation (wlan0/wireless): connection 'ET0020000F3528' has security, and secrets exist.  No new secrets needed.
Sep  7 05:49:11 Default NetworkManager[925]: <info> Config: added 'ssid' value 'ET0020000F3528'
Sep  7 05:49:11 Default NetworkManager[925]: <info> Config: added 'scan_ssid' value '1'
Sep  7 05:49:11 Default NetworkManager[925]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep  7 05:49:11 Default NetworkManager[925]: <info> Config: added 'psk' value '<omitted>'
Sep  7 05:49:11 Default NetworkManager[925]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  7 05:49:11 Default NetworkManager[925]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  7 05:49:11 Default NetworkManager[925]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep  7 05:49:11 Default NetworkManager[925]: <info> Config: set interface ap_scan to 1
Sep  7 05:49:11 Default NetworkManager[925]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  7 05:49:12 Default wpa_supplicant[1040]: Trying to associate with 00:8b:5d:7e:37:72 (SSID='ET0020000F3528' freq=2447 MHz)
Sep  7 05:49:12 Default NetworkManager[925]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  7 05:49:12 Default kernel: [  386.171401] wlan0: authenticate with 00:8b:5d:7e:37:72 (try 1)
Sep  7 05:49:12 Default kernel: [  386.173645] wlan0: authenticated
Sep  7 05:49:12 Default kernel: [  386.196638] wlan0: associate with 00:8b:5d:7e:37:72 (try 1)
Sep  7 05:49:12 Default kernel: [  386.202987] wlan0: RX AssocResp from 00:8b:5d:7e:37:72 (capab=0x431 status=0 aid=1)
Sep  7 05:49:12 Default kernel: [  386.202994] wlan0: associated
Sep  7 05:49:12 Default wpa_supplicant[1040]: Associated with 00:8b:5d:7e:37:72
Sep  7 05:49:12 Default NetworkManager[925]: <info> (wlan0): supplicant connection state:  associating -> associated
Sep  7 05:49:12 Default NetworkManager[925]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Sep  7 05:49:12 Default NetworkManager[925]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Sep  7 05:49:12 Default wpa_supplicant[1040]: WPA: Key negotiation completed with 00:8b:5d:7e:37:72 [PTK=CCMP GTK=TKIP]
Sep  7 05:49:12 Default wpa_supplicant[1040]: CTRL-EVENT-CONNECTED - Connection to 00:8b:5d:7e:37:72 completed (reauth) [id=0 id_str=]
Sep  7 05:49:12 Default NetworkManager[925]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Sep  7 05:49:12 Default NetworkManager[925]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ET0020000F3528'.
Sep  7 05:49:12 Default NetworkManager[925]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep  7 05:49:12 Default NetworkManager[925]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep  7 05:49:12 Default NetworkManager[925]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Sep  7 05:49:12 Default NetworkManager[925]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep  7 05:49:12 Default dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Sep  7 05:49:12 Default NetworkManager[925]: <info> dhclient started with pid 1875
Sep  7 05:49:12 Default NetworkManager[925]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep  7 05:49:12 Default dhclient: Copyright 2004-2010 Internet Systems Consortium.
Sep  7 05:49:12 Default dhclient: All rights reserved.
Sep  7 05:49:12 Default dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep  7 05:49:12 Default dhclient: 
Sep  7 05:49:12 Default NetworkManager[925]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep  7 05:49:12 Default dhclient: Listening on LPF/wlan0/4c:0f:6e:6b:78:1c
Sep  7 05:49:12 Default dhclient: Sending on   LPF/wlan0/4c:0f:6e:6b:78:1c
Sep  7 05:49:12 Default dhclient: Sending on   Socket/fallback
Sep  7 05:49:12 Default dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Sep  7 05:49:14 Default dhclient: DHCPOFFER of 192.168.1.79 from 192.168.1.1
Sep  7 05:49:14 Default dhclient: DHCPREQUEST of 192.168.1.79 on wlan0 to 255.255.255.255 port 67
Sep  7 05:49:14 Default dhclient: DHCPNAK from 192.168.1.1
Sep  7 05:49:17 Default dhclient: DHCPREQUEST of 192.168.1.79 on wlan0 to 255.255.255.255 port 67
Sep  7 05:49:17 Default dhclient: DHCPNAK from 192.168.1.1
Sep  7 05:49:20 Default dhclient: DHCPREQUEST of 192.168.1.79 on wlan0 to 255.255.255.255 port 67
Sep  7 05:49:20 Default dhclient: DHCPNAK from 192.168.1.1
Sep  7 05:49:25 Default dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Sep  7 05:49:26 Default dhclient: DHCPOFFER of 192.168.1.79 from 192.168.1.1
Sep  7 05:49:26 Default dhclient: DHCPREQUEST of 192.168.1.79 on wlan0 to 255.255.255.255 port 67
Sep  7 05:49:26 Default dhclient: DHCPNAK from 192.168.1.1
Sep  7 05:49:29 Default dhclient: DHCPREQUEST of 192.168.1.79 on wlan0 to 255.255.255.255 port 67
Sep  7 05:49:29 Default dhclient: DHCPNAK from 192.168.1.1
Sep  7 05:49:33 Default dhclient: DHCPREQUEST of 192.168.1.79 on wlan0 to 255.255.255.255 port 67
Sep  7 05:49:33 Default dhclient: DHCPNAK from 192.168.1.1
Sep  7 05:49:38 Default dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Sep  7 05:49:39 Default dhclient: DHCPOFFER of 192.168.1.79 from 192.168.1.1
Sep  7 05:49:39 Default dhclient: DHCPREQUEST of 192.168.1.79 on wlan0 to 255.255.255.255 port 67
Sep  7 05:49:39 Default dhclient: DHCPNAK from 192.168.1.1
Sep  7 05:49:42 Default dhclient: DHCPREQUEST of 192.168.1.79 on wlan0 to 255.255.255.255 port 67
Sep  7 05:49:42 Default dhclient: DHCPNAK from 192.168.1.1
Sep  7 05:49:45 Default dhclient: DHCPREQUEST of 192.168.1.79 on wlan0 to 255.255.255.255 port 67
Sep  7 05:49:45 Default dhclient: DHCPNAK from 192.168.1.1
Sep  7 05:49:50 Default dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Sep  7 05:49:51 Default dhclient: DHCPOFFER of 192.168.1.79 from 192.168.1.1
Sep  7 05:49:51 Default dhclient: DHCPREQUEST of 192.168.1.79 on wlan0 to 255.255.255.255 port 67
Sep  7 05:49:51 Default dhclient: DHCPNAK from 192.168.1.1
Sep  7 05:49:54 Default dhclient: DHCPREQUEST of 192.168.1.79 on wlan0 to 255.255.255.255 port 67
Sep  7 05:49:54 Default dhclient: DHCPNAK from 192.168.1.1
Sep  7 05:49:57 Default NetworkManager[925]: <warn> (wlan0): DHCPv4 request timed out.
Sep  7 05:49:57 Default NetworkManager[925]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1875
Sep  7 05:49:57 Default NetworkManager[925]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Sep  7 05:49:57 Default NetworkManager[925]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Sep  7 05:49:57 Default NetworkManager[925]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep  7 05:49:57 Default NetworkManager[925]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Sep  7 05:49:57 Default NetworkManager[925]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Sep  7 05:49:57 Default NetworkManager[925]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Sep  7 05:49:57 Default NetworkManager[925]: <info> (wlan0): device state change: 7 -> 9 (reason 5)
Sep  7 05:49:57 Default NetworkManager[925]: <warn> Activation (wlan0) failed for access point (ET0020000F3528)
Sep  7 05:49:57 Default NetworkManager[925]: <info> Marking connection 'ET0020000F3528' invalid.
Sep  7 05:49:57 Default NetworkManager[925]: <warn> Activation (wlan0) failed.
Sep  7 05:49:57 Default NetworkManager[925]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Sep  7 05:49:57 Default NetworkManager[925]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Sep  7 05:49:57 Default NetworkManager[925]: <info> (wlan0): deactivating device (reason: 0).
Sep  7 05:49:57 Default NetworkManager[925]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep  7 05:49:57 Default NetworkManager[925]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep  7 05:49:57 Default kernel: [  431.219844] wlan0: deauthenticating from 00:8b:5d:7e:37:72 by local choice (reason=3)
Sep  7 05:49:57 Default kernel: [  431.358514] cfg80211: All devices are disconnected, going to restore regulatory settings
Sep  7 05:49:57 Default kernel: [  431.358527] cfg80211: Restoring regulatory settings
Sep  7 05:49:57 Default kernel: [  431.358537] cfg80211: Calling CRDA to update world regulatory domain
Sep  7 05:49:57 Default wpa_supplicant[1040]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Sep  7 05:49:57 Default kernel: [  431.364846] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Sep  7 05:49:57 Default kernel: [  431.364852] cfg80211: World regulatory domain updated:
Sep  7 05:49:57 Default kernel: [  431.364853] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep  7 05:49:57 Default kernel: [  431.364857] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  7 05:49:57 Default kernel: [  431.364859] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep  7 05:49:57 Default kernel: [  431.364862] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep  7 05:49:57 Default kernel: [  431.364864] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  7 05:49:57 Default kernel: [  431.364867] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```

No idea what's going on.

---

### Post by wildmanne39 on 2011-09-07
Hi, a couple of things to mention then I am gone for the night.

Your tex power is down to 13 it is usually 20 see if you can change that in your router. I have never done it but if you can't I will look into it tomorrow.

Make sure in your router that the wireless radio is on and set to 100 percent.

This is related to the first issue mentioned your signal strength is weak get closer to your router and see if it will connect.

Is this how you ran these commands?
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
That is what they should look like and you run them one at a time, and you need to unplug your wired connection to use your wireless.
Thank you

---

### Post by SpaceQuadrant on 2011-09-07
> **wildmanne39 said:**
> Hi, a couple of things to mention then I am gone for the night.

Your tex power is down to 13 it is usually 20 see if you can change that in your router. I have never done it but if you can't I will look into it tomorrow.

Make sure in your router that the wireless radio is on and set to 100 percent.

This is related to the first issue mentioned your signal strength is weak get closer to your router and see if it will connect.

Is this how you ran these commands?
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```That is what they should look like and you run them one at a time, and you need to unplug your wired connection to use your wireless.
Thank you

Yep I ran them commands, I am pretty much less than 1m away from my router. Don't see why there should be a power issue works fine on Windows 7. Good night to you and thanks. I am getting off the floor now as my whole body is aching!

---

