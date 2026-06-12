---
title: "PPP PPTP auto-reconnect"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by Ringtail on 2009-09-09
Hi all.  I have an Ubuntu Server 9.04 box set up as my home fileserver and router.  It connects to the Internet via PPTP, and performs NAT for the other computers on the network.  The problem is that whenever the PPTP connection drops (and it does so randomly once in a few days), it wouldn't automatically reconnect.  I have to ssh to the box and do "sudo /etc/init.d/networking restart" manually.

I have no idea what's the problem.  I tried adding **persist **and **maxfail 0 **options to every PPP-related file I could think of, but still no luck.  This is what my PPP config looks like:

**/etc/ppp/options**:
```
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx
persist
maxfail 0
```**/etc/ppp/options.pptp**:
```
lock
noauth
refuse-pap
refuse-eap
refuse-chap
refuse-mschap
nobsdcomp
nodeflate
persist
```**/etc/ppp/peers/myisp**:
```
pty "pptp *vpn.myisp.net *--nolaunchpppd"
file /etc/ppp/options.pptp
user *username*
noauth
nodeflate
nobsdcomp
defaultroute
persist
maxfail 0
```**/etc/networks/interfaces**:
```
auto lo eth1 eth0 ppp0

iface lo inet loopback

# Home network
iface eth1 inet static
        address 192.168.42.1
        netmask 255.255.255.0

# Outside network
iface eth0 inet static
        address 10.1.174.26
        netmask 255.255.255.0
        dns-nameservers 10.0.0.1 10.0.0.2
        dns-search *my-dynamic-dns-domain.org*
        up route add -net 10.0.0.0/8 gw 10.1.174.3 dev eth0

# Internet
iface ppp0 inet ppp
        provider myisp
```By the way, I'm a fan of Ubuntu Server.  I've been using it on this box since June, and apart from this reconnect problem I have never had any issues with it(*).  I used to be a Gentoo fan, but got sick of having to chase all the weird little bugs which appear after each upgrade, instead of doing something actually useful.  After all, what's the point of building your own headless homeserver and spending a week compiling and configuring everything if you still have to run circles around it every so often?  When I replaced Gentoo with Ubuntu Server, I was like "It only took me *half a day* and *everything* is already working perfectly?  No way!" :)  Later I even tried installing desktop Ubuntu out of curiosity, and was similarly impressed that it is actually fairly usable and works pretty much out of the box.  Still sticking with my Vista, though.  I gave up on desktop Linux two years ago (after three years with Red Hat, Slackware and then Gentoo), and I'm not going back.

(*) Although AFAIR pptp-linux package was not included on the installation ISO.  Setting up my Internet connection for the first time was understandably non-trivial.

---

### Post by lswb on 2009-09-09
I'm a little rusty on setting up ppp, but check out the "demand" option in the man page, I seem to recall using it when I needed something similar with a ppp connection some time ago.

---

### Post by Ringtail on 2009-09-09
> **lswb said:**
> I'm a little rusty on setting up ppp, but check out the "demand" option in the man page, I seem to recall using it when I needed something similar with a ppp connection some time ago.
But the man page says demand option is for demand-dialling, and this isn't what I'm trying to do.  I just want my PPTP connection to be permanently up, and auto-reconnect whenever it drops for any reason.

---

