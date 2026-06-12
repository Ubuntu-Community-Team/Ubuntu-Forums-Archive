---
title: "Network messaging with ubuntu"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by superpink99 on 2009-09-20
ok so i have an asus wireless N router, now when i checked the computers connected to my network. i see other computers i don't know, now i want to share my connection with certain people like my neighbors so putting a password is not my option right now. 

im pretty sure there is a way to send messages to other users via there IP address with ubuntu, the question is i don't know so anyone who can help me please?

if possible i want the following:
1. To be able to send messages
2. To be able to check there computer specs or something
3. if possible for them to be able to reply when i give them messages

---

### Post by scorp123 on 2009-09-21
> **superpink99 said:**
>  i see other computers i don't know You're running an open wireless access point? That's dangerous. You might be held responsible for whatever these people do on your network! If they download illegal stuff then the authorities will have _YOUR_ public IP address. The excuse "But there were other people on my network ... " usually doesn't fly.

> **superpink99 said:**
>  now i want to share my connection with certain people like my neighbors so putting a password is not my option right now.  Why not??? What's wrong with defining a WPA2 password? Nobody is stopping you from sharing that specific password with specific neighbours. If anything strange happens you at least know whom you shared your WiFi password with.

The (complicated!) alternative would be that you enable MAC filtering on your router. So each neighbour would have to tell you their MAC address or else they will get thrown out ... But not all people are tech savvy and finding one's MAC address might be too complicated for some.

> **superpink99 said:**
>  im pretty sure there is a way to send messages to other users via there IP address with ubuntu No. There is a stupid sub-protocol in Microsoft SMB that allowed for sending pop-up messages ("net send" command on Windows) but Linux systems per default don't implement this stupid protocol and nowadays even Windows systems block it because it was very often abused for spreading "scare ware" and spam messages.

> **superpink99 said:**
> 1. To be able to send messages  See above. A mechanism like this across platforms doesn't even exist. The only message you can "send" is to shutdown that open WLAN of your's. That would be as close to a "clear message" as you can get.

> **superpink99 said:**
>  2. To be able to check there computer specs or something That would require remote access to the other system. Without that the closest you could do is to use certain network tools such as "nmap" that try to identify a remote OS via certain typical TCP/IP packets that each OS sends out (despite TCP/IP being a standard there are enough subtle differences so that one could tell the difference between a packet that was send from a Linux or a Windows system). However: Being able to use such tools requires some knowledge. And those tools might also be abused for illegal activities and in some countries downloading and possessing such tools might even be illegal.

> **superpink99 said:**
> 
3. if possible for them to be able to reply when i give them messages Again: There is no common protocol between all the platforms that would implement this.

Please shutdown your open WiFi, enable a strong WPA2 password and only share it with people you really want it to share with. That's the best thing you can do.

---

