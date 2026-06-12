---
title: "Third party Open Source frimware for linksys befw11s4."
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by Sylslay on 2010-02-11
Did not find frimware other than from vendor. I checked openwtr, dd-wrt, tomato frimware.

Have 2 broband routers. Standard wi-fi B. They can work as switch, router or gateway. Please help me and post any idea of good use of them.
It's old hardware.

Lan is 100mb, 
No AP.
Wi-fi is 11Mb, 

1. I can use them as switch for cable lan (on  wi-fi lan not sure yet it will work as switch).

There is not linux in those boxes.

2. But if I connect one of them to home network made from 1 PC and 2 laptops I  will be able to watch movie thru Lan wi-fi, by share folder on PC with huge amount of free space , music and movie.

3.  Internet Connection Sharing with 3G, 
Share internet from laptop with 3G and my LAN made from 2 PC, according to that thred.
Just wrote Ip of laptop as gateway and DNS from Internet prowider in to router, switch of DHCP and add static Ip for lan pc.

[http://ubuntuforums.org/showthread.php?p=8814475#post8814475](http://ubuntuforums.org/showthread.php?p=8814475#post8814475)

4. Use DMZ.

5. Use VPN

Any other idea for home networking for linksys befw11s4:P ?

I have d-link g624t B/G standard working as my internet provider as well , ADLS router with Linux on board.

1) Make router, not gateway.
2) Disable DHCP server
3) Both routers need to be set to the same IP range. 10.10.10.1 and 10.10.10.2 for example or 192.168.1.1 and 192.168.1.2. I can assign a static IP to one of your PCs like 10.10.10.100 and then be able to access the router's config.

So any configuration for use of my boxes will be Appreciate.

I have d-link g624t B/G standard working as my internet provider as well , ADLS router with Linux on board. It can work as bridge.

PS.I don't wanna study Cisco Academy. Just lernt something about networking.

Please close the thread as I read manual and found this How-to

[http://tldp.org/HOWTO/html_single/Linksys-Blue-Box-Router-HOWTO/](http://tldp.org/HOWTO/html_single/Linksys-Blue-Box-Router-HOWTO/)
thx

---

### Post by Sylslay on 2010-02-11
Found something useful: 

You have one router running in your network. This router connects to the internet. Now you want to hook up a second router (e.g. a wireless router to have wireless access) in your network connecting both with an ethernet cable. The following is in most cases the best approach for home networks. You'll find similar answers with some screenshots in the Linksys Easy Answers, e.g. 4579

The setup:

1. Unplug the second router from anything. Connect a single computer to the router. Do not connect the second router to the first at the moment!

2. Configure the router at [http://192.168.1.1/](http://192.168.1.1/)

3. Change the LAN IP address of the second router from 192.168.1.1 to a free address in your LAN (e.g. 192.168.1.2 should be O.K. if the first router is also a Linksys router). The address you change to (192.168.1.2) must not be used by any other device with static IP address in your network nor should be assigned by the DHCP server your network. A default Linksys router uses 192.168.1.1 itself and the DHCP server assigns 192.168.1.100-149.

4. Turn off the DHCP server on the second router.

5. Save the setting.

6. Unplug the computer from the second router.

7. Connect an ethernet cable from a numbered LAN port of the first router to a numbered LAN port of the second router. Do not use the Internet/WAN port on the second router!

8. That's it! If you don't know or don't want to know more about networking you don't have to read the rest here.

What do you have now?

The second router is connected through a LAN port to your existing network. This basically means that the router part of the device is actually not used. So you have a router device that you don't operate as router in your network. Whatever you connect to the second router either through one of the remaining LAN ports or through a wireless if it has one, is directly connected to your LAN. Devices connected to the second router use the DHCP server of the first router to get an IP address. They use the first router directly for internet access. Everything is connected to a single larger ethernet network. Everything is in a single "broadcast" domain.

If the second router is not a wireless one, you basically have a few more ports in your network. In that case it might have been cheaper to get a simple switch/hub instead to extend your network.

Please remember: as the second router is not connected through the Internet/WAN port many configurations and functions of the second router won't work simply because they require an internet connection on the router itself. Some examples are: access restrictions, dynamic DNS service, port forwardings, MAC address clone, the firewall... All these things must be configured on the first router and only there.

Why is this better than connecting the second router with the Internet port?

A router is a separating network element. It separates two networks and allows certain traffic to cross. Sometimes this is necessary in a network setup but for most home networks it only creates a lot of obstacles.

1. In default Gateway mode the second router does network address translation (NAT). This means computers connected to the second router can connect to computers connected to the first router but not in the opposite direction.

2. If you use Router mode on the second router: you have to configure "routes" on the first router and possibly your computer connected to the first router so that IP packets find their way into the subnet of the second router.

3. You have two separate ethernet networks and thus two "broadcast" domains. A broadcast in the first router's subnet reaches all computers connected there. The same applies to the second router. A broadcast will never cross the second router, though. This is an obstacle for applications that depend on broadcasting to locate other computers and services. Windows file and printer sharing is one example here. With the second router in between, computers on one side do not know about computers on the other side. You cannot search your workgroup for the computer on the other side even when they use the identical workgroup name. You will be able to access the other computer using the IP address directly (e.g. \\192.168.1.100\share) but that's usually a hassle and the IP address may change if it is assigned by the DHCP server to the computer. There are ways to deal with some of these issues (e.g. save the host names in lmhosts files...) but all this requires more effort and attention to keep everything up-to-date.

4. Port forwardings become more complicated. If you need a port forwarding (i.e. you want a port on a computer in your network to be accessible from the internet) on a computer connected to the second router you have to setup two forwardings: one on the first router to the second router and one on the second router to the computer.

5. If you have two wireless routers: you cannot roam between both routers without loosing the connection. This is simply because if a wireless computers moves from one router to the other it needs a different IP address.

6. The whole configuration becomes more complicated: you always have to think about where to configure what, e.g. dynamic DNS service, access restrictions, ...

Bottom line: unless you have good reasons why you must have some computers separated from the other computers in your network, there is no good reason to in a home network to do so. For normal home networking with simple to use file and printer sharing it is better to connect the second router as suggested in this post...

---

