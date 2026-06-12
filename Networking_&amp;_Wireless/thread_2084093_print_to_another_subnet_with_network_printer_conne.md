---
title: "print to another subnet with network printer connected to a second router?"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2012-11-14
I would like to do that.
I plugged the Linksys SPS router into the 4 port router.
It connects and gets an IP and assigns 192.168.0.3 to the network laserjet 4000 printer.

However, I can not ping that address and ubuntu can not find the printer.

So what to do?
I include a diagram to show how I would like to hook up the connections.

---

### Post by redmk2 on 2012-11-14
> **sdowney717 said:**
> I would like to do that.
I plugged the Linksys SPS router into the 4 port router.
It connects and gets an IP and assigns 192.168.0.3 to the network laserjet 4000 printer.

However, I can not ping that address and ubuntu can not find the printer.

So what to do?
I include a diagram to show how I would like to hook up the connections.
Why are you using a second router?  A typical subnet for home or small business can handle 254 devices needing IP addressing.  If you only need more LAN ports I would add a 4 or 8 port switch.  Just plug the switch into the port that you have the second router plugged into now and the printer into one of the switch ports.  The printer should be on the same original subnet and available to all computers in that network subnet.

---

### Post by efflandt on 2012-11-14
When you say "another subnet" it sounds like you are probably connected to the WAN side of the Linksys SPA router which does NAT for the printer on its LAN side.  In that case to connect to the printer you would need to connect to the WAN IP of the Linksys SPA as the printer IP and configure port forwarding on the Linksys SPA to forward ports for whichever printer protocols you are using to the LAN IP of the printer.

That can work, but as mentioned it would be easier to use a network switch and have everything on the same subnet.

---

### Post by sdowney717 on 2012-11-15
Just thinking of working with the hardware I have now.
I currently have the linksys SPA voip router hooked to 4 port router with the win7 pc running off the linksys.
This causes in networking gui the machines to be invisible to each other, no icon, although I can get to them by typing in their IP number.

Could you turn off DHCP in the linksys voip router, then the 4 port router will be supplying the IP numbers?

Port forwarding for printing which ones? Interesting to try and you say the printer config in ubuntu would be the IP number of the Linksys. I dont know what protocols I do see where you can enter port numbers in the Linksys, udp and a lot of options.

---

### Post by Morbius1 on 2012-11-15
A network switch would be my solution as well ( It's always hard to argue with redmk2 :) ) so turn one of your routers into a switch by enabling "Bridge Mode" on that router which affectingly turns off the DHCP server on that router. Now the bridged router acts as a switch extending the ports available to the other router and everyone ends up in the same subnet. I do this on my own network. I have an antique wired router and has as one input a wireless router in bridged mode acting as a Wireless Access Point - a switch.

I'm not familiar with the Linksys router ( or any Linksys router ) so I don't know if it can do that but perhaps you can rearrange things a bit as far as which router connects to the internet the other router can be set to bridge mode.

---

### Post by Morbius1 on 2012-11-15
Did a quick search and found this HowTo on setting up a Linksys SPA in bridge mode so it appears it can be done at least for this model number:
[http://www.cisco.com/en/US/products/ps10024/products_qanda_item09186a0080a35e85.shtml](http://www.cisco.com/en/US/products/ps10024/products_qanda_item09186a0080a35e85.shtml)

---

### Post by sdowney717 on 2012-11-15
Ok, put it in bridge mode which is it turns off DHCP

This is the SPA Linksys page screenshot now. I tried putting in the Linksys LAN to match the 4 port router but it always sets to a different subnet, in this case 192.168.2.1
If it is turning off DHCP, why would it put anything in there.
Could it be this Linksys SPA 2102 can not do this? 

My 4 port router is assigning IP's from 192.168.1.100 and up

So then how do you assign an IP address to the HP Laserjet 4000TN?
Would the manually assigned  IP have to be say 192.168.1.115?
Looks like has to be manually assigned? Which I looked into before and supposedly can be done, but my printer options did not match the web site instructions.

---

### Post by sdowney717 on 2012-11-15
ok, there is an admin login to the router
I did that and I get some more options

under networking service you can set to 
NAT
BRIDGE
AUTO

so I tried bridge this time
and now can also set LAN this time to 192.168.1.50 with 50 leases

And now it is working! I can see the printer at 192.168.1.102

---

### Post by sdowney717 on 2012-11-15
Here is screenshot showing network able to view machines
This is much better, less confusing, which was the goal.

So if you have SPA2102, you have to 
log in with admin 
goto Lan setup
select BRIDGE
set LAN IP's to a range which will fit in with your router farther upstream, a range of IP with same subnets but differnt last digits as you dont want issues.

You wont get the NAT-Bridge-Auto option unless you log in as an admin.

This actually does not solve printing to another subnet in my LAN, I solved by adjusting my routers to work in the same subnet.
My Home theater PC downstairs also has another 4 port router, but I dont care to ever print, just watch internet videos and it works well.

---

### Post by redmk2 on 2012-11-15
> **sdowney717 said:**
> This actually does not solve printing to another subnet in my LAN...
The reason is: there is no route to the 2nd subnet from the first subnet.  The 2nd subnet would also need its own interface (i.e. eth1).
 
In non technical terms, when you send traffic with the destination unknown to router (not in the routing table) the router sends that traffic to the default gateway.  In your case it goes to the WAN side (the internet side) and is dropped.  No private IP addresses are routed on the internet (e.g 192 or 172.16 or 10).

[COLOR="Blue"]Edit: A router is a device that is the gateway from one subnet to another.  When you have multiple subnets they are, by design, separated by routers.  The device that you are calling a router is actually 2 devices.  The router and an integrated switch.  When you use "bridge mode" you are tuning off all routing functions and the networking services (DHCP and DNS). [/COLOR]

---

### Post by sdowney717 on 2012-11-16
Google has developed Cloud Printing, which might work to print to your home printer from anywhere.

[http://www.google.com/cloudprint/learn/#utm_campaign=en&utm_source=en-ha-ww-sk&utm_medium=ha&utm_term=google%20cloud%20print](http://www.google.com/cloudprint/learn/#utm_campaign=en&utm_source=en-ha-ww-sk&utm_medium=ha&utm_term=google%20cloud%20print)

Might work to get around home networking but maybe not with layers of routers in between, I dont really know.

I just added my classic HP 4000 and it is showing up.
I will test it out and see. Right now not sure how to use this.

---

### Post by sdowney717 on 2012-11-16
It works for me. 
I think must though be configured thru your PC as a classic printer so your network must be able to use it in order for goole print to work. My HP 4000TN is hooked up directly to a router port.

they have some options classic versus 'cloud ready' type newer design printer.

Scanned copy.

---

