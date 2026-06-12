---
title: "Problem connecting through KVpnc"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by Urahara on 2009-11-10
Hello,

I tried to setup KVpnc to access two different vpn accounts (pptp), the first was Secure-Tunnel, the second was VPNGates. In both cases I seem to connect fine, as in the program reports that the connection was established but I can't access the net at all.

Using Firefox or any browser would show the "Connecting to website...." message in the status bar.

I checked both "Require MPPE" and "Allow MPPE stateful mode" options and selected "CHAP" as authentication method, and left everything else on default.

When KVpnc is attempting to connect one of the messages that appear in the "log" is "not replacing existing default route via 192.168.15.1" which is my gateway. The other is "cannot determine ethernet address for proxy ARP".

I'm using Ubuntu 9.10 and KVpnc 0.9.3.

Any help is appreciated. :)

---

### Post by dgoosens on 2009-11-10
you might want to check the routing of the VPN.
you should only use the VPN for the demands to that particular network and pass through your regular connection for the other requests.

in Ubuntu (Gnome) this can be done easily within the network-manager under the IPv4 tab > Routes

this is where you enter the addresses and netmasks (you can leave the rest of the line blank) where the VPN should be used.

finally, make sure you check the "Use this connection only for resources on its network"

---

### Post by Urahara on 2009-11-10
I checked that tab, the routes tables was empty. My current usage scenario is to use the VPN connection for browsing the net. Is there a way to configure it in that way?

---

### Post by dgoosens on 2009-11-10
I am not quite sure I understand.
Why do you want to use the VPN to browse the web ?
A VPN is meant for you to access data on a distant network...

However, it is possible...
But then I guess there is a problem with the firewall or the network that your VPN connects to...
Does it allow you to browse through the VPN ?

---

### Post by Urahara on 2009-11-10
I'm not using it for work, I'm using it to bypass the ISP's proxies. Where I live we have restricted access to the net mandated by the gov, the list of sites banned here includes porn, betting, political sites (well...opposition political sites ;) ) and some other sites that I allow us to access the previous sites like proxies for example.

So to have unhindered access to the net, I have to either find a proxy that works, which is hard and most of the times tends to be slow or get access to a commercial vpn provider, hence my subscription to Secure-Tunnel/VPNGates.

Anyway, I remember it working back when I tried it on 8.10 I think, so I dunno why I'm having trouble with it now.

---

