---
title: "confusing VPN connection"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by newway on 2009-04-27
ok first of all this is not technically a Ubuntu problem, but it helped confusing me.

I work at a University where they have a VPN server that I need to connect to at home. 

I have 2 laptops at home, one running windows XP & ubuntu,
one running Vista & ubuntu. I have a wireless router in my flat that i use to connect to the internet, I also have permission & access of my neighbour friend's wireless (good it is unlimited).

Neither Windows XP nor Vista can connect to the VPN using my own wireless(Error 619 blah blah...). But I can with my friends wireless network. So immediately i believe my router is blocking the connection.
I double check the PPTP, IPsec passthough and shut off any firewall settings but still no help. I also enabled DMZ and no help either.

Things got interesting when I was using Ubuntu, in ubuntu(8.04 & 8.10) i use vpnc package, both of my laptops can connect to VPN without any problem using both wireless networks. This shed some light on me and I downloaded Cisco VPN client for windows and vola! it worked on both of my XP and Vista machines.

although "solved", i am still haunted by this weird behavior in windows:

If I just switch wireless networks, VPN works on one (my neighbours) but not the other(mine), I promise I didn't change any VPN settings/options

If I switch VPN clinet software, VPN works on Cisco VPN client but not the windows embeded one.

I am very confused and hope if anybody out there can help me diagnose?

---

### Post by version7x on 2009-05-02
I find your post almost as confusing as the situation you found ;)

Actually I just havent had any coffee yet.

One thing that's bound to cause confusion is that your microsoft client and vpnc use totally different (incompatible) technologies.  If you want to connect to a Cisco vpn with windows(or mac) you need a cisco compatible client.  The one in windows is a pptp type of vpn.  I believe the term for cisco's is IPSec(not sure on the lingo there).

If you need to connect to cisco, vpnc is your option on linux.  If its a windows vpn solution, you'll need a pptp client (like network-manager-pptp).

I am completely astounded that the windows client worked on a different network.  Might be that there are a couple of different vpn's you might be connecting to?  I'm completely lost there!

Hope that helps a little!  I know I'm confused :)

---

