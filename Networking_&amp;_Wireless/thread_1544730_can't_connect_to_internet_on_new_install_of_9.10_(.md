---
title: "can't connect to internet on new install of 9.10 (64bit)"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by McNuke on 2010-08-02
I've just installed ubuntu 9.10 (64bit) on a new Dell Precision M4500 (actually I've made it dual boot with Win7).

I'm unable to connect to the internet.  For now, I'd like to get the ethernet card working.

Connection is fine under Windows 7, so I think it is not a hardware problem.

To start with in ubuntu, I *was* able to connect to the internet via the NIC.  Subsequently (not sure why), the ability to connect became intermittent:  at startup, I would either be able to connect or not.  If able, I remain able until reboot; if not, I remain unable until reboot.  Now, I am not able to connect at all.  All this makes me suspect that the NIC driver in ubuntu is OK.

On the suggestion of a local expert, I manually edited /etc/resolv.conf (originally blank) to contain the lines:
search tamu.edu
nameserver XXX.XXX.XXX.XXX (using the IP the expert gave).
This did not seem to help.

less /etc/network/interfaces
shows:
auto lo
iface lo inet loopback

The output of "ifconfig" is shown below.

Thanks for your help getting me connected!
-McNuke



ifconfig shows:

eth0      Link encap:Ethernet  HWaddr 00:26:b9:e3:03:81  
          inet6 addr: fe80::226:b9ff:fee3:381/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:26979 (26.9 KB)  TX bytes:2178 (2.1 KB)
          Memory:e9600000-e9620000 

eth2      Link encap:Ethernet  HWaddr c4:46:19:30:a5:20  
          inet6 addr: fe80::c646:19ff:fe30:a520/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:120
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by dineshs on 2010-08-03
can you run ```
sudo dhclient
```then check ```
ifconfig -a
```?

---

### Post by McNuke on 2010-08-03
sudo dhclient
outputs:
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth2/c4:46:19:30:a5:20
Sending on   LPF/eth2/c4:46:19:30:a5:20
Listening on LPF/eth0/00:26:b9:e3:03:81
Sending on   LPF/eth0/00:26:b9:e3:03:81
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.93.122 from 192.168.93.1
DHCPREQUEST of 192.168.93.122 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.93.122 from 192.168.93.1
bound to 192.168.93.122 -- renewal in 39870 seconds.

ifconfig -a
outputs:
eth0      Link encap:Ethernet  HWaddr 00:26:b9:e3:03:81  
          inet addr:192.168.93.122  Bcast:192.168.93.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b9ff:fee3:381/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:22899 (22.8 KB)  TX bytes:5067 (5.0 KB)
          Memory:e9600000-e9620000 

eth2      Link encap:Ethernet  HWaddr c4:46:19:30:a5:20  
          inet6 addr: fe80::c646:19ff:fe30:a520/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:151
          TX packets:0 errors:12 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth2:avahi Link encap:Ethernet  HWaddr c4:46:19:30:a5:20  
          inet addr:169.254.5.61  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by JBAlaska on 2010-08-03
Please post the output of:
```
sudo iwconfig
```

---

### Post by dineshs on 2010-08-03
What do you get for
```
ping -c3 4.2.2.1
```

---

### Post by McNuke on 2010-08-03
iwconfig
outputs:
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:159
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


ping -c3 4.2.2.1
outputs:
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=55 time=11.5 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=55 time=11.3 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=55 time=11.8 ms

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 11.354/11.596/11.880/0.216 ms

---

### Post by dineshs on 2010-08-03
Can you try this
Right-click on the NM icon( on top right of the panel) and then click on Edit Connections. 
select the tab wired
select eth2 then edit
set DNS under ipv4 select-automatic PPPoE addresses only and give DNS as [COLOR="Blue"]4.2.2.1[/COLOR] and apply

---

### Post by McNuke on 2010-08-03
> **dineshs said:**
> Can you try this
Right-click on the NM icon( on top right of the panel) and then click on Edit Connections. 
select the tab wired
select eth2 then edit
set DNS under ipv4 select-automatic PPPoE addresses only and give DNS as [COLOR="Blue"]4.2.2.1[/COLOR] and apply

In the "Network Connections" dialog, in the wired tab, the only thing listed is eth0.  Shall I add eth2, or is there a more fundamental problem?

---

### Post by dineshs on 2010-08-03
> **McNuke said:**
> In the "Network Connections" dialog, in the wired tab, the only thing listed is eth0.  Shall I add eth2, or is there a more fundamental problem?
I am not  sure.What is there under wireless tab?

---

### Post by McNuke on 2010-08-03
Auto hpsetup is the only entry under the wireless tab.

---

### Post by dineshs on 2010-08-03
Are you getting internet via wireless?if not Can you give DNS as 4.2.2.1 as I told in this hpsetup(I havent used wireless so not sure.But there is no problem in trying)

---

### Post by McNuke on 2010-08-03
> **dineshs said:**
> Are you getting internet via wireless?if not Can you give DNS as 4.2.2.1 as I told in this hpsetup(I havent used wireless so not sure.But there is no problem in trying)

I'm not getting internet by wireless.  I'm using my home ethernet hookup with my old computer.  Beyond that, I don't understand what you are asking.  Can you please rephrase the suggestion?

---

### Post by dineshs on 2010-08-03
I think eth2 is wireless(I have no idea about wireless so not sure)
Since you get reply when you ping 4.2.2.1 which is an open DNS ,you are connected to internet.Still if you are not able to browse it can be a DNS issue.To make sure,open firefox and type the following IP  on the address bar and hit enter.
66.102.7.99
Are you getting google?

---

### Post by McNuke on 2010-08-03
> **dineshs said:**
> I think eth2 is wireless(I have no idea about wireless so not sure)
Since you get reply when you ping 4.2.2.1 which is an open DNS ,you are connected to internet.Still if you are not able to browse it can be a DNS issue.To make sure,open firefox and type the following IP  on the address bar and hit enter.
66.102.7.99
Are you getting google?

OK, yes with 66.102.7.99 I see Google's home page in Firefox.  But more that that, I can successfully go to: [www.google.com](www.google.com), [www.iub.edu](www.iub.edu), [www.xkcd.com](www.xkcd.com), and [www.ucla.edu](www.ucla.edu).  There's no way the last of these was cached from a previous visit - I've never visited that site.  Also, I get 4.92 million hits by searching google for "what the heck".

I don't know why I now have access.

---

### Post by dineshs on 2010-08-03
I think your problem got solved when you got IP(after running sudo dhclient)
Am I right?

---

### Post by McNuke on 2010-08-03
yes, your are right.

verification: I unplugged the ethernet cable, and couldn't connect to anything.  I plugged it back in and still couldn't connect.  I ran sudo dhclient and can now connect.  A google search for "progress" returns 271 million hits.  So, is there a way to automate this?

---

### Post by dineshs on 2010-08-03
what is there in /etc/network/interfaces?pl post output
```
cat /etc/network/interfaces
```

---

### Post by McNuke on 2010-08-03
```
cat /etc/network/interfaces
```
outputs:
```
auto lo
iface lo inet loopback
```

earlier I tried adding (without success)
```
auto eth0
iface eth0 inet loopback
```

---

### Post by dineshs on 2010-08-03
Let us try this .If it doesnt work we can make it default,no problem
Right-click on the NM icon and then click on Edit Connections. 
Select the tab, wired 
select eth0 
select ipv4 
method-manual 
click add 
address [COLOR="Red"]192.168.93.122[/COLOR] 
mask [COLOR="Red"]255.255.255.0[/COLOR] 
gateway [COLOR="Red"]192.168.93.1[/COLOR]
[COLOR="Blue"]then hit enter[/COLOR] 
DNS [COLOR="Red"]4.2.2.1[/COLOR]
then click apply
Restart the machine and try

---

### Post by McNuke on 2010-08-03
After doing the above and hitting apply (but before rebooting), I am no longer connected.  After rebooting, I am still not connected.

---

### Post by dineshs on 2010-08-03
The IP we assigned is one in the DHCP range.May be that is the reason.You can repeat the same steps but 
method- Automatic DHCP(the other fields will automatically fade)
then apply
Do you remember what was the `method' previously?

---

### Post by McNuke on 2010-08-03
The method was previously Automatic DHCP.

---

### Post by dineshs on 2010-08-03
You can continue automatic DHCP

---

### Post by McNuke on 2010-08-03
OK, so I switched the method back to Automatic DHCP, applied it, and rebooted.  So currently I'm not connected to the internet.

---

### Post by dineshs on 2010-08-03
what about *sudo dhclient eth0*

---

### Post by McNuke on 2010-08-03
*sudo dhclient eth0*
outputs:
```
Listening on LPF/eth0/00:26:b9:e3:03:81
Sending on   LPF/eth0/00:26:b9:e3:03:81
Sending on   Socket/fallback
DHCPREQUEST of 192.168.93.122 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.93.122 from 192.168.93.1
bound to 192.168.93.122 -- renewal in 41546 seconds.
```

---

### Post by dineshs on 2010-08-03
Able to browse?

---

### Post by McNuke on 2010-08-03
oh! yes, i am

---

### Post by dineshs on 2010-08-03
So now the only problem is you have to run dhclient on every reboot.Am I right?

---

### Post by McNuke on 2010-08-03
Yes, as it stands now I'd have to run dhclient on every reboot, but also I'd have to run it if I unplug the ethernet cable and plug it back in.

---

### Post by dineshs on 2010-08-03
I googled this issue but couldnt get an answer.Let us wait for today and see if experts like lowan can suggest something

---

### Post by McNuke on 2010-08-03
OK, thanks very much for your help!  Getting a reliable way to connect was a very important step.  Best regards, -McNuke

---

### Post by dineshs on 2010-08-03
One small last question.Is network manager ticked in startup applications?
system-preferences-startup applications

---

### Post by McNuke on 2010-08-03
yes, it is.

---

### Post by McNuke on 2010-08-03
For the purposes of diagnosing the problem, I note:
after booting up, plugging in the ethernet cable, and running dhclient,
although I am connected to the internet, the NM does not seem to know.
A left click on the NM tray icon shows that "Wired Network" is disconnected. Auto eth0 is listed under "Available".

---

### Post by McNuke on 2010-08-03
We haven't solved what we thought we did.

Executing *sudo dhclient* does not work every time.  After I boot up, I left click the NM in the task panel.  If eth0 is listed under "Available", then dhclient will work.  But eth0 is not always listed, and if it is not, then dhclient will not work.

After several restarts, all without eth0 available, I actually shut down the machine and then booted up.  At that point, eth0 was listed.  Could a shutdown really be doing something more than a restart, or is this just coincidence?

I'm going to add eth0 to /etc/network/interfaces so the file reads:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```
and see if I can reproduce the problem.

---

### Post by McNuke on 2010-08-04
Problem solved with this addition to /etc/network/interfaces.  Connected automatically at startup, and this appears to occur consistently.  Only one quirk remains: if I boot in windows and then reboot into linux I can't connect.  Shutdown from windows and boot to linux is ok, but not restart.

Thanks for your help.

-McNuke

---

### Post by dineshs on 2010-08-04
1)I have heard that NM in 9.10 has bug especially reg DSL connections.Dont know whether this is the reason.
[http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10](http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10)
2)If NM is active configuring /etc/network/interfaces may cause problems.Pl refer this
[http://www.uluga.ubuntuforums.org/showthread.php?p=8981408](http://www.uluga.ubuntuforums.org/showthread.php?p=8981408)

---

