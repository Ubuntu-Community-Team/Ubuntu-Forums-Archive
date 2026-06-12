---
title: "Need help with configuring LINKSYS AG241 ADSL MODEM GATEWAY 4-PORT SWITCH"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by khelben1979 on 2009-04-19
I need help configuring up this: LINKSYS AG241 ADSL MODEM GATEWAY 4-PORT SWITCH. I have spent x hours with it and e-mailed Linksys (no replies yet). So far it can't connect to the internet and I don't know how to fix it.

The lamps on the modem: DSL = no light (but it did work before I resetted it back to factory settings), Internet = no light ever. The lamps which is to indicate if it detects ethernet ports lights up correctly.

I'm actually using Internet Explorer under Windows with it to configure it, but the settings in the web interface has the same settings with Linux also, so this doesn't matter much. Any suggestions? (Also, the settings is different depending the country one is in, the settings should be adjusted to work correctly here in Sweden)

Help is greatly appreciated.

See attached picture for more information.

---

### Post by inobe on 2009-04-19
khelben i noticed it's set to bridged but i think it should be automatic DHCP, also i have reset my dsl modem and needed to re-enter my user name and password.

example of user name and password your isp assigns 

[email]blah@att.net[/email]

then password

xxxxxxxxxx

---

### Post by puppywhacker on 2009-04-19
A green light named "DSL" should be on, most likely it isn't, since you have to set the ADSL values for VPI and VCI, for your provider Telia in Sweden that should be something like this.

G.dmt
VPI to 8
VCI to 35

Once you have set these it might take a few minutes to fully initialize the ADSL link. When the ADSL link is working you can focus on getting the IP network up and running.

The Linkys is running on a small linux system itself, that is where all the settings are stored. So it doesn't matter if you configure it in Linux or Windows.

---

### Post by khelben1979 on 2009-04-19
The choice of automatic DHCP is not available on that button. These are things I'm able to choose:

RFC 1483 Bridged
RFC 1483 Routed
RFC 2516 PPPoE
RFC 2364 PPPoA
Bridge Mode Only

---

### Post by inobe on 2009-04-19
> **khelben1979 said:**
> The choice of automatic DHCP is not available on that button. These are things I'm able to choose:

RFC 1483 Bridged
RFC 1483 Routed
RFC 2516 PPPoE
RFC 2364 PPPoA
Bridge Mode Only

RFC 2516 PPPoE

or

RFC 2364 PPPoA

---

### Post by inobe on 2009-04-19
i have set my modem to bridged once before and needed to reset my modem, i was totally locked out, i couldn't even access the modems page.

several lights went out.

i remember changing it from PPPoe to bridged when that happened.

---

### Post by khelben1979 on 2009-04-19
> **inobe said:**
> khelben i noticed it's set to bridged but i think it should be automatic DHCP, also i have reset my dsl modem and needed to re-enter my user name and password.

example of user name and password your isp assigns 

[email]blah@att.net[/email]

then password

xxxxxxxxxx

This has been a problem from the start for me. What information do I enter for login and password? :confused: These new settings demanded username and password so I chose something simple this time, just to get the new settings "working".

Telia says that I don't have a username or password for this. I'm just used to use DHCP and then everything just works, but this modem is a bit special.

I have changed all the settings according to what has been written down in this thread, and now the DSL LED lights up in green again.

---

### Post by inobe on 2009-04-19
that user name and password is an isp issue, in order for me to even get online i need that user and password set correctly.


when you originally had your internet installed' didn't you have to go online and setup an account ?


this account is the email address and the password !

i don't really know if this is done in other countries, it is done here.

---

### Post by puppywhacker on 2009-04-19
Nothing will work if you don't set the VPI and VCI

[SIZE="7"]VPI : 8
VCI : 35[/SIZE]

---

### Post by khelben1979 on 2009-04-19
> **puppywhacker said:**
> Nothing will work if you don't set the VPI and VCI

[SIZE="7"]VPI : 8
VCI : 35[/SIZE]

:D

Already done this. And... please turn down the font size. :-k

---

### Post by khelben1979 on 2009-04-19
It still doesn't work. The modem can't get it's own DHCP IP address from what I can see. My correct information for my e-mail account has now been inserted also, but it didn't help.

I have disabled the internal firewall since yesterday, just in case it would cause problems.

I'll post a new screen dump + my output of ifconfig:

81-224-174-203-o1123:/etc/init.d# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:e4:85:9f:0e  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:e4ff:fe85:9f0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:107609 errors:5 dropped:4 overruns:0 frame:4
          TX packets:63362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:147843754 (140.9 MiB)  TX bytes:10039704 (9.5 MiB)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62368 (60.9 KiB)  TX bytes:62368 (60.9 KiB)

---

### Post by inobe on 2009-04-20
host and domain along with user and password, this information should be provided by your isp.

here where i live the isp ships the modem, the user connects it and is prompted to create and account once a web browser is launched, the connection to the server automatically configures the modem remotely during the setup.

in your situation it seems you purchased the modem/router, it would be important to copy the information from the old modem to the new one' or contact your isp to obtain it.

when you first got your internet service' what steps did you need to do in order to activate the service ?

please include more information about the old modem if any.

the user name and password is to assure no one else connects for free.

---

### Post by jla on 2009-04-20
I just set up a Befsr41 Dsl router for an imac. I ended up using 255.255.255.192 rather than 255.255.255.0.for subnet address. Lan ip address 192.168.1.1 subnet address 255.255.255.192 I no expert but that's what worked for me.

---

