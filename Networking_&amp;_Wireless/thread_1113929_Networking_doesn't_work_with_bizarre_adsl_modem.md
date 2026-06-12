---
title: "Networking doesn't work with bizarre adsl modem"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by walkingbeard on 2009-04-02
Hi,

I've just moved house and I've got a D-Link DSL-320T, owned by the other housemates.

It works fine in Windows, but it's a bit strange, because if you log onto the modem (192.168.1.1) in a browser, it's all set up to give my PC an IP address by DHCP, between 192.168.1.2 and 192.168.1.254.  The actual address you get is the public IP address we are assigned by the ISP, though, with my gateway being 192.168.1.1.

My trouble is that it just doesn't work in Ubuntu (8.10 64 bit), which I find baffling, since it's connected to my PC by ethernet cable - there's nothing that Windows gets that Ubuntu does not.

Can anyone help?  The modem has the latest firmware and is running Busybox.

Furthermore, I would like to enable NAT on the modem, so I can connect through a normal five port switch, to more than one computer at a time.  Any takers for this part?

Cheers,

Beard

---

### Post by walkingbeard on 2009-04-02
My connection details in Ubuntu are showing what they do in Windows XP too, but I can't get any web connection for example, and I can't ping the modem.

---

### Post by superprash2003 on 2009-04-02
you use a dialer in windows to connect to the internet? post output of ifconfig from the terminal of ubuntu.. also posting ipconfig from a windows machine could help

---

### Post by walkingbeard on 2009-04-03
Here's the result of ipconfig /all:

```
Windows IP Configuration

        Host Name . . . . . . . . . . . . : aubrey
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
#2
        Physical Address. . . . . . . . . : xx-xx-xx-xx-xx-5C
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : xxx.xxx.xxx.249
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : xxx.xxx.xxx.13
        Lease Obtained. . . . . . . . . . : 03 April 2009 19:14:30
        Lease Expires . . . . . . . . . . : 03 April 2009 19:15:30
```0

The modem's web admin tells me that it is set up to deliver my PC an address between 192.168.1.2 and 192.168.1.254, but in fact it gives me the public IP address, xxx.xxx.xxx.249.

Ubuntu details to follow shortly.

---

### Post by walkingbeard on 2009-04-03
Here's the result of ifconfig -a:

```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:5c  
          inet addr:xxx.xxx.xxx.2  Bcast:xxx.xxx.xxx.2  Mask:255.255.255.255
          inet6 addr: xxxx::218:xxxx:feda:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71230 (71.2 KB)  TX bytes:209514 (209.5 KB)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2016176 (2.0 MB)  TX bytes:2016176 (2.0 MB)

pan0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:4f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by coffeecat on 2009-04-03
I'm as baffled as you, but just a couple of comments.

I had a D-link modem-router once. It worked well enough, but D-Link must have the worst web configuration interface in the whole of the known Universe. It's appalling.

That being said, is it possible that somewhere in that ghastly configuration, someone has set it up for some sort of IP address forwarding? And if the NAT is switched off, perhaps that's the reason it's got its knickers in a twist. Although the interface was bad, I seem to remember that enabling NAT was clear enough and the default setting was for NAT enabled. Which leads me to....

Why not do a hard reset of the thing back to the factory settings? Either a little depressed button somewhere on the back, or a 'reset to factory' settings somewhere in the web interface. (If you can find it. :() You'd have to reconfigure with your ISP settings, but that might get rid of this weird behaviour. And you could then check to see if NAT has been enabled. If your housemates don't like the idea, say that without NAT the security on that thing is bad. A reset is for security. :p

One last thing. How old is it? I bought mine in 2005 and it came with 2004 firmware which couldn't cope with IPv6 addressing, which nicely mucked up my early Linux experience. It took me ages to work out what was wrong. Solved eventually with a firmware upgrade, but that and the web interface has soured me against D-Link.

I use a Linksys now. :wink:

---

### Post by walkingbeard on 2009-04-04
Keepy-uppy

---

### Post by coffeecat on 2009-04-04
My apologies, **walkingbeard**. I clearly didn't read your first post properly. I must have been tired. I know how irritating that is.

:oops:

---

