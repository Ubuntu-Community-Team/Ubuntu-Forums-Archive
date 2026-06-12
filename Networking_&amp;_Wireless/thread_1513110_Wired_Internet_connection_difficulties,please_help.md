---
title: "Wired Internet connection difficulties,please help :("
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by ...waffles? on 2010-06-19
Hello everyone, 
I'm totally new here and new to Ubuntu but I am already a big fan of it. As the title implies, Im having difficulty connecting using a wired connection to my verizon FIOS router. I installed Ubuntu 10.04 on my laptop and everything runs fine, then I installed it on my desktop but had to use the alternate CD. During installation I didn't have my ethernet cable plugged in to the PC so I skipped the Network configuration bit, and once the install was finished I couldn't connect. I read quite a few of these forums and tried a few things, but nothing has worked. So far as I remember I have tried manually inputting the IPv4 address, subnet mask, and default gateway, trying the other settings in IPv4 and IPv6 areas of the Network Connections, a different cable, the same cable on another PC to make sure it worked, and stuff like rebooting and disconnecting reconnecting the cable. I'm unaccustomed to anything besides Windows, and I hated/hate Windows. I am also very new to FIOS or any kind of home networking. I appologize for rambling and here are some specifics: HP Pavillion p6210y PC with Nvidia nforce 10/100 Mbps Ethernet adapter, and a wired connection to an Ultraline Series3 model 9100em router. I'm really unsure where to even start and don't know what information will be useful but I'm grateful in advance to all who respond and I'm glad to be here.

Oops forgot, after manually inputting IPv4 settings it said auto eth0 connection active or something like that but I couldn't get online so I tried pinging and tracerouting my router, and ubuntu.com, and other computers on my LAN, but nothing went through. However, when I logged into the Wireless broadband router management console from another computer, my PC showed up on the network as connected to ethernet and online along with an IP address of 192.168.1.4, where as previously it always said offline. I don't know what this means but it is discouraging to see that it is "Online" but I still have no internet connection :( 

thanks again, ...waffles?

---

### Post by think13 on 2010-06-19
I'm glad you like Ubuntu...

I'm not sure what your problem is; I think we need a little more information to debug the problem.

Can you post the results of ```
sudo lshw -class network
``` (which lists your network hardware) and ```
ifconfig
``` (which shows your network configuration)?

---

### Post by ...waffles? on 2010-06-19
Thanks for the speedy reply!!!  Here is the network hardware:

  	 	 	 	 	 	  *-network                
        description: Ethernet interface  
        product: MCP77 Ethernet  
        vendor: nVidia Corporation  
        physical id: a  
        bus info: pci@0000:00:0a.0  
        logical name: eth0  
        version: a2  
        serial: 90:e6:ba:58:4f:2d  
        size: 100MB/s  
        capacity: 100MB/s  
        width: 32 bits  
        clock: 66MHz  
        capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s  
        resources: irq:29 memory:fce7c000-fce7cfff ioport:c880(size=8) memory:fce7e400-fce7e4ff memory:fce7e000-fce7e00f  
 

and here is the network config:
  	 	 	 	 	 	  



eth0      Link encap:Ethernet  HWaddr 90:e6:ba:58:4f:2d   
           inet6 addr: fe80::92e6:baff:fe58:4f2d/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:9 errors:1 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:1782 (1.7 KB)  
           Interrupt:29 Base address:0xe000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:92 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:92 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:6912 (6.9 KB)  TX bytes:6912 (6.9 KB)

---

### Post by think13 on 2010-06-19
Your eth0 only has IPv6 information, so that could be a problem. You could try ```
ifconfig eth0 192.168.1.4
```. That is not a permanent solution (the setting isn't saved) but it is something to try.

I'm not an expert, so until one comes along, I will refer you to these pages: [http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)
[http://ubuntuforums.org/showthread.php?t=86389](http://ubuntuforums.org/showthread.php?t=86389)
[http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/ac6983ac71a95aebca256f3800170b4f?OpenDocument](http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/ac6983ac71a95aebca256f3800170b4f?OpenDocument)

---

### Post by lymanjayan on 2010-06-19
Your problem is unique. If you get any solution of that problem please tell me. You said your IP address showing you online but you can't access internet. I think you have to check your network setting.  B'cos you check ping and its work that means there is no problem in connection.

---

### Post by ...waffles? on 2010-06-19
OK...when I type the command ifconfig eth0 192.168.1.4 it says "unable to resolve host MyPC" then asks for password, and when i enter password nothing happens. The only way I can get it to activate auto eth0 is if I manually input IPv4 settings and set IPv6 to Ignore, but despite the "wired network connection Auto eth0 is active" message I can't do as much as ping another computer on my network. Could this problem be linked to the fact that I skipped the network configuration part of install or whatever it was? If so would something as drastic as a fresh install be necessary? Any insight at all will be of great help to me, if i could just narrow down the possibilities.

---

### Post by think13 on 2010-06-20
Does your network use DHCP, or do you have all static addresses?  If you use DHCP, /etc/network/interfaces should have ```
auto eth0
iface eth0 inet dhcp
```. You can check this with ```
cat /etc/network/interfaces
``` and you can edit that file with ```
sudo gedit /etc/network/interfaces
``` You probably need to restart the interface with ```
sudo ifdown eth0
sudo ifup eth0
``` if you change that file.

If you don't have a lot of important information on your system, a total reinstall won't be the end of the world. I hate recommending it, but unless a networking guru steps in here, we may be stuck.

---

### Post by Iowan on 2010-06-21
Brain is not fully engaged tonight (sorry). You mentioned an IP address of 192.168.1.4 - but via a different computer... **ifconfig -a** doesn't show that address for eth0?  You can see if **sudo dhclient eth0** results in a valid IP address.

---

### Post by ...waffles? on 2010-06-24
Sorry for the late response, but I'm a full time student, which makes connectivity issues all the more frustrating. Anyway, what I meant in my earlier post was that when I access my router by going to [http://192.168.1.1/](http://192.168.1.1/) via my laptop, my trouble PC is listed as online in my network connections list. However, it says that the device type is unknown and I cannot ping the router or do anything at all from the PC. I have purchased a wifi card (because I needed one anyway), and so will hopefully be able to get access using that, and perhaps help troubleshoot my wired issue, but I'm still really confused as to why my router seems to recognize my PC, but I can't connect to it OR the internet :(. The only way I can get this far (as in, having my computer show up on the network at all) is by going to network connections and editing the connection by entering the IPv4 and MAC addresses, when I enter the gateway and click ok, it automatically reverts to 0.0.0.0. Also, I haven't entered any DNS settings, could this be the problem? I figured once I was connected to the router it would take care of that but...:(. What exactly would I put for the DNS settings, does Verizon FIOS have a default DNS or something? Thanks to all those who have helped, and I hope to get some more insight into this issue. My wifi card should arrive in the next two days, maybe it will help shine some light on the problem, or at least give me Internet :guitar:

---

### Post by Iowan on 2010-06-24
It's probably in the thread somewhere, but... did you configure via Network Manager or did you edit */etc/network/interfaces*?

---

