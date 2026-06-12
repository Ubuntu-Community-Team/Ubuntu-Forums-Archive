---
title: "ipw2200 can connect but can't handle packets"
date: 2005-12-18
forum: Networking &amp; Wireless
---

### Post by yvovandoorn on 2005-12-18
I can't get my intel 2200b/g card to work, no matter what I try.

I installed a fresh copy of Ubuntu 5.10 and upgraded immediately to kernel 2.6.12-10 and such.

I then followed the instructions here: [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623) (with further instructions on page 49 for the newer drivers)
So this is what I have installed: the latest driver (1.0.6 -> 1.0.8), latest firmware (2.3 -> 2.4) and latest ieee80211 subsystem (1.0.3 (i think) -> 1.1.6).

I restarted my laptop and once back it gets detected fine. I can setup and I even get an IP from my Linksys WRT54G. 

So this is where the mystery starts. I can ping my router (192.168.1.1), my imac (192.168.1.102), my windows pc (192.168.1.103) and my jetdirect (192.168.1.110). However any IP outside the 192.x.x.x it just can't ping or reach. All packets are lost. Same goes for host names (of course). 

I get no errors in any logs located in the /var/log directory. 

So far I have only tried enabling hwcrypo=0 in the ipw2200 located in the /etc/modprobe.d directory. 

The wifi network is currently unsecured, no WEP nor WPA. When I boot into Windows the wifi card works fine (with DHCP as well). 

More information:
HP zt3000 with latest bios
Ubuntu 5.10
Kernel 2.6.12-10 
ipw2200 driver 1.0.8
ipw  firmware 2.4
ieee80211 subsystem 1.1.6
Router is a Linksys WRT54g with 4.20.6 firmware, currently unsecured.

---

### Post by yvovandoorn on 2005-12-18
Here is the output of my iwconfig & ifconfig.

Also it seems to finally connect after a very long period of time (like a burst, about 60-70 seconds)

```

yvo@ubuntulappie:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"yvoandcam"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:41:51:E0
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-33 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1

sit0      no wireless extensions.

yvo@ubuntulappie:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:0E:35:A4:50:9B
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fea4:509b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:110702 (108.1 KiB)  TX bytes:7588 (7.4 KiB)
          Interrupt:5 Base address:0xe000 Memory:90000000-90000fff

```

---

### Post by TwistedAnimator on 2005-12-18
Sounds like a DNS problem. If you are assigning a static IP address to the computer that cannot ping, then you need to add the DNS servers to your /etc/resolv.conf manually. If you are assigning the IP using DHCP, the DNS addresses should be set up properly when the computer gets an IP. 

Manually assigning DNS servers can be a hassle on a laptop. This is because once you take it to a different network, different DNS servers are needed. You should look into the programs guessnet and resolvconf.

---

### Post by Lambert on 2005-12-18
What's the output of 

```
route
```

---

### Post by yvovandoorn on 2005-12-23
sorry for the non reply. 

well i figured out what it was. if i disable my wired card in the config settings it works fine even though the default is set to the wifi card in network-config, it wont work until I complete disable the wired ethernet port.

Seems to work jolly and actually better then Windows.

---

