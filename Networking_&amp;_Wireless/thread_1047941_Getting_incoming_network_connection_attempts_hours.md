---
title: "Getting incoming network connection attempts hours after Azureus is closed"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by mrpeenut24 on 2009-01-22
Hours after Azureus (Vuze) is closed, I'm still getting incoming connection attempts.  Netstat doesn't show it, but both my router's logs and wireshark do.  The following is a wireshark capture about 5 hours after I shut down azureus.  "oms" is the port that I'm running it on (4662) and it's forwarded to my computer.  You can see it's using TCP/UDP/ICMP, however, the TCP is the only one that seems to be able to be acknowledged.

```
No.     Time        Source                Destination           Protocol Info
      1 0.000000    76.101.124.129        192.168.1.102         TCP      writesrv > oms [SYN] Seq=0 Win=48180 Len=0 MSS=1452 WS=0
      2 0.000124    192.168.1.102         76.101.124.129        TCP      oms > writesrv [RST, ACK] Seq=1 Ack=1 Win=0 Len=0
      3 3.192542    76.101.124.129        192.168.1.102         TCP      writesrv > oms [SYN] Seq=0 Win=48180 Len=0 MSS=1452 WS=0
      4 3.192591    192.168.1.102         76.101.124.129        TCP      oms > writesrv [RST, ACK] Seq=1 Ack=1 Win=0 Len=0
      5 6.055616    76.101.124.129        192.168.1.102         TCP      writesrv > oms [SYN] Seq=0 Win=48180 Len=0 MSS=1452 WS=0
      6 6.055667    192.168.1.102         76.101.124.129        TCP      oms > writesrv [RST, ACK] Seq=1 Ack=1 Win=0 Len=0
      7 10.152410   76.101.124.129        192.168.1.102         TCP      eicon-x25 > oms [SYN] Seq=0 Win=48180 Len=0 MSS=1452 WS=0
      8 10.152464   192.168.1.102         76.101.124.129        TCP      oms > eicon-x25 [RST, ACK] Seq=1 Ack=1 Win=0 Len=0
      9 11.691533   76.101.124.129        192.168.1.102         TCP      eicon-x25 > oms [SYN] Seq=0 Win=48180 Len=0 MSS=1452 WS=0
     10 11.691586   192.168.1.102         76.101.124.129        TCP      oms > eicon-x25 [RST, ACK] Seq=1 Ack=1 Win=0 Len=0
     11 14.147625   76.101.124.129        192.168.1.102         TCP      eicon-x25 > oms [SYN] Seq=0 Win=48180 Len=0 MSS=1452 WS=0
     12 14.147679   192.168.1.102         76.101.124.129        TCP      oms > eicon-x25 [RST, ACK] Seq=1 Ack=1 Win=0 Len=0
     13 15.151152   HonHaiPr_4b:ed:ed     Cisco-Li_78:5a:a1     ARP      Who has 192.168.1.1?  Tell 192.168.1.102
     14 15.154268   Cisco-Li_78:5a:a1     HonHaiPr_4b:ed:ed     ARP      192.168.1.1 is at 00:13:10:78:5a:a1
     15 18.139609   82.170.65.100         192.168.1.102         UDP      Source port: 27372  Destination port: oms
     16 18.139669   192.168.1.102         82.170.65.100         ICMP     Destination unreachable (Port unreachable)
     17 22.631071   192.168.1.103         192.168.1.255         CUPS     ipp://192.168.1.103:631/printers/HP-OfficeJet-5610xi (stopped)
     18 23.655199   192.168.1.103         192.168.1.255         CUPS     ipp://192.168.1.103:631/printers/KX-MB271 (stopped)
     19 27.151826   91.156.6.76           192.168.1.102         UDP      Source port: 34626  Destination port: oms
     20 27.151909   192.168.1.102         91.156.6.76           ICMP     Destination unreachable (Port unreachable)
     21 27.151949   193.204.177.134       192.168.1.102         UDP      Source port: 61321  Destination port: oms
     22 27.151979   192.168.1.102         193.204.177.134       ICMP     Destination unreachable (Port unreachable)
     23 27.152049   85.92.36.245          192.168.1.102         UDP      Source port: 59383  Destination port: oms
     24 27.152081   192.168.1.102         85.92.36.245          ICMP     Destination unreachable (Port unreachable)
     25 27.152205   71.131.182.241        192.168.1.102         UDP      Source port: 28627  Destination port: oms
     26 27.152234   192.168.1.102         71.131.182.241        ICMP     Destination unreachable (Port unreachable)
     27 30.121340   88.254.85.221         192.168.1.102         UDP      Source port: 45682  Destination port: oms
     28 30.121402   192.168.1.102         88.254.85.221         ICMP     Destination unreachable (Port unreachable)
     29 35.532473   94.212.48.158         192.168.1.102         UDP      Source port: 54978  Destination port: oms
     30 35.532542   192.168.1.102         94.212.48.158         ICMP     Destination unreachable (Port unreachable)
     31 36.965891   93.106.70.246         192.168.1.102         UDP      Source port: 50000  Destination port: oms
     32 36.965959   192.168.1.102         93.106.70.246         ICMP     Destination unreachable (Port unreachable)
```This is slowing my 3mb internet connection down to the equivalent of 56k.  And it's not just my computer that's acting slow, everyone on my router is.  The only way I've found to fix it is some combination of restarting my computer, router, & modem; most likely because I'm getting a new IP address.

My thoughts are that azureus isn't properly closing the torrent connections.  Can anyone testify to the same problem?  When I start azureus, though, all of my torrents have 0 seeds, 0 peers.

I'm using Azureus v3.1.1.0-3ubuntu3 from the repositories along with sun-java 6-10-0ubuntu2 also from the repositories.


Sorry about the hard readability, the forums don't like preformatted text.

---

### Post by dmizer on 2009-01-23
This is normal behavior for just about any P2P client.

For future reference, if you use [noparse]```

```[/noparse] tags instead of quote tags, formatting will be retained.

---

### Post by mrpeenut24 on 2009-01-23
That was what I thought, but I've never had a problem with this before though.  I thought that after a certain amount of time, the incoming connections would stop from a timeout.  Also, why does my computer respond with ACKs, is it not an application layer response?  I'm only curious because this is crippling my network, which is kind of surprising.

---

### Post by dmizer on 2009-01-23
How did you close the client? Unless Azureus reports to the tracker that you've gone offline, the tracker will still retain your ip as connected.

What port are you running Azureus on? There could be something else responding.

Edit:
Now that I think about it, it's probably java that's responding. It's been too long since I've used Azureus, but you may have to kill java in order to stop the replies.

---

### Post by mrpeenut24 on 2009-01-23
To kill azureus I usually do Alt-F X (Exit).  "ps -xa"  shows no instance of java running after this.  I've also done "killall java", but with the same result.  I'm running it on 4662, which to my knowledge, is the only thing running on that port, however, I've tried different ports with the same outcome.

---

### Post by sedawk on 2009-01-23
You can play around with the tools "netstat" and "lsof" to check
for open network connections or to see if some process still
uses port 4662.

If you have opened any ports in your router (port forwarding/triggering)
to make the p2p stuff work you might think about disabling that
"rule" whenever you are finished with using Asureus.

(I never debugged p2p stuff, but from the log you send I assume
 there is an (old) active p2p connection between 76.101.124.129 
 and your computer and afterwards there are lots of failing UDPs
 from other machines (p2p clients trying to connect?)).

I do not know about Azureus, but I have been asked to fix
some Windows PCs and what I found - to the surprise of the owners -
was a p2p software that was running all the time in the background
without the users knowing. Some of them already forgot they had
used that software in the past and it was still installed (and
active) on the computer. Nasty background services ;-)

---

