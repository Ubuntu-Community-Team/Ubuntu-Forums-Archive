---
title: "use as Hotspot, mobile connects but can't browse internet"
date: 2013-06-09
forum: Networking &amp; Wireless
---

### Post by Andra on 2013-06-09
hallo

I can establish my ubuntu laptop as hotspot, I can connect it from my mobile, however, I cannot just use it - can't browse internet on phone.

Ubuntu 12.04
wireless network - use as Hotspot, Mode: Ad-hoc, Ipv4: Shared, ipv6: ignore or automatic, Security: wep 40/128 (tried key length 8 or 5, ascii)
It seems there is no way how to see connected devices.
Connection information: ip: 10.42.0.1

Mobile: Nokia C5-03
Connection Log files show that some kb info is sent and received.

Please help, I couldn't find anything helpful by googling either.

Edit Jun 10:
I have now tried to test it with Wireshark. The mobile gets ip address ok, it gets dns answers ok, it connects to the requested http hosts and receives responses from them. It JUST does not open any webpage :confused:. Ok, I have a firewall (ufw),  but it does not seem to be the trouble: 1) adding ad-hoc adds necessary rules; 2) nothing bad appeared in syslog; 3) I tried also_ with disabled firewall_.
I have successfully connected to the internet using this phone - both in "normal" wireless networks and by gprs. I don't see any settings in the phone that could disallow such ad-hoc - and actually it does not disallow, it uses the ad-hoc, it "talks" with webhosts, it receives responses (I cannot figure out how much valid, but, for example,  on "GET  / HTTP/1.1" it received ACK, SYN, and "HTTP /1.1  302 Found (text/html)").
I don't have currently other devices to test and use my hot-spot.

Edit Jun 10, No2:
Searched this "302 Found", it's one page with redirect. So, the phone never receives "200 OK".
Describe one test: 1) "GET"; 2) response http > 43417 [ACK] Seq=1 Ack=468 Win=6912 Len=0; 3) mobile sends > http [FIN, ACK] Seq=468 Ack=1 Win=129940 Len=0' 4) receives [TCP Previous segment lost] http > 43417 [ACK] Seq=8635 Ack=469 Win=6912 Len=0. There is other communication but with this host that's all, well, when the phone says FIN, then FIN.

Edit Jun 10, No3:
I have WinVista on the same computer...and it's ok, there are some problems (I have the ad-hoc always to create anew) but it works. I write this not to praise Win, it's just the result of another test.

---

### Post by Andra on 2013-06-18
sudo ifconfig eth0 mtu 1500

Congratulations to myself :D
The crucial packets turned out to be not HTTP (TCP whatever), but "ICMP nn Destination unreachable (Fragmentation needed)". Indicating that something is wrong with MTU. Which MTU? That of the wired connection... By default it was 576. And in Windows it is by default 1500 for Ethernet.

---

