---
title: "Creating static IP with Ubuntu 9.10"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by kiklion on 2010-01-01
I just purchased a new computer and installed windows 7, and decided to dual boot into ubuntu in order to learn ubuntu and then to install and run a web server using apache.

I installed apache, created a simple html file that I can access from any computer on the network using address [http://192.168.0.101](http://192.168.0.101).  I am trying to currently portforward port 80 through my linksys BEFSR41, to a computer with an IP address of 192.168.1.xxx etc.

I am not sure how 192.168.0.101 reaches the file, as wouldn't my router require all computers to be in the 192.168.1.x class? I vaguely remember putting in 192.168.0.101 at some point... the last 6 hours were filled with trial and error and google searches as I am new to both ubuntu and networking.  

Current /etc/network/interfaces file

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
network 127.0.0.151
broadcast 192.168.0.255
gateway 192.168.1.1
```Any help with setting a static IP address or explaining how I set 192.168.0.101 to apache2 would be greatly appreciated.

---

### Post by Iowan on 2010-01-01
The interfaces file is... different. **address** and **netmask** look alright. **network** and **broadcast** are not absolutely necessary, but when used,**network** is ordinarily the lowest address in the subnet (in this case, 192.168.1.0) and **broadcast** is the highest (192.168.1.255). The **gateway** should be in the same subnet, and is probably the address of your router.

If your server is *supposed* to be at 192.168.0.101, the address,network, broadcast and gateway, could be changed to this range.

---

### Post by oldfred on 2010-01-01
On my linksys WRT54GL I could not use any of the default DHCP addresses starting at 100. As long as I used .20 it worked but .100 did not. I tried resetting the DHCP range to .120, but that did not help. Since I only wanted one or 2 numbers to be fixed I just used .20.

---

### Post by kiklion on 2010-01-02
thank you Iowan explaining what each part was might help alot.  I used those numbers as guesses through trial and error between looking at ifconfig and resetting the network, and those numbers let me get internet, so it might be odd as they were semi-random

---

### Post by kiklion on 2010-01-02
Ok new info if anyone else can help

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.11
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1 
```is my interfaces file, when I do sudo /etc/init.d/networking restart it runs through and I can then access the website I made in dreamweaver through the address 192.168.1.11/Project.htm , However I cannot access the internet at all.  When I run sudo dhclient it resets my IP address to 192.168.0.101.  I can then access the internet, but need to use the IP address 192.168.0.101/Project.htm to access the website.  I need my IP address to be 192.168.1.xxx in order for port forwarding to work.  

Edit~ I found out that dhclient asks a DHCP server for an IP address, so I went with ifdown eth0; ifup eth0; and ping 192.168.1.1 with 100 packet loss.

As I understand it, when another computer attempts to reach my computer IP address on a port that apache2 is listening on, it redirects it to the given page. This is OT but it is secondary, within apache2/available-sites I have the site "mysite" which is a copy of the default site bundled with apache.  I changed the DocumentRoot to ```
/home/david/public_html/
``` and the Directory to ```
<Directory /home/david/public_html/Project.htm>
``` thinking that it would then load that htm file when going to the IP address, instead I get a 403 forbidden error with just the IP address and need to add /Project.htm to it for it to load.  How would I get apache2 to load the Project.htm file by default?

---

### Post by kiklion on 2010-01-02
Fixed it, brother changed network setup without me knowing, making it go from modem -> router -> switch -> computers to modem -> router - > wireless router - computers, and that messed up the static IP addresses.

---

### Post by Iowan on 2010-01-02
Glad you got it - ain't the school-of-hard-knocks a wonderful teacher?
If it's fixed, you

---

### Post by Iowan on 2010-01-02
Glad you got it - ain't the school-of-hard-knocks a wonderful teacher?

---

