---
title: "How to verify monitor mode running?"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by cheesy73 on 2010-05-06
I am trying to enable the monitor mode on my Intel 3945 bg card on Ubuntu Lucid Lynx.
Even though iwconfig reports that the card is in monitor mode, I am a little doubtful since I am not seeing any packets with regular ip addresses on wireshark. Most of the packets I am seeing are of the type "broadcast" which is making me think that the card is still in managed mode.

Also the interface name in iwconfig is still wlan0. Isn't it supposed to be wifi0 with the new drivers?

I am very confused at this point.

---

### Post by jbrown96 on 2010-05-07
I have that card and it's still wlan0. I have never done this before, but you can't just switch your card to monitor and intercept the packets. You are going to need to do something in the wireless sub-system to make it capture and keep those packets, then you will probably need to decrypt them. And finally, you will need some sort of iptables rules to pass them to the input chain.

---

### Post by cheesy73 on 2010-05-07
But in any case are you able to change the mode of your card from managed to monitor? As far as I understand, there is no extra hardware required to sniff packets on a wireless network. All that the card is being asked to do is report even those packets which are not addressed to it. I am not interested in decrypting anything, just sniffing unencrypted packets.

---

### Post by cheesy73 on 2010-05-07
Really looking towards some guidance.

---

### Post by cheesy73 on 2010-05-08
*bump*

---

### Post by jbrown96 on 2010-05-08
What do you hope to gain by sniffing packets? If they aren't encrypted, then just associate to the network and use wireshark to sniff at the IP level.

---

### Post by cheesy73 on 2010-05-08
Therein lies the issue. Most of the sniffed packets are not showing a regular ipv4 address. The only packets I am seeing are the broadcast ones or probe responses or beacons. No packets with protocols such as TCP, HTTP etc. are being seen on when I am sure such packets are flowing in the network.
Could this mean that despite showing mode as monitor the card is still in managed mode?

---

### Post by cheesy73 on 2010-05-09
*bump*

---

### Post by cheesy73 on 2010-05-09
*bump*

---

### Post by jbrown96 on 2010-05-09
I'd say it's safe to assume that no one here knows how to solve this problem. You should look into trying BackTrack for something like this.

---

### Post by khianhui on 2010-05-10
What do you expect from the monitor mode actually?
If you put the interface to monitor mode(wlan), you cannot connect to any network and of course 
wireshark are useless at this point(correct me if I am wrong). You should use other tools like
airodump to capture the packet.
To use wireshark, you must put your interface to promisc mode in order to "sniff" data.
The reason why your interface is wlan0 is because you are not using airmon to enable monitor mode for wlan0(correct me if I am wrong), I supposed you watch youtube for wifi cracking aren't you?

---

### Post by cheesy73 on 2010-05-10
I thought monitor mode with wireshark would be same as using airodump which would display all packets. Is that not correct?

---

