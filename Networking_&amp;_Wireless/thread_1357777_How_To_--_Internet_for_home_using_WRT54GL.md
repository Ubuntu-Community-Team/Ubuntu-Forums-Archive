---
title: "How To? -- Internet for home using WRT54GL"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by smandoli on 2009-12-17
Running Karmic.  Setting up wireless home network using a WRT54GL router.  It would be great to have a LAN, but a simple Internet hot spot works for now.  I want this arrangement:
```

                          o ~ ~ ~ ~ o
           Cable          |         |
Internet---Modem---PC---router    laptop(s)

```
The router follows the PC so I can share filtered Internet (using dansguardian).  I've turned off firehol, tinyproxy and dansguardian while I get a working configuration.  I still have LAMP going.  

I can't get working Internet to show on the laptop.  I've been trying different settings in the Network Settings GUI.  Sometimes I lose my Net connection but so far I can restore.  At this moment eth0 is "roaming" and eth1 is address=192.168.0.20, SubnetMask=255.255.0.0, Gateway=192.168.0.42.  (Woops.  I just had to change those -- lost my signal.  Now eth0 is DHCP and eth1 is disabled ... I think ... the checkbox is unchecked at least.)  Also from Network Settings:  Host and Domain names are blank, DNS is 192.168.0.20.  

I wish I knew more about pinging, either from the command line or the Network Tools GUI.  If you want to know about my ports, open DNS, etc., please give me a command line instruction.  

I haven't done anything to the router.  Here is ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:15:f2:27:a2:2c  
          inet addr:192.168.0.140  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe27:a22c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3848040 (3.8 MB)  TX bytes:529269 (529.2 KB)
          Interrupt:23 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:12:17:53:11:55  
          inet addr:192.168.0.20  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::212:17ff:fe53:1155/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:993 errors:4 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:474360 (474.3 KB)  TX bytes:100002 (100.0 KB)
          Interrupt:17 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1536720 (1.5 MB)  TX bytes:1536720 (1.5 MB)
```

---

### Post by pdc124 on 2009-12-17
where is the DNS server ?

what is the IP address of the laptop 
whats the last line of sudo route -n on the laptop ?
whats the IP address of the router ?

I would do it by setting up the router as a Wireless Access point, with a static IP address and doing the DNS from the laptop , which should take care of the routing.

---

### Post by smandoli on 2009-12-17
pdc124:

where is the DNS server ?  [COLOR="Purple"]How would I determine this?[/COLOR]
what is the IP address of the laptop  [COLOR="Purple"]See below.  Windows. [/COLOR] 
whats the last line of sudo route -n on the laptop ?
whats the IP address of the router ?   [COLOR="Purple"]How would I determine this?[/COLOR]

The laptop is running Windows.  I want it to pick up a signal as if at Starbucks (but cheaper), so I don't imagine it identifying itself.  [EDIT:  Well, I want encrypted signal, so I guess it DOES obviously.  But I don't know how to answer the question.]

---

### Post by pdc124 on 2009-12-17
if you are using your router 'out of the box' then I suspect its doing DHCP to the laptop.

Log into the router ( its in the instructions somewhere - usually estahlish a wired connection and then open a browser and got to 
[http://192.168.0.1](http://192.168.0.1)
or [http://192.168.1.2](http://192.168.1.2) 
or [http://192.168.1.1](http://192.168.1.1) 

or ..... ( you get the message)

in the config screen it will say if its a DNS server.

if you want to do it my way ( and there are probably better ways of doing it)
i would 
1. install dnsmasq on the PC and configure it to give out addresses to your LAN. ( eg 192.168.0.10-192.168.0.49). there are examples in the man page. give your LAN -facing NIC a static Ip address ( eg 192.168.0.5)
2.Try googling for the make of your router and 'configure as Access point'. To do it you need to log into the router and disable its DHCP server. then  give it a static IP address. eg 192.168.0.50.
then configure the wireless LAN you want the laptop to connect to.
- start with un encrypted , then add encryption as you check things work.
3 then get your laptop to connect to the WLAN you set up in 2)
4 check the laptops IP address ( should be in the range 192.168...10-49)

then 
try and ping the router 
windows start->cmd -> ping 192.168.0.50

then try pinging the PC ( ping 192.168.0.5)

then try pinging [www.google.com](www.google.com)
if it doesnt work and the previous stuff does then try ping 216.239.59.99. If this works and the previous one doesnt , you have a DNS problem.

to use dansguardian , you need to direct the web traffic from port 80 to squid/DG (8080 IIRC)
so either configure the laptop browser to use 192.168.0.5:8080 as a proxy and block port 80 , or use transparent proxying on the PC (shorewall is my preferred front end to iptables for this)




its easy adn straightforward as long as you make sure one step is working correctly before going on to the next

---

### Post by smandoli on 2009-12-17
The first router URL you suggested takes me to a SonicWall login screen.  I couldn't logon using admin/password -- in 3 hours I will be able to check the manual and hopefully get access.  

Searching on "configure as AP" sounds productive.  So far I have [this article]("http://www.aperture.ro/index.php/2009/03/configuring-linksys-wrt54gl-wireless-router-as-wireless-access-point/").  

I also have a Ubuntu laptop I can use to pilot this, maybe will simplify things.   THANKS for the noob instructions.

---

### Post by smandoli on 2009-12-17
I have the hardware set up as I diagrammed it.  I have firehol etc. disabled.  On the PC, I have regular internet, but can't pick up 192.168.1.1.  On the Vista laptop via wireless, no internet, but I am logged onto the router (factory default is user=blank, password=admin.)  

I see it is set to Auto Cofig DHCP.  I don't see whether it is a DNS server (but DDNS service is disabled).  

I'm gonna try the article I linked earlier, then try dnsmasq.

---

### Post by smandoli on 2009-12-17
No change, no progress.  I can see the router configuration on the wireless laptop, but I'm thinking that is not the place to make any changes.  

When I run sudo /etc/init.d/networking restart, I usually get something negative.  Often it's "ignored unknown interface eth0=eth0."  Right now it's "SIOCADDRT: No such process, failed to bring up eth1, failed to bring up eth0."  Yet I'm on the Internet ...:?

---

### Post by cariboo on 2009-12-18
It looks like your router is setup to be the dns server. THis is probably why you can't connect to the internet. THe best way to check if it is a dns problem is to try and ping google by name & number. Open a terminal and type:

```
ping www.google.com
```

THat probably won't work, so try:

```
ping 74.125.53.99
```

If the above works, you have a dns problem.

To fix the dns problem, right-click the network-manager icon in the top panel and select Edit Connection. Next highlight you network device and click the Edit button. Click the IPV4 tab and select Automatic (DHCP) addresses only from the method drop down. next enter your isp's dns server's ip address in the DNS Servers text box. Click Apply, you should be asked for your password. Once your password has been accepted it should restart networking. You should then be able to connect to the internet.

---

### Post by pdc124 on 2009-12-18
so the router and laptop are talking to each other :-)
whats the IP address of the laptop? and where is it getting its IP address from ?
if its within the range you set in dnsmasq on the PC then its likely the PC is talking to the laptop via the router :-)
can you ping 192.168.0.5  ie from the laptop to the PC ?


can stuff get from the router to the PC ( or vice versa) ?

whats the output of sudo ifconfig on the PC?
from the PC can you ping 192.168.0.50  ( the router) ?

---

### Post by smandoli on 2009-12-19
cariboo:  I tried your instructions DHCP Auto Only, but the settings wouldn't stick.  Wasn't sure your ping instructions.  From the PC, all pings good naturally.  Didn't look into how to ping on the Vista laptop.  

pdc124:  Not knowledgeable enough to get answers most of your questions.  I have not installed dnsmasq.  

I currently have a working router, using the trad arrangement (not my diagram).  I want to get the (inadequately minimal) built-in filtering up.  I will work on my preferred set up later, but maybe not today.  I need to learn some fundamentals of networking!  

Sorry so pokey to answer.  Other stuff going on.  I'll leave this thread open unless suggested otherwise.  Thanks a lot for all your help.  
----------------------

---

### Post by smandoli on 2009-12-19
What's next:
[LIST=1]
[*]Map the current topography (provisional, functioning).  Fill in every tech detail and address I can.  Include LAMP.  
[*]Change my current router config from Automatic DHCP to static IP.  This makes the configuration explicit.  
[*]Learn the fundamentals of network addressing and proxying.  (Welcome any tutorial links on that.)  
[*]Map the desired topography (in which PC enables content filtering). 
[*]Achieve goal.  Write new résumé, apply for high-paying Admin jobs, call tow truck to haul away Chevy Celebrity in the front yard.
[/LIST]

---

