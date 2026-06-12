---
title: "Can't connect to Telstra ADSL ?"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by jujuM on 2010-03-08
I signed up to Telstra ADSL [Australia].
They send me modem and installation CD.  CD requires XP minimum.
Tech support said I needed drivers for the connection and suggested I get Windows.  This doesn't sound right, I could plug and go with my old Optus connection.  
I tried the new Telstra modem as well as my trusty old Motorola.  They both send/receive but I can't get the internet working.
I'm connecting through Ethernet.
I have my DNS, gateway and IP address, but when I try to edit the connection manually it won't let me apply changes.  
I have a pretty limited knowledge of Ubuntu, and any help would be muchos appreciated.

---

### Post by dineshs on 2010-03-08
Connect your modem to the ethernet port.Open a terminal(applications-accessories-terminal),type this command and post the output back
```
ifconfig -a
```

---

### Post by jujuM on 2010-03-13
Sorry for the delay, limited internet connection [duh].
 
>  
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:cb:01:13  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::2c0:9fff:fecb:113/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1198 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1234 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:165889 (165.8 KB)  TX bytes:81943 (81.9 KB) 
          Interrupt:16 Base address:0x2000 
eth1      Link encap:Ethernet  HWaddr 00:13:ce:1d:7d:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17 Base address:0xa000 Memory:b0101000-b0101fff 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:580 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:580 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:37312 (37.3 KB)  TX bytes:37312 (37.3 KB) 
pan0      Link encap:Ethernet  HWaddr 66:af:04:99:65:05  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 



---

### Post by dineshs on 2010-03-13
A modem driver is not required since you are connecting thru ethernet port.pl try this command
```
route -n
```
This will show the def gateway ie the router IP.Let it be say 10.0.0.254
Open firefox and type 10.0.0.254 in the address bar.you will get the router page.You can configure router if havent already.
To put DNS
```
gksudo gedit /etc/resolv.conf
```
and add this line
```
nameserver 8.8.8.8
```
assuming that your DNS is 8.8.8.8

---

### Post by cascade9 on 2010-03-13
> **jujuM said:**
> I signed up to Telstra ADSL [Australia].
They send me modem and installation CD.  CD requires XP minimum.
Tech support said I needed drivers for the connection and suggested I get Windows.  This doesn't sound right, I could plug and go with my old Optus connection.  
I tried the new Telstra modem as well as my trusty old Motorola.  They both send/receive but I can't get the internet working.


You should just be able to hook up to the modem, input the username and pasword, and off you go. I've done it with telstra before on linux (not ubuntu though). That was a while ago, maybe things have changed....but it should be possible. Bluddy telstra :|  

BTW I've got to ask- why optus to telstra? That is 'out of the frying pan and into the fire' IMO.

---

### Post by jujuM on 2010-03-16
@dineshs Thank you so much.  :)
@cascade9 Optus don't connect to this new apartment- I wouldn't have gone with Telstra if I wasn't desperate.  I needed internet asap for uni and everyone else had a 3-4 week wait.  I have a feeling they'll be hearing lots from me.  They already blamed a line connection fault on my new handset, now this.

---

### Post by cascade9 on 2010-03-16
3-4 weeks? o.O 

I dont have any idea of what ISP are avaible where you are, but 3-4 weeks is just amazing. I recently moved, and from when I started through to totally conencted took less than a week. Telstra..er..'el cheapo' phone line, took 1 day, then 3 days for TPG to connect me. I'm pretty sure that I could have done it faster with a different ISP, but I really wanted the best d/l for my money so I went with TPG. 

BTW, I checked with my friends house who has telstra ADSL, and the whole connection was from the modem, and configured via a browser (not that this is how the telstra install disc would do it, but more than do-able from a browser). 

You would need PPPoE with linux OR to go into the modem, reset it and save the passwords with firefox (or any other browser that saves passwords).

---

