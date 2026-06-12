---
title: "[SOLVED] DNS problem?"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by NDPeter on 2008-12-22
I've got a laptop that I usually use at work.  It's forced to use a static IP there.  I also have a server setup at work so I can access stuff I can't always carry with me.

My problem as best I can identify is this.

Server is at 136.142.x.x

My assigned laptop IP is 136.142.x.y

When I'm at work and on that subnet(is this right?) everything works perfectly.

Now that I'm out of town, I'm connecting wirelessly and am no longer on that network.  I can see the server from any windows computer here...even my laptop.  In Ubuntu though I find "No Route to Host" if I try using ssh.  I also can't get any of the web pages hosted there to load.

traceroute for the website of your choice will start out 192.168.0.1 and go on from there.

traceroute for my server shows that it starts with my laptop's ip... 136.142.x.y


I haven't been able to find where it is that this is set so that I can switch it so instead of looking on my same subnet or whatever it will go out to the intertubes and actually connect.

Thanks.
NDPeter

---

### Post by jonobr on 2008-12-22
Hello


You mention a DNS problem, however, Im guessing its a dynamic ip address allocation issue?

Im assuming at work you have a static IP and now your mobile you need to have a dynamic one.

If you go to your network manager and change your settings to DHCP (before noting your configuration) does that get an IP address from your router?

Thanks

---

### Post by NDPeter on 2008-12-22
It could be a dynamic ip problem.  I was just taking a stab with the DNS...can never think of an appropriate title for the thread.  

You're right...at work I have static IP with the same first 3 sets of numbers 136.142... as the server has.  

I am on a wireless network now and using DHCP to assign my IP.  It works fine.  I can access any other page (including this one!)  Just seems to be the way I'm routed to things on that same network (the 136.142.... one) I have a network printer there that I also can't get to, though can access from windows on my laptop, on the same wireless network.

Thanks for the tip.  now to maybe rename the thread...

---

### Post by NDPeter on 2008-12-22
Some additional info that I think might help diagnose what's going on...at least it raises a red flag to me even if I'm not sure what to do next.

trying to get to the server...
```

traceroute to polonium.chem.pitt.edu (136.142.xxx.yyy), 30 hops max, 40 byte packets
 1  ndirish.chem.pitt.edu (136.142.xxx.zzz)  3000.158 ms !H  3000.156 ms !H  3000.143 ms !H

```

trying any other page.

```
traceroute to www.ubuntu.com (91.189.94.8), 30 hops max, 40 byte packets
 1  192.168.0.1 (192.168.0.1)  19.976 ms  41.435 ms  51.574 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
```


So if it's on that same beginning IP I'm dead...but any other place and I'm great.

---

### Post by jonobr on 2008-12-22
Hey

I would recommend, disconnect the hard wire connection which I assume you are forced to use at work given your static Ip assignment,
and post the results of ifconfig from the terminal windows once your connection is wireless only

---

### Post by NDPeter on 2008-12-22
Here goes...if it makes any difference, I've deleted my wired settings, and restarted several times during my attempts to run this down the last few days.

```
ndpeter@ndirish:~$ ifconfig
eth0      Link encap:Ethernet  
          inet addr:136.142.xxx.yyy  Bcast:136.142.xxx.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8968 (8.9 KB)  TX bytes:8968 (8.9 KB)

wlan0     Link encap:Ethernet    
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:65310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55952 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17944005 (17.9 MB)  TX bytes:8726433 (8.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-7B-4B-2D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by jonobr on 2008-12-22
Ok, I see your eth0 is up,
it may be useful to bring it down during testing.

I would recommend you try ping your local interface to make sure alls ok

ping 192.168.0.105

Then ping your gateway 
192.168.0.1

once thats ok, then 

ping 74.125.45.100

See if you get a response to that,
If that works try typing 
nslookup google.com

see what it says back.
if that works and gives you an ip address, type
w3m google.com

that should be a text based version of google, to quit the page hit q.

Let usknow what worked what didnt

---

### Post by NDPeter on 2008-12-22
I'd seen that my wired was up, and thought that odd...especially since it still had the old info associated with it.  Didn't know how to shut it off though.  Once you suggested it, I asked the little brother how, and that fixed it.  Didn't even try the rest of the items listed there.  

Now as he described to me...that connection will restart when I reboot.  There isn't a way to shut that down the way you do a wireless connection is there?

Thanks so much for your help ironing this out.  I could see things that looked weird to me, but didn't know what to do with that info.

Thanks again.

---

### Post by jonobr on 2008-12-22
Sure thing glad to help.

Remember to mark as solved using thread tools.
Would also recommend changing the subject line for folks doing a search witha similar problem

---

### Post by steve.olson on 2008-12-22
I had a similar issue where wireless was associated and I could ping the gateway but not beyond and I could not reach the internet.  Both eth0 and wlan0 showed up in spite of the fact that eth0 was not plugged in. After issuing 'sudo ifdown eth0' I was able to reach the internet.  This is great but I don't understand why I had to do this, Windows does not work this way <Yes I'm a Linux lightweight :-) >

Hope this helps you as well as me.

Merry Christmas all !

SteveO

---

