---
title: "Intermittent wireless (Atheros) connection on Vaio running 9.04"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by ZeroCool69 on 2009-04-26
Hello community, I'm a bit new so please bare with me.

Running a Sony Vaio VGN-FW140D dual-boot with Jaunty 9.04 and Vista.

My wireless issue is this. I can connect but only at limited speeds; my wlan0 connection information shows a speed of 1 Mb/s. Though when I'm wired I have a rate of 100 Mb/s. When connected online wirelessly, I'll do a packet test at speedtest.net and see my full true bandwidth (what it should be) only to see the test hang up and my connection drop. I'm able to click my wireless network and reacquire a connection, but again, limited. If I am indeed connecting at high speed why does the connection info read 1 Mb/s? Furthermore, why will the connection drop? I've read threads referring to madwifi and other fixes, but this seemed to be for those not being able to connect at all.

If anyone can shed some light, I would greatly appreciate it.

[lspci]
```
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```[iwconfig wlan0]
```
wlan0     IEEE 802.11bgn  ESSID:"XXXXXX" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: XX XX XX XX XX XX  
          Bit Rate=1 Mb/s   Tx-Power=20 dBm  
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B  
          Power Management:off
          Link Quality=92/100  Signal level:-61 dBm  Noise level=-120 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```[lsmod]
```
ath9k                 263224  0
```[sudo lshw -C network]
```
*-network              
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: XXXXXXXXX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=XXXXXXXX latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by WakkiTabakki on 2009-04-27
When your connection drops, bring up a terminal and type:
```
dmesg | grep -i wlan
```
And post the result, it may provide some clue as to what causes the dropouts...
BTW, you'll want to check that there is no sensitive stuff before posting it :p

/N

---

### Post by dooma on 2009-04-28
HI -

I think I might be having the same problem. I have a Lenovo T60P which with AR5418 card. In Intrepid, wireless worked great. Upgraded to Jaunty and wireless performance has been very poor:

1) At high bandwidth usage, wireless will disconnect, but WICD (and n-m -I tried both) will show the network is still connected. But there is no connection. I must press refresh on wicd and manually recconect. This is annoying

2) After prolonged usage (about an hour) the wireless will just disconnect all together. The only way to reconnect at this point is to restart the computer

I am running Ath9k.

I don't think these things are connected, but figure I should note that I also have an ATI card (Fire GL 5250) and for osme reason whenever the wireless breaks, I get some message about x-session-manager in the daemon log (looking at the log viewer under preferences).

None of these problems were present in intrepid, so I'd love to see the wifi working for me again.

---

### Post by rajamouli2000 on 2009-04-28
I have a similar problem. I have ubuntu 9.04 installed on Toshiba Pro M300 satellite laptop. I have dual boot with Vista. I connect to a Linksys-WRT54G router. My wireless connection stops working even though my connection notifier shows connection is active. I have to switch off and switch on my wireless switch on my laptop, for it to connect again. Even this stops working in a while. This affects all applications that need Internet connectivity (firefox, apt-get, etc. ).

Relevant section of Lspci command is 

```
7:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c (rev 16)
08:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```

---

### Post by rajamouli2000 on 2009-04-28
The post by Anton Khokhlov [here]("https://answers.launchpad.net/ubuntu/+question/16768") might be helpful. A lot of people seem to have solved the problem by updating the microcode images. Testimonies can be found [here]("http://ubuntuforums.org/showthread.php?t=695756")

My connection has been up for 20 mins now.

---

### Post by ktechman on 2009-04-28
Try compat wireless it works with the ath9k driver in Intrepid I believe it is broken in Jaunty 

[http://ubuntuforums.org/showpost.php?p=5535562&postcount=3]("http://ubuntuforums.org/showpost.php?p=5535562&postcount=3")

Regards Ktechman

---

### Post by jcat1 on 2009-05-01
bump...

---

### Post by Jguy on 2009-10-19
I'm having a similar problem. 

Here is the output of dmesg | grep -i wlan when the connection drops:

```
jguy@jguy-laptop:~$ dmesg | grep -i wlan
[   24.928794] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.645004] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   30.844067] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   31.044064] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   31.244064] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[   43.692231] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   43.700948] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   43.900065] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   44.100065] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   44.300069] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[   56.504273] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   56.513019] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   56.712062] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   56.912062] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   57.112061] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[   69.564328] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   69.573076] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   69.772076] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   69.973784] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   70.172066] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[   82.444403] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   82.454046] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   82.652039] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   82.856069] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   83.056089] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[   91.512341] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   91.521486] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   91.720079] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   91.920070] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[   92.120077] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[  104.584311] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  104.593938] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  104.792035] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  104.992031] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  105.192057] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[  117.648345] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  117.657530] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  117.856077] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  118.056077] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  118.256039] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[  128.504346] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  128.513502] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  128.712091] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  128.912077] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  129.112076] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[  141.592427] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  141.600690] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  141.800110] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  142.000099] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  142.200106] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[  151.520362] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  151.528598] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  151.724073] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  151.924078] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  152.124030] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[  164.592325] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  164.601571] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  164.800073] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  165.000098] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  165.200074] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[  177.664306] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  177.672562] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  177.868039] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  178.068070] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  178.268075] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[  190.736327] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  190.745140] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  190.948334] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  191.148203] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  191.348063] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[  203.572409] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  203.581581] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  203.780062] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  203.980088] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  204.180095] wlan0: authentication with AP 00:1c:f0:53:71:ab timed out
[  211.508644] wlan0: authenticate with AP 00:1c:f0:53:71:ab
[  211.510032] wlan0: authenticated
[  211.510038] wlan0: associate with AP 00:1c:f0:53:71:ab
[  211.512587] wlan0: RX AssocResp from 00:1c:f0:53:71:ab (capab=0x431 status=0 aid=3)
[  211.512593] wlan0: associated
[  211.524923] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  221.548019] wlan0: no IPv6 routers present
jguy@jguy-laptop:~$ 

```

And the output of lspci | grep -i wireless

```
jguy@jguy-laptop:~$ lspci | grep -i wireless
07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
jguy@jguy-laptop:~$ 

```

Every 2 or so minutes, my wireless will drop out on this laptop, a HP G60-120US. Running: 

```
jguy@jguy-laptop:~$ uname -a
Linux jguy-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux
jguy@jguy-laptop:~$ 
```

Ubuntu 9.04.

But what's weird is the output of ifconfig doesn't show any errors:

```
wlan0     Link encap:Ethernet  HWaddr 00:24:2b:c3:a2:cd  
          inet addr:192.168.0.127  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fec3:a2cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20328654 (20.3 MB)  TX bytes:14235048 (14.2 MB)

```

sorry to bump this old thread, but I would really like some advice. thanks.

---

### Post by tracyyep on 2009-10-27
To all Jaunty users with Atheros wireless problem.
I have this same problem , I have a HP G60, with Atheros wireless card.
It works very poor. Connection is intermittent, and then disconnect.
My solution is , I bought a USB netgear wireless
**[SIZE=4]NETGEAR WG111 v3 IEEE 802.11b/g USB 2.0[/SIZE]**

Plug it in and it works. You need to disable the Atheros for this to take precedence and works.
:)
Cheers.....
[IMG]file:///tmp/moz-screenshot.jpg[/IMG]
> **dooma said:**
> HI -

I think I might be having the same problem. I have a Lenovo T60P which with AR5418 card. In Intrepid, wireless worked great. Upgraded to Jaunty and wireless performance has been very poor:

1) At high bandwidth usage, wireless will disconnect, but WICD (and n-m -I tried both) will show the network is still connected. But there is no connection. I must press refresh on wicd and manually recconect. This is annoying

2) After prolonged usage (about an hour) the wireless will just disconnect all together. The only way to reconnect at this point is to restart the computer

I am running Ath9k.

I don't think these things are connected, but figure I should note that I also have an ATI card (Fire GL 5250) and for osme reason whenever the wireless breaks, I get some message about x-session-manager in the daemon log (looking at the log viewer under preferences).

None of these problems were present in intrepid, so I'd love to see the wifi working for me again.

---

### Post by tracyyep on 2009-10-27
To all Jaunty users with Atheros wireless problem.
I have this same problem , I have a HP G60, with Atheros wireless card.
It works very poor. Connection is intermittent, and then disconnect.
My solution is , I bought a USB netgear wireless
**[SIZE=4]NETGEAR WG111 v3 IEEE 802.11b/g USB 2.0[/SIZE]**

Plug it in and it works. You need to disable the Atheros for this to take precedence and works.
:smile:
Cheers.....


> **ZeroCool69 said:**
> Hello community, I'm a bit new so please bare with me.

Running a Sony Vaio VGN-FW140D dual-boot with Jaunty 9.04 and Vista.

My wireless issue is this. I can connect but only at limited speeds; my wlan0 connection information shows a speed of 1 Mb/s. Though when I'm wired I have a rate of 100 Mb/s. When connected online wirelessly, I'll do a packet test at speedtest.net and see my full true bandwidth (what it should be) only to see the test hang up and my connection drop. I'm able to click my wireless network and reacquire a connection, but again, limited. If I am indeed connecting at high speed why does the connection info read 1 Mb/s? Furthermore, why will the connection drop? I've read threads referring to madwifi and other fixes, but this seemed to be for those not being able to connect at all.

If anyone can shed some light, I would greatly appreciate it.

[lspci]
```
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```[iwconfig wlan0]
```
wlan0     IEEE 802.11bgn  ESSID:"XXXXXX" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: XX XX XX XX XX XX  
          Bit Rate=1 Mb/s   Tx-Power=20 dBm  
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B  
          Power Management:off
          Link Quality=92/100  Signal level:-61 dBm  Noise level=-120 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```[lsmod]
```
ath9k                 263224  0
```[sudo lshw -C network]
```
*-network              
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: XXXXXXXXX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=XXXXXXXX latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by tracyyep on 2009-10-27
> **ZeroCool69 said:**
> Hello community, I'm a bit new so please bare with me.

Running a Sony Vaio VGN-FW140D dual-boot with Jaunty 9.04 and Vista.

My wireless issue is this. I can connect but only at limited speeds; my wlan0 connection information shows a speed of 1 Mb/s. Though when I'm wired I have a rate of 100 Mb/s. When connected online wirelessly, I'll do a packet test at speedtest.net and see my full true bandwidth (what it should be) only to see the test hang up and my connection drop. I'm able to click my wireless network and reacquire a connection, but again, limited. If I am indeed connecting at high speed why does the connection info read 1 Mb/s? Furthermore, why will the connection drop? I've read threads referring to madwifi and other fixes, but this seemed to be for those not being able to connect at all.

If anyone can shed some light, I would greatly appreciate it.

[lspci]
```
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```[iwconfig wlan0]
```
wlan0     IEEE 802.11bgn  ESSID:"XXXXXX" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: XX XX XX XX XX XX  
          Bit Rate=1 Mb/s   Tx-Power=20 dBm  
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B  
          Power Management:off
          Link Quality=92/100  Signal level:-61 dBm  Noise level=-120 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```[lsmod]
```
ath9k                 263224  0
```[sudo lshw -C network]
```
*-network              
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: XXXXXXXXX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=XXXXXXXX latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
```
To all Jaunty users with Atheros wireless problem.
I have this same problem , I have a HP G60, with Atheros wireless card.
It works very poor. Connection is intermittent, and then disconnect.
My solution is , I bought a USB netgear wireless
**[SIZE=4]NETGEAR WG111 v3 IEEE 802.11b/g USB 2.0[/SIZE]**

Plug it in and it works. You need to disable the Atheros for this to take precedence and works.
:smile:
Cheers.....

---

