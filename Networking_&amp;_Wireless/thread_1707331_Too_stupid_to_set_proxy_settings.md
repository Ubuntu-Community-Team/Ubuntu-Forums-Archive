---
title: "Too stupid to set proxy settings"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by hartz on 2011-03-15
Good day.

I have a weird-ish problem.  At home and on the road I have a direct connection to the internet.  At the office I have to go via a Microsoft ISA proxy server.

Empathy works everywhere, but I always need to manually connect, by which I mean it always assume there is no connection when things change, until I click the Connect, and then a few moments later it is working again.  I assume that the office firewall server allows xmmp to pass through.

Firefox works using QuickProxy, so I can enable/disable the proxy depending on where I am.  I have my Windows network login name and password set in the Firefox network settings.

Everything else have a problem.

1. I have not tested bittorrent recently.
2. Synaptic, Update-manager, wget, and so on stumbles over ISA authentication failures.

I have tried setting environment variables in /etc/bash.bashrc with limited effect.  No setting (direct connection) results in a timeout;  Setting the proxy settings gives the 407 error.

I have tried the Gnome Network Proxy Manager with essentially the same result:  A time-out if I set a direct connection, and an authentication failure when I set the proxy.

I have tried a wget with a .wgetrc file with the same results.

I have installed the ntlmaps proxy.  Adjusting the proxy settings to localhost:5865 to use it as a proxy service (in any of the above places) gives me the same result:  Proxy server returns an authentication required / failed result.

I have briefly tried examining what is going on on the wire, comparing the packets between the firefox requests and those of the other protocols, but I am still stumbling around in the dark here a bit.  Isn't there something easier than wireshark?  I have not yet tried this with the ntlmaps solution active, but for other cases it looks like the authentication information is left out of the http request packets.  I might just not be looking in the right place though.

I don't realy think that I should be truing to debug at the packet layer for this kind of problem, I decided to first post here for some advice before continuing.  So ... any takers?

Thanx,
  _hartz

P.S. Right now I'm reduced to manually downloading software from packages.ubuntu.com, followed by dpkg -i

P.P.S I almost forget - the reason why I think it is weird-ish, is because I get the feeling that the proxy setting I set takes, but the username/password is ignored.  Is there another hidden place where this can be set?  Regarding this, when changing the proxy settings via gnome proxy settings, I have little confidence in whether it works.  How do I know that there is no residual of a setting left?  I generally open a new shell and check whether there is env variables left over and it SEEMS TO have taken effect, but I can't be sure.  In particular the gnome proxy setting tool authentication process seems a bit buggy...

P.P.P.S package management times out on my direct connections as well, as if gnome proxy settings doesn't clear everything properly.

---

### Post by hartz on 2011-03-15
Oh and another thing:

In firefox I have not specified an NTLM domain name, but it works.

For the other solutions I have tried it with and without a domain name, always the same results.

FWIW to simplify matters I have set a password which does not contain shell special characters.

---

### Post by hartz on 2011-03-16
By the way, does anybody else experience the problem with Empathy not automatically re-establishing its connection?

  (And BUMP)

  _h

---

