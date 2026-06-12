---
title: "wireless settings"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by linux_ocean on 2009-10-01
Hi every body.
I have a problem with my wireless connection.
I want to use internet in my university, so I have to do some settings on my wireless card.
In windows vista I can connect to internet, but in Ubuntu I can't.
Here is my settings in Vista:

> IP address: 192.168.50.180
Subnet mask: 255.255.255.0
Defult gateway: 192.168.50.1
Preferred DNS server: 217.218.127.104
Alternate DNS server: 4.2.2.4

I do these settings in ubuntu, but I can't connect to internet.
I don't know where I can enter alternate DNS server in ubuntu.
does anyone know what should I do?
Thanks a lot.

---

### Post by linux_ocean on 2009-10-01
Isn't here anybody know how can I manualy config my wireless card adaptor to connect to internet?

---

### Post by chili555 on 2009-10-01
May I assume you are using Network Manager?  I suspect you will have more luck using DHCP rather than trying to set these settings manually. Using DHCP, the University's router will supply the DNS nameservers automagically. If you right click the NM icon and Edit connections, then select your wireless interface and then IPv4 settings, change to Automatic (meaning DHCP) and save. Then when you left click the icon, you should see the University's network. Select that network and try to connect.

What happens? What goes wrong?

---

### Post by linux_ocean on 2009-10-01
Hi chili555.
I know that. but in my university access to Internet is limited and I can't set it to automatic DHCP!
but in windows, as I said I can connect without permission of admin, by entering ip manualy.
the question is : "Why I can connect to internet in windows with the same settings, and in Ubuntu I can't?"

---

### Post by chili555 on 2009-10-01
Have you tried putting in the static IP, and other details you used in Windows in the appropriate spot in NM? Please see my attachment above.

You could also do this from the command line, but let's try NM first.

---

### Post by linux_ocean on 2009-10-01
My dear friend, as I said last time, I can enter ip, netmask, gateway and DNS server in NM.
but the problem isthat I can't connect to internet by same configuration in ubuntu!

---

### Post by chili555 on 2009-10-01
Sorry I didn't fully understand; I'm getting old. The only thing I can suggest is from the command line. Please do:```
sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth0 address 192.168.50.180
sudo ifconfig eth0 up
ping -c3 192.168.50.1
```If you get ping returns, you are connected. Your DNS details go in */etc/resolv.conf*. Please do:```
sudo gedit /etc/resolv.conf
```Add two lines:```
nameserver 217.218.127.104
nameserver 4.2.2.4
```Proofread, save and close. If this doesn't work, I am fresh out of ideas.

---

### Post by linux_ocean on 2009-10-01
thanks a lot.
I will exam it and if it was success, I will tell the result.

---

### Post by linux_ocean on 2009-10-03
Hi again.
today I can connect to internet with same settings for wireless card.
but I didn't make any changes in settings!!
but I see my wifi LED is blinking and after a while it lost internet connection and I couldn't connect to internet again!!
now I know my settings are true, because I connect for a while.
Is there any problem with my wireless card driver in ubuntu?
it's dell 1515 wireless mini card.

---

### Post by linux_ocean on 2009-10-04
Does anybody know why I can connect to internet some time and often not!?
and why the LED of WIFI is blinking continuesly anf then I lose connection?
Thank you. help me pleaze. it's very important because I can't use ubuntu without connecting to internet.

---

