---
title: "Bridging a GT701D to a WRT54G2"
date: 2011-06-04
forum: Networking &amp; Wireless
---

### Post by FernandoTertiary on 2011-06-04
Hola,

Am attempting to connect to OSGrid,  & have discerned that the modem being used is not compatible. The  option is to do Transparent Bridging from a Actiontec GT701D to a  Linksys WRT54G2 to utilize its' capabilities that ARE compatible with  OSGrid. The problem's with various incremental questions pertaining  setup. The online sites do not prove very helpful and the manuals do not  cover Bridging.
1) The Actiontec modem establishes a 192.168.0.1  gateway address, & the Linksys establishes a 192.168.1.1 gateway  address, though the modem reflects the address to be 192.168.0.3 &  that appears wrong. Am wishing to code a static IP via the Network  Connections utility when the bridge is accomplished. Though am  attempting to be methodical about the Bridging sequence.
2) The page [http://www.dslreports.com/forum/remark,14709801](http://www.dslreports.com/forum/remark,14709801) suggests a RFC Transparent Bridge mode, & page [http://forums.techguy.org/networking/48 ... gt701.html]("http://forums.techguy.org/networking/480301-port-forward-actiontec-gt701.html")  appears to scarcely pertain and the theory is to discover a good  resource, though the ##networking IRC channel, nor the #ubuntu-server  channel appear to wish to assist. Am very grateful for any assistance & suggestions anybody might provide. 

Muchos Gracias for the attention!

Update: Forgive the edit, though did not quit at the post and rather continued. For posterity sake, doing a Modem Bridge is as easy as turning off the DMZ Hosting, the NAT, & Setting WAN to RFC Transparent Bridging from within the Modem, then enter the Router config & configure it for PPPoE & Voila!

The questions now pertain correct configurations within the Router Settings. Am curious about Port Triggering, is it necessary? Have enabled NAT (actually, in the Linksys it is disabling the NAT Filter), & thus what tests are to be conducted to ascertain correct configuration to see if WAN is visible? Persons with blogs have suggested it is difficult to see a WAN address from within a network. As well have disabled the DHCP Server & configured a Static IP. The address [http://refael.dyndns-work.com](http://refael.dyndns-work.com) proves visible in the message "It Works!", though the direct Router Address does not. The nmap LAN proves 9000/tcp open & 9000/udp open|filtered & the nmap WAN proves the same 9000/tcp open & 9000/udp open|filtered. When testing from the Terminal ```
virgae@virgae-Matheimael:~$ host refael.dyndns-work.com
refael.dyndns-work.com has address 76.242.184.206
;; connection timed out; no servers could be reached
;; connection timed out; no servers could be reached
``` is the result. [http://refael.dyndns-work.com](http://refael.dyndns-work.com) just displays "It Works!" from the local network. Ubuntu Firewall Settings display ```
virgae@virgae-Matheimael:~$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), deny (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
9000/tcp (OpenSim Listener) ALLOW IN    Anywhere
9000,9001,9002,9003/udp (OpenSim Regions) ALLOW IN    Anywhere

```
The Linksys Port Forwarding Config is [http://imagebin.org/156788](http://imagebin.org/156788) & the Router Status displays [http://imagebin.org/156789](http://imagebin.org/156789) , though curious about configuring Advanced Routing to syncronize the Router & Local Addresses via the [http://imagebin.org/156790](http://imagebin.org/156790) page config settings page. 

Secundo Tiempo, Muchos Gracias Amigos!

---

