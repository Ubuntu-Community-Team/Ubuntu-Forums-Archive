---
title: "Redirect VPN connection though proxy"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by mridang on 2009-09-16
Hi Guys.

I need to access a web server through a VPN. Once I set up the VPN connection this works just fine but in one scenario I'm behind a corporate firewall that doesn't let me initiate VPN connections. I can however proxy to another computer though.

I have an Unbuntu server running in an open network i.e. no VPN restrictions. Would it possible to somehow proxy to that home pc and that would redirect all HTTP connections thorough the VPN tunnel to the webserver that i need to access?

I'm pretty new to Ubuntu but nerdy enough to understand tech terms.

Any help from the gurus?

Mridang.

---

### Post by lvlint67 on 2009-09-16
> **mridang said:**
> Hi Guys.

I need to access a web server through a VPN. Once I set up the VPN connection this works just fine but in one scenario I'm behind a corporate firewall that doesn't let me initiate VPN connections. I can however proxy to another computer though.

I have an Unbuntu server running in an open network i.e. no VPN restrictions. Would it possible to somehow proxy to that home pc and that would redirect all HTTP connections thorough the VPN tunnel to the webserver that i need to access?

I'm pretty new to Ubuntu but nerdy enough to understand tech terms.

Any help from the gurus?

Mridang.


Does the corporate firewall all ssh? If not what about doing something crazy like running the home ssh server on port 80?

if it does allow this then you should be able to tunnel through the ssh session. I have to do this on campus to hop on irc. -_- Just monitoring a game server... not downloading ANYTHING but you know how strict firewalls go. :(

----------------
if that falls through... What i did back in highschool:
Setup apache+php on the home server

Write or Find a php script that will do all the forwarding...
(IE: you type a url into a text input on the home server's page and the PHP script connects to and retrieves the desired page)
There are pre-built scripts that will do this.

---

### Post by mridang on 2009-09-16
Nopes. I can't seem to SSH out. I've tried everything. I don't know how they do it — maybe packet level filtering or something.

I found [this]("http://www.exiledmind.net/vpn-tunnel") on a page but I don't know if it is what i'm looking for. He also mentions something about fixing up routing tables and so on. I'm not too good with unless I have explicit instructions.

---

### Post by lvlint67 on 2009-09-16
I would give up on the vpn thing then.

Have you ever set up a webserver with php support on ubuntu?
if so:
 [http://sourceforge.net/projects/php-proxy/](http://sourceforge.net/projects/php-proxy/)

Aside from filtering the work 'proxy' I can't see a feasible way for the firewall to block that.
It's a sort of dirty solution but without reprogramming the firewalls it may be the most feasible.

---

### Post by fwre01 on 2009-09-16
mridang, firewalls can filter traffic at layer 7 (ie, the actual payload of the packet) but mostly they filter at layers 3/4. (IP address and Port number). SSH tunneling is a great way of getting around corperate firewalls, but if they are blocking port 22 it wont work. Have u tried changing the default SSH port number from 22 to something a little less well-known? Then the SSH tunneling option is once again viable. The sshd.conf file I believe allows you to do this.

---

