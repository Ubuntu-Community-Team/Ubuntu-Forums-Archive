---
title: "r8168 network card incredible slow after kernel update to 3.2.0-43-generic"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by futo on 2013-05-19
I have a RealTek r8168 network card on a laptop. Each time the kernel updates I install the driver again. This procedure always worked until this kernel upgrade. This time the wired network speed is incredible slow after installing the driver. Wireless runs perfect.

I've tested the wired connection by excluding any hardware except for the router and the laptop. Another laptop, also running 12.04 and also updated with the new kernel, doesn't have any problems with the speed.

Speed should be 10.000/1.000 - but is only 150/300 Mbps

ipv6 is disabled.

Any suggestions?...

(Trained linux user)

---

### Post by praseodym on 2013-05-19
Which driver version do you use? Please try this one (the latest "35") with dkms:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

---

### Post by futo on 2013-05-19
Thx praseodym,

Yes, have the r8168-8.035.00-driver. Just re-downloaded from RealTek and reinstalled before I posted the first time. The same driver as before.

Why dkms?...

I'm using the driver from RealTek: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

Any problems with that?...

So far I'm installing the driver I had with help from this link: [http://askubuntu.com/questions/46942/how-do-i-stop-my-ethernet-network-connection-from-dropping](http://askubuntu.com/questions/46942/how-do-i-stop-my-ethernet-network-connection-from-dropping)
- Where the procedure is:

> 
<Remove the wrong driver>
# rmmod r8169  

<Quick install with proper kernel settings> 
Unpack the tarball : # tar vjxf r8168-8.aaa.bb.tar.bz2 

Change to the directory: # 
cd r8168-8.aaa.bb 

If you are running the target kernel, then you should be able to do : 
# ./autorun.sh (as root or with sudo) 

You can check whether the driver is loaded by using following commands. 
# lsmod | grep r8168 
# ifconfig -a 

If there is a device name, ethX, shown on the monitor, the linux driver is loaded. Then, you can use the following command to activate the ethX. 

# ifconfig ethX up

I'm just unsure about dkms is making any difference to my problem?... Except of not having to reinstall the driver manually each time the kernel is updated. :) (Thx for the tip!)

(PS: I know to read and write german - so I'm able to grasp what your link says)

ADDITION +22min: The ping is with wireless somewhere below 30ms - with wired network it is sometimes up around 500ms ...

---

### Post by praseodym on 2013-05-19
Please install ethtool and show:
```

sudo apt-get install ethtool
sudo ethtool eth0
```

---

### Post by futo on 2013-05-19
```

sudo ethtool eth2

Settings for eth2:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes


```

---

### Post by futo on 2013-05-19
```

ifconfig

eth2      Link encap:Ethernet  HWaddr 10:7f:00:44:bc:c6  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::127f:ff:fe44:bcc6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17949 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11994029 (11.9 MB)  TX bytes:3360286 (3.3 MB)
          Interrupt:45 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:379621 (379.6 KB)  TX bytes:379621 (379.6 KB)

wlan0     Link encap:Ethernet  HWaddr 0c:d2:92:04:9f:93  
          inet6 addr: fe80::ed2:92ff:fe04:9f93/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21120 (21.1 KB)  TX bytes:14678 (14.6 KB)


```

---

### Post by futo on 2013-05-19
```

curl -w "@curl-timing.cfg" -o /dev/null -s http://www.bt.dk/

      DNS lookup                          :  1,236
      Connect to server (TCP)             :  1,576
      Connect to server (HTTP/S)          :  0,000
      Time from start until transfer began:  1,576
      Time for redirection (if any)       :  0,000
      Total time before transfer started  :  2,201

             Total time                   :  18,576
             Size of download (bytes)     :  227481
             Average d/l speed (bytes/s)  :  12245,000


curl -w "@curl-timing.cfg" -o /dev/null -s http://www.flickr.com/

      DNS lookup                          :  1,281
      Connect to server (TCP)             :  1,433
      Connect to server (HTTP/S)          :  0,000
      Time from start until transfer began:  1,433
      Time for redirection (if any)       :  0,000
      Total time before transfer started  :  1,889

             Total time                   :  5,433
             Size of download (bytes)     :  141067
             Average d/l speed (bytes/s)  :  25966,000


curl -w "@curl-timing.cfg" -o /dev/null -s http://www.flickr.com/photos/piazta/8406763908/?f=hp

      DNS lookup                          :  0,795
      Connect to server (TCP)             :  0,851
      Connect to server (HTTP/S)          :  0,000
      Time from start until transfer began:  0,851
      Time for redirection (if any)       :  0,000
      Total time before transfer started  :  4,959

             Total time                   :  34,919
             Size of download (bytes)     :  668495
             Average d/l speed (bytes/s)  :  19144,000


```

- Created from instructions on this page: [http://askubuntu.com/questions/147377/how-to-debug-slow-browsing-speed](http://askubuntu.com/questions/147377/how-to-debug-slow-browsing-speed)

---

### Post by futo on 2013-05-19
```

sudo lspci | grep RTL

03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)



lsmod | grep r8168 

r8168                 248895  0 

```

---

### Post by futo on 2013-05-19
Maybe a NP-Complete problem?... ;) ... I'm most afraid that the driver or the kernel has to be rewritten 8-[ ...

---

### Post by praseodym on 2013-05-19
Try to deactivate the auto-negotiation:
```

sudo ethtool -s eth2 speed 1000 autoneg off
```

---

### Post by futo on 2013-05-19
I tried it now - but it will not switch to off.

Searched for an answer to that and found this; Saying not to turn autoneg off - and they give a reason why:
[http://www.unix.com/unix-dummies-questions-answers/174797-not-able-turn-off-auto-negotiation-gigabite-interface.html](http://www.unix.com/unix-dummies-questions-answers/174797-not-able-turn-off-auto-negotiation-gigabite-interface.html)

> 
.... Speed, Duplex, and MASTER/SLAVE configuration during 1000BASE-T operation,  are determined through the Auto-Negotiation process. Clause 40.5.1 states:  &#8220;All 1000BASE-T PHYs shall provide support for Auto-Negotiation (Clause 28) and  shall be capable of operating as MASTER or SLAVE. Auto-Negotiation is performed  as part of the initial set-up of the link, and allows the PHYs at each end to advertise  their capabilities (speed, PHY type, half or full duplex) and to automatically select  the operating mode for communication on the link. Auto-negotiation signaling is  used for the following two primary purposes for 1000BASE-T:  a) To negotiate that the PHY is capable of supporting 1000BASE-T half duplex  or full duplex transmission. b) To determine the MASTER-SLAVE relationship between the PHYs at each  end of the link.  This relationship is necessary for establishing the timing control of each PHY.  The 1000BASE-T MASTER PHY is clocked from a local source. The SLAVE  PHY uses loop timing where the clock is recovered from the received data  stream.

I'll stop search for a solution for today. - Have some work to do. Will come back tomorrow.

Thx 4 now! :)

---

### Post by mobo on 2013-06-07
> **futo said:**
> I tried it now - but it will not switch to off.

Searched for an answer to that and found this; Saying not to turn autoneg off - and they give a reason why:
[http://www.unix.com/unix-dummies-questions-answers/174797-not-able-turn-off-auto-negotiation-gigabite-interface.html](http://www.unix.com/unix-dummies-questions-answers/174797-not-able-turn-off-auto-negotiation-gigabite-interface.html)



I'll stop search for a solution for today. - Have some work to do. Will come back tomorrow.

Thx 4 now! :)

Just wondering if you resolved this issue..I'm having the same issue with the same card..

---

