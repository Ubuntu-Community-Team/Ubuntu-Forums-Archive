---
title: "searching for a proxyserver"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by jackel7007 on 2009-09-23
For an upcomming lanparty i have been asked to create "something" which allows the crew to do the following things:

- It has an Easy to use GUI
- Acts as DHCP
- Monitor trafic (amounts & speed)
- Wring the speed of specified users (for instance those who think lanparty's are ment to play WOW on your own, or people who think they have to download "the complete internet"

Now I think i need A proxy server to do all these things (correct me if i'm wrong) 
And then my question is, who has advice for me about what proxy server to use?

If possible Proxy + webserver will run on 1 ubuntu machine

---

### Post by sedawk on 2009-09-23
There seems to be an internet connection, so what hardware
is used to connect to the internet?
A simple DSL-Modem connected to one computer, or a
DSL-router with DHCP, firewall, etc.
I recommend to use a DSL-router so you can use
its DHCP server and its firewall to block outgoing
traffic (with the exception of your proxy server).

You can easily set up a proxy with tools like privoxy.
It might be possible to monitor (and limit) traffic per
client, but that is nothing I ever tried so far.
But keep in mind that games running on the steam-platform
do not work behind a proxy - one of the very annoying things
about steam!

If you only have a computer with a DSL-Modem you have
to setup DHCP on that computer and privoxy will make
sure that people can connect to the internet. If
you do not want a proxy (e.g. because of steam) you
also have to configure this computer as a router
(IP-forwarding). Normally it is turned off.

---

### Post by jackel7007 on 2009-09-23
well no.. 
for the lanparty we rent a space.

there is a modem, which acts as dhcp server.

so we want to be so friendly to give everyone access to the internet, but as mentioned before, some people are abusing that connection for binaries or games like WOW (which i think should absolutely not be played at a lan party :-)

---

