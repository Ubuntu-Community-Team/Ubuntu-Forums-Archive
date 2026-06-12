---
title: "VPN slows down internet connection"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by regsnerven on 2011-04-20
Hey guys,

i'm trying to connect to a VPN.

That is what i want:
 - i want to connect to the vpn server (Windows Server 2008)
 - i want to use the routes of the dns server which is - oh what a suprise - the vpn server
 - i DON'T! want to use the internet connection of the vpn server
 - i want to have access to all the computers and network resources in the vpn network

This is what i got:
 
 Either:
  - i have access to all the routes
  - i may have access to the network resources and computers (could not figure out how to get access to it until now)
  - i have the internet connection of the vpn server WHICH I DONT WANT!!
 
  Or i have:
   - an awefully slow internet connection with my home internet connection
   - NO access to vpn network routes or resources


I used the network manager on my Netbook with Ubuntu Netbook Edition and i couldn't find a midway.

Can you help me with a solution?

Gr33tZ
Rn

---

### Post by prankstar008 on 2011-04-20
Correct me if I'm wrong, but I don't believe you can have both. VPN encrypts all traffic. I don't think you can have it encrypt CIFS traffic and not HTTP traffic. When you connect to a network via VPN, you are essentially physically connected to that network through an encrypted tunnel, and all traffic must go through the tunnel. I imagine there is a workaround here, but I don't happen to know one.

---

### Post by regsnerven on 2011-04-20
Yeah but on my windows machine i have a vpn and i do have access to the resources and stuff but i use my own internet connection.

Why shouldn't this work on linux? :(
That would be very sad.

By the way: is it important to mention that the vpn server is inside a domain? and the user i use to connect to it is also a user of that domain?

---

### Post by oracle2b on 2011-04-20
You can access only the resources on the VPN network. 

Go to the vpn properties/settings. select the 'IPv4 Settings' -> 'Routes' -> check 'Use this connection only for resources on it's network'

---

### Post by regsnerven on 2011-04-20
yeah...no.

This is not working.

If i enable that option i have an awefully slow internet connection and the internal routes are also not resolved as they should be.

---

### Post by wormyblackburny on 2011-04-20
> **oracle2b said:**
> You can access only the resources on the VPN network. 

Go to the vpn properties/settings. select the 'IPv4 Settings' -> 'Routes' -> check 'Use this connection only for resources on it's network'

This always worked for me too. Not sure what is wrong with your connection if that didnt fix it...?

---

### Post by regsnerven on 2011-04-23
Okay..i found out that ALL! the dns entries made by the vpn server are slow.
I configured it like the above suggestion but i don't have any connection to the computer on the vpn network. 

What more can i give you to help you to help me? ^^

---

### Post by oracle2b on 2011-04-23
It should have worked. You should have been able to access computers/shared folders on the vpn while utilizing your own broadband. try pinging a resource on the vpn network just to be certain samba isn't mis-configured. If you can ping a resource successfully than I'd check with you samba config.

---

### Post by regsnerven on 2011-04-26
Either i have access to the vpn internet connection + computers
or
i have NO! access to any computer of the vpn network and have an awefully slow internet connection.
even though i cant ping the computers on the vpn network.

and what "samba" are you talking about? 
The vpn server i connect to is on Windows Server 2008 and as far as i know i don't have to install samba on my netbook to access to other network resources. 
even though i should be able to ping the computers on the vpn network even without samba (if i should need it).

---

### Post by oracle2b on 2011-04-26
Samba is what enables you to see networked windows shares in the first place.  If you're accessing windows shares from your netbook than samba is installed. You do not need samba to ping a network pc. Was the ping successful or not?

---

### Post by regsnerven on 2011-04-29
Nope. The ping fails.

---

