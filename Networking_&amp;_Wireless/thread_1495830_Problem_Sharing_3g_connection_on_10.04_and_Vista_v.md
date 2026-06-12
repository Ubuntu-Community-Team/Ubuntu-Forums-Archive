---
title: "Problem Sharing 3g connection on 10.04 and Vista via router?"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by mbuotidem on 2010-05-28
Hi, i'm totally new to Linux and Ubuntu. I own a huawei 3g modem through which I connect to the internet. I plan to share the internet from that connection between my Vista pc and another pc running Ubuntu Lucid Lynx. The computer I plan to use to share the internet, let me call it Server, is equalling running Ubuntu Lucid Lynx. My Server perfectly recognises my modem and connects to the internet using it and I can browse.

I plan to connect the routers internet port  to my Server using my servers network card. Then i intend to let the router do the sharing of the internet to the other computers on its own. 

I don't have any idea how to go about doing this. Originally, I tried a direct connection between my Server and the other pc running Lucid Lynx without bothering with the router and using the following settings which i found on an online tutorial:


Server ip 192.168.0.1
netmask 255.255.255.0
and no gateway 


then on the client
client ip 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1
I used open DNS servers for the DNS

However, i was unable to browse the internet from the client even though a connection between the two was established.


Then I thought to myself, why go through this trouble, I have a router so why not go ahead and use it. But then I do not know how to do that. Using the router will enable me to effortlessly connect all my computers irrespective of operating system and ease the network creation process.

thanks.

---

### Post by rollin77 on 2010-05-28
I'm trying to do pretty much exactly what you are looking to do,  although I'm currently having issues with my computers nic card so I  can't say whether or not this method will work, so take this with a  grain of salt until I can confirm if it works nor not.  I believe you  will need to right click on your servers network icon and click **Edit  Connections**.  This will bring up Network Connections, and you should  have one labeled as **eth0** under the Wired tab.  Click on that so  it is highlighted, then on the right, click **edit** and select the  IPv4 settings tab.  In the drop down menu to the right of Method choose **Shared  to other computers**.

You might need a crossover cable if your NIC card doesn't auto sense it  being the wrong cable, because typically you need a crossover to connect  a PC to a PC, or a PC to the WAN link of a router.  

As far as your IP settings go, your server will need a gateway to  connect to the internet.  I'm not really sure about the rest of the  settings, but without a gateway none of your computers will know how to  reach the internet.

---

### Post by rollin77 on 2010-05-30
I just wanted to confirm what I said in my previous post should work, I have pretty much the same setup as you do.  I didn't change any of my IP settins, that's all still set to automatic.  I didn't need a crossover cable either, I'm a bit new to networking and I guess the curriculum I've been learning in class is a bit outdated because my NIC is ancient and it has auto sensing capabilities.

---

### Post by mbuotidem on 2010-05-30
Did you succeed using the system you described? I am yet to try your suggestion but I will. My network cards are very modern so I am sure they would auto detect  but in any case, I am using  crossover cables so that wouldn't be a problem. 


What I am wondering is, does selecting the setting, **Shared to other computers** make my Server pc start carry out the dhcp function? If it does, then my problem would be halved solved because, If you recall, I plan to route the internet through my router too so that my other pc's can connect.

Also, you mentioned not having to change any of your IP settings. You know, if i am using a direct cable connection, that is, my Server directly connected to the other Ubuntu Pc, There are two IP settings involved under IPV4 settings. The IP settings on the Server Pc and the IP settings on the client Pc. Now, I have nothing to do with the IP settings that connect me to the internet, my 3g modem does all that. The only setting I can control is that on eth0, my internal nic which is what you said I am to set to **Shared to other computers**. My question is, what setting do I then set on the client pc? on Ubuntu 10.04, there are several options namely: 
[B]

Automatic (DHCP)[/B], 
**Automatic (DHCP) addresses only**, 
**Manual**, 
**Local-Link only**, and 
**Shared to other computers.** 

If your setup worked, which of those settings did you pick? 
Anyway, I'm off to try it out. And i'll play with each of the settings till I get the one that works and I will be sure to give an update on the method that worked for me.

---

### Post by mbuotidem on 2010-05-31
Hey rollin77. I used your suggestion and chose the option **Shared to other computers** and voila! my client pc was able to browse through my direct crossover connection. I am presently struggling with getting my client to browse through my router. Its proving quite difficult because I am not yet sure of how to configure my router. Thanks anyway. At least, I've moved forward one step.

---

### Post by mbuotidem on 2010-05-31
> **rollin77 said:**
> 

As far as your IP settings go, your server will need a gateway to  connect to the internet.  I'm not really sure about the rest of the  settings, but without a gateway none of your computers will know how to  reach the internet.


Yeah, I guess the reason why i don't need to input a  gateway into my IP settings is that, the 3g stick already connects me to the internet so I don't need a gateway to share the connection.

---

