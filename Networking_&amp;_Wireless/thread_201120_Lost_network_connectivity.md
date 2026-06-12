---
title: "Lost network connectivity"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by Scaramanga19 on 2006-06-21
I have a fresh install of Ubuntu Dapper 6.06 (server install from ISO) on a Dell Poweredge 1850, there are no other O/S installed.  When I originally loaded Dapper, I had the server located in my office, and was able to connect via Putty from my Windows XP box.  When I was ready to move the server to the 
networking area, I exited my session within Putty, closed Putty, shut down the Dapper server, and moved it.  We only have one subnet in this location, so the server is still connected to the same bank of switches that it was previously connected to.

Here is where the problem starts.

Upon booting, the server will no longer connect to the network.  I see an error line that says “Configuring network interfaces FAIL” during boot.  I checked my /etc/network/interfaces file, and it shows the following:
----
# The loopback network interface
  auto lo
iface lo inet loopback

#The primary network interface
  auto eth0 
iface eth0 inet static
address	   192.168.1.5
netmask	   255.255.255.0
network    192.168.1.0
broadcast  192.168.1.255
gateway    192.168.1.250

# dns-* options are implemented by resolvconf package, if installed
dns-nameservers	198.6.1.60
dns-nameservers 198.6.1.10
----

Since everything looked okay to me, I tried /etc/init.d/networking restart, and received the following message:

----
*Reconfiguring network interface...
/etc/network/interfaces:18: duplicate option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:18: duplicate option
ifup: couldn't read interfaces file "/etc/network/interfaces"              [fail]
----

Has anybody else encountered a problem like this?  Any suggestions on how to fix it?  On the surface, the only thing that has changed is the location of the server, and it is still on the same subnet.  There is very little installed on the server so far, other than ssh, and the original Putty connection seemed to 
work fine.

---

### Post by Slim Odds on 2006-06-21
[quote=Scaramanga19]
Since everything looked okay to me, I tried /etc/init.d/networking restart, and received the following message:

----
*Reconfiguring network interface...
/etc/network/interfaces:18: duplicate option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:18: duplicate option
ifup: couldn't read interfaces file "/etc/network/interfaces"              [fail]
----
[/quote] 
What does this file (/etc/network/interface) look like? Line 18? Duplicate option?

---

### Post by Scaramanga19 on 2006-06-21
That was it Slim!  

I had posted the contents of /etc/network/interfaces earlier in my post, but I did not show the line numbers.  Lines 18 and 19 are:
...
dns-nameservers 198.6.1.60
dns-nameservers 198.6.1.10
...
I deleted the 2nd dns-nameservers entry, and I was back on the network.  

So I have learned that you cannot use dns-nameservers as the heading for 2 or more different entries in /etc/network/interfaces, even if you have different numbers for the addresses.  I also have seen a number of replies where the dns nameservers are listed in the /etc/resolv.conf file. 

For a setup where you want your Dapper server to have a static IP and static DNS nameservers, should you be setting the values for the nameservers in the /etc/network/interfaces or the /etc/resolv.conf files?  Or should you be adding the addresses to both?

Thank you again for the reply, I'm back to learning Ubuntu!!

---

### Post by Slim Odds on 2006-06-21
[quote=Scaramanga19]For a setup where you want your Dapper server to have a static IP and static DNS nameservers, should you be setting the values for the nameservers in the /etc/network/interfaces or the /etc/resolv.conf files?  Or should you be adding the addresses to both?[/quote] 
I don't know, but one of the great things about linux is that everything is there for you to see. For example, all of the startup scripts are just bash shell scripts. So go to /etc/init.d/ and have a look. They're not that hard to follow. Most of the scripts call other scripts and read some of those config files you were mentioning.

---

