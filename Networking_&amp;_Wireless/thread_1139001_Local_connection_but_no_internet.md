---
title: "Local connection but no internet"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by tad1073 on 2009-04-26
NM shows that I am connected but when I try to access the internet fx always times out.
There seems to be a local connection but no internet connection.

---

### Post by DGortze380 on 2009-04-26
> **tad1073 said:**
> NM shows that I am connected but when I try to access the internet fx always times out.
There seems to be a local connection but no internet connection.

Need a whole lot more info than that.

Lets start with how are you connected to the internet? Specifically.

---

### Post by tad1073 on 2009-04-26
wireless connection

---

### Post by DGortze380 on 2009-04-26
> **tad1073 said:**
> wireless connection

Ok... maybe I wasn't clear. Need A LOT MORE INFORMATION.

Who your ISP?
What type of service (cable, dsl, dial-up, 3G)?
Do you have a Modem?
Do you have a router?
Access Point?
Has the connection ever worked?
Have you changed anything on the computer recently?
Brand and model of your wireless card?

 And any other information you have please...

---

### Post by tad1073 on 2009-04-26
ISP is not important, where as, I can connect using vista and w7

DSL modem connected to a Linksys wireless N router

the wireless router
[http://www.bestbuy.com/site/olspage....=1194054018722]("http://www.bestbuy.com/site/olspage.jsp?skuId=8639967&type=product&id=1194054018722")

the wireless card
[http://www.dlink.com/products/?pid=531]("http://www.bestbuy.com/site/olspage.jsp?skuId=7843747&type=product&id=1142298456916")

```
*-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1f:e2:01:ea:2d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.9-2 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wmaster0
       version: 01
       serial: 00:21:91:06:37:28
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 3e:91:cd:9b:e2:cf
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

ubuntu@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

---

### Post by tad1073 on 2009-04-28
bump

---

### Post by Iowan on 2009-04-28
Maybe not related, but what is output from **route**? (wondering about gateway...)

---

### Post by tad1073 on 2009-04-28
I have since removed ubuntu.

There is a nasty bug somewhere in the kernel. After rebooting into vista, somehow some thing in the linux kernel captures my wirless card, gives me limited connectivity eg. no internet connection, can not disable wireless card, causes me to have to do a hard shutdown etc.

---

### Post by DGortze380 on 2009-04-29
> **tad1073 said:**
> After rebooting into vista, somehow some thing in the linux kernel captures my wirless card, 

ummm... no. lol.

I'm am quite sure your deleted linux kernel is not interfering with Vista.

Good Luck.

---

### Post by tad1073 on 2009-04-30
> **DGortze380 said:**
> ummm... no. lol.

I'm am quite sure your deleted linux kernel is not interfering with Vista.

Good Luck.

This was before I removed ubuntu

---

### Post by DGortze380 on 2009-04-30
> **tad1073 said:**
> This was before I removed ubuntu

I am also quite sure your linux kernel has nothing to do with your issues while booting Vista... that's like saying the word document on your flash drive that you left at the office is causing your home computer to not print correctly... it makes no sense.

---

### Post by tad1073 on 2009-04-30
> **DGortze380 said:**
> I am also quite sure your linux kernel has nothing to do with your issues while booting Vista... that's like saying the word document on your flash drive that you left at the office is causing your home computer to not print correctly... it makes no sense.

All I know is, that, after restarting form ubuntu then booting into vista I was having the same issue where I had limited connectivity with my wireless connection.

I would restart and boot into W7 and wireless would work fine. I then would restart and boot Vista and wireless would work normally. 

It is just kind of odd, that's all.

---

### Post by hyuecn on 2009-04-30
I am having a similar problem; when I boot up I can connect to the internet, after about 10 mins I still have network access but can't get online. Works fine in Vista still

---

### Post by tad1073 on 2009-05-03
Still no working connection via wireless.

I have changed security to AES w/mixed mode (B+G+N)
I have disabled security and changed the mode to G
Booted 8.10 live cd to see if I could connect with 8.10.

Nothing works!!!

---

### Post by DGortze380 on 2009-05-03
> **tad1073 said:**
> Still no working connection via wireless.

I have changed security to AES w/mixed mode (B+G+N)
I have disabled security and changed the mode to G
Booted 8.10 live cd to see if I could connect with 8.10.

Nothing works!!!

I thought you removed Ubuntu?

It would be a good start if you'd give us the information we asked for so we could try to help.

> **Iowan said:**
> Maybe not related, but what is output from **route**? (wondering about gateway...)

the output of the following would also be helpful.

```

ifconfig -a

```

```

lspci

```

```

cat /etc/network/interfaces

```

---

### Post by tad1073 on 2009-05-03
```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@no hacking
       logical name: eth0
       version: 02
       serial: no hacking
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.9-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@no hacking
       logical name: wmaster0
       version: 01
       serial: no hacking
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  

ubuntu@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: No Hacking
                    ESSID:"thompson"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/100  Signal level:-88 dBm  Noise level=-101 dBm
                                       Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=no hacking
                    Extra: Last beacon: 24ms ago

pan0      Interface doesn't support scanning.


ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr No hacking  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3504 (3.5 KB)  TX bytes:3504 (3.5 KB)

wlan0     Link encap:Ethernet  HWaddr no hacking  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr no hacking  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"thompson"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


ubuntu@ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"thompson"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ubuntu@ubuntu:~$ lsb_release -d
Description:    Ubuntu 9.04


ubuntu@ubuntu:~$ lsb_release -d
Description:    Ubuntu 9.04
ubuntu@ubuntu:~$ uname -mr
2.6.28-11-generic x86_64


ubuntu@ubuntu:~$ lsmod | grep "ath9k"
ath9k                 288568  0 
mac80211              251144  1 ath9k
led_class              13064  1 ath9k


ubuntu@ubuntu:~$ dmesg | grep wlan0
[   91.675581] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   92.334609] wlan0: authenticate with AP no hacking
[   92.336133] wlan0: authenticated
[   92.336135] wlan0: associate with AP no hacking
[   92.339733] wlan0: RX AssocResp from no hacking (capab=0x401 status=0 aid=1)
[   92.339737] wlan0: associated
[   92.348089] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   92.348196] wlan0: disassociating by local choice (reason=3)
[  103.157026] wlan0: no IPv6 routers present
[  137.448548] wlan0: authenticate with AP no hacking
[  137.452272] wlan0: authenticate with AP 
[  137.652028] wlan0: authenticate with AP 
[  137.852030] wlan0: authenticate with AP 
[  138.052020] wlan0: authentication with AP  timed out

and more of the same

```

---

### Post by iv76erson03 on 2009-05-03
I am having this problem too with Remix on my Aspire One. All of a sudden no internet, but I can connect to the router. Also my weather bug thing updates, but nothing else connect. 

Edit: Hmm, just found out that I can connect to a website by typing in its IP address instead of [www.*.com](www.*.com). That's probably why my weather bug works because it's looking up an ip instead of a url. Does this help anyone solve my problem?

---

### Post by DGortze380 on 2009-05-03
> **tad1073 said:**
> ```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@no hacking
       logical name: eth0
       version: 02
       serial: no hacking
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.9-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@no hacking
       logical name: wmaster0
       version: 01
       serial: no hacking
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  

ubuntu@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: No Hacking
                    ESSID:"thompson"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/100  Signal level:-88 dBm  Noise level=-101 dBm
                                       Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=no hacking
                    Extra: Last beacon: 24ms ago

pan0      Interface doesn't support scanning.


ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr No hacking  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3504 (3.5 KB)  TX bytes:3504 (3.5 KB)

wlan0     Link encap:Ethernet  HWaddr no hacking  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr no hacking  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"thompson"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


ubuntu@ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"thompson"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ubuntu@ubuntu:~$ lsb_release -d
Description:    Ubuntu 9.04


ubuntu@ubuntu:~$ lsb_release -d
Description:    Ubuntu 9.04
ubuntu@ubuntu:~$ uname -mr
2.6.28-11-generic x86_64


ubuntu@ubuntu:~$ lsmod | grep "ath9k"
ath9k                 288568  0 
mac80211              251144  1 ath9k
led_class              13064  1 ath9k


ubuntu@ubuntu:~$ dmesg | grep wlan0
[   91.675581] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   92.334609] wlan0: authenticate with AP no hacking
[   92.336133] wlan0: authenticated
[   92.336135] wlan0: associate with AP no hacking
[   92.339733] wlan0: RX AssocResp from no hacking (capab=0x401 status=0 aid=1)
[   92.339737] wlan0: associated
[   92.348089] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   92.348196] wlan0: disassociating by local choice (reason=3)
[  103.157026] wlan0: no IPv6 routers present
[  137.448548] wlan0: authenticate with AP no hacking
[  137.452272] wlan0: authenticate with AP 
[  137.652028] wlan0: authenticate with AP 
[  137.852030] wlan0: authenticate with AP 
[  138.052020] wlan0: authentication with AP  timed out

and more of the same

```

Obviously you think you know better which commands will help me explore my theory of what's wrong better than I do..

If you want help, you can at least have the courtesy to post the output requested.

I'm no longer following this thread. Maybe someone can put up with the bull and help you.

---

### Post by tad1073 on 2009-05-12
removed by poster

---

### Post by tad1073 on 2009-05-12
> **DGortze380 said:**
> Obviously you think you know better which commands will help me explore my theory of what's wrong better than I do..

If you want help, you can at least have the courtesy to post the output requested.

I'm no longer following this thread. Maybe someone can put up with the bull and help you.


```
thomas@tad:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr censored
          inet addr:192.168.1.96  Bcast:censored  Mask:censored
          inet6 addr: censored Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1484342 (1.4 MB)  TX bytes:228037 (228.0 KB)
          Memory:censored 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

pan0      Link encap:Ethernet  HWaddr censored  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr censored  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr censored  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


thomas@tad:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


thomas@tad:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@censored
       logical name: eth0
       version: 02
       serial: censored
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.9-2 ip=censored latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@censored
       logical name: wmaster0
       version: 01
       serial: censored
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: censored
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


```

---

### Post by tad1073 on 2009-05-12
bump

---

### Post by tad1073 on 2009-05-13
bump

---

### Post by Iowan on 2009-05-13
When you lose connectivity, can you ping via IP address? Also, check results of **route -n** to see if the gateway is your router (or modem, or whatever connects you to network).
It might also be good to check contents of /etc/resolv.conf to see if DNS service has changed.  I'm somewhat suspicious that NM keeps this information elsewhere - but I haven't discovered secret hiding place yet...

---

### Post by tad1073 on 2009-05-13
> **Iowan said:**
> When you lose connectivity, can you ping via IP address? Also, check results of **route -n** to see if the gateway is your router (or modem, or whatever connects you to network).
It might also be good to check contents of /etc/resolv.conf to see if DNS service has changed. I'm somewhat suspicious that NM keeps this information elsewhere - but I haven't discovered secret hiding place yet...

I only gained limited connectivity one time and after that nothing. I was getting an error that /etc/resolve.conf doesn't exist.

---

### Post by tad1073 on 2009-05-13
```
thomas@tad:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
thomas@tad:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"thompson"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

thomas@tad:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:F3:60:B8
                    ESSID:"Wade"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=14/100  Signal level:-89 dBm  Noise level=-98 dBm
                    Encryption key:on
                    IE: Unknown: 000457616465
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000018926df3a
                    Extra: Last beacon: 356ms ago
          Cell 02 - Address: 00:1A:70:6B:A7:98
                    ESSID:"Beach"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=15/100  Signal level:-88 dBm  Noise level=-98 dBm
                    Encryption key:on
                    IE: Unknown: 00054265616368
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020015000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000af334564189
                    Extra: Last beacon: 100ms ago
          Cell 03 - Address: removed by poster
                    ESSID:"thompson"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/100  Signal level:-83 dBm  Noise level=-98 dBm
                    Encryption key:on
                    IE: Unknown: 000874686F6D70736F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1606051300000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A00011010440001021041000100103B00010310470010475F282D18EEFDBC3646F17B6B7ADA24102100074C696E6B737973102300075752543136304E102400063132333435361042000234321054000800060050F2040001101100075752543136304E100800020084
                    IE: Unknown: DD090010180200F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406051300000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000d21944d17
                    Extra: Last beacon: 376ms ago
          Cell 04 - Address: 00:1A:70:57:89:67
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=9/100  Signal level:-92 dBm  Noise level=-98 dBm
                    Encryption key:off
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F5000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000074983e188
                    Extra: Last beacon: 388ms ago

pan0      Interface doesn't support scanning.

thomas@tad:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1f:e2:01:ea:2d
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.9-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@removed by poster
       logical name: wmaster0
       version: 01
       serial: removed bu poster
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: removed by poster
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

end

```

---

### Post by tad1073 on 2009-05-13
more info
```
thomas@tad:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver madwifi
wpa-ssid thompson
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk removed by poster
thomas@tad:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
thomas@tad:~$ sudo ifdown -v wlan0
ifdown: interface wlan0 not configured
thomas@tad:~$ sudo ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/dhclient3-apparmor
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver madwifi
wpa_supplicant: "madwifi" wpa-driver is unsupported
wpa_supplicant: using "wext" wpa-driver instead ...
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -q -s -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: creating sendsigs omission pidfile: /lib/init/rw/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "thompson" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise CCMP -- OK
wpa_supplicant: wpa-group CCMP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto RSN -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/removed by poster
Sending on   LPF/wlan0/removed by poster
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant

```

---

### Post by tad1073 on 2009-05-14
bump

---

### Post by Iowan on 2009-05-14
> **tad1073 said:**
> I was getting an error that /etc/resolve.conf doesn't exist.It doesn't... it's /etc/resolv.conf - without the final "e".

---

### Post by tad1073 on 2009-05-14
contents of resolv.conf
```
#Generated by Network Manager
```

---

### Post by tad1073 on 2009-05-15
bump

---

### Post by tad1073 on 2009-05-16
bump

---

### Post by tad1073 on 2009-05-18
Ugraded to 9.10 alpha 1 and wireless worked right off the bat.

---

