---
title: "Slow Internet 10.04"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by Lvcoyote on 2010-11-11
Hello Everyone,

I'm running Linux Mint 9 (Based on Ubuntu 10.04) and absolutely love it!  I have spent hours getting it all set up and customized but I am left with one nagging issue, the speed at which FireFox browses the Internet. 

I have spent a countless amount of time on Google searching for a fix and have tried just about everything but nothing has worked as of yet.  I've tried all the about:config changes that people suggest, disabling Ipv6, open DNS, Checked router and Min 9 to make sure both are at 1500 MTU, different browsers including Opera and Chrome.  I attempted so many things that I was thinking I may have something all jacked up so I did a fresh install a few weeks ago.  Now that I have it all set up again, I thought I would solicit some expert advice and try and get this fixed the first time.

Typically what happens is when I click on a link there is about a 10 second delay before it finally kicks in, then about 95% of the page loads quickly and it takes another 10 seconds or so for page to finish off.  After the first ten seconds it's extremely fast until that last 5%.  So basically its at the beginning and end of each attempt to access a web site.

I dual boot with Windows 7, which does not have the issue described. In Windows 7 the Internet flat out flies, no issues at all.

Any advice would be appreciated!

Thanks!

---

### Post by dineshs on 2010-11-12
My suggestion is (Sorry if you have already tried this)
1) First confirm whether it is an MTU issue .Ref [this]("http://ubuntuforums.org/showthread.php?t=872346")
2)If yes note down the optimum MTU value 
3)Set MTU temporarily using```
sudo ifconfig [COLOR="Red"]eth0[/COLOR] mtu [COLOR="Red"]1492[/COLOR]
```
Note ;substitute your values for interface and MTU
To set the value permanently,pl say Are you using Network manager or /etc/network/interfaces

---

### Post by Lvcoyote on 2010-11-12
Ok, setting the MTU to 1492 seems to help the beginning of the navigation process.  I still get the stall at the end of the navigation sequence.  What other MTU values are good to try at this point?  I havent used Network Manager or /etc/network/interfaces at this point.  I assume your asking so I can set the new MTU value permanantly?

Thanks for the help dineshs!

---

### Post by Lvcoyote on 2010-11-12
Here is the output of ifconfig:
dino@dino-desktop ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:bc:01:14:35  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:bcff:fe01:1435/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:8409 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7214865 (7.2 MB)  TX bytes:1347112 (1.3 MB)
          Interrupt:29 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

---

### Post by Lvcoyote on 2010-11-12
I'm trying to dial in the MTU value, and when pinging google with the command

```
ping -s 1464 -c1 google.com
```

I get good results.  I also tried 1463 and 1462 MTU values with good results as well.  My question is two fold now.  When running the above in terminal I get different "rtt min/avg/max/mdev" values.... anywhere from 53.180 to 50.385 depending on the MTU value I set when pinging google. Is the rtt value better if the number is lower or higher??  Also once I determine the best results what is the best way to permanently apply the new MTU value.

Thanks!

---

### Post by dineshs on 2010-11-12
I think you can set MTU as 1482 (higher value).
1)Just try this in terminal
```
gksudo nautilus /etc/NetworkManager/system-connections
```
What are the files you see?
2)Post the contents of```
sudo gedit /etc/network/interfaces
```

---

### Post by Lvcoyote on 2010-11-12
sudo gedit /etc/network/interfaces returns just the following:
```
auto lo
iface lo inet loopback
```

---

### Post by Lvcoyote on 2010-11-12
When I run - "gksudo nautilus /etc/NetworkManager/system-connections" a window opens with a "Auto eth0" file.  I opened that and here is what is in that file:

[connection]
id=Auto eth0
uuid=f1e863e1-0d43-4f63-8ab5-31e3c983260d
type=802-3-ethernet
autoconnect=true
timestamp=0

[ipv4]
method=auto
ignore-auto-routes=false
ignore-auto-dns=false
dhcp-send-hostname=false
never-default=false

[802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mac-address=0:1f:bc:1:14:35
mtu=0

[ipv6]
method=ignore
ignore-auto-routes=false
ignore-auto-dns=false
never-default=false

---

### Post by dineshs on 2010-11-12
> [802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mac-address=0:1f:bc:1:14:35
[COLOR="Red"]mtu=0[/COLOR]Make
```
mtu=1482
``` 
Restart machine and see if it helps
Note:If you are using DSL connection via NM,modification should be done in that file

---

### Post by Lvcoyote on 2010-11-12
At the end of what section??  That file has four sections...... I posted the contents of that file above, where exactly do I add mtu=1482 ??

---

### Post by dineshs on 2010-11-12
Sorry I edited my post(post #9)

---

### Post by Lvcoyote on 2010-11-12
Ok, its much better now, I really appreciate the help.  I'll let the mtu=1482 be for a few days and see how it acts, but it is much faster now.  Thanks again for all the help dinesh!

---

### Post by dineshs on 2010-11-12
Let us wait before marking it solved

---

### Post by Lvcoyote on 2010-11-12
Sounds good.  I do have one question though.... you had me add the mtu=1482 to the 802-3-ethernet section.  Isn't that related to a wireless connection??  Should I add it to the "connection" area??  I wired on this machine.... not using wireless.

---

### Post by dineshs on 2010-11-12
[http://en.wikipedia.org/wiki/IEEE_802.3](http://en.wikipedia.org/wiki/IEEE_802.3)
[http://en.wikipedia.org/wiki/IEEE_802.11](http://en.wikipedia.org/wiki/IEEE_802.11)
> When I run - "gksudo nautilus /etc/NetworkManager/system-connections" a window opens with a "Auto eth0" file. I opened that and here is what is in that file:
For wireless you will see something like wlan0
In brief in /etc/NetworkManager/system-connections you will have seperate files for eth0 (wired),eth1(wired) wlan0(wireless) ,DSL connection etc
You can set  MTU in GUI way as follows
right click NM icon on right top of the panel -edit connections-select the connection say auto eth0-click edit-set MTU and apply
Restart or run
```
sudo service network-manager stop
```then
```
sudo service network-manager start
```

---

### Post by Lvcoyote on 2010-11-12
Understood, thanks again!

---

### Post by Lvcoyote on 2010-12-10
Just as a follow up to provide a solution that worked for me.

```
sudo gedit /etc/nsswitch.conf
```

Look for this line:
hosts: files **mdns4_minimal [NOTFOUND=return]** wins dns **mdns4**

1. Remove the text in bold 
2. Change the order of wins dns to dns wins

The line should read **hosts: files dns wins** when finished.

Reboot and see if this helps you.

Thanks to Ngirl at the LinuxMint forums for the tip!

---

### Post by sergioabreu on 2012-06-10
> **dineshs said:**
> My suggestion is (Sorry if you have already tried this)
1) First confirm whether it is an MTU issue .Ref [this]("http://ubuntuforums.org/showthread.php?t=872346")
2)If yes note down the optimum MTU value 
3)Set MTU temporarily using```
sudo ifconfig [COLOR=Red]eth0[/COLOR] mtu [COLOR=Red]1492[/COLOR]
```Note ;substitute your values for interface and MTU
To set the value permanently,pl say Are you using Network manager or /etc/network/interfaces

THANK YOU INDEED! You saved our lives (or our internet navigation =P)
Millions of thanks to your explanation and configs, my internet is REALLY FAST  now  :guitar::popcorn::P!

---

