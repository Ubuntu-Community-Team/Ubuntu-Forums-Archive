---
title: "Wireless file sharing"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by kumoshk on 2009-03-24
So, I have a laptop and a desktop. They both have functional wireless cards and normal network cards. I have some shares on both computers. They work fine on the wired connections. However, when I try wireless (via the same hotspot) the shares don't show up at all. How do I fix this?

I should note, though, that daap is still functional through Rhythmbox between the two computers (enabled through gconf-editor), on the wireless connection.

I'm using Jaunty alpha 6 (though it's been updated with whatever updates came out today) on the desktop and Intrepid Ibex on the laptop&#8212;the result is the same on both computers.

---

### Post by kumoshk on 2009-03-25
I found a way to do this (works for both wirless connections and wired through a router instead of a switch).

Just right click on the network connection icon. Go to edit connections. Find the connection you want. Edit it. Go to the IPv4 Settings tab. Click on the Routes... button. Add the routes there. Use ifconfig to get the information. I'm not sure if I put the right 'address' in (I was guessing that was my IP address of the computer I'm using, and so that's what I did), but it still worked. I put the IP address of the computer I wanted to access through the network in the gateway part. I had to either log out or restart my computer when I tried it for the wireless connection, but it worked automatically without that for the wired router connection.

---

### Post by kumoshk on 2009-03-25
Now, I want to do something else. I want to be able to access my wired connection from my wireless connection. The wireless connection comes from a router plugged into a switch that the wired connection is plugged into.

Is this possible?

---

### Post by BkkBonanza on 2009-03-25
Hmmm. Isn't that what this network thing is all about... you just need to configure it correctly and it should do what you want. Make sure your machines have ips on the same subnet, or use DHCP to get you all on the same page.

---

### Post by kumoshk on 2009-03-25
> **BkkBonaza said:**
> Hmmm. Isn't that what this network thing is all about... you just need to configure it correctly and it should do what you want. Make sure your machines have ips on the same subnet, or use DHCP to get you all on the same page.

Can I put them on the same subnet, if they are different, through software means? I thought DHCP was the default that I'm already using. Or do you mean something different that requires configuration?

---

### Post by BkkBonanza on 2009-03-25
Your router should allow having wireless and wired clients on the same subnet. In which case they should all be talking to each other. There may be a setting you have to check that the assigned addresses are on the same net. Or it could be that you need to specify the network for each lan and wlan and they should match.

If you think they are on the same network (subnet) then try using ping to see of they can reach each other.

eg. using whatever real ips you have,

from machine 192.168.0.1 try,
ping 192.168.0.1

from machine 192.168.0.1 try,
ping 192.168.0.2

Both those tests should give responses that don't say "unreachable".

---

