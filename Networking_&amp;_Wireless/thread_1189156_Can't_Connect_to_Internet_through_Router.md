---
title: "Can't Connect to Internet through Router"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by Dead_$partan on 2009-06-16
Hi Guys was wondering if someone can help.

I have a Dell XPS M1710 notebook, has an Intel Pro Wireless 3945 ABG card in it, it hooks up to a D-Link DSL-G604T wireless DSL router.

I have 2 HDD's for this system, so popped 2nd one in installed Ubuntu 9.04, all seemed to go fine, detected WiFi card be default and let me hook up to the wireless router fine but im not able to get any web pages up or access the internet in any way(tried to run the system updated but couldnt connect either).

The router is set up for static addressing and MAC address filtering, plus WPA security but this is the same system, there is only one,  im just swapping out HDD's between Linux and Windows.  

When I put my windows HDD in its all good, but on Linux it just doesnt connect to the net.  I can connect wirelessly to the router with no issues, login to it make changes so the wireless security and IP details seem fine, have disabled the firewall in the router and get the same issue.  Cant think of anything else, could someone help please?

Many Thanks.

---

### Post by dnairb on 2009-06-16
It's possible this is a DNS problem.

Try the following as an address in your browser.

74.125.65.99

(It should open google.com)

Also - which Ubuntu are you using?

---

### Post by Dead_$partan on 2009-06-16
Hey,

Thanks for getting back to me.  Yes it seems I can access google using the IP, I can also get full internet connectivity via my NIC so it is specific to the WiFi card.  I am going to delete the settings in network manager for the WiFi and try again.

---

### Post by chili555 on 2009-06-17
The ability to access websites by number but not name is a sure symptom of an incorrect or missing DNS nameserver setting. The DNS nameserver translates the name, [www.google.com](www.google.com), for example, to the IP address, 74.125.157.99.

If you set up a static IP address, which it appears you have:> The router is set up for static addressing You are responsible to supply a correct nameserver. If you used DHCP, one would be provided for you by the router, modem or other DHCP server. 

When you gave the static IP address to Network Manager, did you see a space to fill in DNS nameserver? The address of the router or other access point, 192.168.1.1, for example, will usually work.

---

### Post by Dead_$partan on 2009-06-18
Hi Chili thanks for the reply.

I was using the 1.1 address for the DNS server when putting in the details, for some reason it wont work on WiFi but does on the NIC.  I have set the router up for DHCP to test and it seems to be better but the system will all of a sudden lose the DNS info and will refuse to display web pages unless I put the IP in.  Restarting the router seems to resolve this but it never happens on windows so this seems to be an issue specific to 9.04.

The network connection also seems slower in Ubuntu via LAN or WiFi that it does in windows, dunno if that is a seperate issue or if it may be tied to the same thing, im doing some digging around the forums for similar issues.

---

