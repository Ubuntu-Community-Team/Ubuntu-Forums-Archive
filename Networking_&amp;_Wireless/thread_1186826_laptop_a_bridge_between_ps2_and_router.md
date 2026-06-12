---
title: "laptop a bridge between ps2 and router"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by astropirit on 2009-06-13
Hello guys.
I am trying to make my wireless laptop into a network bridge between my ps2 and my router. I have a game called starwars battlefront 2 and i'm trying to connect to the Internet in that game. and i have a wire that is long enough to reach my laptop and the ps2 but not long enough to get the router

So my request is if you know how to make my laptop into a network bridge, would you please explain to me how i can make mine.

Again, my ps2 is connected to my wireless laptop, and i'm trying to access the Internet with my ps2 through the laptop.


Thank you for taking your time reading this, and thank you in advance if you can help or not.


Ps, i'm using linux mint gloria.

---

### Post by synapsys on 2009-06-13
buy a wireless adapter for your ps2

---

### Post by astropirit on 2009-06-13
u see i really don't wanna waste any money, right now i'm broke and i wanna do this, so if you know, will you plz tell me how?


Thankyou.

---

### Post by kevdog on 2009-06-14
Do you really want a bridge -- or just a way to set up ICS - internet connection sharing?

What type of ports or wired/wireless cards does your laptop have.

---

### Post by Vostrocity on 2009-06-14
Guys it's not that hard. All you're doing is connecting your laptop via WiFi and then sharing that connection thru Ethernet. This should work, but if you don't want to use the terminal someone can probably figure out a way to do this graphically.
> Share your Internet connection using the following Procedure

Note: Type all the following commands in a root terminal

Start by configuring the network card that interfaces to the other computers on you network

# ifconfig ethX ip

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

Then configure the NAT as follows

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

where ethX is the network card that the Internet is coming from

# echo 1 > /proc/sys/net/ipv4/ip_forward

Install dnsmasq and ipmasq using the following command

# apt-get install dnsmasq ipmasq

Restart dnsmasq using the following command

# /etc/init.d/dnsmasq restart

Reconfigure ipmasq to start after networking has been started

# dpkg-reconfigure ipmasq

Start by configuring the network card that interfaces to the other computers on you network

# ifconfig ethX ip

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

Then configure the NAT as follows

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

where ethX is the network card that the Internet is coming from

# echo 1 > /proc/sys/net/ipv4/ip_forward

Add the line “net.ipv4.ip_forward = 1&#8243; to /etc/sysctl.conf

# gedit /etc/sysctl.conf

Reboot your system is optional.

---

### Post by superprash2003 on 2009-06-14
yea , ICS would do , the above procedure should work

---

