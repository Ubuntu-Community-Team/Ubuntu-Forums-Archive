---
title: "Help with home server"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by audio_uphoria on 2009-05-17
Hi, I'm setting up a home server using ubuntu 8.04 desktop version. I installed apache, mysql, php, and openssh. When I type 
$ ifconfig | grep inet it tells me that my inet addr: is 192.168.1.11

Does that mean it's getting it's ip from a gateway or something? I dont know alot about networking and the set up I'm using is in my apt building. There's about 20 or so apt's that all have a dsl connection. I only have an ethernet port in my apt and no access to any of the hard ware. How can I get my server up and running? Thanks.

---

### Post by kaprikawn on 2009-05-17
That's the IP address of your computer *on your local network*.  It's not the IP address of your computer on the internet at large.

So if you wanted another computer on your local network to see files on that computer, it could use SSH and it would need that IP address to connect to your server.

The number (the 11 from 192.168.0.11) seems rather low which leads me to suspect that it was assigned automatically.  To run a server on your local network you will need to create a static IP address (e.g. 192.168.0.120).  Otherwise your ip address could change every time you restart the computer which would break any connections.

```
sudo gedit /etc/network/interfaces
```

Change ```
auto eth0
iface eth0 inet dhcp
```
to
```
auto eth0
iface eth0 inet static
address 192.168.1.120
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

That will give you an ip address of 192.168.0.120 on your local network, other computers can use this to access your server.

It is unclear what kind of server you are setting up.  Is it just to serve files to other computers on your local network?  Is it to serve web pages for development purposes?  Is it to serve webpages to the internet?

If you only want to serve files to your local network you don't need most of the programs you've installed.  If the other computers you want to serve files to all run Linux then SSH is sufficient.  If you want to serve files to Windows machines too then you might want to consider Samba instead.

Apache, Mysql and PHP are for serving webpages.

---

### Post by audio_uphoria on 2009-05-17
Sorry, I guess I wasn't very specific. I want to set up a server that can be accessed over the internet. I would like to set up a web page and also be able to share files with windows computers over the internet. I don't have any intention of setting this server up on my lan. The only problem is I don't have access to the router. I've been trying to use ddclient and dyndns with no avail. When I go to my dns page (bryan.isa-geek.net)on a different network it says there is a page load error. When I try to access that on the actual server it will ask me for login and everything I try doesnt allow me to login. Is it possible to get my server on the interweb without having any access to the router or other equipment on my network?

---

### Post by puppywhacker on 2009-05-17
the 192.168.x.x ip address that you get is an internal one, you can not route it over the internet, the apartments router has the real ip-address and is NAT'ing for you. This means that you can only have internet connections that you initiate, connecting from the internet to you will stop at the apartments router which would have no idea where to route it next.

there is very little you can do about it if you don't have access to the router

---

### Post by superprash2003 on 2009-05-18
yes , you need access to the router as you need to open port 80 for your webserver ( apache) without that , your webpage will not be accessible outside your LAN

---

### Post by Iowan on 2009-05-18
The router *might* be able to associate name/address, but it's usually easier to port forward to a static address (hence the original suggestion).  If the DHCP server (router?) is capable, setting up a static _lease_ based on MAC address is another (good) option.

---

