---
title: "How to connect smc adsl router"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by emab on 2009-07-29
Hi
I have a new smc adsl router, and I have installed it on windows operating system, but I don't know how to connect it in ubuntu!
Actually I used pppoeconfig and I created a connection, but when I enter
```
pon dsl-provider
```
I recieve:
```
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
```
Actually my auto connection activates, but I have no internet connection using firefox!
and this is my net config
```
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up
provider dsl-provider

auto eth0
iface eth0 inet auto
```
 
 
 
The provider told me that configuration is saved in your modem, but I don't know what is wrong! In windows I have no problem.:confused:

---

### Post by emab on 2009-07-29
nobody helps?

---

### Post by cgb on 2009-07-29
If your ISP is stating the configuration is stored in your modem then there is no reason you need to create a PPPoE connection on your computer.  What does the Route command tell you?

```
route
```

---

### Post by emab on 2009-07-29
```
route
Destination          Gateway        Genmask             Flags   Metric  Ref   Use Iface
192.168.2.0         *                   255.255.255.0        U       1        0      0 eth0
link-local             *                   255.255.0.0v          U       1000   0      0 eth0

```
 
I tried plog, and I got the message incorrect authentication!!!!!
Actually i'm unable to connect through my adsl connection, just my loop back connetion get connects!

---

### Post by cgb on 2009-07-29
Not sure if you just missed a line or if that is the whole route output you received but I dont see that it ever found your gateway?  This could be the problem.  Do you happen to know if you are setup for a static IP in ubuntu or is it trying to pull from DHCP?  You may want to verify that you either have the correct static IP information entered or set it to automatically obtain under system/Preferences/Network Connections.  You could also verify if you are receiving any error messages with the below code.

```
sudo dhclient eth0
```

---

### Post by emab on 2009-07-29
In fact, I checked my modem configuration. Its dhcp is activated so i don't need to use static ip and it must get it from ip pool of modem(it was a range from 192.168.2.100-199)!
 
It connects to my auto eth0, and it must just gets an ip and start working, but it does't ACCESS WWW!
 
I'm confused, where should I set my username and password!
Also plog told me that authentication was incorrect!

---

### Post by cgb on 2009-07-29
You stated in windows you get a connection?  Do you need to setup a PPPoE connection in Windows for it to connect or does it just automatically connect?  Again from what your ISP is telling you, you shouldn't need to setup a PPPoE connection in ubuntu.  This authentication should be taken care of by the modem/router.  Did you try running the below command to see if any error messages or ensure the settings under toolbar (system/preferences/network connections) are correct?  

```
sudo dhclient eth0
```

Also are you able to communicate with your local network?  ex: try pinging the router?

```
ping 192.168.2.1
```

---

### Post by emab on 2009-07-30
I can ping the router 192.168.2.1
 
In windows I have to create a pppoe connection, and also provider told me that I have to create one in linux!
He told me that, when I connect the modem to computer, my automatic connection must get an ip, then my pppoe connection must get activate!
He said I have to enter my username and password in pppoe connection and is not set in modem! So the modem is just a dhcp for supporting more than one computer!
 
The exact problem i have here: PAP authentication is failed!
Actually i disabled all types of encryptions in network manager, and also provider told me that they don't use any encryption method, but still I get this error message!!!!
 
```
dhclient eth0
...
wmaster0: unknown hardware address type 801
/etc/dhcp3/dhclient.conf line 24: no option named rfc3442-classless-static-routes in space dhcp
        rfc3442-classless-static-routes,
        ^
/etc/dhcp3/dhclient.conf line 24: ntp-servers: expected option name.
        rfc3442-classless-static-routes, ntp-servers;
                                      ^
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:...(my net card mac)
Sending on LPF/eth0/00:...(my net card mac)
Sending on /Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.2.100 from 192.168.2.1
DHCPREQUEST of 192.168.2.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.100 from 192.168.2.1
 * Reloading /etc/samba/smb.conf smbd only
No process in pidfile '/var/run/samba/smbd.pid' found running; none killed.
   ...done.
bound to 192.168.2.100 -- renewal in 898592213 secounds.

```
 
 
somebody told me to remove lines:
option named rfc3442-classless-static-routes...
rfc3442-classless-static-routes...
but it didn't worked!

---

### Post by cgb on 2009-07-30
Hmm..  I am not sure what is going on then.   My only advice would be to possibly use another router if you have one available that allows PPPoE connection built in so that the computer itself does not need to perform this task.  You could set the original modem into bridge mode and allow the secondary router to handle the DHCP requests and PPPoE authentication.  Other then that hopefully someone else has some suggestions.

---

### Post by emab on 2009-07-30
Imagine you are given a router with a username and password!
What would you do to connect to the internet?
 
then:
- imagine your provider doesn't support encryption methods
- imagine your /etc/dhcp3/dhclient.conf has gotten some problem
- imagine you have to set ip and... statically (in windows I can get DNS ip and other info)
- imagine your whole network manager has been in problem
I think I have to solve these problems. And also print dhclient.conf if you don't mind!
thank for your help

---

### Post by emab on 2010-03-24
Thank you anyway, the problem is solved.

I clicked on Network Manager applet and below "Wired Networks" it was written "Device not managed", and my /etc/network/interfaces file was containing below:
```
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up
provider dsl-provider

auto eth0
iface eth0 inet auto
```

so I changed it to below and restarted my system:
```
 auto lo
iface lo inet loopback


#auto dsl-provider
#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth0 up
#provider dsl-provider

#auto eth0
#iface eth0 inet auto 
```


after restart, then i understood that my acccount had been finished. then went to modem configuration and set a new password for adsl connection, after saving in firefox i was connected :D

---

