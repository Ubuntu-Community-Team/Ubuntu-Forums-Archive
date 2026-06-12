---
title: "How do I route all my traffic that doesnt go through tor through a vpn?"
date: 2013-03-02
forum: Networking &amp; Wireless
---

### Post by ShapeShifter499 on 2013-03-02
I have a netbook running Ubuntu 12.10 32 bit acting as a wifi router based off this guide [http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/](http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/)      I would like to have it take in all data and send it through tor  and   vpn, if the data is tor-supported (TCP, Web Traffic, etc.) send it  to   tor and if the data is not tor-supported (UDP, whatever else) send  it   through vpn otherwise BLOCK IT. I'm unclear how to do this.  I  don't   have any vpn or tor set up yet. Also I do want to be able to ssh  into   this box at all times, right now I have ddclient updating  dyndns.org to   remedy this. Below is my set up as it stands now..
  Internet<--->DNS<--->Cable Modem<--->Ubuntu Netbook/Wifi Router<--->All other devices

---

### Post by bellaseem on 2013-03-02
Basically, when you set up a VPN connection, everything gets routed through it as far as I know... So what you have to do is set up a VPN connection first (btw, you won't be able to get your hand on a good free VPN, if you want it for a small amount of usage (say 1-2Gb per month) then you'll find free trials). Once the VPN is set up, Tor's traffic will be routed through the VPN, and so everything should be good.

---

### Post by ShapeShifter499 on 2013-03-02
what about "leaks"? how can I make sure that if the connection goes down data doesn't end up going through the normal way again?

---

### Post by ShapeShifter499 on 2013-03-03
bump

---

### Post by haqking on 2013-03-03
> **bellaseem said:**
> Basically, when you set up a VPN connection, everything gets routed through it as far as I know... So what you have to do is set up a VPN connection first (**btw, you won't be able to get your hand on a good free VPN**, if you want it for a small amount of usage (say 1-2Gb per month) then you'll find free trials). Once the VPN is set up, Tor's traffic will be routed through the VPN, and so everything should be good.

I would disagree with that though only my opinion.

personally i use a paid for with bitocins VPN (AirVPN)

but i also occasionally use one of a few free ones which are all excellent in my experience:

The following ones are free (though your mileage may vary) and are all pptp and not OpenVPN but still decent for a free service.

VPNBook

Server #1: euro1.vpnbook.com
username:  pptp
pasword:   9jHbfKiN

Server #2: euro2.vpnbook.com
username:  pptp
password:  9jHbfKin

Justfreevpn

Server UK: uk.justfreevpn.com
username:  justfreevpn
password:  3159

Server USA: us.justfreevpn.com
username:   justfreevpn
password:   8882

Server Ca: ca.justfreevpn
username:  justfreevpn
password:  8398

Free Uk VPN

server: bestukvpn.com
username: free
password: 1370 

To the OP, connect to the VPN which protects everything and continue to use Tor when connected giving you an increased layer of anonymity and privacy though not necessarily security.

Peace

---

