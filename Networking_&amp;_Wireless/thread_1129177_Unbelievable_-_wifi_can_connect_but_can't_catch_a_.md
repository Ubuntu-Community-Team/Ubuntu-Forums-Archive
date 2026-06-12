---
title: "Unbelievable - wifi can connect but can't catch a single packet"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by tasuki on 2009-04-18
Hello good people. Sorry for the sensationalist title, but I needed to grab your attention. :P

I have a Thinkpad R61 with the following wireless card:
```
*-network
 description: Wireless interface
 product: AR5008 Wireless Network Adapter
 vendor: Atheros Communications Inc.
 physical id: 0
 bus info: pci@0000:03:00.0
 logical name: wifi0
 version: 01
 serial: 00:1c:26:15:85:7e
 width: 64 bits
 clock: 33MHz
 capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
 configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

I tried all the various drivers (ath9k, ath5k, madwifi, ndiswrapper) with similar results - I can see the networks, and with madwifi (ath_pci) I can even connect to them. I am currently using madwifi from the trunk.

```
root@gandalf:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"knury"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:60:B3:65:08:A2   
          Bit Rate:1 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=40/70  Signal level=-56 dBm  Noise level=-96 dBm
          Rx invalid nwid:1107  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Yep, I am connected, also wavemon shows nice green bars.

```
root@gandalf:~$ ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:1c:26:15:85:7e  
          inet6 addr: fe80::21c:26ff:fe15:857e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@gandalf:~$ ifconfig wifi0
wifi0     Link encap:UNSPEC  HWaddr 00-1C-26-15-85-7E-E0-54-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13473 errors:0 dropped:1216 overruns:0 frame:17080
          TX packets:913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:823516 (823.5 KB)  TX bytes:39221 (39.2 KB)
          Interrupt:17

root@gandalf:~$ ifconfig wifi0
wifi0     Link encap:UNSPEC  HWaddr 00-1C-26-15-85-7E-E0-B4-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14177 errors:0 dropped:1216 overruns:0 frame:17100
          TX packets:971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:868837 (868.8 KB)  TX bytes:41685 (41.6 KB)
          Interrupt:17 

```

I'm not quite sure as to the distinction between ath0 and wifi0, but as you can see, the number of RX and TX packets on wifi0 keeps growing.

And now the problem: I can't communicate with anything, and can't even catch a single packet through tcpdump or wireshark.

```
root@gandalf:~$ tcpdump -i ath0
tcpdump: WARNING: ath0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on ath0, link-type EN10MB (Ethernet), capture size 96 bytes
^C
0 packets captured
0 packets received by filter
0 packets dropped by kernel
root@gandalf:~$ tcpdump -i wifi0
tcpdump: WARNING: wifi0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wifi0, link-type IEEE802_11 (802.11), capture size 96 bytes
^C
0 packets captured
0 packets received by filter
0 packets dropped by kernel

```

I can wait forever and nothing ever happens. Same in wireshark. And all this while the number of RX packets keeps on growing steadily.

```
root@gandalf:~$ ping -I ath0 192.168.1.1
PING 192.168.1.1 (192.168.1.1) from 192.168.1.42 ath0: 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 192.168.1.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1014ms

root@gandalf:~$ ping -I wifi0 192.168.1.1
PING 192.168.1.1 (192.168.1.1) from 192.168.1.42 wifi0: 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 192.168.1.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms
```

Also, I'm not quite sure why pinging is not permitted...

Could someone explain what's going on?
And what should I do to be able to use my wifi?
Or just point me in the right direction?

All answers are welcome, thank you for your time! :)

---

### Post by tasuki on 2009-04-19
I forgot to mention - I am running on 8.10 but I tried 9.04 and it behaves just the same.

---

### Post by superprash2003 on 2009-04-19
post output of **sudo dhclient ath0** . you arent getting an ipv4 address..

---

