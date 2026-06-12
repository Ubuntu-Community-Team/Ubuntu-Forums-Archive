---
title: "Networking worked now doesn't"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by Richard Owen on 2010-08-18
Hi guys,
 
I have a problem with the networking running Ubuntu 10.4 on my Sony Vaio.
 
It was working fine (and had been for the few months since I upgraded to 10.4)
 
I was fiddling round in the workshop and disconnected the router from the phone socket. So the PC could still see the router but couldn't see beyond that. Forgetting that I'd disconnected the router from the phone socket I tried to recieve mail, which obviously didn't work. I then tried to update some web pages with the obvious results. I have a second router so I switched the wireless connection to that. Still couldn't get my mail or connect to a web page.
 
Anyway, after much angst and reconnecting the router and trying everthing I could think of here is the current situation:
 
Both routers connect to the internet.
 
All other PCs in the house (both Windows and Ubuntu) connect to the internet via either router.
 
My PC connects to either router and I can log onto the router. Network tools tells me I'm connected to the internet and I can ping and trace routes using names so I don't think I've got a DNS problem.
 
I've also checked the proxy settings on Firefox and even checked that firefox and evolution haven't gone into offline mode (which they haven't.) But neither of them will connect.
 
It doesn't matter if I connect with a wire or wireless, the behaviour is the same.
 
Where should I look next?

---

### Post by Richard Owen on 2010-08-18
Quick Update. After reading another post about what's working and what's not working, I tried update manager. Which works.
 
So, the computer is connected to the internet and some things will communicate effectively, but Firefox and Evolution won't.
 
Some guidance as to where to start looking would be most appreciated.
 
Thanks,
   Richard

---

### Post by kestrel1 on 2010-08-18
Give us the output of the command
ifconfig
This should help diagnose the problem.

---

### Post by Richard Owen on 2010-08-18
Hi,
 
Thanks for the message. Below is the output from ifconfig. Reading other posts with networking problems, they were asked to run route and lshw commands as well. So I've done all three and posted the output below. Hopefully if will be of some use.
 
Richard
 
 
[EMAIL="richard@ubuntu:~$"]richard@ubuntu:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:a9:80:90:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:222110 (222.1 KB)  TX bytes:222110 (222.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:b5:de:bc  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:feb5:debc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27445946 (27.4 MB)  TX bytes:1118244 (1.1 MB)
 
[EMAIL="richard@ubuntu:~$"]richard@ubuntu:~$[/EMAIL] route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

[EMAIL="richard@ubuntu:~$"]richard@ubuntu:~$[/EMAIL] sudo lshw -C network
[sudo] password for richard: 
  
*-network               
       
description: Ethernet interface
       
product: 88E8036 PCI-E Fast Ethernet Controller
       
vendor: Marvell Technology Group Ltd.
       
physical id: 0
       
bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
       
logical name: eth0
       
version: 13
       
serial: 00:13:a9:80:90:60
       
capacity: 100MB/s
       
width: 64 bits
       
clock: 33MHz
       
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 
autonegotiation
       
configuration: autonegotiation=on broadcast=yes 
driver=sky2 
driverversion=1.25 
firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       
resources: irq:27 memory:d6000000-d6003fff ioport:2000(size=256)
  
*-network
       
description: Wireless interface
       
product: AR5001 Wireless Network Adapter
       
vendor: Atheros Communications Inc.
       physical id: 0
       
bus info: [EMAIL="pci@0000:06:00.0"]pci@0000:06:00.0[/EMAIL]
       
logical name: wlan0
      
 version: 01
       
serial: 00:16:cf:b5:de:bc
       
width: 64 bits
       
clock: 33MHz
       
capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       
configuration: broadcast=yes driver=ath5k ip=192.168.0.2 l
atency=0 multicast=yes wireless=IEEE 802.11bg
       
resources: irq:18 memory:da000000-da00ffff
[EMAIL="richard@ubuntu:~$"]richard@ubuntu:~$[/EMAIL]

---

### Post by Richard Owen on 2010-08-18
Hi guys,

I know it's mostly me contributing to this thread, but I keep trying things to see if I can get it working. Also, I'm hoping the combination of adding more information and refreshing the thread will draw it to the attention of someone who can help.


My latest thought was that it might be a firewall problem.

I haven't configured the firewall since I built the system and was unsure of its state, so I checked.

And it's inactive. So it isn't that.

Any and all contributions are welcome.

---

### Post by kestrel1 on 2010-08-18
From what I can see you have a connection via wireless. Have you tried connecting a LAN cable to see if you are getting to the Internet via that route?
Try pinging your router:

ping 192.168.0.1

Do you get any response? or does it time out?

---

### Post by Richard Owen on 2010-08-18
Thanks for taking the time to get back to me.

Wired or wireless, it's the same behaviour.

Not only can I ping the router, I can ping anywhere in the world. 

In fact everything on this PC will talk to the outside world apart from Firefox and Evolution.

---

### Post by kestrel1 on 2010-08-18
You need to make sure that you haven't set a global proxy by mistake if you are using a direct connection to the net. Not on Ubuntu at present, but i think it is under System -> Preferences -> Network Proxy

---

### Post by Richard Owen on 2010-08-18
Hi,

Just checked and Proxy Configuration is set to Direct Internet Connection.

I've clicked the Apply System-Wide button in case it made any difference. But it didn't.

What should I try next?

---

### Post by kestrel1 on 2010-08-19
Is Firefox set to No Proxy?
Check the file apt.conf & see what it has in it:
> gedit /etc/apt/apt.conf
If there is any proxy setting in there delete them, but you will need to use:> sudo gedit /etc/apt/apt.conf to do this.

---

### Post by Richard Owen on 2010-08-19
File is empty.

---

### Post by Richard Owen on 2010-08-19
Firefox is set to no proxy.

---

### Post by kestrel1 on 2010-08-19
Have you tried any other web browsers or email clients?
I normally use Thunderbird for mail & you can install it with```
sudo apt-get install thunderbird
```

---

### Post by Richard Owen on 2010-08-20
Now that's an interesting thought.

Another mail client sounded like too much work, but another browser didn't, so I downloaded and installed Chromium and Epiphany.

They both work. 

I have Firefox, Chromium and Epiphany all open on the screen. Any given web address works with the later two but no web address gets me anything other than a 'this website took too long to reply' message with Firefox.

There isn't a DNS cache somewhere in the system is there? Could it be that when I changed routers, for some reason, Firefox and Evolution continue to look for the old settings?

And, Yes, I have checked again and Firefox is set to No Proxy.

---

### Post by kestrel1 on 2010-08-20
If you go to System -> Preferences -> Network Connections you should be able to see what each connection is using. I would suspect that wired & wireless are both set to use DHCP, so this should be fine. I cannot see why Firefox would use different DNS to other browsers.
What you could try is removing the .mozilla folder from your profile then running firefox again. This should recreate a profile for firefox.
I would suggest renaming the .mozilla folder to something like .mozillaold & move it to another location.
You need to open your home folder & then select View & Show Hidden Files to see the .mozilla folder. If this works you can do the same for Evolution.

---

### Post by varunendra on 2010-08-23
> **kestrel1 said:**
> What you could try is removing the .mozilla folder from your profile then running firefox again. This should recreate a profile for firefox.
I would suggest renaming the .mozilla folder to something like .mozillaold & move it to another location.
+1

Or,
just try to clear entire cache of Firefox (Tools>Clear Recent History>select 'Everything')

---

### Post by masoomac on 2010-08-26
Hi,
Seems like the problem is with IPV6 settings. It needs to be off for internet to work on firefox and evolution. 
Check out this - [http://ubuntuforums.org/showthread.php?t=1522409](http://ubuntuforums.org/showthread.php?t=1522409)

It got internet connection started on Firefox but not Evolution though. I still have to figure what to do with Evolution - I uninstalled using the Software Center but could not re-install it again... 

Hope this helps

---

### Post by mathia on 2010-09-16
Hi Richard,
please install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8036 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

if it did not work try to boot with options "noapic nolapic acpi=off" in grub and let me know if it works.

have a lot of fun ...:razz:

---

