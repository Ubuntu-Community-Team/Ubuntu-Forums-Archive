---
title: "unable to access 192.168.1.1 to set up Linksys E2500 router"
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by Vpc on 2013-05-16
I am trying to set up my new Linksys E2500 router according to the instructions here: [http://kb.linksys.com/Linksys/ukp.aspx?pid=80&vw=1&articleid=3687](http://kb.linksys.com/Linksys/ukp.aspx?pid=80&vw=1&articleid=3687)
and I am unable to connect to [http://192.168.1.1](http://192.168.1.1) 

With the ethernet cable connecting my pc to the router I try  (Note: I ran 'sudo route add default gw 192.168.1.1' before I connected the ethernet cable to the router and it ran without producing the error message that it did below):
```
sudo dhclient eth1
RTNETLINK answers: File exists
sudo route add default gw 192.168.1.1 
SIOCADDRT: No such process
sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          
Ignoring unknown interface eth1=eth1.
```

My /etc/network/interfaces file:
```
auto lo
iface lo inet loopback
```

Output of ifconfig:
```
eth1      Link encap:Ethernet  HWaddr 38:60:77:d5:9b:27  
          inet6 addr: fe80::3a60:77ff:fed5:9b27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112866 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:136856245 (136.8 MB)  TX bytes:13575572 (13.5 MB)
          Interrupt:20 Memory:fe700000-fe720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1609192 (1.6 MB)  TX bytes:1609192 (1.6 MB)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:f6:e5:c6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Also, I disabled Network Manager a few weeks ago and have been using WICD without any problems. I followed the instructions here to disable without uninstalling: [https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager) 
```
sudo stop network-manager
echo "manual" | sudo tee /etc/init/network-manager.override
```
Would uninstalling NM also help?

Output of ifconfig with the ethernet cable connected to the modem and internet connection established:
```
eth1      Link encap:Ethernet  HWaddr 38:60:77:d5:9b:27  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3a60:77ff:fed5:9b27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:136880676 (136.8 MB)  TX bytes:13594190 (13.5 MB)
          Interrupt:20 Memory:fe700000-fe720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1657400 (1.6 MB)  TX bytes:1657400 (1.6 MB)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:f6:e5:c6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Is there a way to fix this or is there a problem with the router?

---

### Post by ajgreeny on 2013-05-16
Can you ping your router, or is that also not working for some reason?

Are you certain that eth1 really is your ethernet connection; it does appear to be but I don't really know what your original **dhclient** command may have done.

What is the output of command **route**?

---

### Post by papibe on 2013-05-16
Hi Vpc.

I'm not familiar with WICD, but...

If Network-manager is disabled, the proper way to use the default networking stack (like in a server) would be to enable your ethernet interface (eth1) in /etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

```
and then restart the network:
```
sudo service networking restart
```
Let us know how it goes.
Regards.

---

### Post by Vpc on 2013-05-16
> **papibe said:**
> Hi Vpc.

I'm not familiar with WICD, but...

If Network-manager is disabled, the proper way to use the default networking stack (like in a server) would be to enable your ethernet interface (eth1) in /etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

```
and then restart the network:
```
sudo service networking restart
```
Let us know how it goes.
Regards.

Hi papibe. After doing the above I was able to access 192.168.1.1 but when I get to step 4 of the set up instructions: [http://kb.linksys.com/Linksys/ukp.aspx?pid=80&vw=1&articleid=3687](http://kb.linksys.com/Linksys/ukp.aspx?pid=80&vw=1&articleid=3687)
I get the message "Can not get an IP address from PPPoE" when I try to connect. I reset the router as instructed e.g. by "unplugging the power adapter of the router for 30 seconds then plugging it back in" but the Internet IP address and DNS servers show zeroes even after that.

Also, when I ran 'sudo service networking restart' after editing '/etc/network/interfaces' I got:
```
stop: Unknown instance: 
networking stop/waiting
```

And when I ran 'sudo /etc/init.d/networking restart' after unplugging the router to reset it as described above, I got:
```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                               
 RTNETLINK answers: No such process
```

The output of 'route':
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default           192.168.1.1     0.0.0.0            UG    100    0        0 eth1
link-local            *               255.255.0.0      U     1000   0        0 eth1
192.168.1.0        *               255.255.255.0    U     0      0        0 eth1
```

---

### Post by papibe on 2013-05-16
Glad you are making progress.
> **Vpc said:**
> ... when I ran 'sudo service networking restart' after editing '/etc/network/interfaces' I got:
If you're able to get to the router, it means that your interface and networking capabilities are, for the most part, working. I wouldn't worry about that message.
> **Vpc said:**
> ... but when I get to step 4 of the set up instructions: [http://kb.linksys.com/Linksys/ukp.aspx?pid=80&vw=1&articleid=3687](http://kb.linksys.com/Linksys/ukp.aspx?pid=80&vw=1&articleid=3687)
I get the message "Can not get an IP address from PPPoE" when I try to connect. I reset the router as instructed e.g. by "unplugging the power adapter of the router for 30 seconds then plugging it back in" but the Internet IP address and DNS servers show zeroes even after that.
I'm afraid there's little that we can help you with that. It is very dependent on your ISP, and in some extent to Linksys.

Here are some thoughts:
[LIST]
[*]Are you replacing your previous router? If so, make sure:
[LIST]
[*][*]Your ISP allows you to do that.
[*][*]Find out if you need to active your router's MAC with them.
[*][*]Find out if there any other technical settings you need to set on the router in order to work with your ISP.
[/LIST]
[*]If you are connecting your new router to your existing modem or router, you should be use the 2nd alternative: DHCP.
[*]Linksys has a relative 'decent' support in their website over chat. They may provide more troubleshooting ideas.
[/LIST]
Let us know how it goes.
Regards.

---

### Post by Vpc on 2013-05-16
> **papibe said:**
> Glad you are making progress.

If you're able to get to the router, it means that your interface and networking capabilities are, for the most part, working. I wouldn't worry about that message.

I'm afraid there's little that we can help you with that. It is very dependent on your ISP, and in some extent to Linksys.

Here are some thoughts:
[LIST]
[*]Are you replacing your previous router? If so, make sure:
[LIST]
[*][*]Your ISP allows you to do that.
[*][*]Find out if you need to active your router's MAC with them.
[*][*]Find out if there any other technical settings you need to set on the router in order to work with your ISP.
[/LIST]
[*]If you are connecting your new router to your existing modem or router, you should be use the 2nd alternative: DHCP.
[*]Linksys has a relative 'decent' support in their website over chat. They may provide more troubleshooting ideas.
[/LIST]
Let us know how it goes.
Regards.

I've used two other new routers (D-Link, TP Link) with this ISP without any problems. I always set it up the same way, using a PPPoE connection setting as described here:
[http://kb.linksys.com/Linksys/ukp.aspx?pid=80&vw=1&articleid=3687](http://kb.linksys.com/Linksys/ukp.aspx?pid=80&vw=1&articleid=3687)
Basically I just do what's listed as step 2: "Enter the PPPoE Username and Password provided by your ISP" and nothing more too it. The only other setting is setting the password for the wireless. There are no other techinical settings. With this router, I just see the extra step in step 4, of having to restart the router by unplugging it. And after that, I still do not get a non-zero IP address and then I get the error "Can not get an IP address from PPPoE" when I try clicking the Connect button again. So how can I get an IP address from PPPoE? And why would I use DHCP instead of PPPoE?

Also, after re-starting the computer, I had to disable Network Manager again and now the output of 'route' has changed to:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         speedtouch.lan  0.0.0.0         UG    0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
```

Also, I cannot connect to the internet through the router (when it's connected to the modem). I only have internet access when the pc is directly connected to the modem.

---

### Post by Irihapeti on 2013-05-16
How have you got the modem set up? Is it in half-bridge mode i.e. assigning the external IP address to the router?

---

### Post by Vpc on 2013-05-16
> **Irihapeti said:**
> How have you got the modem set up? Is it in half-bridge mode i.e. assigning the external IP address to the router?

I configured my Speedtouch ST516 modem for PPPoE (the other choice is Bridging). I connected my pc directly to the modem for internet access. But I was also able to use it with the D-Link and TP Link routers (connected with a wired connection with others using the wireless connection). The last router I used with my modem was a TP Link 841N. 

I don't know what half-bridge mode is or how to "assigning the external IP address to the router". 

So is it the case for this Linksys E2500 that I have to use DHCP? What makes it different from the other routers that I have to used DHCP this time instead of PPPoE where I enter the username and password for my ISP?

---

### Post by Irihapeti on 2013-05-16
I just wondered - the IP routing table said "speedtouch.lan". I happen to have  Speedtouch modem set up in half-bridge mode. Essentially, it means that the modem does the username-and-password thing with the ISP, and gets the external IP number. But the actual routing and firewall part is done by the router.

I think that if you want to use the router for the PPPOE connection, you need to put the modem in bridging mode. If you use the modem to make the connection, then the router needs to be set as an access point. Meaning that it just handles the passwords for wireless devices and that's all.

---

### Post by Vpc on 2013-05-17
> **Irihapeti said:**
> I just wondered - the IP routing table said "speedtouch.lan". I happen to have  Speedtouch modem set up in half-bridge mode. Essentially, it means that the modem does the username-and-password thing with the ISP, and gets the external IP number. But the actual routing and firewall part is done by the router.

I think that if you want to use the router for the PPPOE connection, you need to put the modem in bridging mode. If you use the modem to make the connection, then the router needs to be set as an access point. Meaning that it just handles the passwords for wireless devices and that's all.

Thanks for the info. First, after disconnecting the ethernet cable from the modem (that connects to the pc) and connecting it to a port in the router, I was able to access 192.168.1.1 again after I used dhclient to refresh the IP address:
```
sudo dhclient -r
sudo dhclient eth1

```
Or run 'sudo service networking restart'. Run 'route' to check that the IP routing table is not empty. The output of 'route':
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
```

Then I was able to set up the router with DHCP configuration by following the instructions here:
[http://kb.linksys.com/Linksys/ukp.aspx?pid=80&vw=1&articleid=3687](http://kb.linksys.com/Linksys/ukp.aspx?pid=80&vw=1&articleid=3687)
After changing the value of the 3rd quadrant of the IP address field in step 3, use the above dhclient commands to refresh the IP in step 4 instead of “ipconfig/renew” or go to the "Status" section and click the "Release IP Address" and "Renew IP Address" buttons.

After completing the configuration and connecting the modem to the router, the output of 'route' is:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth1
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
```

As noted in the configuration instructions, 192.168.2.1 is now the new IP address of the router to prevent IP addressing conflicts between the modem and router operating as DHCP servers under the same network.

My remaining question is what are the advantages/disadvantages of having the modem in bridge mode with router using PPPoE vs. modem in routing mode (PPPoE) with router using DHCP? Right now the latter arrangement seems to be working fine but would I have better internet connections with the modem in bridge mode?

---

### Post by Irihapeti on 2013-05-17
> **Vpc said:**
> My remaining question is what are the advantages/disadvantages of having the modem in bridge mode with router using PPPoE vs. modem in routing mode (PPPoE) with router using DHCP? Right now the latter arrangement seems to be working fine but would I have better internet connections with the modem in bridge mode?

It's probably a case of personal preference.

The reason I put the modem in bridge mode is because I have a router running Tomato. My modem is pretty basic (supplied by the ISP), while Tomato has a number of advanced features, such as a much more configurable DHCP server and bandwidth logging. I'm playing with webservers on my home LAN, so I want these features.

But for a basic internet connection, either should work equally well.

---

### Post by Vpc on 2013-05-17
> **Irihapeti said:**
> It's probably a case of personal preference.

The reason I put the modem in bridge mode is because I have a router running Tomato. My modem is pretty basic (supplied by the ISP), while Tomato has a number of advanced features, such as a much more configurable DHCP server and bandwidth logging. I'm playing with webservers on my home LAN, so I want these features.

But for a basic internet connection, either should work equally well.

Yes my SpeedTouch ST516 modem is pretty basic too but I'm just using a basic internet connection so far. I am looking to share this connection with users on the floor below me so maybe I will change the configurations to try out Tomato in future as bandwidth logging may be useful and especially if it can improve signal quality. A reason I didn't want to change the modem configuration right away is that I'm not able to get into it's configuration settings i.e. I can't seem to enter the right username/password into the login prompt. I was told I would have to reset the modem, which has been working without any problems for a few years.

---

### Post by Irihapeti on 2013-05-17
If you're sharing a connection with others, Tomato's QOS features might be useful. They're good for limiting people who would otherwise tie up all your bandwidth with massive downloads. No personal experience with this one, though.

Just a suggestion - if you're going to play with Tomato, it's a good idea to figure out ahead of time how you're going to recover your router if you happen to "brick" it - which I've done more than once! My router is an Asus RT-N10, and they're really easy to reset. I think that Linksys might be a bit more, shall we say, interesting, but not impossible.

---

### Post by Vpc on 2013-05-26
After using the default username "Administrator" (from [http://www.speedtouch.ca/troubleshooting.php](http://www.speedtouch.ca/troubleshooting.php)) I was able to log into the configuration page of my SpeedTouch ST516 modem and set it to bridge mode according to the instructions here: [http://www.speedtouch.ca/bridgemode.php](http://www.speedtouch.ca/bridgemode.php)

I then tried to set up the router to use PPPoE according to the instructions here: [http://kb.linksys.com/Linksys/ukp.aspx?pid=80&vw=1&articleid=3687](http://kb.linksys.com/Linksys/ukp.aspx?pid=80&vw=1&articleid=3687) 
I still get the message "Can not get an IP address from PPPoE" again when I try to set up the connection in step 4. Resetting the router does not help. I also tried running 'sudo service networking restart' and the 'sudo dhclient -r; sudo dhclient' but still got the same message.

I double checked that I used right login information and vpi from my ISP. I used the same info to configure the modem to PPPoE mode again so I can connect to the internet. I had to reset the modem back to factory defaults using the reset button at the back to access the modem configuration page after I disconnected the ethernet cable from the router and plugged it into the modem.

So I'm still looking for a way to get the router to work in PPPoE mode since this can be useful e.g. to use Tomato as describe above.

---

### Post by Irihapeti on 2013-05-26
Unfortunately, I can't be of much help here, as my modem has a completely different configuration. Telecom NZ has gone for a thing called PPPoA and so the modems have been customised accordingly. 

Also I have no experience with Linksys routers. You might find, though, that you have more success doing this with Tomato, which tends to be more capable than many (most?) manufacturers' firmwares.

My suggestion would be to look for information on a router-specific forum e.g. [http://www.linksysinfo.org](http://www.linksysinfo.org) and ask for help there if needed.

---

### Post by Vpc on 2013-05-26
> **Irihapeti said:**
> Unfortunately, I can't be of much help here, as my modem has a completely different configuration. Telecom NZ has gone for a thing called PPPoA and so the modems have been customised accordingly. 

Also I have no experience with Linksys routers. You might find, though, that you have more success doing this with Tomato, which tends to be more capable than many (most?) manufacturers' firmwares.

My suggestion would be to look for information on a router-specific forum e.g. [http://www.linksysinfo.org](http://www.linksysinfo.org) and ask for help there if needed.

Thanks I will look into your suggestions. One thing I'm curious about is there doesn't seem to be Tomato specifically for the E2500, only for the older WR models. So I'm thinking maybe it would be better to try to have the PPPoE configuration done first with the Linksys firmware?

---

### Post by Irihapeti on 2013-05-26
Certainly it's safer to get the factory firmware working first, and in theory it should work.

If you're thinking of trying Tomato, you need to look for modern versions of Tomatousb, which is a further development of the original Tomato, which ceased development a few years ago. I'd suggest looking at the Toastman and Shibby variants - both these gentlemen post on the linksysinfo.org forum in the Tomato section. Incidentally, your router appears to be mentioned here: [http://tomato.groov.pl/?page_id=69](http://tomato.groov.pl/?page_id=69) (Shibby's website).

All of these involve some risk to your router, and it would definitely be safer to get the current firmware working.

---

### Post by Vpc on 2013-05-27
Thanks for the info. Also, should I have to edit my /etc/network/interfaces file after changing my modem to bridge mode and router to PPPoE? Currently I have:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
```

I noticed in the boot messages when I restarted my computer with the modem in bridge mode it seemed to hang at the "network configuration" and there was a message that it would try again. I don't know if the right configuration was found. This never happened with my modem in PPPoE mode.

---

### Post by Irihapeti on 2013-05-27
Sorry, I think I've gone about as far as I can go on this one. Perhaps someone else here can help, or there's some clue to be found on the Linksys forum.

If I happen to have brainwave later on, I'll post back, but I don't think it very likely. :(

---

### Post by papibe on 2013-05-28
> **Vpc said:**
> ```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
```
You should keep this configuration if you are going to keep using your wired connection (eth1) with no network-manager in the mix.

On the other hand, if you are going to be mainly using wireless managed by WCID, you may revert back to what you have before.

In any case, none of these configurations are related on how the modem and the router talk to each other. Your computer will interact with the router's part that is facing your LAN.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Vpc on 2013-06-22
Thank you papibe and Irihapeti. I have removed the lines:
```
auto eth1
iface eth1 inet dhcp
```
from my interfaces file because I used Network Manager again. This time to establish PPPoE connections (created by going to Edit Connections -> DSL -> Add) with my SpeedTouch ST516 modem in bridge mode and also a TP-Link TD-8616 modem which runs in bridge mode. I was able to use both modems to access the internet with my computer directly connected to them. But I got the message "Can not get an IP address from PPPoE" again when I tried to connect to the internet with my computer connected to the Linksys E2500 router (set to PPPoE) and the router connected to either modem. Adding back those two lines above to the interfaces file did not fix this either.

---

### Post by Vpc on 2013-06-23
There may be a problem communicating with the modems in bridge mode in general. I also cannot access the modem configuration pages when they are in bridge mode although they can connect to the internet through a PPPoE connection in Network Manager. This problem is posted in this thread.
[http://ubuntuforums.org/showthread.php?t=2156120](http://ubuntuforums.org/showthread.php?t=2156120)

---

