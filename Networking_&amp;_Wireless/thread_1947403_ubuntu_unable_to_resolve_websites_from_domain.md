---
title: "ubuntu unable to resolve websites from domain"
date: 2012-03-26
forum: Networking &amp; Wireless
---

### Post by dave09 on 2012-03-26
I am connecting to internet using usb modem, it connects to internet but when i open in browser it shows no internet connection. I tried to ping website in terminal it gives error message as unknown host. And when i ping using website ip address it gets reply. 
This happens when m logged in as administrator, when i log in as root internet works perfect, it resolve websites properly and also works in browser.

---

### Post by jonobr on 2012-03-26
Hello


Your DNS server doesnt appear to work
You could temporarily put in 8.8.8.8 as a try, but it sounds as if your either not given it by your ISP or you have configured something else.

If you run 
```
cat /etc/resolv.conf
```
it will show your current setup

Jonobr

---

### Post by dave09 on 2012-03-26
It says permission denied when i run the code given by you.
I tried same from root login it gave the following reply
  	 	 	 	 	 	   nameserver 121.242.190.210 nameserver 4.2.2.2

---

### Post by jonobr on 2012-03-26
ok 
so are
```
nameserver 121.242.190.210 nameserver 4.2.2.2
```
real DNS server IP address?

Also, Im not sure if they should be on the one line.

Way to check if they are working correctly is to 
```
nslookup google.com
```
if you get a response with numbers in it, then your DNS is ok
if not /etc/resolv.conf or network manager is wrong or your DHCP response is wrong.

---

### Post by dave09 on 2012-03-26
sorry they were not on one line, they were one below other i copy pasted them so they came like that way.

i tried what you said it gave "connection time out " error

Are the 'resolv.conf' file same for root and administrator?
if yes then at both the places dns are same.

---

### Post by MagneticFlux on 2012-03-26
This once happened to me too, Ubuntu sometimes has problems with getting DNS servers from ISPs. You could select Network icon -> Edit Connections... and select your connection. Click edit and on the "IPv4 Settings" tab select "Automatic (DHCP) addresses only" and enter your own DNS servers. I currently use the OpenDNS ones, which are ```
208.67.222.222, 208.67.220.220
```
Most people prefer using a GUI tool if one exists, but if you are ok with configuration files and such, by all means go tinker with it.

---

### Post by jonobr on 2012-03-26
Hi there


It sounds like as if you are getting DNS information but its junk or not functional. 
Thats why you cannot resolve websites.

Most people choose 8.8.8.8 as they are pretty reliable and belong to google.

Its best to use the GUI as if you modify the config file directly then the network application manager will overwrte the settings on the next boot,

---

### Post by dave09 on 2012-03-27
You mean to say i should replace dns by 8.8.8.8??

Can you provide me with the link o name of the software needed to change the dns?

---

### Post by dave09 on 2012-03-27
hey magneticflux


i use net via net setter so it don't give dial up, i use software to connect to internet.


if you know how to create dialup for net setter then please let me know.

---

### Post by MagneticFlux on 2012-03-27
Hi,
So you do not connect through Ubuntu's default networking interface? Could you explain what "net setter" is? I suppose it is a trademark, but if we could understand how it works a way around could be found.

---

### Post by dave09 on 2012-03-29
i use idea usb netsetter.

idea e1732

---

