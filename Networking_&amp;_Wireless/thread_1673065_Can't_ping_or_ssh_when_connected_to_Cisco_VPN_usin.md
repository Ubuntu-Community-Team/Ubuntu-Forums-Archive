---
title: "Can't ping or ssh when connected to Cisco VPN using vpnc"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by tgirsch on 2011-01-21
I'm brand-spanking-new to Ubuntu and am having some problems with vpnc-gnome.  When I connect to my company's VPN (it's a Cisco), it connects just fine and displays the broadcast message, but once connected I can't ping anything or ssh anywhere.  Not on the private network, not on the Internet (e.g., google.com), nothing.  I can still browse the web without difficulties when connected to the VPN, but no ssh or ping.  With ping, it properly resolves the host name, but I get 100% packet loss.

Once I disconnect from the VPN, a ping of google.com works exactly as expected.

I don't have any firewalls set up on this host that I'm aware of (unless something is installed and configured by default).

I'm using Ubuntu 10.10, amd64 build.

Has anyone encountered this, or does anyone have any insight into what to try?

---

### Post by tgirsch on 2011-01-22
I should add that I configured the connection using a .pcf file that works flawlessly in M$ Windows, both with Cisco's provided VPN client and with a freeware VPN client I've tried.

---

### Post by MystaMax on 2011-02-26
hello,

I'm having the same exact problem. I did a clean install of 10.10 and can't ping anything on my company's side of the network. 

For this 10.10 install, I used a brand new hard drive. I have a 9.10 install on another hard drive and my VPN works on it.

I also used a .pcf file i grabbed from a windows box to import.

Did you ever find a fix to this problem? If so, you mind sharing?

Thanks.

---

### Post by MystaMax on 2011-02-26
WOW, I don't know how many times i looked at the route settings for the VPN connection in network manager. But, I guess I never unchecked the box that said, "Use this connection only for resources on its network". Its probably the only setting I didn't attempt to change.

Once I unchecked that box, everything worked as expected! I tested http, ssh, and rdp. All worked! I'm typing this message over the VPN now. I'm very happy, and upset it was so easy for me to fix. I had to run a windows virtual machine to get work done. Not fun.

I've attached a screenshot of the window I'm talking about.

Let me know if this works for you.

*Rant:* Regardless, wouldn't you say that checkbox is a little misleading? I assume it means when the PC asks for a resource thats on the internet, don't route over the VPN. Could I be wrong?

---

### Post by SeijiSensei on 2011-02-26
Yes.  Use the VPN connection only to reach resources available only via that connection.  The phrase "only for resources on *its* network" seems pretty clear to me.  By implication everything else, like the Internet itself, is not routed over the VPN.

Some VPN setups are designed for exactly the opposite purpose.  I might run a VPN from a public wifi location and tunnel all my traffic over it to avoid having it sniffed.

---

### Post by vipseixas on 2011-04-01
I had a similar problem, but even with this route option I couldn't get to ping or ssh the servers. 

For me the solution was to change the **NAT option to Cisco UDP at the VPN tab**. Now I can access everything normally.

---

