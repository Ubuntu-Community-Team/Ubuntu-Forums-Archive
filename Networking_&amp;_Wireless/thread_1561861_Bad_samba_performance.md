---
title: "Bad samba performance"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by ubit on 2010-08-26
Hi,

i build a small homeserver with ubuntu 10.04.1 server edition today. After installing the base packets i installed samba too because the system should serve mainly as a file server.

I than run atto diskbench from a windows machine against the samba installation. I got write performance of around 40 MByte/sec peak - what is in the range i expected. But read performance is very bad. Only arount 8-8,5 MByte/sec.

I than tried iperf -s on the windows and iperf -c on the ubuntu system and got only 70 MBit/sec. With iperf -s on ubuntu and iperf -c on windows i got 130 MBit/sec.

I think something is wrong with the networking and/or samba configuration.

Here is what ethtool gave me:
[FONT="System"][INDENT]sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Full
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes[/INDENT][/FONT]

Everything looks like gigabit-Ethernet full duplex for me.

ifconfig gave me:
[FONT="System"][INDENT]sudo ifconfig eth0
eth0      Link encap:Ethernet  Hardware Adresse xx:xx:xx:xx:xx:xx
          inet Adresse:192.168.0.22  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6-Adresse: fe80::4261:86ff:fe85:6b29/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:1617935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1292200 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:2110913745 (2.1 GB)  TX bytes:1322338494 (1.3 GB)
          Interrupt:26 Basisadresse:0x2000[/INDENT][/FONT]

In smb.conf i only activated wins and included a share:

[FONT="System"][INDENT]
[data]
        comment = Zentraler Datenspeicher
        read only = no
        locking = yes
        path = /srv/data
        create mask = 0700
        guest ok = yes
        guest only = yes
[/INDENT][/FONT]

Just for the first tests without any user management within samba.

I do not understand why networking/samba is so slow. Anyone with an idea out there? The system is based on a mainboard MSI 785GM-E51 with an Athlon II X2 245 CPU and 2 Samsung hd154ui disks configured as a software raid 1.

Ciao, Udo

---

### Post by ubit on 2010-08-26
Update...

The bad performance i have only from a pc with vista x64. Another pc using windows xp does write and read both with good performance. Seems to be a problem of vista... 

Nevertheless: Anyone out there with a tipp?

Ciao, Udo

---

### Post by elico on 2010-08-26
what is the read speed?
you can use DOWNTESTER to check the speed.

i had a problem downloading from my ubuntu samba server and it was because of the VIRTUALBOX interface on one machine and on the other machine it was microsoft nic driver.
so i downloaded nvidia drivers and it works fantastic now.

---

### Post by ubit on 2010-08-26
Virtual box is an idea... I have virtual box installed on the vista pc and use bridged mode. I will try to disable this.

Ciao, Udo

---

### Post by ubit on 2010-08-26
Yes. That was the problem :-( Bad news... I need the virtual box bridge drivers to connect my virtual machines to the internet. 

Ciao, Udo

---

