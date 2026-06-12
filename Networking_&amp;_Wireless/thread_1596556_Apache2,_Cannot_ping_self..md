---
title: "Apache2, Cannot ping self."
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by ironic.demise on 2010-10-14
I had a website running for a while on this computer, I'm now using 10.10 but this problem occurred near the end of 10.04.

I set up Apache, If I localhost I get the website but from another computer on the internet I cannot reach my computer, it times out.

UFW is disabled for now.

I thought it was because my ISP (Sky) blocked port 80 (As to whether they do or not, I have no idea but it worked quite recently).

On another computer I tried ping and it failed, from my own computer I ping myself, the router and google and they all worked but when I tried to ping the computer I used to ping myself, I got errors?

Can anybody tell me what's wrong as I an't see any obvious thing I did differently in setup?

---

### Post by ironic.demise on 2010-10-21
I've re-installed the system, Apache2 and I have the same problem remaining, So I assume it's a router firewall.

Does Sky block port 80 (I have tried other ports and it's not working)
and the router is set to port forward to my pc.

---

### Post by CharlesA on 2010-10-21
Try forwarding a different port number, like 8080 or 8880 or something and see if you can connect.

You can keep the port set in apache to 80 and just change what port gets forwarded.

Have you tried running something like shieldsup, to see if those ports are actually being shown as open?

---

### Post by ironic.demise on 2010-10-21
First I checked Shieldsup, Something I'd never came across before.
Shieldsup said that Port 80 is open.
On my router I've set port 8880 to forward to my internal ip. (see SS).
I'm about to test it on another machine.

Thanks for the heads up on the shieldsup, atleast I know that now it's a router setting and that the ISP didn't block the port.

---

### Post by CharlesA on 2010-10-21
Just for the heck of it, I pinged the domain that you listed in yer signature and it spit back "Destination host unreachable." Have you made sure that yer ip address hasn't changed, or that dyndns is up-to-date?

What I would suggest doing is this:

Run an nmap scan from another machine on the network to the box with Apache and whatnot running to see if those ports are open.

If they are (and they should be if everything works internally), try using the standard ports and connecting from the outside. Shields up or nmap would work for scanning for ports from the internet.

EDIT: If the port forwarding stuff isn't correct, it won't work. The firewall rules look.. off somehow, but since I haven't worked with that specific type of router before, I don't know what they should look like.

Check [here]("http://portforward.com/") for a good site with info on port forwarding and whatnot.

---

### Post by ironic.demise on 2010-10-21
> **CharlesA said:**
> Just for the heck of it, I pinged the domain that you listed in yer signature and it spit back "Destination host unreachable." Have you made sure that yer ip address hasn't changed, or that dyndns is up-to-date?

What I would suggest doing is this:

Run an nmap scan from another machine on the network to the box with Apache and whatnot running to see if those ports are open.

If they are (and they should be if everything works internally), try using the standard ports and connecting from the outside.

I just tried connecting to the ip from another machine on the internet and had no joy.

my IP is 90.208.141.171.
I've double-checked the DynDns account with my externally IP to see if it's keeping track and every few days it's still been updated properly...

The other machines on my network are running windows and I've been unable to connect through a liveCD because they lack the network card drivers, When I get chance I will try and use an ethernet cable to connect them to the router and then nmap scan the network, until then there's not a lot I can do to troubleshoot the problem.

The port is open, the router IS updating dyndns and I have tried to connect via IP before, the router is also set to port forward 80 and 8880 to my ip, which I double checked with ifconfig and iwconfig.

ufw is still inactive, the website DOES work internally, I'm getting the default html page from Apache.
I'm connecting via [http://localhost](http://localhost), if I input my ip, the router loops me into it's web settings page.

---

### Post by CharlesA on 2010-10-21
Good luck getting to the bottom of it.

If port 80 shows as open, and apache is listening on that port, it should connect fine. That's the confusing part.

---

### Post by ironic.demise on 2010-10-21
> **CharlesA said:**
> Good luck getting to the bottom of it.

If port 80 shows as open, and apache is listening on that port, it should connect fine. That's the confusing part.

Tell me about it, nothing I've tried shows any good.

[edit]
I've changed the settings to:
inbound,80,lan:myinternalip,wan:all

I hope this works.

---

### Post by CharlesA on 2010-10-21
Hope it'll work for you. :)

See if it writes anything in the logs about connection attempts.

EDIT: Are you putting in the subnet mask too? That might be messing with it.

---

### Post by ironic.demise on 2010-10-21
I'll let you know if it worked ;)

---

