---
title: "Realtek wireless works on all APs except for my WRT54G2"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by holotone on 2009-08-23
My Toshiba a215-s5808 laptop has a wireless card that appears to work everywhere I've tried it but (of course) at my own house, which serves cable internet through a Linksys WRT54G2. Odd thing is, the AP gives me  an IP address and the connection information all appears just fine. No network access though - I can't ping anything, including the gateway.

lspci lists the ethernet controller as 'RTL8202E/RTL8202E'

According to 'sudo lshw -C network', I'm using the r8169 driver

The AP sees me in it's client table and does not indicate any issues, and many other Windows and Ubuntu clients use this AP with no problem at all. Completely resetting the router to completely default configuration with no security does not resolve the problem.

This is driving me nuts - HALP!

---

### Post by holotone on 2009-08-24
Anyone?

---

### Post by holotone on 2009-08-25
Any suggestions as to how I can start troubleshooting this problem?  I've searched the web for days, asked on IRC numerous times, and have come up with nothing but silence - I'm feeling **really** stuck here. _Any_ help would be seriously appreciated...

---

### Post by holotone on 2009-08-26
Am I posting in the wrong sub-forum or something?

---

### Post by holotone on 2009-08-27
Maybe I just smell.. You'd tell me if I smelled, right?

---

### Post by holotone on 2009-08-27
Would there be a better way to ask the question? Can someone at least suggest an alternative place to get help?

---

### Post by dbalascak on 2009-08-28
Is there a MAC address filter on the WRT54G?  That would allow you to connect, receive an IP address ( if you're using DHCP ) and appear on the LAN, but would drop all packets from your MAC.

---

### Post by holotone on 2009-08-28
> **dbalascak said:**
> Is there a MAC address filter on the WRT54G?  That would allow you to connect, receive an IP address ( if you're using DHCP ) and appear on the LAN, but would drop all packets from your MAC.

I checked to make sure MAC address filtering wasn't abled **_and_** reset the AP itself back to factory defaults, no security. Still no dice.

Thanks for the response!

---

### Post by TransitMan on 2009-08-28
Did you input the requested WPA2 password for connection between you and the router?
If not, then you will get nowhere.

I had a Dell Netbook here recently, and had to set the IP to a static address, gateway to the router, and DNS to the router. The input the proper password for security/WPA2 and after about 2 minutes was good to go.

Double check your settings at home. From your post, it sounds like you surfed opened AP's and yours is password protected, like it should be.

---

### Post by holotone on 2009-08-28
> **TransitMan said:**
> Did you input the requested WPA2 password for connection between you and the router?
If not, then you will get nowhere.

I had a Dell Netbook here recently, and had to set the IP to a static address, gateway to the router, and DNS to the router. The input the proper password for security/WPA2 and after about 2 minutes was good to go.

Double check your settings at home. From your post, it sounds like you surfed opened AP's and yours is password protected, like it should be.

Thanks for your suggestions, TransitMan - Like I said, I've both disabled WPA security on the AP **_and_** completely reset the AP to factory defaults - That is to say that this problem occurs even when the AP is completely unsecured and back in its standard, default, fresh-out-of-the-box configuration.

I'm getting an IP address and the AP sees me in it's clients table, so I don't think that setting static IPs is the solution (though I have tried that too!).

---

### Post by holotone on 2009-09-02
Any other suggestions?

---

### Post by dbalascak on 2009-09-02
So what does the network look like.  Any other active or nonactive interfaces?  Are you running a firewall?
Post 
*netstat -rn* 
*ifconfig -a*
*cat /etc/network/interfaces*

---

### Post by holotone on 2009-09-03
> **dbalascak said:**
> So what does the network look like.  Any other active or nonactive interfaces?  Are you running a firewall?
Post 
*netstat -rn* 
*ifconfig -a*
*cat /etc/network/interfaces*

It's a *super* simple network - A cable modem receives WAN and passes it on to a WRT54G2 which broadcasts it wirelessly. No firewall anywhere on the network.
 
While connected to the problem AP...

netstat -rn:
```
molly@andorifthen:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
```


ifconfig -a:
```
molly@andorifthen:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:93:4d:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:440 (440.0 B)  TX bytes:440 (440.0 B)

pan0      Link encap:Ethernet  HWaddr 06:48:ca:ef:c4:e5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:8a:ec:06  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fe8a:ec06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1994 (1.9 KB)  TX bytes:8278 (8.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-8A-EC-06-63-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


cat /etc/network/interfaces:
```
molly@andorifthen:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

**Thanks, dbalascak!!**

---

### Post by holotone on 2009-09-04
I'm not sure if it's relevant, but the output of those commands is the same when I'm connected to any other AP.

---

### Post by holotone on 2009-09-05
Is there maybe a different driver I can try?

---

### Post by holotone on 2009-09-06
Cross-posted to:
[When was the last time you had a computer problem that nobody else in the *world* had (according to multiple google searches)?]("http://www.reddit.com/r/AskReddit/comments/9huc0/when_was_the_last_time_you_had_a_computer_problem/")

---

### Post by dbalascak on 2009-09-06
Your wireless interface show packets sent and received. Check and see it your IPtables is blocking anything.  This is what sould be seen if there are no blocking rules.

```

$ sudo iptables -L 


Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

---

### Post by holotone on 2009-09-06
> **dbalascak said:**
> Your wireless interface show packets sent and received. Check and see it your IPtables is blocking anything.  This is what sould be seen if there are no blocking rules.

```

$ sudo iptables -L 


Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

My output looks exactly like yours - Like I'd mentioned before, the wireless on this laptop works fine **except** when I'm connected to this very specific AP. Every other computer that connects to the problem AP (Ubuntu or otherwise) works exactly as expected.

---

### Post by bkratz on 2009-09-06
In your searches did you see this?  It seems relevant, once he was able to connect to the router wired he was also able to connect wirelessly.

[http://ubuntuforums.org/showthread.php?t=1223154&highlight=WRT54G2](http://ubuntuforums.org/showthread.php?t=1223154&highlight=WRT54G2)

---

### Post by dbalascak on 2009-09-06
Your interface is receiving and sending packets. You have other systems on the same WRT54G2 that are working? Confirm that you are on the correct WAP by doing an *iwconfig*. Execute the command *sudo tcpdump -i wlan0*. This command will display (continuously) packets sent and received on the interface wlan0.   From another machine or the WRTG54G2  do a ping.  Do you see the packets in the tcpdump window? They will be ICMP Echo packtes. 

Open a second terminal and ping the default router. Are the packets leaving displayed in the tcpdump window?

---

