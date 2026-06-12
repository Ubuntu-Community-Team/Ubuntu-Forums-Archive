---
title: "constant upload despite no programs running"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by kilgore9 on 2012-04-06
Dear Ubuntu users!

A strange network problem has surfaced in the last couple of days. My computer is constantly uploading at a rate of about 200kb/second although there are no programs running. 

I can't figure out what data is being sent, to where, and why! Any one know whats going on?

Attached are screen shots of the system monitor, showing the network activity as well as the running processes.

Thanks!
kilgore9

---

### Post by prshah on 2012-04-06
> **kilgore9 said:**
> My computer is constantly uploading at a rate of about 200kb/second although there are no programs running. 

I can't figure out what data is being sent, 

I think that you probably have (maybe accidentally) enabled UbuntuOne sync.

Any other guesses cannot be made intelligently, unless you can remember a recent change?

Is the computer in question acting as a "server" for other devices?

Please open a terminal (Applications-Accessories-Terminal) and give the command```
netstat -avA inet
``` which will give you some information about active Internet connections. Please post back if you think you see something suspicious in the output.

You can also use the *lsof* (list open files) terminal command to see open (in-use) files, though it will spit up a huge list and I don't see how you can sift through it except manually.

Regards,

---

### Post by kilgore9 on 2012-04-06
Hi prshah, thanks for the reply.

I don't think UbuntuOne is activated...I'm not even registered for the service. And I didn't make any recent changes.

```
netstat -avA inet
```

gives me the following output. I don't know enough about it to know wether anything is suspicious...

```

Aktive Internetverbindungen (Server und stehende Verbindungen)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:58025         *:*                     LISTEN     
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 Trout.local:33825       Everlasting-Gobsto:5000 VERBUNDEN  
tcp        1      1 Trout.local:48686       l3.ycs.vip.ams.yaho:www LAST_ACK   
tcp    72688   2671 Trout.local:43098       Everlasting-Gobstop:x11 VERBUNDEN  
tcp        1      0 localhost:49779         localhost:58025         CLOSE_WAIT 
tcp        0      0 Trout.local:56387       fra07s07-in-f113.1e:www TIME_WAIT  
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:mdns                  *:*                                
udp        0      0 *:60224                 *:*   

```

The list of open files is indeed very long and I have no idea what most of it means!

I never intended for my computer to act as a server, do you know how I can check if it is being used in that way for some reason?

Thanks for the help, anyway!

---

### Post by kilgore9 on 2012-04-06
Solved....atleast I think so!

A bit complicated to explain, but here it goes....

The problem I was having was only happening at my work space, not at home or elsewhere. At work I connect through an apple "airport" device instead of through the main router. Never had a problem with it.

Over the weekend my BF got an airport device as well, and I downloaded a few packages so that I too can use his airport to send things like music through his speakers. 

Then suddenly this problem at work....

Well I'm now connected to the main router instead of the airport, and presto, no more crazy uploads.

I'm still not exactly sure what was happening, but my guess is that with those new packages I mentioned, ubuntu recognized that I was connected to an airport and was streaming "something" (or nothing?) through to the airport. 

Make sense?

---

