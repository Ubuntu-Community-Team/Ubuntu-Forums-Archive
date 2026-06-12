---
title: "Keep loosing network connection"
date: 2005-12-29
forum: Networking &amp; Wireless
---

### Post by jbo on 2005-12-29
Hello,
My system is loosing it's internet connection every once in a while.

I have to issue the command
/etc/init.d/networking restart

to get it going again. Could this be a DHCP oriented problem? (I have an dynamic ip adress).
Is there something I should check to make sure all things are set up ok?

---

### Post by djgenesis on 2005-12-29
Are you wired or wireless?

---

### Post by jbo on 2005-12-30
I have a wired network,
so my setup would be something like this:

System -> NIC -> Wire -> ADSL-Modem -> ISP -> Internet 

Also problem seems to worsen when my connection is inactive,
but will happen regardless eventually. Maybe i should get syslogs?

---

### Post by djgenesis on 2005-12-30
Are you using a router to connect ? I don't know for sure but i would assume you could try  and let the DHCP-Server give a longer leasetime or switch to static. When you lose internet connectivity is the DSLmodem up and running normally? Have you tried another PC on the same modem with dynamic address?

---

### Post by jbo on 2005-12-31
I am not useing a router. But I have an old D-link 604, if you think connecting it, can help. 

I have used two other computers, a laptop with Windows XP, to the extent of my memory, I didn't expirence this problem with the laptop, but I am very unsure. The second was my old desktopcomputer which did have the same problem. 
I have tired to change the ADSL modem, but this did not help. But atleast I have got a new modem.. :P Otherwise the modem seems ok when it looses connection, apart from that the send and recive lights stops flickering, but I guess that his is due to the nature of the problem. I have had this problem quite a while.

Do you think it can be power management, maybe the card is being put to sleep?

---

### Post by djgenesis on 2005-12-31
Since you tried an other PC on the same modem and it worked fine, apparently the problem resides on your ubuntu desktop. 
Also the DHCP lease time is issued by your ISP so there is not much you can do about it. 
Even if you connect the router, it won't make any difference since there might be an issue with your linux box. Try playing with the diagnostics and see if you have something different than this: #




```

genesis@ubuntuj:~$ sudo ethtool eth1
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes

```

Also when your network goes down try:

```

genesis@ubuntuj:/var/run$ sudo mii-diag eth1
```
And see if you get anything else than this.

```


Basic registers of MII PHY #32:  1000 782d 0000 0000 01e1 40a1 0001 0000.
 The autonegotiated capability is 00a0.
The autonegotiated media type is 100baseTx.
 Basic mode control register 0x1000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
 Your link partner advertised 40a1: 100baseTx 10baseT.
   End of basic transceiver information.

```


I wish i could help about power management on Ubuntu but unfortunatelly i am not familiar with the options or where it resides.

Try the suggestions above and let us know.
Genxx

---

### Post by jbo on 2006-01-01
```
sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000001 (1)
        Link detected: yes
```

Normal status

```
sudo mii-diag eth0
Basic registers of MII PHY #1:  3100 786d 0101 8f2a 05e1 41e1 0007 2801.
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x3100: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
 Your link partner advertised 41e1: 100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   End of basic transceiver information.
```

Interrupted status

```
sudo mii-diag eth0
Password:
Basic registers of MII PHY #1:  3100 786d 0101 8f2a 05e1 41e1 0005 2801.
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x3100: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
 Your link partner advertised 41e1: 100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   End of basic transceiver information.
```

Seem pretty similar to me? The connection actually came alive after I issued
the 'sudo mii-diag eth0' & 'sudo ethtool eth0' without have to do the normal
'sudo /etc/inet.d/networking restart' go figure

I find these entries in my syslog, process is dhclient, could they play a part?

```
can't create /var/run/dhclient.eth0.leases: Permission denied
```

---

### Post by jbo on 2006-01-01
...

---

### Post by jbo on 2006-01-01
Sorry for the multiple post. My network was didnt react at first so I tried again, and when the posting succeded, there where three of them. Can't find the function for deleting the extra ones

---

### Post by qferret on 2006-01-01
Bug reported & supposedly fixed.

patch available here.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=20553](https://bugzilla.ubuntu.com/show_bug.cgi?id=20553)

---

### Post by jbo on 2006-01-01
Hmm, I am not sure what to do, since i haven't got any experience with patches in ubuntu, you just run them? Have you tried this? That page mentions version dhcp3 (3.0.3-5ubuntu3) dapper, in synaptic I have 3.0.2-1ubuntu6?

---

### Post by qferret on 2006-01-01
hmmm....the page mentions that it was fixed in the newer version. Maybe simply adding the dapper repos in Synaptic and upgrading the package would fix it?

Otherwise, in a terminal, CD into the directory that has the file that needs to be patched and issue "patch -p0 < [patch-file-name]" to apply the patch you downloaded.

---

### Post by jbo on 2006-01-02
Did a dist-upgrade to ubuntu dapper, and now I have all sorts of problems :P lost network all together, alot of reboots, and 'apt-get -f install's later I almost have kde running, but currently kdm hangs.. Atleast there´s progress.. :P

---

