---
title: "Faster web borwsing using open dns"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by san_antonio9.10 on 2010-10-05
Open DNS server,  is the #1 DNS service provider around the world.  OpenDNS is FREE and is not require  nothing to download, and  it  will not replace your existing Internet connection. Open DNS   []("http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml#")[official home page]("http://www.opendns.com/").

Here is what you must do. Please back up your DNS addresses before  replacing them with the ones from OpenDNS, in case you want to return to  them later for whatever  reason. The DNS server addresses for OpenDNS  are:

[B]208.67.222.222
208.67.220.220

[/B]For static IP Address 

If you have a static IP address that you must manually configure in order to have Internet access[[COLOR=#0066CC]__[/COLOR]]("http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml#"), please use the following method.

Open a console and type:

 Internet connection it will just make it better. Also, OpenDNS offers  some other free services. For more information about OpenDNS please  visit the      **CODE**[/SIZE]
sudo gedit /etc/resolv.conf
 
and add the following lines, above the existing lines in that file:

[B]nameserver 208.67.222.222
nameserver 208.67.220.220[/B]

[B]
For Dynamic IP address (DHCP)[/B]


If you are using a dynamic IP address (DHCP), that means you get your Internet [[COLOR=#0066CC][/COLOR]]("http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml#") IP address, subnet mask, DNS and gateway automatically from your ISP's DHCP server, please follow the instructions below:

Open a console and type:

     sudo gedit /etc/dhcp3/dhclient.conf

Replace the line that says:

*#prepend domain-name-servers 127.0.0.1;*

with this one:

*prepend domain-name-servers 208.67.222.222, 208.67.220.220;*

Restart your network so the changes can  take effect:[/SIZE] 

[B]sudo /etc/init.d/networking restart
[/B]

**For Ubuntu users**

If you use Ubuntu, please go to *System -> Administration -> Networking*,  click on the third tab (DNS) and add, one by one, the OpenDNS addresses  on top of the first field (DNS Servers). Close the window and restart  your computer.

[WWW.VIVA-OPENSOURCE.BLOGSPOT.COM](WWW.VIVA-OPENSOURCE.BLOGSPOT.COM)

---

### Post by san_antonio9.10 on 2010-10-07
Open DNS server,  is the #1 DNS service provider around the world.  OpenDNS is FREE and is not require  nothing to download, and  it  will not replace your existing Internet connection. Open DNS   []("http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml#")[official home page]("http://www.opendns.com/").

Here is what you must do. Please back up your DNS addresses before  replacing them with the ones from OpenDNS, in case you want to return to  them later for whatever  reason. The DNS server addresses for OpenDNS  are:

[B]208.67.222.222
208.67.220.220

[/B]For static IP Address 

If you have a static IP address that you must manually configure in order to have Internet access[[COLOR=#0066CC]__[/COLOR]]("http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml#"), please use the following method.

Open a console and type:

 Internet connection it will just make it better. Also, OpenDNS offers  some other free services. For more information about OpenDNS please  visit the      **CODE**[/SIZE]
sudo gedit /etc/resolv.conf
 
and add the following lines, above the existing lines in that file:

[B]nameserver 208.67.222.222
nameserver 208.67.220.220[/B]

[B]
For Dynamic IP address (DHCP)[/B]


If you are using a dynamic IP address (DHCP), that means you get your Internet [[COLOR=#0066CC][/COLOR]]("http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml#") IP address, subnet mask, DNS and gateway automatically from your ISP's DHCP server, please follow the instructions below:

Open a console and type:

     sudo gedit /etc/dhcp3/dhclient.conf

Replace the line that says:

*#prepend domain-name-servers 127.0.0.1;*

with this one:

*prepend domain-name-servers 208.67.222.222, 208.67.220.220;*

Restart your network so the changes can  take effect:[/SIZE] 

[B]sudo /etc/init.d/networking restart
[/B]

**For Ubuntu users**

If you use Ubuntu, please go to *System -> Administration -> Networking*,  click on the third tab (DNS) and add, one by one, the OpenDNS addresses  on top of the first field (DNS Servers). Close the window and restart  your computer.

[WWW.VIVA-OPENSOURCE.BLOGSPOT.COM](WWW.VIVA-OPENSOURCE.BLOGSPOT.COM)

---

### Post by overdrank on 2010-10-07
Threads merged.

---

### Post by pricetech on 2010-10-07
Not closed ??

---

### Post by realzippy on 2010-10-16
Nice HowTo.
Next time when you copy and paste something,do not forget to
name the source:

[http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml](http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml)

---

### Post by PC_load_letter on 2010-10-19
> **realzippy said:**
> Nice HowTo.
Next time when you copy and paste something,do not forget to
name the source:

[http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml](http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml)

Or this: 
[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

I did this today and now I'm using OpenDNS, much better than the erratic timeouts I always got from my ISP crappy DNS, way to go OpenDNS.

---

