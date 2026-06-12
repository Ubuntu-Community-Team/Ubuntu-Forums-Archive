---
title: "Iwp2200 help.."
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by Inglor on 2006-06-09
I have a laptop with Intel Wireless Pro 2200 b/g wifi card and my desktop pc has the Asus Wifi@home card running it as Soft-AP mode (software AP).

I had some probs first with the wireless couldn't connect so I followed the installation of iwp2200 from this usefull HOWTO: [http://www.ubuntuforums.org/showpost.php?p=130227p=423584]("http://www.ubuntuforums.org/showpost.php?p=130227p=423584")

My encryption is WEP

my iwconfig:
```
inglor@Selene:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"home"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0E:A6:7F:0D:4A
          Bit Rate=11 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-17 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13439   Missed beacon:98

sit0      no wireless extensions.
```

```
inglor@Selene:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:0E:A6:7F:0D:4A
                    ESSID:"home"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rate:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality=99/100  Signal level=-22 dBm
                    Extra: Last beacon: 3673ms ago
```

And my from /etc/network/interfaces 
```
iface eth1 inet static
        address 192.168.0.20
        netmask 255.255.255.0
        gateway 192.168.0.1
        wireless-essid home
        wireless-key s:*****
```

With all the above I can't connect to the wireless.. Ofc no firewall active when trying. :)

Also something ireletive i think but I would like to fix it.. When my eth0 and eth1 are both active by default pc chooses the default gateway device as eth1, which is currently not working :( 

Forgive my newbie questions..

---

### Post by Inglor on 2006-06-10
I figure out that I can't tell my laptop from which interface I connect to the Internet.

Is there a file in which I configure that?

edit:typo

---

### Post by Inglor on 2006-06-11
Last update is that I can connect to the network but i can't see any of the other pcs of the network or the router, and ofc no internet.. :S

---

### Post by Inglor on 2006-06-11
This is getting annoying.. I can connect to my wireless network without doing something special if I use the Live CD of ubuntu.
I even copy paste the /etc/network/interfaces from live cd.
Still not working.
](*,) 

```
inglor@Selene:/etc/init.d$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

```
This is what I get if I ping when eth0 is down and eth1 is up.
Any idea what it means?

---

### Post by Room101 on 2006-06-16
Have you disabled any firewall? i.e. stopping firestarter

---

### Post by Inglor on 2006-06-17
The discussion continues in [http://www.ubuntuforums.org/showthread.php?t=196657]("http://www.ubuntuforums.org/showthread.php?t=196657")
cause i have made two threads.. :S

sorry for trouble.

---

