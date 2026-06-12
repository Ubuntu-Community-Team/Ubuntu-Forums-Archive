---
title: "sharing internet connection from ppp0 to eth0"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by LeonLinux on 2010-01-23
Hello Ubuntu folks!
i want to share the internet connection from **Laptop** to **PC** via LAN crossover cable
here's how i connect to the internet in laptop, and connected PC via LAN:

[IMG]http://img138.imageshack.us/img138/3613/ics.png[/IMG]

i need to share pppoe(ppp0) to (eth0) , that is what i've been doing in Windows before,
but i dont know how to share in Linux,
i tried to follow Ubuntu Help about ICS, but it doesn't work
please help me
thanks

---

### Post by mionescu on 2010-01-23
Try installing the program firestarter (from Synapptic or Add/Remove). I think it is the easiest way to share the internet.

---

### Post by LeonLinux on 2010-01-23
> **mionescu said:**
> Try installing the program firestarter (from Synapptic or Add/Remove). I think it is the easiest way to share the internet.

mionescu, thanks for your help.
i tried with Firestarter before, sometimes will share the internet, and sometimes not,
and that Firestarter will disconnect ppp0 when eth0 get disconnect, 
it does not work well for me, i dont know the reason, but looks like there are bugs in Firestarter.
is there are any way to make ICS in Terminal?

---

### Post by mionescu on 2010-01-23
I did share the internet a couple of years ago as described in the following sites:
[http://www.howtoforge.com/internet-connection-sharing-masquerading-on-linux](http://www.howtoforge.com/internet-connection-sharing-masquerading-on-linux)
or
[http://lindesk.com/2007/04/internet-connection-sharing-using-iptables/](http://lindesk.com/2007/04/internet-connection-sharing-using-iptables/)

You can give it a try.

---

### Post by LeonLinux on 2010-01-24
> **mionescu said:**
> I did share the internet a couple of years ago as described in the following sites:
[http://www.howtoforge.com/internet-connection-sharing-masquerading-on-linux](http://www.howtoforge.com/internet-connection-sharing-masquerading-on-linux)
or
[http://lindesk.com/2007/04/internet-connection-sharing-using-iptables/](http://lindesk.com/2007/04/internet-connection-sharing-using-iptables/)

You can give it a try.

hi mionescu
i followed two links, but it doesnt work :(
and Laptop can't ping the PC, 
here is IP for Laptop 192.168.0.1 (IPv4 in NM is: "Shared to other computers"), and for PC is 192.168.0.10 (dhcp)

---

### Post by LeonLinux on 2010-01-24
up :confused:

---

### Post by mionescu on 2010-01-24
So is it working now?

---

### Post by LeonLinux on 2010-01-24
> **mionescu said:**
> So is it working now?
no :(

---

### Post by mionescu on 2010-01-24
> **LeonLinux said:**
> 
here is IP for Laptop 192.168.0.1 (IPv4 in NM is: "Shared to other computers"), and for PC is 192.168.0.10 (dhcp)

I am not sure I understand what you did. You connect to the internet from your laptop using the wireless card and you want to share the internet via the cable with the desktop. Am I right?

Then you need to have 3 IPs. One for the wireless card, one for the ethernet card on the laptop and one for the ethernet card on the desktop.

What are the name of the devices on the laptop? You can find them either from NM or using the following command in a terminal: ifconfig

Assume that the wired device on the laptop is called eth0 and the wireless device is called eth1 (it could be wlan0, or something like this). Then, after changing the value of net.ipv4.ip_forward in /etc/sysctl.conf to 1 (and probably rebooting the computer), you would write once:

sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
sudo service iptables save

If the wireless card is not eth1, then substitute the name of your device in the first line. 

Then you should give a fixed (static) internet address to eth0 (the wired card). To do this, you can right click on NM, and select "Manage Connections". Go to wired connections and select your device from the list. Make sure you uncheck dhcp for address and enter the information as posted in one of the links there. For example, write
192.168.1.20 for the ip address (make sure it is not already used by the wireless card).
Netmask : 255.255.255.0
Gateway : 192.168.1.1 (IP of the router); if you are not sure what the ip of the router is, you should be able to find this information by right-click on Network Manager and select connection information for the wireless conection.

Press Apply (or Save, I don't remember for sure) and you should be done on the laptop. On the desktop, you need to enter again a static ip address as you did for the wireless.
Choose any number you want for the IP address (192.168.1.30 should be fine). 
Netmask : 255.255.255.0
Gateway : the ip address of the wired connection on the laptop; eg 192.168.1.20 in my example. This is very important. The desktop should not be "dhcp".
After applying these changes you should be done. 

I hope this works. I have only one computer now, so I can not test it myself. I found, though, some notes I wrote a couple of years ago when I made this kind of a setup.

I hope this helps.

---

### Post by LeonLinux on 2010-01-28
Hey mionescu,
i did and followed what you said exactly.
and then i can ping Laptop and Desktop, but the internet in Desktop is still not work,
after that.. i added the address of DNS server to the LAN settings in Desktop, and it did open the internet!! :D

there are another problem, it is a bug in Network-Manager, because when i disconnect LAN connection...the ppp0 will get disconnect too.
but i fixed this, by uninstalling network-manager
until now, everything is work like charm!
i'm very happy now :KS
thank you very much for your help  :p
best regards
~Leon.

---

