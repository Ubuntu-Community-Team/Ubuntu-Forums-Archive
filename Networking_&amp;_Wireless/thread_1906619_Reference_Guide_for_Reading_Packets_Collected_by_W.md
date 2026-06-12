---
title: "Reference Guide for Reading Packets Collected by Wireshark"
date: 2012-01-09
forum: Networking &amp; Wireless
---

### Post by Wiking on 2012-01-09
Hi, I was able to setup Wireshark and collected packets from my local network. I looked at the packets and all the info, and it might as well be Mandarin because I don't understand any of it.

Is there a reference guide or somewhere where you guys can point me to so that I may decipher all that mumbo jumbo? 

I've been reading the Wireshark wiki and understand some terms, but most of the wiki deals with running and configuring Wireshark, the analyzed data all looks very foreign to me.

Thanks.

---

### Post by jonobr on 2012-01-09
Hello


The key to understanding wireshark is understanding the 7 layer (or 5 layer depending on your resource) [OSI]("http://en.wikipedia.org/wiki/OSI_model")model

Once you know that then wireshark will make a lot more sense.
Knowing the difference between layers helps a lot.

eg Layer 1 = physical media 
layer 2 - (data link layer) mac addresses
Layer 3 - (Networking layer) Ip addressing networking
Layer 4 - (transport layer) - TCP/UDP/sctp etc

Right up to layer 7 - application layer - ftp ssh etc.
Be aware, OSI model is a huge topic,

Take a look at the first picture is shows the breakdown of wireshark-wireshark1.png

There are 3 areas high lighted with black boxes,
the top area shows the high level information - source and destination IP address of the traffic caught, the protocols used, timestamps and packet number  and there is an info box showing high level information
The second box, goes further into the packet showing the information in the Ethernet frame by protocol layer.

The layers have a + which allows you to expand each section and look at the packet contents.
the first line shows the frame, the second the mac information (from layer2) the third the IP addressing used (layer 3) the fourth layer  the protocol used  (in this case udp and the port number (137 which is netbios)

The upper layers all get a bit mushy (session, presentation) so what you see at the end is the application layer stuff, basically the information being transported across the network.
You can see in the example I gave I have drilled a bit into the netbios packet that was sent.

The bottom box, shows all the same information but in hex format,

For decoding packets people mostly use the middle one.

Your use will depend on the problem you are having so , for example, if your not sure how DNS is working and think the DNS response your getting is wrong, you would look at the application layer (7) response from the DNS , and you would be able to read it  to see if its correct.

If you are having problems getting to the DNS the you would look at layer 3 and 4 to see if it is routing across the network correctly.

Another thing you need to be able to do is use the filter bar at the top.
if I wanted to filter based on IP address or port number or a combination, I can construct a filter to only show certain traffic. This is very important on busy networks generating a lot of traffic

You will find If you are having issues on your network , or trying to resolve IP or application issues, wireshark is  invaluable, however, try and learn the OSI model to help you make sense of it.

---

### Post by Wiking on 2012-01-09
Thanks, I have some resources on network protocols and will read up. Just needed a kick in the right direction.

---

