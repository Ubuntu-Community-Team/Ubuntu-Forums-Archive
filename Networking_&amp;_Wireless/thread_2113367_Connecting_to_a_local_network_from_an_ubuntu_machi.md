---
title: "Connecting to a local network from an ubuntu machine (using ssh)"
date: 2013-02-07
forum: Networking &amp; Wireless
---

### Post by Raafat1991 on 2013-02-07
Hi guys...I want to connect to a ubuntu machine on a local network (behind a DSL modem ) from a ubuntu machine on another different network via SSH .

Also to a ubuntu server ( on the same remote network) from my firefox .


how can i do that ?


thank you .

---

### Post by PowerBarry43 on 2013-02-07
Hi

You can do this one of a couple of ways, either with port forwarding so you'd add a rule in your router that redirects any traffic it gets on port 8022 to port 22 on the ip of your local ubuntu box. Theres tons of material out there on how to do this. The other way is to set up a vpn, you might want to investigate logmein's hamachi linux beta as well as haguichi which is a graphical front end as the linux beta is currently command line only. From there create a network in hamachi and add all machines to it.

[https://secure.logmein.com/es/labs/](https://secure.logmein.com/es/labs/)
[http://www.haguichi.net/](http://www.haguichi.net/)

Hope this helps!

Barry

---

### Post by Lars Noodén on 2013-02-07
To get access to your local network from the outside you'll have to use your DSL modem to forward the desired ports.  In addition to port 22 mentioned above for SSH, to get web access you'll need to forward ports 80 and 443.

---

### Post by Raafat1991 on 2013-02-07
Hi guys...i gone to my DSL modem , advanced , NAT , port mapping and i do what you said to me (about forwarding our ports ) but nothing happened.

Also please tell me what is SSH's syntax to i connect to a local network ( ssh username@aLocalIP i don't think that hhh)


thanks .

---

### Post by Lars Noodén on 2013-02-07
To connect from one machine on your local network to another machine on your local network you only need to know the username and IP number.

```

ssh username@*xx.yy.zz.aa*

```

If that is not working then there is something wrong over on the SSH server.  Either sshd is not running or there is a firewall blocking the connection.

---

### Post by Raafat1991 on 2013-02-07
> **Lars Noodén said:**
> To connect from one machine on your local network to another machine on your local network you only need to know the username and IP number.

```

ssh username@*xx.yy.zz.aa*

```If that is not working then there is something wrong over on the SSH server.  Either sshd is not running or there is a firewall blocking the connection.

Hi...i want from a local network to another different local network .

---

### Post by Lars Noodén on 2013-02-07
The remote local network that you wish to connect to is either behind a router or a jump host.  If it's a router, port 22 needs to be forwarded to the host on that local network you wish to connect to.  Then it's just a matter of connecting to the router and it automatically connects you to the other host.

---

### Post by Raafat1991 on 2013-02-07
> **Lars Noodén said:**
> The remote local network that you wish to connect to is either behind a router or a jump host.  If it's a router, port 22 needs to be forwarded to the host on that local network you wish to connect to.  Then it's just a matter of connecting to the router and it automatically connects you to the other host.

A nice abstaction for my post ):P .

so my post simply how do i enable forwarding to a internal host from a external host.


i'm waiting you guys .

---

### Post by Lars Noodén on 2013-02-07
You need to clarify what you have on the receiving end.  Is it a router?  Then the specifics of port forwarding vary depending on both make and model.  If you have a more general purpose computer, then you can use ssh all the way through.  

Which is it?

---

### Post by Lars Noodén on 2013-02-07
Here is a web site that claims to have instructions:

[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

But it is possible that you specific model might not be listed.

---

### Post by Raafat1991 on 2013-02-07
> **Lars Noodén said:**
> You need to clarify what you have on the receiving end.  Is it a router?  Then the specifics of port forwarding vary depending on both make and model.  If you have a more general purpose computer, then you can use ssh all the way through.  

Which is it?

Really i don't know what is my modem a router or not but i think it's a router .

what about snapshots ?

i'm checking your post about the models

---

### Post by Lars Noodén on 2013-02-07
It's probably a router, which brand and model is it?

---

### Post by Raafat1991 on 2013-02-07
> **Lars Noodén said:**
> It's probably a router, which brand and model is it?

Look below but  i have a newer version 

[http://www.huaweidevice.com/br/productFeatures.do?pinfoId=660&directoryId=2663&treeId=663](http://www.huaweidevice.com/br/productFeatures.do?pinfoId=660&directoryId=2663&treeId=663)

---

### Post by Lars Noodén on 2013-02-07
When you log into it as admin are you able to find where to set the port forwarding?  If HG520 is not listed in the site I posted above, you'll either have to dig around yourself or use a paper manual that might or might not have shipped with the unit.

---

### Post by Raafat1991 on 2013-02-07
> **Lars Noodén said:**
> When you log into it as admin are you able to find where to set the port forwarding?  If HG520 is not listed in the site I posted above, you'll either have to dig around yourself or use a paper manual that might or might not have shipped with the unit.

As i told before i found this label : port Mapping

and i read a paper manual and this is what i read :

```
[FONT=ËÎÌå] Port Mapping[/FONT]
   [FONT=ËÎÌå]a. Introduction[/FONT]
    [FONT=ËÎÌå]When NAT is enabled on the gateway, only the IP address on the WAN side is visible externally. When certain services, such as the FTP service, need to be enabled on a computer on the LAN side, the WAN-side port of the gateway needs to be redirected to the FTP port of the computer on the LAN side. Thus, the host on the WAN side can access the host on the LAN side through this WAN-side port.[/FONT]
    [FONT=ËÎÌå]b. Operation[/FONT]
    [LEFT]You can select between two types of port mapping, that is, **Customization** and **Application**.[/LEFT]
 [LEFT]For both types of port mapping, you should enter the IP address of the host on the LAN side. In other words, you need to specify the LAN-side host to which the services are mapped through the WAN-side port.[/LEFT]
 [LEFT]**Interface**: It is the interface name of the WAN connection. 
**Protocol**: It is the protocol, such as TCP and UDP, supported by port mapping. 
**External port**: It is the source port number used by the external network. 
**Internal port**: It is the destination port number used by the internal network. 
**Internal host**: It is the LAN-side host IP address to which the port is mapped. It is mandatory to set this parameter. 
**External source IP address**: It is optional to set this parameter. If you enter the IP address, it indicates that only the WAN-side host with this IP address can be mapped to the LAN-side host through the port. 
**Mapping name**: It is mandatory to set this parameter.[/LEFT]

```i think that what we are looking for but i don't know what is wrong

---

### Post by Lars Noodén on 2013-02-07
Yeah port mapping and port forwarding are two names for the same activity.  I couldn't find info for the Huawei HG520 at that site, so you might just have to log into the modem (router) and search for the right settings.  What menu are you presented with when you log into the router?

---

### Post by Raafat1991 on 2013-02-07
> **Lars Noodén said:**
> Yeah port mapping and port forwarding are two names for the same activity.  I couldn't find info for the Huawei HG520 at that site, so you might just have to log into the modem (router) and search for the right settings.  What menu are you presented with when you log into the router?

i have several options...i gone to advanced and to NAT and port mapping and i added this rule :

Mapping Name      Interface   Protocol   Remote Host   External Start Port   External end Port   Internal Port   Internal Host   Enable   Remove   SecureShellServer(SSH)___ WAN5_INTERNET_TR069_R_ATM1_0_35 TCP/UDP  22222 22222 22 192.168.1.2 Enable 
where 192.168.1.2 is my machine and  the remote host is empty .

---

### Post by Raafat1991 on 2013-02-07
Also after typing this command :

```
ssh raafat@myIP -p 22222
```

this is what i got :

```
ssh: connect to host 94.99.x.x port 22222: Connection refused
```

---

### Post by Lars Noodén on 2013-02-07
What about on the inside from within that LAN?  Can you connect from another machine on the same LAN to that machine using port 22?

---

### Post by Raafat1991 on 2013-02-07
> **Lars Noodén said:**
> What about on the inside from within that LAN?  Can you connect from another machine on the same LAN to that machine using port 22?

Yes , i did that many times .

---

### Post by Raafat1991 on 2013-02-07
Does generally accept ssh server external connections ?

Also i disabled my modem's firewall and my iptables has no rules .

---

### Post by Raafat1991 on 2013-02-08
Guys i'm here....

---

### Post by Raafat1991 on 2013-02-09
Hi...about a ubuntu server i succeed . but about SSH until now i did'n try anything , i will try it and i will replay . 

thank you

---

### Post by Raafat1991 on 2013-02-11
Thank you [PowerBarry43 Lars Noodén ]("http://ubuntuforums.org/member.php?u=1269383")
[]("http://ubuntuforums.org/member.php?u=1269383")

---

