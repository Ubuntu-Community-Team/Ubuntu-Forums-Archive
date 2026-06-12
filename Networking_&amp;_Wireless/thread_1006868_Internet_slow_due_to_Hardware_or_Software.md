---
title: "Internet slow due to Hardware or Software?"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by eternalnewbee on 2008-12-09
Hi there.
I recently got a TP-LINK TD-8800 Ethernet ADSL Router, and ever since, I'm having the following problem:
As soon as I run Transmission, it becomes almost impossible to open web pages.
Transmission's download speeds go up briefly, and then settle down at 0.
Is this due to Hardware, or configuration of the Hardware?
Btw, in Network Tools I get two Network Device choices:
Loopback Interface (Io), and Ethernet Interface (eth0)
I really have no idea how to fix this.
If anyone can help, and need some more information, please let me know.
Thanks.

---

### Post by jonobr on 2008-12-09
hello

I would recommend going to google.com on your browser and assess how long that takes and then in a terminal window  type w3m google.com

W3m is a text based browser and will compare one against the other/

Next I would do (from a terminal window or using the networking tools available in the network gui) 
ping pingplotter.com
or another pingable address

You could also try a traceroute pingplotter.com

You could post the results of that  and the result of running ifconfig eth0 here people may be able to figure where you issue is

---

### Post by eternalnewbee on 2008-12-09
Thanks for your reply jonobr.
As soon as I get back home, I will try to follow your advice. Stay tuned[-o<

---

### Post by eternalnewbee on 2008-12-09
> I would recommend going to google.com on your browser and assess how long that takes
I typed in speed, in the searchbar. It took **0.16** seconds to load
> and then in a terminal window type w3m google.com


---

### Post by eternalnewbee on 2008-12-09
> Next I would do (from a terminal window or using the networking tools available in the network gui)
ping pingplotter.com
See screenshot:

---

### Post by eternalnewbee on 2008-12-09
> You could post the results of that and the result of running ifconfig eth0 here people may be able to figure where you issue isbird@bird-desktop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0b:6a:ce:c1:56  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:fece:c156/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46929 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16653548 (16.6 MB)  TX bytes:47115954 (47.1 MB)
          Interrupt:23 Base address:0x6d00

---

### Post by jonobr on 2008-12-10
Hello

Your ifconfig looks fine,
on your ping tests, I would be comparing rhe load time of each to see if there are marked differences to rule out problems with a particular browser or if its right across the board,
so the question would be , for the web pages you opened, did they all seem around the same?

One thing I do notice about your ping times,
they are high.
Not unbearable, but still 500msec (half a second) seems like a long time for a 64 k packet.

Im wondering if you could try pining something in your country to see what is interrnation vs national.

Im thinking international pings should be a little over 100msec for adsl,

Im also seeing you had 80 % packet loss.

WHat I would recommend also is rerunning that test and increase the number of pings to eg 100 to get a fairer picure of how many packets you are loosing.

If there are delays on your ping, and you are loosing packets, both would combine to give you a bad experience.

---

### Post by eternalnewbee on 2008-12-10
> Hello

Your ifconfig looks fine,
on your ping tests, I would be comparing rhe load time of each to see if there are marked differences to rule out problems with a particular browser or if its right across the board,
so the question would be , for the web pages you opened, did they all seem around the same?

One thing I do notice about your ping times,
they are high.
Not unbearable, but still 500msec (half a second) seems like a long time for a 64 k packet.

Im wondering if you could try pining something in your country to see what is interrnation vs national.

Im thinking international pings should be a little over 100msec for adsl,

Im also seeing you had 80 % packet loss.

WHat I would recommend also is rerunning that test and increase the number of pings to eg 100 to get a fairer picure of how many packets you are loosing.

If there are delays on your ping, and you are loosing packets, both would combine to give you a bad experience.
Thanks again for your assistance.
The highest number of ping (99) for a local address produced this result.
I've added an another address, abroad (hope it's useful)

---

### Post by eternalnewbee on 2008-12-10
Btw, in Network Tools, Loopback Interface (Io) is the default Network Device.

---

### Post by jonobr on 2008-12-10
interesting,

You can see the comparison between the international traffic and local.

Your local website seems good, 50msec looks ok, not great, just ok,

When you go international the traffic delay increases significantly
to half a second,
Im positive you will see a marked difference between sanook and ubuntu when you ping in a terminal window.

Heres from the US to Sanook

PING sanook.com (58.181.243.6) 56(84) bytes of data.
64 bytes from 58.181.243.6: icmp_seq=1 ttl=45 time=229 ms
64 bytes from 58.181.243.6: icmp_seq=2 ttl=45 time=219 ms
64 bytes from 58.181.243.6: icmp_seq=3 ttl=45 time=229 ms
64 bytes from 58.181.243.6: icmp_seq=4 ttl=45 time=220 ms
64 bytes from 58.181.243.6: icmp_seq=5 ttl=45 time=219 ms
64 bytes from 58.181.243.6: icmp_seq=6 ttl=45 time=229 ms



Although the thing is slow its not as slow as yours.

Additionally, your packets loss is 10% local traffic and goes up to nearly 20% for international.

That means for anything you do international, you are going to loose (based on this one test) 1/5th of your traffic which will have to be resent again due to it being lost.

Add that packet loss to the delay, Im thinking that there are problems outside you which are beyond your control.

I was wonderiong if there was a way you could test a download locally versus a download internationally?

What kind of service did you have before the Router you have now,
did you have these problems with that?

---

### Post by eternalnewbee on 2008-12-10
> What kind of service did you have before the Router you have now,
did you have these problems with that?
The internet service provider is still the same, but the Router is different. No firewall is enabled. Could it have something to do with the configuration of the Router? (that was actually my first thought).
Thanks again for taking the time to help. Much appreciated.

---

### Post by eternalnewbee on 2008-12-11
Even my internet provider had no ideas...

---

### Post by eternalnewbee on 2008-12-11
This is how my Network Manager looks like:

---

### Post by eternalnewbee on 2008-12-12
It's just been 17 hours since my last reply?
Hoping this friendly **push** will increase my chances at getting a (hopefully) constructive response...

---

### Post by eternalnewbee on 2008-12-12
Transmission has been slower than a snail for about a week now...:cry:

---

### Post by eternalnewbee on 2008-12-13
This is turning into a very exciting monologue.
So, suppose I'd reinstall Transmission. Would I still be able to continue downloading my incomplete files?

---

### Post by psycosmyth on 2008-12-13
You say this is only a torrent issue?
Where do you live?
You may have some throttling with your ISP. 
This has been happening in several countries lately and mostly with torrents. If this is the case, you may not have any control there.
The data you have posted looks solid and your speeds are average.
Try another torrent tool like Tornado and see if it's any different.

---

### Post by eternalnewbee on 2008-12-13
> **psycosmyth said:**
> You say this is only a torrent issue?
Where do you live?
You may have some throttling with your ISP. 
This has been happening in several countries lately and mostly with torrents. If this is the case, you may not have any control there.
The data you have posted looks solid and your speeds are average.
Try another torrent tool like Tornado and see if it's any different.
Thanks psycosmyth.
I'm on it.

---

### Post by oedipuss on 2008-12-13
Sorry if this is completely irrelevant, but I've had problems with my connection when my torrent client was setup with no upload limit. 

Try setting transmission's upload limit at half your maximum upload capacity, and go from there, or if you've got one already, try lowering it. 
Also, try using less total connections. I've seen disconnects with one router and a high number of connections that didn't happen with another router.

---

### Post by eternalnewbee on 2008-12-13
> **oedipuss said:**
> Sorry if this is completely irrelevant, but I've had problems with my connection when my torrent client was setup with no upload limit. 

Try setting transmission's upload limit at half your maximum upload capacity, and go from there, or if you've got one already, try lowering it. 
Also, try using less total connections. I've seen disconnects with one router and a high number of connections that didn't happen with another router.
Thanks oedipuss. Been using Transmission for two years now, with max upload at 10kb.

---

### Post by jonobr on 2008-12-15
Hey

Sorry for not getting back sooner,

All things being equal, and from what you have explained, its doubtful that the change in hardware (your router) and your ISP ping results, 
and your downloads being slow all occurred together,
Im thinking that, you probably got used to the large latency times of around half a second, with your old router and your new router is probably showing the same.

One stupid question for you.
You mentioned torrents in particular, what happens when you download a regular file not using torrent, do you see the same issue.

Thanks

BTW, I preffered the old avatar:-(

---

### Post by eternalnewbee on 2008-12-19
> **jonobr said:**
> Hey

Sorry for not getting back sooner,

All things being equal, and from what you have explained, its doubtful that the change in hardware (your router) and your ISP ping results, 
and your downloads being slow all occurred together,
Im thinking that, you probably got used to the large latency times of around half a second, with your old router and your new router is probably showing the same.

One stupid question for you.
You mentioned torrents in particular, what happens when you download a regular file not using torrent, do you see the same issue.

Thanks

BTW, I preffered the old avatar:-(
Avatar fixed, by special request):P
As a matter of fact, using Tornado is very smooth. High download rates and normal speeds when browsing the web at the same time.
So now I'm thinking the problem is related to Transmission.
Btw, sorry for my late reply...
Thanks again for replying. Really appreciate it.

---

### Post by jonobr on 2008-12-19
No problem, and its great to see the old face I recognise:-)

I think now that it seems torrent specific, there are a few articles regarding transmission,
here is one

[http://ubuntuforums.org/showthread.php?t=747852](http://ubuntuforums.org/showthread.php?t=747852)

I would also recommend getting on to your ISP over there response times, they look quite slow,.
My guess is that you are used to those times, and I reckon the ISP probably wont fix it, but you never know your luck in the big city :-)

---

### Post by eternalnewbee on 2008-12-28
Hi jonobr.
The apologies are mine for not getting back to you sooner.
I'm hardly ever logged nowadays.
Anyways, I'm using Tornado at the moment with varying speeds, but my web browsing doesn't suffer from it.
Thanks again for helping out.

---

