---
title: "Ubuntu router causes external servers to occasionally stop responding"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by ksteuber on 2013-03-25
EDIT: I think I found the root of the problem. You can probably skip reading this and go right to my third post.

I have been building an router using Ubuntu. Just to give an idea of the general things going on that might affect the problem, here is the router's general setup:
Router connects to WAN (eth0) with default DHCP client.
dnsmasq serves DHCP addresses to LAN (eth2). eth2 is connected to a gigabit switch to allow multiple clients.
A DD-WRT router configured as an access point is connected to the switch to allow wireless clients.

iptables is configured like this:
```
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT
iptables -A INPUT -i lo -s localhost -d localhost -j ACCEPT
iptables -A INPUT -i eth2 -j ACCEPT
iptables -A FORWARD -i eth2 -s 192.168.42.0/255.255.255.0 -j ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A INPUT -i eth0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i eth0 -o eth2 -d 192.168.42.0/255.255.255.0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p udp --dport 1194 -j ACCEPT
```

A variety of other services are running on the router including software RAID, SAMBA, Apache, PHP, DynamicDNS updater and OpenVPN.

The problem I am having is this: Occasionally, when attempting to visit a site, Chrome will give these two errors:
Error 103 - Connection Aborted
Error 324 - Empty Response
I tried with some other browsers and Firefox seems to say "The connection was reset", while Internet Explorer just says "Internet explorer cannot display the webpage". 

This problem typically affects one site at a time; any other site still loads properly. The problem happens somewhat frequently, but seems to be restricted to a few sites. I have had a problem with google.com, tumblr.com and cracked.com. No other sites visited have ever exhibited this problem. (If it weren't for google, this problem might not even be worth fixing).

After encountering this problem, it usually persists for 10-30min, then resolves itself. Occasionally the problem just seems to be totally intermittent (refresh, it doesn't work; refresh again it works).

Certain computers in the house seem to see this problem frequently: My Windows 7 desktop (wired connection) and my roommate's Windows 8 laptop. Other computer never seem to have the problem: My Ubuntu laptop, my roommate's Windows XP laptop. However, when the Windows 8 laptop cannot access google.com, the Windows 7 desktop does not necessarily lose connection at the same time, but sometimes does.

When the problem occurs, resetting network adapter seems to solve the problem temporarily. 

Because the problem is intermittent, I have had a hard time troubleshooting. I have managed to start tcpdump in time to capture a number of failed transmissions and they always seem to follow this format:
Client->Server: SYN. 
Server->Client: SYN-ACK. 
Client->Server: ACK. 
Client->Server: HTTP GET request
Client->Server: Continuation of HTTP request
Server->Client: TCP Window Update. This packet is not seen in every case. No response from server is ever heard past this point.
Client->Server: Numerous TCP re-transmissions.
Client->Server: TCP reset

Sometimes the TCP resets are scattered through the numerous TCP re-transmissions.

When loading the page and no problems occur, sometimes an ICMP "destination not reachable (fragmentation needed)" is sent from the router to the client after a particularly long http request (ex. 1314 bytes), which prompts the re-transmission of the request in smaller packets. Many times, isolated duplicate ACKs are seen. Occasionally there are two consecutive duplicate ACKs followed by a number of re-transmissions. I don't know much about the first issue, but from my understanding of TCP, the duplicate ACKs are ok.

So this leads me to three questions: 1) What other data can I/should I be gathering to help diagnose this? 2) What other info would it be helpful for me to post here? 3) Does anybody have any ideas what could be causing this problem?

I am a bit concerned about doing things like posting whole tcpdump captures here because of the information I might be unintentionally revealing in it. If it would help to post those, what Wireshark filters should I use to extract only the relevant information? Right now I am using "ip.addr==<client-ip>&&ip.addr==<server-ip>".

---

### Post by ksteuber on 2013-03-27
Ok, I have done a bit more looking around with tcpdump and it looks to me as if this might be an iptables problem. I captured on both the LAN interface (eth2) and the WAN interface (eth0) during a "problem period" and filtered the WAN capture by the ip address of the problem website. What I saw seems rather unusual. 

First there is the regular SYN,SYN-ACK,ACK.
Next, before each of the HTTP transmissions, there is a packet, always of length 586, labeled as "Fragmented IP protocol [Reassembled in #(next packet)]". The next packet showing the HTTP data is always length 58.
After the second packet is sent, an ACK is received from the server requesting the second packet.
After the ACK, another fragmented HTTP packet is transmitted, then a non-fragmented, smaller HTTP packet.
Then the server sends two duplicate ACKs, prompting a TCP re-transmission.
However, before each re-transmission, there is a FIN-ACK packet sent to the server, but it is not NAT-ed properly; the source IP is the client's internal IP address! The re-transmissions, like the originals, are fragmented. It is worth pointing out, that these were not received fragmented on the LAN; the router must have fragmented them.
Then after the re-transmissions, (during which the server has not responded) , the client attempts send two RST-ACK packets. The second one is properly NAT-ed, but the first one has an internal address as the source IP.
Then the client sends another SYN packet and the server starts responding again.
This whole process repeats a second time except the FIN-ACK packets are not sent. After the second set of TCP re-transmissions, the server responds with bunch of ICMP messages: "Time-to-live exceeded (Fragment reassembly time exceeded)". These are never forwarded to the internal client. The ICMP messages seem weird too. The TCP headers contained within the ICMP message all have a sequence number of 4257237544 and an ACK number of 2985940850. The re-transmissions sent were all of the same packet with the sequence number 557. 

I feel that the improper NAT problem implies that iptables is configured incorrectly. 

Can anybody give me a few pointers? I am really confused.
Thanks.

---

### Post by ksteuber on 2013-03-28
I  think I stumbled upon the solution!
Setting the MTU to 576 seems to solve the problem. I think for some reason this is what my ISP, Comcast, wants; can't imagine why. However, I am still having one little problem:

I have tried adding "dhcp-option=option:mtu,576" to /etc/dnsmasq.conf, but for some reason it is not doing this properly. When I connect from my Ubuntu laptop, I can see that the option is being sent in the DHCP ACK, but when I connect from the desktop, the option is not being sent. It seems that this is because the desktop does not request the value. The DHCP request parameter request list for the laptop includes the MTU; for the desktop the parameter request list does not include the MTU. I would like the router to work for everyone with no extra client configuration (like most routers), so I would like to know if there is a way to force the MTU on the client or something. 

Maybe this is only a problem because the router is not fragmenting the packets properly? This would be consistent with what I have seen with my more recent tcpdumps: The packets on the output interface are sometimes not the correct size. The TCP header will claim that the length is 556, but the entire packet is only 58 bytes. My understanding of TCP is a bit limited, but this seems very, very wrong. Perhaps what I really want to fix is the router's improper fragmentation?

Any ideas? Anybody?

Edit: Also, why is the windows machine being so dumb? It receives a ICMP message saying "Destination Unreachable (Fragmentation needed)", with a field "MTU of next hop:576", but then it ignores that and sends 610 byte packets. Why would it do this?


As a summary: the router is taking 610 byte packets from the internal interface and forwarding them to the external interface as 58 byte packets (not fragmenting them, just losing most of the data). It seems that of the 556 byte payload, only the last 24 bytes actually make it to the external interface. The TCP header of the packet still indicates that it contains 556 bytes of data. I really feel that I have reached the end of my ability to troubleshoot this problem and google has not turned up any helpful information.

Can anybody please give me some tips on why my system is doing this or how to figure out why my system is doing this?
Thank you in advance!!!

---

### Post by ksteuber on 2013-03-28
I take it back! It was not dropping the majority of the packet content, I was filtering the packets badly. I was filtering the packets on the external interface by server IP and the port number that NAT using, but this was filtering out the fragmented packets because the port number could not be read until the packet was reassembled.

However, it does seem that manually changing the MTU on the problem computers fixes the problem. 
I still could use some help troubleshooting this because I am really confused. I want computers to work without manually changing the MTU. Ideally, I would like to maintain a high MTU on the internal network where this is supported and have the packets fragment when sent on the network that requires a lower MTU. It kind of seems like it is already doing this, but the server sends an ACK for the first packet, then never responds again.

---

