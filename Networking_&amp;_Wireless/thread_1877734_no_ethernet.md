---
title: "no ethernet"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by jacknet52 on 2011-11-08
My dual boot Ubuntu 11.10/Win7 ethernet connection died when I switched from wireless to wired. Works fine on the Windows side but Ubuntu is like there is no cable even connected. How do you trouble shoot this?

---

### Post by An Sanct on 2011-11-08
Does the output of ifconfig show a configured eth0 (LAN)?

---

### Post by jacknet52 on 2011-11-08
no sir Hardware addr: all 0's

---

### Post by An Sanct on 2011-11-09
*HWaddr* should be the mac in *XX:XX:XX:XX:XX:XX* form and *inet addr* should be an assigned IP address.

There might be something wrong with your configuration. Please recheck the IP/DNS and (if enabled by router) DHCP settings

---

### Post by jacknet52 on 2011-11-09
Thanks An for responding again. I'm really new and I'm not sure how you check for ip. When I run ifconfig I get the settings for eth0 and lo. There is no ip in the eth0 report and no hardware address. But if it can report an eth0 doesn't that mean it at least sees it? And I'm writing this from the same machine but on the win7 boot so it's not the hardware. What commands can I run to do some checking?

---

### Post by jacknet52 on 2011-11-09
thanks an for trying to help. It was a driver and my boss at work a linux guru whipped his magic on it. Now I just have to figure out what he did.
Take Care,
Jack

---

### Post by jonobr on 2011-11-09
You should get your boss to join the forums :P

---

### Post by An Sanct on 2011-11-09
> **jonobr said:**
> You should get your boss to join the forums :P
+1 to that :)

note: ifconfig output looks like this, I've bolded some the MAC, IP(v4 and v6) ... 

(the bb:bb:bb:bb part was edited out ...)
```

eth0      Link encap:Ethernet  **HWaddr bc:bb:bb:bb:bb:af  **
          **inet addr:192.168.1.7**  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: **fe80::beae:c5ff:fe12:7baf/64** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10425260 (10.4 MB)  TX bytes:4232047 (4.2 MB)
          Interrupt:55 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:561136 (561.1 KB)  TX bytes:561136 (561.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:bb:bb:bb:bb:fb  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:6bff:fe18:1cfb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58917 (58.9 KB)  TX bytes:12351 (12.3 KB)

```

PS. please close this thread, if your problem was solved, as it was not solved by this thread, please drop a line on how it was solved, so it can help others :) not everybody has a cool boss like that ;)

---

### Post by jacknet52 on 2011-11-09
@An - Well that was at work. Now I'm home and my boss ain't answering his phone. @work it was fine. I got it home and it's just as described above. However in the additional drivers sys. settings it shows the driver he loaded but says it's activated but not in use. How do you put it in use. You know, I have some very expensive linux and Ubuntu books and no where in there do they say a thing about loading drivers or how to do anything along those lines. I guess they think we all live in a perfect world. Thanks.

---

### Post by An Sanct on 2011-11-10
Well, then there is a good reason, why you should ask your boss, what he did ;)

Okay, on the top panel, on the right side, you should see two arrows, pointing up&down. Right click on them and select "Edit Connections...", from the newly opened "Network Connections" window, select the "Wired" tab and select the entry (normally) named "Wired Connection 1". Click Edit and...

-Make sure, "Connect automatically" is checked,
-Select the IPv4 tab and make sure the settings are correct according to your router/access
-If needed, do the same with IPv6, If not needed, select "Ignore" from the drop down.
-It is a good idea to make the "Available to all users" checked too, unless you have some security obligations (I hardly doubt that you have...but who knows :))

Click Save and that should be it, your network should be configured.

If this does not work "out of the bow", then open a terminal and run this:
```
sudo /etc/init.d/networking restart
```
This restarts the netowrking...

If this still did not help you, please post the output of [I]ifconfig.
[/I]

---

### Post by jacknet52 on 2011-11-10
Good Morning An - My boss is wierd. He won't take my calls or emails. I won't see he again till Monday. I don't have the two arrows. I have the blanked out triangle thing like for wireless. When I click on that the "Wired Network" and "disconnect" tabs are grayed out. Same thing when I go into "Networking" services. The driver is there but and it says it's activated but "not in use". How do I reload the driver and make it work so everytime I shutdown it will still be there when I restart it? Thanks

---

### Post by jacknet52 on 2011-11-10
My boss finally called and gave the solution:


cd ~/DriverInstall
sudo ./install.sh
Thanks for all those who tried to help.

---

