---
title: "Help me setup a simple network for ssh'ing, please?"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by ramidavis on 2010-03-01
All i really want to do is be able to ssh into my other linux system. I am **not** interested in internet sharing, or even file sharing.
My situation is as follows: 

[linux laptop with unused ethernet port]-windows-mobile-ppc connected by usb for internet-tehtering [linux running on my wii accross the room]-nintendo lan adapter

I want to be able to ssh login to my wii, from my laptop. That is all i want. Do i need a router in between the two for this, or can i just connect them with ethernet cable?
No samba, no nfs, no fancy stuff. Just want to be able issue commands from laptop to my wii. (if you are wondering 'how in the heck do you run linux on your wii?', just go to the gc-linux [website]("http://www.gc-linux.org/wiki/Main_Page"))

---

### Post by UrBob on 2010-03-01
Well, if you want to connect two computers directly to each other, you will need a cross-over Ethernet cable. This can easily be made up with the right tools, but you might have to shop around to get a sensible price for a ready made one. (I have a good supplier in South Yorkshire, England who supplies mail order or collect, [http://www.electroconnection.co.uk](http://www.electroconnection.co.uk)).
 
I think you will probably have to configure the IP addresses manually, unless one of the machines provides DHCP services.
 
Hope this helps.

---

### Post by ramidavis on 2010-03-01
Thanks. Yes, i think the wii-linux is configured by default for DHCP.
Would you mind telling me though, how, if i needed to do so, to change my ip address? But i am pretty sure it is set up for DHCP, so hopefully i should not have to mess with that. Thanks for the help.:D

---

### Post by ICEB3AR on 2010-03-01
What exactly do you mean it is set up for dhcp ? I do not really think that your wii has a dhcpd-server instead it would have a dhcp-client. That means you have to ste up a dhcp-server on your computer or you have to made the connection static.

Setting up dhcp-server: [https://help.ubuntu.com/community/dhcp3-server]("https://help.ubuntu.com/community/dhcp3-server")

Making Static Connection: [https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html]("https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html")

---

### Post by ramidavis on 2010-03-01
Not tot be rude, but the following is from the [setup instructions]("http://www.gc-linux.org/wiki/WL:whiite-linux#Secure_Shell_.28ssh.29"):
[I]If a Nintendo RVL-015 LAN adapter or compatible adapter is attached to your Nintendo Wii console, the whiite-linux system will try to configure the adapter using DHCP on the existing LAN.

Also, since whiite-linux-1.10 and when booting via BootMii, the /root/whiite-ez-wifi-config tool can be used to configure the internal WLAN card of the Nintendo Wii according to your wireless network security settings.

If a network card is successfully configured, the already installed Secure Shell server of the whiite-linux system can be used to logon to the system.

Use a ssh client to connect to the IP address assigned to your Nintendo Wii console and introduce your credentials. [/I]


Which is why i said that it is setup for DHCP in my last post. I just was not sure if i needed a router in between the two or not. Thanks again.

---

### Post by Iowan on 2010-03-01
> **ramidavis said:**
> 
*... the whiite-linux system will try to configure the adapter using DHCP on the existing LAN. * Sounds like it will try to get an address via DHCP.  But also sounds like there's a tool for manual configuration. A router shouldn't be required if you have a hub/switch/crossover.

---

### Post by ramidavis on 2010-03-02
I knew this was going to be over my head. I got the cross over cable in place, i booted the wii into linux, and it is trying to 'dhcpdiscover on 255.255.255.255, port 67' and getting nowhere. I have no idea how to configure dhcp, client _or_ server side. Would i be better off just setting each system a static ip address? And if that is the case, would i just follow the instructions [here]("https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html") on each of the 2 systems, but input a differnt address for each? So on one machine i would have /etc/network/interfaces:

iface eth0 inet static
	address 192.168.0.2

and on the other machine i would have /etc/network/interfaces:

iface eth0 inet static
	address 192.168.0.3

Then, i should be able to do  $ ssh root@192.168.0.3 right?
Or am i just all screwed up in the head?:confused:

---

### Post by ICEB3AR on 2010-03-03
Not to be rude, but it is exactly as I already said. ;)

Your Wii tries to get the Network-Information (Ip-Address etc.) from a DHCP-Server in your network. Your Network only consists of your Wii and your Computer, which means your computer has to deliver the network-information for your wii (== dhcp-server), if you want to use DHCP.

But for you it should be enough to just made the Connection static instead of using DHCP. So you can just follow the guide Which you found and your solution should work. For sure your Computer has to have another number at the end of your IP-Address then your Wii has, else where should your Computer know which device is meant when you address the ip. (Easy example: When you and your neighbour have the same House-Number where should the postman know where to put the post in? ;) )
If that above would be your complete /etc/network/interfaces you should add:
```
 netmask 255.255.255.0
```

---

### Post by ramidavis on 2010-03-03
Thanks everyone, for getting me up and going. I do have 1 more minor issue though: i was able to ssh into the wii linux, but when i tried to ssh into my laptop, i get 'ssh: connection to host 192.168.0.2 port 22: connection refused'
Would anyone mind telling me how to open that port on my laptop so i can login both ways? Big **thanks** to everyone for putting up with me and helping me out!:popcorn:

---

### Post by ICEB3AR on 2010-03-03
For that you have to install openssh-server on your Laptop.

```
sudo apt-get install openssh-server
```

Check out [https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html")

---

