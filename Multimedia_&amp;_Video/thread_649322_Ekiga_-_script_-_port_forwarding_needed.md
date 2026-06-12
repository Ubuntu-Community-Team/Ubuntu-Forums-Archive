---
title: "Ekiga - script - port forwarding needed?"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by candtalan on 2007-12-24
I am new to webcam and ekiga stuff and with this new camera I am trying to use ekiga for video phone things. The camera works in ekiga, but when configuring ekiga initially I get a warning that Ekiga detected Symmetric NAT, suggesting that my router does not natively support SIP. The suggestion then is to use port forwarding 'to your internal machine' (is this my adsl router??) to change my Symmetric NAT into Cone NAT.

On the ekiga site 
[http://ubuntuforums.org/attachment.php?attachmentid=45924&d=1192061454](http://ubuntuforums.org/attachment.php?attachmentid=45924&d=1192061454)
it says for this situation for the case:
'when it reports "Symmetric NAT" and that you are using GNU/Linux, please use the script (or a variation of it) given below.'

it offers a script on that page:
'6.2. What iptables rules could I use for GNU/Linux?'
about which is said - 'it does not forward any port'.

I am reluctant to use a script, not understanding the implications, but I am also confused because the ubuntu community site
[https://help.ubuntu.com/community/Ekiga](https://help.ubuntu.com/community/Ekiga)
it does not mention the script. But it does give ports information.

Ports forwarding is also referred to in many other sites which relate to ekiga help comments.

I seem to have a network situation which is a problem, but I do not know if I should use port forwarding or have a go with the script, or both, or what?

I am using kubuntu 7.10, a Vigor 2600 (wired) adsl router which is capable of port forwarding (if I knew exactly what to do), and a logitech Quickcam Communicate STX plus.

For example Is port forwarding any particular security risk I wonder? If not I would feel inclined to maybe avoid use of a script which I did not understand.
tia

---

### Post by YannickDefais on 2007-12-25
Hi,

The script is rather old and I do not recommend it, especially if the problem is on your router as it wont solve it. This was an early solution when Ekiga 2.0 was release in the first place to bypass firewalls badly configured for SIP.

Port forwarding is appropriate for symmetric routers and isn't a security risk, as probably only Ekiga will listen on those ports, thus the attacker (if any) should find a weakness in Ekiga itself to grant access to the computer running Ekiga. Ekiga is part of Gnome since a long time, and is under surveillance of security teams.

The problem with port forwarding is it will only pick up the computer the router will forward the packets to. If you only have one computer it is obviously not a problem. If you have a LAN behind your router, you will have to repeat the operation for each computer and assign different ports for each one of them and configure each Ekiga to listen on those ports. In this situation, you also can use a SIP proxy to which you'll forward ports and the proxy will route to the right Ekiga (but this will be even more complex to setup for domestic use...).

A good solution if you have a LAN behind your router and if your router support the feature is "Dynamic navigation of NAT routers". More informations about this here:
[http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router#Symmetric_NAT:_Dynamic_navigation_of_NAT_routers](http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router#Symmetric_NAT:_Dynamic_navigation_of_NAT_routers)

Regards,
Yannick

---

### Post by candtalan on 2007-12-25
grateful thanks!

---

