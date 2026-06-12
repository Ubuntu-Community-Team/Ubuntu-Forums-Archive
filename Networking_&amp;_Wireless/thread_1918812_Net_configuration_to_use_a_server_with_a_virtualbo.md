---
title: "Net configuration to use a server with a virtualboxbox"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by esbrinartot on 2012-02-01
I've installed Ubuntu server to Virtual Box.

Now I want to use it as a server at my local network but I can't configure it properly. I want to configure Static IP according to my network configuration so I tryed to edit:

/etc/network/interfaces

I put next text:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.168.2.20
	netmask 255.255.255.0
	gateway 192.168.2.1

then if I type ifconfig the the IP and all the other data seems correct but I don't have internet connection.

I'm crazy looking for a solution but I can't fidn it.

---

### Post by restorator on 2012-02-01
In Virtualbox settings for this machine, change networks from NAT to bridged.

---

### Post by esbrinartot on 2012-02-02
> **restorator said:**
> In Virtualbox settings for this machine, change networks from NAT to bridged.

I've done it and doesn't work. I obtained teh same results

In the configuration I've also indicated eth0

There must be something I have to do and I have done yet.

Trust me that I've tried to look up for solutions but I didn't suceed

---

### Post by JKyleOKC on 2012-02-02
You say that you've installed Ubuntu server in vbox, but what is your host system running? For vbox VMs to connect to the Internet, you must have the VM's net adapter set to "bridged" and the interface of the host system must be specified in the VM's net adapter setting, also.

Any address beginning with 192.168 cannot be reached from the Internet, since this block of addresses is defined for private use. 

If you have a static IP from your ISP, you can set it as the address of your VM server and in that case you may not need to connect the host system -- in fact, it should NOT have the same IP address. This implies that you can have either the host or the VM on line, but not both at the same time -- and reconfiguring and rebooting each time you want to make the switch can be a hassle...

If you're getting a dynamic IP assigned by your ISP, then the server would have to deal with getting it, and that adds another layer of possible confusion. Tell us more about what your goal is, and what you have (cable, DSL, dial-up, satellite? Systems on the host? And so on and on and on...).

---

### Post by esbrinartot on 2012-02-04
Thks restorator. Your proposal was correct.

Instead of eth0 I had to use wlan0 because virtual box is working in a machine that is connected through wlan0.

Now the problem is solved and the VM is working fine.

---

### Post by esbrinartot on 2012-02-04
> **JKyleOKC said:**
> You say that you've installed Ubuntu server in vbox, but what is your host system running? For vbox VMs to connect to the Internet, you must have the VM's net adapter set to "bridged" and the interface of the host system must be specified in the VM's net adapter setting, also.

Any address beginning with 192.168 cannot be reached from the Internet, since this block of addresses is defined for private use. 

If you have a static IP from your ISP, you can set it as the address of your VM server and in that case you may not need to connect the host system -- in fact, it should NOT have the same IP address. This implies that you can have either the host or the VM on line, but not both at the same time -- and reconfiguring and rebooting each time you want to make the switch can be a hassle...

If you're getting a dynamic IP assigned by your ISP, then the server would have to deal with getting it, and that adds another layer of possible confusion. Tell us more about what your goal is, and what you have (cable, DSL, dial-up, satellite? Systems on the host? And so on and on and on...).

Thks now the problem is solved but your comments were interesting. May I ask next: (be patient due to I'm still a beginner)

1- I have static IP but I can't see the advantage of putting my public IP instead of my local IP. From my not so high knowledge al the computer have 2 IP. (local and public.) 

If I decide to create a web server then yes... of course I have to use the public IP but the configuration is done while you install the server.

Also for example if you want a DNS server to work even when you are out of your local network you can do it by modifying:
/etc/resolv.conf
/etc/bind/named.conf.options

2- If I put the static IP I also have to switch on my host system. If there is no host system VM is switched off. So i Don't understand your comment sorry.

Probably your comments are out of my current knowledge. My idea was use the VM to create a DNS server and also to surf safer by creating and ssh tunnel through the VM server. Now I will also try to install a NFS server.

My Internet connection is through satellite because I live far away from the city.

---

### Post by haqking on 2012-02-04
> **esbrinartot said:**
> Thks now the problem is solved but your comments were interesting. May I ask next: (be patient due to I'm still a beginner)

1- I have static IP but I can't see the advantage of putting my public IP instead of my local IP. From my not so high knowledge al the computer have 2 IP. (local and public.) 

If I decide to create a web server then yes... of course I have to use the public IP but the configuration is done while you install the server.

Also for example if you want a DNS server to work even when you are out of your local network you can do it by modifying:
/etc/resolv.conf
/etc/bind/named.conf.options

2- If I put the static IP I also have to switch on my host system. If there is no host system VM is switched off. So i Don't understand your comment sorry.

Probably your comments are out of my current knowledge. My idea was use the VM to create a DNS server and also to surf safer by creating and ssh tunnel through the VM server. Now I will also try to install a NFS server.

My Internet connection is through satellite because I live far away from the city.

Your public IP, the one assigned to your router (public facing interface)which is static from your ISP is the one you connect to from the outside world to access your network.

To access your local IP's from the public internet then you just need to port forward on your router.

All the services on your 192.168.x.x addresses can be accessed with port forwarding and why this service exists.

You dont assign your public/static IP to your server if its on your network behind a router or it will never be seen from anywhere unless its public facing but you have indicated it is not.

Leave your LAN with the private NAT address range and then port forward as required
CHeers

---

