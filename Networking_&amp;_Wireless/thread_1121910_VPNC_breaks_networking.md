---
title: "VPNC breaks networking"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by Temujin_12 on 2009-04-10
I installed vpnc to connect to my corporate Cisco VPN. Connecting worked great.  However after I disconnect (via. vpnc-disconnect), my networking seems to have completely broken.  It is unable to resolve anything.

I've since removed vpnc and resolvconf(?) which was installed with vpnc.

I've tried the following:
 -restarting the computer
 -running "sudo /etc/inid.d/networking restart"
 -restarting the interface (eth0) via ifconfig.

Has anyone run into this that knows how to fix it?  Does anyone know of a command to have ubuntu reconfigure networking from scratch?

Thanks.

---

### Post by Temujin_12 on 2009-04-10
Bump.

Anyone know what might be going on here or now to fix it?  My machine is pretty much useless with out networking.

---

### Post by hartz on 2009-04-14
I've posted a similar question, but I suspect it is the network manager which is screwing up because it doesn't understand resolvconf.

And I got the impression that when vpnc disconnects by itself, it "cleans up better" than what I see when I run vpnc-disconnect.  However of course some times you get a "zombie tun0" with no real vpn connection working, and then you have to run vpnc-disconnect to get it cleaned out.

---

### Post by jtniehof on 2009-04-14
> **hartz said:**
> I've posted a similar question, but I suspect it is the network manager which is screwing up because it doesn't understand resolvconf.
Try installing network-manager-vpnc and managing your VPN connections through there?

---

### Post by hartz on 2009-04-15
> **jtniehof said:**
> Try installing network-manager-vpnc and managing your VPN connections through there?

Incidentally I do have it installed.  But I don't know what to fill in where.

In my conf file I just specify a few items: 
IPSec gateway
IPSec ID
IPSec secret
Xauth username

Now looking at the vpn tab in the network manager, the input fields have different names:
Gateway
Groupname
User password
group password
User name
Domain
Encryption method
NAT traversal

So my question is how do I correlate which of the items in my vpn CONF file goes where in the GUI?

Thanx!

---

### Post by Mordac85 on 2009-04-15
Being on kubuntu and using kvpnc I'm not as familiar with the ubuntu variant, but is there an option to import your Cisco profile?  That has all of the info you're looking for and should get you going.  Worst case you can grab most of the info from there and enter it manually since it's just a text file.

---

### Post by jtniehof on 2009-04-15
Gateway is the name of the VPN gateway/server, same as IPSec gateway in vpnc's conf.
Group name is IPSec ID
User password is your personal password (Xauth password)
Group password is IPSec secret
User name is your personal username (Xauth username)

Domain is I think the same as Domain in vpnc (NT domain to use for login); I've gotten by fine with it blank.
Encryption method I leave on Secure (default) and that should generally work
NAT traversal may require some playing. I connect from behind a NAT and find it works with NAT traversal disabled, not so well with the other options.

I also disable dead peer detection; don't recall why :)

You can leave everything under IPv4 settings on automatic; it'll just switch your default gateway to the VPN on connect and switch back when you disconnect. I haven't been able to get as much flexibility (e.g. using the vpn for one network only) out of Network Manager as I would hacking on the vpnc scripts directly.

---

### Post by Chudilo on 2009-05-06
DNS lookup seems to be broken in VPNC in Jaunty.
Meaning after making a vpn connection DNS information is invalidated .

---

### Post by jtniehof on 2009-05-12
> **Chudilo said:**
> DNS lookup seems to be broken in VPNC in Jaunty.
Meaning after making a vpn connection DNS information is invalidated .
After you make a VPN connection, the DNS information is updated with the information from the VPN server. (I just verified it works on my Jaunty machine.) If the server doesn't provide good DNS information, you can set the DNS manually. Edit the VPN connection and, on the "IPv4 settings" tab, set "Method" to "Automatic (VPN) addresses only" and type in your preferred DNS servers.

If you've hand-edited resolv.conf, that may also be a source of issues.

---

