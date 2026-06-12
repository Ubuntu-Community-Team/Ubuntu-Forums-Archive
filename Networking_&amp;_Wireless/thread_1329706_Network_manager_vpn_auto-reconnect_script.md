---
title: "Network manager vpn auto-reconnect script"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by b166er on 2009-11-17
Hi
I'm quite annoyed with the way vpn seams to behave. No matter what OS or vpn provider I try - I always seam to get disconnected after a while.

I have heard from other "real" people as well as forums posts and many seam to have experienced the same thing. Dosen't matter which OS or vpn-provider.

I have tried ubuntu (jaunty-32/karmic-64), Mac OSX 10.5.x, and that "other OS" (name starts with Win).

I've tried both openvpn and pptp. (openvpn only in linux)

And it always seams to disconnect after a couple of hours. (sometimes minutes). It might be because of server-load or some "kick-rule" for people who use up allot of bandwidth. Or some bug.

But I don't really care if my vpn disconnects. It's not really a big deal. Because I can always simply click on the network-manager and choose to reconnect to my vpn-connection. No harm done.
Only sets me back about 3 seconds.

Although problems arise when I'm away from my computer.
There doesn't seam to be an "auto-reconnect on disconnect" option anywhere.

But I thought... What if I could find/make a script that does this for me!
A script that checks every other minute if I'm connected to the vpn and when I'm not, it reconnects for me.

But I Don't know anything about scripting with vpn-connections. Does this have to be done through network-manager or are there other apps? and how can it verify if I'm connected to a vpn?


I have some scripting experience. But none in this area. So does anyone wanna help out?

---

### Post by marano on 2009-12-23
Im having the same problem, I would love to see an auto-reconnect option on the network manager!

---

### Post by babarhaq on 2011-10-05
Had the same problem so wrote this tiny script which uses command line vpnc. The script keeps trying to connect until it connects. 
[http://babarhaq.blogspot.com/2011/04/vpnc-auto-connect.html](http://babarhaq.blogspot.com/2011/04/vpnc-auto-connect.html)

---

