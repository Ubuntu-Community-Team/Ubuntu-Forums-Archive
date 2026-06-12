---
title: "Help! network won't work"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by itlarson on 2009-03-24
I have had my internet stop working, and am hoping forum users can help me.  Here is what happened:

-tried to access the internet on my mythtv system, and realized it wasn't working.
-tried my desktop computer, and it also wasn't working.
-was able to get the desktop working by pluging the ethernet cable directly into the cable modem, bypassing the router.
-tried this with the mythtv system, but it still won't connect, even after a reboot.

Here here my questions:
-The mythtv box has a 50' cable run, is it possible the modem is providing a weak signal?
-how can I tell if networking is "turned on" in a system?
-could someone give me some commands to start/stop networking from the command line, and otherwise control and monitor it.  In the past it's mostly "just worked", but when it didn't, I had to resort to rebooting.

Any help at all will be greatly appreciated.

---

### Post by jonobr on 2009-03-24
on your mythtv boxx, which I am assuming is an ubuntu box, type

```
ifconfig
```
in the terminal window,

see what IP address comes back,
see if the returned interface (usually eth0) says UP in the response.
If you get an IP address, trying pinging that IP address.
If that works,
ping your router after that.
Post back how far you get.

---

### Post by itlarson on 2009-03-24
ifconfig shows an eth0.  Are the hex digits separated by colons newfangled ip addresses?  anyway, they don't ping.  Neither will google.  Thanks for helping.

---

### Post by itlarson on 2009-03-24
crud-  I was hoping my ethernet cable was damaged, but when I lugged my desktop upstairs it connected right away. I can ping 127.0.0.1 (which shows up in the 'lo' section of ifconfig output), but that's just talking to myself.  Other numeric addresses give "network is unreachable". Is it possible that the ethernet in my myth box died?  I suppose I could install a network card.

---

### Post by itlarson on 2009-03-24
How weird that my router seems to have died at the same time.  Power surge?  The weather was was windy and rainy Sunday night, but I didn't hear any thunder.

---

### Post by jonobr on 2009-03-25
Hello

The ip address is usually an address like 192.168.xxx.xxx or something like that.

The thing you are looking at with the : is most most likely the hardware address which is a physical address burned onto the card itself.

From Reading your problem though it sounds like you have a blown power supply, or a fired unit.


Im also thinking you should stay in doors for a while and avoiid standing next to trees....:-)

---

### Post by itlarson on 2009-03-25
Then there's no ip address in the eth0 section of the ifconfig output.  The power supply on the router is ok since the lights on it work.  I'm not using it though, since nothing will connect through it- I'm currently swapping cables into the cable modem.  How do I ping the router when it is installed?  Maybe this could help troubleshoot it.

---

### Post by jonobr on 2009-03-25
Hi

Im guessing you are using dhcp, so try 

```
sudo /etc/init.d/network restart 
```

and then see if you got an address with 

```
ifconfig
```

---

### Post by itlarson on 2009-03-25
No Dice- the networking restart does nothing-  it seems to already be started.  My plan B has been shot down too.  I pulled a DVB card and inserted an old ethernet card, but it still won't connect.  I copied the output to a usb stick and sneaker- netted it downstairs to post: 

> 
itl@mythbox:~/Config$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...                           [ OK ]

itl@mythbox:~/Config$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:9e:7e:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:18:4d:6f:3f:ba  
          inet6 addr: fe80::218:4dff:fe6f:3fba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56252 (56.2 KB)  TX bytes:2178 (2.1 KB)
          Interrupt:16 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2704 (2.7 KB)  TX bytes:2704 (2.7 KB)


itl@mythbox:~/Config$ ping 206.190.60.37
connect: Network is unreachable

The cable was plugged into the added card at the time- eth1 I assume.

---

