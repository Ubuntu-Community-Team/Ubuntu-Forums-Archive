---
title: "Sharing Internet connection"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by HolidayQueen on 2010-04-10
I have a tower that receives it's internet connection wirelessly, and a friends' damaged laptop (no wireless). I want to hookup the laptop by cable to my tower, and share my towers' internet connection through it.

i have no dificulty doing it the other way around (a wired internet connection shared through a wireless network) but in this case the same method in reverse doesn't seem to work.

---

### Post by Iowan on 2010-04-11
Sounds like you may have already tried using [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page - substituting the wireless connection for the WAN connection.

---

### Post by stilling on 2010-04-11
The following will explain how to share your Internet connection:

Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

# ifconfig ethX ip <- ( usualy is 192.168.0.1 )

where ethX is the network card that you whant to connect with laptop
2. Then configure the NAT as follows:

# iptables -t nat -A POSTROUTING -o wan0 -j MASQUERADE

where ethX is the network card that the Internet is coming from in your case it will be wan0

# echo 1 > /proc/sys/net/ipv4/ip_forward

3. Install dnsmasq using apt-get:

# apt-get install dnsmasq
4. Restart dnsmasq:

# /etc/init.d/dnsmasq restart

6. Repeat steps 1 and 2.

7. remove # from the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

8. edit /etc/network/interfaces
   auto ethX ( ethx connects to laptop )
   iface ethX inet static
   address 192.168.0.1 <-(ip that you whant)
   network 192.168.0.0   
   netmask 255.255.255.0
   broadcast 192.168.0.255
   gateway 192.168.0.1

to start on restart 

edit /etc/rc.local
and add theiptables line with sudo in front like this

sudo iptables -t nat -A POSTROUTING -o wan0 -j MASQUERADE


hope this helps you 

thanks to anaoum

---

### Post by HyperFlexed on 2010-04-11
This is interesting. Could you explain why sudo won't work? As far as I understand sudo, it allows you to perform any command with root access.

---

### Post by stilling on 2010-04-11
it works but i believe that is easy-er just to type the commands in the terminal

scuze me if i did something wrong and that post was copied from anaoum and i added some modifications for you to understand better

---

### Post by HyperFlexed on 2010-04-11
That's cool, I just avoid using su in case there was malicious code sitting on my machine. Call me paranoid :P

---

### Post by Iowan on 2010-04-11
Sidenote: Ordinarily machine-machine connections require a crossover cable (or hub/switch/router between machines... although some newer (gigabit) NIC's can auto-configure.

---

