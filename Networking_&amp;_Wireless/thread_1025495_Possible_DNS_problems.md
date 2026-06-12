---
title: "Possible DNS problems"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by Derosian on 2008-12-30
Ok, first the symptom.  When connecting to a website for the first time in at least 10-15 minutes it takes 10 seconds for it to look up the website.  

If I use nslookup on a site that I haven't connected to recently or looked up recently it takes 5 seconds, if it is one I have connected to recently it is nearly instantaneous.

My computer(Ubuntu_64 Intrepid Ibex, AMD 6000+ 2x64)  is connected to a router(D-link DI-624) through my onboard network card.  

My Active Network Connection on my computer is as followed.
IP Address: 192.168.0.100
Broadcast Address: 192.168.0.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.0.1
Primary DNS: 192.168.0.1

(192.168.0.1 is my router...)

My router's information for LAN.
IP Address: 192.168.0.1
Subnet Mask: 255.255.255.0 

My router's information for WAN.
IP Address: 72.190.100.146 
Subnet Mask: 255.255.240.0
Default Gateway: 72.190.96.1
DNS: 66.90.132.162 66.90.130.10 

If there is more information required let me know...  I couldn't seem to find anyone else with this specific problem, but if there is a thread about it let me know.

---

### Post by gettinoriginal on 2008-12-30
Have you tried emptying your cache and cookies and trying again ??  I know that when my site response slows, doing this tends to help it along.

---

### Post by Derosian on 2008-12-30
This is on a fresh install of Ubuntu, also I didn't have this problem in Windows, as well as nobody else in my LAN have this problem.

---

### Post by gettinoriginal on 2008-12-30
It doesn't sound like a computer problem, it sounds like a browser problem, something specific to your settings.  If you google "<your browser name> tricks and tips"  :confused:

---

### Post by caljohnsmith on 2008-12-30
Instead of using your ISP's DNS server, how about using the OpenDNS servers, which are free for anyone to use. Just replace your current DNS address with either 208.67.222.222 or 208.67.220.220. See if that makes a difference, because if that fixes your long DNS wait time, that would mean your computer settings are most likely OK and your ISP's DNS server is the problem.

---

### Post by Derosian on 2008-12-30
That seems to have shortened the time it takes to lookup a webpage by about half, thank you caljohnsmith.

---

### Post by caljohnsmith on 2008-12-30
So it's still taking at least a couple of seconds to do the DNS lookup, even with the OpenDNS servers? Have you tried doing a speedtest on your connection just to make sure you aren't having speed issues? You could go to [www.speed.io](www.speed.io) for example. Also, how about doing:
```
ping -c 5 208.67.222.222
```
And look at what it says for "time":
```
john@TECH3142:~$ [COLOR="Blue"]ping -c 5 208.67.222.222[/COLOR]
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=53 [COLOR="Blue"]time=39.1 ms[/COLOR]
64 bytes from 208.67.222.222: icmp_seq=2 ttl=53 [COLOR="Blue"]time=24.6 ms[/COLOR]
64 bytes from 208.67.222.222: icmp_seq=3 ttl=53 [COLOR="Blue"]time=25.4 ms[/COLOR]
64 bytes from 208.67.222.222: icmp_seq=4 ttl=53 [COLOR="Blue"]time=25.5 ms[/COLOR]
64 bytes from 208.67.222.222: icmp_seq=5 ttl=53 [COLOR="Blue"]time=24.2 ms[/COLOR]

--- 208.67.222.222 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4017ms
rtt min/avg/max/mdev = 24.293/27.841/39.183/5.692 ms
```
If you get a latency time of any more than a couple hundred milliseconds (ms), then that would be a concern. Also run the same ping test on a few other sites like Google (74.125.45.100) and Yahoo (206.190.60.37) for example, and let me know what you come up with. :)

---

