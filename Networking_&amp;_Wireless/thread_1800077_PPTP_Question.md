---
title: "PPTP Question"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by Jake.Debord on 2011-07-08
Okay, I have been wanting to switch from my routers VPN to my headless linux box VPN. I have everything setup in the PPTP and then forwarded the ports to it.

Heres the kicker.

My APPLE Iphone connects to the VPN without a problem at all. Views Intranet pages etc.

My Windoz XP is kicking and screaming and one error after another. :(
This is my setup on XP:
I entered Ip
Entered exact same credentials as used for connecting with my iphone
turned off "use  gateway on remote network"
Changed type to PPTP VPN


Any tips for connecting my xp machine to this PPTP server on linux?

---

### Post by poolet on 2011-07-08
Check the following link:::

[http://pigtail.net/nicholas/pptp/](http://pigtail.net/nicholas/pptp/)

---

### Post by Jake.Debord on 2011-07-08
Thanks, I appreciate the advice, but it doesn't really contain anything about setting up the windows side to the VPN. I have the Linux PPTP server setup and can access it with Iphone. I just have the windows VPN part messed up in some way.

---

### Post by Jake.Debord on 2011-07-08
*SOLVED*

Followed this guide:
[http://inebium.com/post/vpn-linux-pptp-windows-client](http://inebium.com/post/vpn-linux-pptp-windows-client)

It was my CHAP settings for windows on the server side that were out of whack.
Followed this guide, then created a fresh new VPN connection from XP machine and bam.

The only thing to watch out for on XP is to go under security>advanced> "uncheck" use remote gateway

---

