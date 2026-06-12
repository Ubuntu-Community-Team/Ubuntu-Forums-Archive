---
title: "adding a second gateway and network"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by PM47 on 2012-07-17
I have two networks, private on 192.168.0.x and business on 192.168.1.x. The two are linked with an IpFire box providing secure access from the private to the business network as this currently hosts our ADSL modem and mail server which serve both networks.

I'm currently trialling a new business network, on 192.168.2.x, and want to temporarily connect this to the private network with a second IpFire box. The original IpFire box has a green IP address of 192.168.0.102, the new IpFire box has a green IP address of 192.168.0.103.

How do I configure a workstation (running Ubuntu 12.04) on my private network with access to both business networks ? The current network setup has the gateway and DNS addresses set to 192.168.0.102. I've tried editing the 'wired connection 1' setup, adding the new IP addresses and routes, but can't quite see how to add the second gateway and network details to get it all to work ?

Thanks for any help.
Paul

---

### Post by Sergius14 on 2012-07-17
You shouldn't have multiple gateways in any device/OS to access diferents networks.

You may have it as backup and only to access the same networks.

If you have to access different networks behids that gatewais, it is very likely to only works the first one or randomly (depending on their respective metrics).


But you can have as many IP address as you want.

What you can have is a second IP address to access Bussiness Network only and keep one gateway to access LAN & internet.

If your bussines have serveral internal networks (vlans/dmzs, etc.) you are in trouble..... in that case you have to manually add each routes.

---

### Post by nothingspecial on 2012-07-17
Prefix changed from lubuntu to ubuntu.

---

### Post by redmk2 on 2012-07-17
> **PM47 said:**
> I have two networks, private on 192.168.0.x and business on 192.168.1.x. The two are linked with an IpFire box providing secure access from the private to the business network as this currently hosts our ADSL modem and mail server which serve both networks.

I'm currently trialling a new business network, on 192.168.2.x, and want to temporarily connect this to the private network with a second IpFire box. The original IpFire box has a green IP address of 192.168.0.102, the new IpFire box has a green IP address of 192.168.0.103.
Is this what you had in mind```

           ISP
             |
pvt(0.0)-->IpFire<--(1.0)bus-->IpFire<--(2.0)bus2
```> 

How do I configure a workstation (running Ubuntu 12.04) on my private network with access to both business networks ? The current network setup has the gateway and DNS addresses set to 192.168.0.102. I've tried editing the 'wired connection 1' setup, adding the new IP addresses and routes, but can't quite see how to add the second gateway and network details to get it all to work ?

Thanks for any help.
Paul

If you have a host on the business (1.0) network with the gw on that same network, then you need to add a static route to the 2.0 business2 network on that host.  See [**_[COLOR="Blue"]here[/COLOR]_**]("https://www.google.com/search?q=route+add+ubuntu+&btnG=Go!") for ideas.  You can add a route to a single host 
```

route add -host 192.168.2.1 netmask 255.255.255.0 dev eth1
```
...or a whole network ```
route add -net 192.168.2.0 netmask 255.255.255.0  dev eth1
```

Note there is NO gateway in these statements as you are not going through the gateway.

---

### Post by PM47 on 2012-07-18
Thanks for your replies, it seems this is not as simple as I'd hoped. As this is only a temporary arrangement to set up and test the new hardware before it replaces the old I don't want to start adding routes and the like to a currently working system. 

Thanks again.

---

### Post by PM47 on 2012-07-18
Just as a matter of interest, I've found a workaround that appears to allow me to set up and test just about everything I need to before the new hardware goes live. I've attached a USB network adapter to my workstation on the private network and connected the network side to the new business network, effectively in parallel with the new IpFire box. I can access the IpFire setup pages as normal from the private network and the IpFire box can access the new business network as expected. The network traffic from the private network to the new business network passes through the USB adapter instead of the IpFire box. The downside of course is there's no security between the two networks, but until the new network goes live this is not a problem, when it does I just have to check the IpFire box is acting correctly as a gateway. Problem solved :-)

---

