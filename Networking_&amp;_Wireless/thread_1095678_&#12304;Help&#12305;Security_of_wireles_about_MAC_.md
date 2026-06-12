---
title: "&#12304;Help&#12305;Security of wireles about MAC address"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by knaiyaya on 2009-03-14
Hi:
  I'm a fish about ubuntu and the network...and the descriptions
below may be not clear..sorry about that..

  I have a very big problem: in my router i set MAC address filtering&#65292;turn off DHCP and IP binding, also use WEP encryption(can not set WPA);)

  But sometimes i found the net speed is very slow, almost can't visit the web site&#65292; i'm sure not because of the virus&#65292;i just know there have some tools such as aircrack-ng can detect the valid information about legal MAC addres , IP address ,DNS and so on, that's mean others can modified theirs informations to become a leganl user...:( and can use legal MAC addres to launch arp attack:(  

  How could i defend that, does there have another security ways to set in my routers?Please help me ,thank your!:)

---

### Post by thesavager on 2009-03-14
Hi,

First of all, 100% safe doesn't exist.

You still use WEB encryption, thats really a bad thing.
Doesn't matter what you do, if you keep use WEB encryption, the "hackers" still could grap your key, from gathering IVS packets.

So u need to get wpa or wpa2 working, "hackers" could grap your fourway handshake , but they still need a passwordlist to hack it.So make a strong password, like:    (-:[NL]$Th3SaVaG3r]:-) 

I WONDER IF THOSE "HACKERS" HAVE THIS KIND OF KEY IN THERE PASSWORDLIST :)

---

### Post by helgman on 2009-03-14
> **knaiyaya said:**
> But sometimes i found the net speed is very slow, almost can't visit the web site&#65292; i'm sure not because of the virus&#65292;i just know there have some tools such as aircrack-ng can detect the valid information about legal MAC addres , IP address ,DNS and so on, that's mean others can modified theirs informations to become a leganl user...:( and can use legal MAC addres to launch arp attack

There could be more reasons then "hackers" playing around with your wireless connection but if you are worried about the "hackers" doing ARP-spoofing or something like that, just install Wireshark and listen to the traffic - if you see a lot of ARP-packets (directed to you) then it's time to investigate. Also, since the wireless network is a shared media I'm pretty sure Wireshark should be able to pick up traffic originating from other clients using your WLAN (depending on your wireless NIC). In short, start sniffing that traffic ...

One other thing, as pointed out by thesavager, WEP really isn't strong encryption and you should try to get WPA/WPA2. If I understod our post correctly you can't use WPA (old AP?) - if that is the case, try to figure out other ways to "defend" yourself (change keys a lot, make sure not to broadcast your network further then the range you need to use it, monitor your network closely ...). Also, read up on the weaknesses of WEP ([http://aircrack-ng.org](http://aircrack-ng.org) is a good place to start).

But, as I said above, there could be other things hampering the speed of your wireless network through interference (like microwaves and other home appliances using the same open frequencies as your wireless AP). If you use the G-standard (802.11G) then try a different channel or, if your clients and AP support it, change to the A-standard. If you live close to your neighbors then the might have set up an wireless network to, using the same frequencies as you (or some frequency very close to yours)
and that might "slow down" your network.

I hope you are able to work it out.

Regards,
Helgman

---

