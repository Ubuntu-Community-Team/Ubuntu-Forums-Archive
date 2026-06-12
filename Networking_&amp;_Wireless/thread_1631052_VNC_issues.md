---
title: "VNC issues"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by benjrooney on 2010-11-26
Hope you can help. I am a bit of a newbie when it comes to networking (dark, dark magic)

I am trying to connect to my corporate VPN. I have two machines - a company MacBook Pro running Snow Leopard and my own netbook running a flavour of Ubuntu (Jolicloud 1.1).

I can connect to the VPN using Snow Leopard's VPN client using the Cisco IPSec without any problems at all.

What I would like to do is to connect my netbook. Alas it doesn't seem to work. I know the   VPN credentials are correct because if I tail the daemon log on the netbook I see the VPN connection being made and the remote server returns the login banner.

However once connected I can't access anything - neither the internal network, nor the internet through the VPN (the company does not allow split tunneling).

I suspect the problem must related to one of the following errors in the daemon log:
"can't open pidfile /var/run/vpnc/pid for writing"
"nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1" -- doesn't sound good, does it?

I have searched the Mac for the correct .pcf file. I found two in /private/etc/opt/cisco-vpnclient/Profiles/ but curiously they don't seem to be correct (I think they are old ones).   I am not sure where the Mac stores the connection information. I am guessing in my user Library somewhere, but I can't seem to find it.

I know this is a long shot - but if anyone has had a similar experience and solved it I would be very appreciative of help - or some suggestions as to how to go forward...

Thanks

Ben

EDIT: I see from my Mac connection that the Automatic Proxy Configuration check box is selected and  a URL given for the Proxy Configuration File.  I am not clear how to pass that information to the Ubuntu VPN connection - which clearly it is going to need.

---

