---
title: "Server not working…"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by Sonny737 on 2013-04-14
Hi there,

The tutorial I used can be found [here]("http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/").

So I wanted to create a dedicated server, and I found a tutorial which details how to do it using ubuntu server. Everything pretty much went according to plan (even though the tutorial is slightly outdated). I am running on OSX, and I used VirtualBox to install and launch ubuntu server on a virtual hard drive. I got up to halfway through step five, where it says to check your server using a browser by pasting in the IP. It doesn't work. So, my question is: why the heck doesn't it work??? Is it because I'm using a virtual hard drive?

Any help would be greatly appreciated…

Thanks in advance guys :D

---

### Post by steeldriver on 2013-04-14
Possibly because your VM is behind a VirtualBox NAT? that's fine for outgoing connections from the VM, but for incoming connections you probably want to switch to a bridged config so that the VM appears to be on the same subnet as your non-virtual hosts

---

### Post by Sonny737 on 2013-04-14
Since I'm a complete newbie to ubuntu and servers in general I have no idea what that means&#8230; Is there any way I can check that? Or would that be something for the VirtualBox forums?

---

### Post by steeldriver on 2013-04-14
Well if you open a terminal on your virtual machine and do an 'ifconfig' you will probably see an IP address in the 10.X.X.X range e.g.

```
steeldriver@steeldriver-VirtualBox:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          [COLOR=#ff0000]**inet addr:10.0.2.15**[/COLOR]  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe1c:7a0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:899 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4011909 (4.0 MB)  TX bytes:109068 (109.0 KB)
```

whereas if you are on a regular home LAN / router your host network's IP is likely in the 192.168.X.X private range

If you go into your VirtualBox machine settings --> Network and change 'Attached To: NAT' to 'Attached To: Bridged Adapter' and then restart networking in the VM you should see the IP change to one in the host subnet e.g.

```
steeldriver@steeldriver-VirtualBox:~$ sudo service network-manager restart
steeldriver@steeldriver-VirtualBox:~$
steeldriver@steeldriver-VirtualBox:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          [COLOR=#ff0000]**inet addr:192.168.1.18**[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe1c:7a0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6606506 (6.6 MB)  TX bytes:390306 (390.3 KB)
```

Hope this helps

---

### Post by Sonny737 on 2013-04-14
Well I did what you said, and it didn't change anything. Still has the 10.0 IP. But then I went back to OSX and found that its IP was also a 10.0. Any thoughts?

---

### Post by steeldriver on 2013-04-14
Well can you ping the server? can you connect via ssh? is it just the web server that you can't reach?

Oh and btw sorry I should have mentioned that if you installed a server ISO then the command to restart networking is probably 'sudo service networking restart' not 'sudo service network-manager restart'

---

### Post by Sonny737 on 2013-04-14
No problem; I figured out the proper command from the internet, as usual. Anyways it works now on my home network, but what about other people? Should people on other networks be able to type the IP into their browsers and have it come up with the "It works" message?

---

### Post by steeldriver on 2013-04-14
10.x.x.x is also a reserved private IP range - so presumably your whole LAN is behind a real NAT device (like a residential router) which just gets a single public IP from your ISP - you would need to set up port forwarding on that router just like for a 'real' host (and some kind of dynamic DNS - unless you pay for a static public IP)

If you go into your router's web setup, you should be able to see the bridged device there and setup its port forwarding

---

### Post by Sonny737 on 2013-04-14
So I should be able to look up port forwarding and have it work?

---

