---
title: "Belkin F7D2101 V1 not detected"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by ahcup4 on 2013-05-23
Hi guys im very new to this forum, Ive been reading and searching solutions about my problem for days. Please help me, Im using VMware to run backtrack 5 R3, and it doesn't detect my belkin adapter!! [PHP]root@bt:~# iwconfig
lo        no wireless extensions.
eth2      no wireless extensions.
wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Auto  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/PHP]    > irmon-ng

Interface Chipset  Driver

 


---

### Post by ahcup4 on 2013-05-23
> root@bt:~# iwconfig
lo        no wireless extensions.
eth2      no wireless extensions.
wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Auto  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
root@bt:~# ifcondig
No command 'ifcondig' found, did you mean:
 Command 'ifconfig' from package 'net-tools' (main)
ifcondig: command not found
root@bt:~# root@bt:~# lspci | grep -i network
root@bt:~#: command not found
root@bt:~# airmon-ng

Interface Chipset  Driver

root@bt:~# ^C
root@bt:~# lsusb
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:845a Belkin Components F7D2101 802.11n Surf & Share Wireless Adapter v1000 [Realtek RTL8192SU]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@bt:~# airmon-ng start wlan0 

Found 2 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
PID Name
1316 dhclient3
2235 dhclient3

Interface Chipset  Driver

root@bt:~# sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth2
       version: 10
       serial: 00:0c:29:b9:c1:d9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical logical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.35 ip=192.168.217.128 latency=64 link=yes maxlatency=255 mingnt=6 multicast=yes
       resources: irq:19 ioport:2000(size=128) memory:d8400000-d840ffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1
       logical name: wlan0
       serial: 94:44:52:61:cc:e2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated
root@bt:~# rfkill list all
0: hci0: Bluetooth
 Soft blocked: no
 Hard blocked: no
root@bt:~# 

 please see my stats and help me with it ): I also tired [http://ubuntuforums.org/showthread.php?t=1509403&highlight=F7D2101+V1](http://ubuntuforums.org/showthread.php?t=1509403&highlight=F7D2101+V1) but it also don't work for me ):

---

### Post by ahcup4 on 2013-05-23
help please );

---

### Post by skatinjj on 2013-05-24
You can just bridge the network connection or configure NAT for your VM.


[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=760]("http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=760")

[http://www.vmware.com/support/ws4/doc/network_bridged_ws.html]("http://www.vmware.com/support/ws4/doc/network_bridged_ws.html")

---

### Post by ahcup4 on 2013-05-25
> **skatinjj said:**
> You can just bridge the network connection or configure NAT for your VM.


[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=760](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=760)

[http://www.vmware.com/support/ws4/doc/network_bridged_ws.html](http://www.vmware.com/support/ws4/doc/network_bridged_ws.html)

I've read it, if I am not wrong. Briding of network connection helps you to access to internet in VM. But my problem is my VM cannot detect my USB wireless adaptor , I can surf internet using my own IP address ;/ correct me if im wrong, I not really good at this ): please help. I want my backtrack 5 in VM able to use my USB adaptor, so that it can scan networks ):

---

### Post by ahcup4 on 2013-05-29
help please guys~~!!

---

### Post by ahcup4 on 2013-05-30
upppppppppppppppppppppppp

---

