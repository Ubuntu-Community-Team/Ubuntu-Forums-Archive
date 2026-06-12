---
title: "Torrent speed problem"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by repilce on 2010-08-30
Hello all, I am having some serious lack of speed in ANY torrent program i have tried (Transmission/Vuse). Now, before i get barraged by the "flowchart" answers, I will try to lay out the things I have already gone through to try and remedy this.

First of all, I have a 3Mb DSL connection, the firewall on my dsl modem is off, i have it routed through a linksys hardwire router with NAT&UpnP both enabled. With the same setup in Win 7 i can get full 300-325Kbs download speed with my torrent programs with no fuss.

Now, I am using Lucid generic x86 , I do have firestarter installed and running with an rule setup to allow both tcp/udp traffic on the port that is selected by transmission for default, and "use UPnP checked".

But the maximum downstream I have seen is about 100Kbs on a good day.. usually hovers around 50-60Kbs.

To try and figure this out I have even already disabled ALL firewalls straight and still got the same results in DL speed with torrents. Now, Any regular downloading through browsers, updates, package manager all go up to my rated downstream 300Kbs + with no probs..

Can anyone give me suggestions or possibly tell me what's wrong?

Thanks in advance.

---

### Post by wojox on 2010-08-30
This is what I followed and noticed a great performance increase 

[ BitTorrent optimization and troubleshooting guide]("http://art.ubuntuforums.org/showthread.php?t=1259923")

I've used that with both Deluge and Transmission.

Hope it helps.

---

### Post by repilce on 2010-08-30
Thanks for the great link. It seems i cant get my port to open.. i've tried a few different specific ports in the 5K range, but i can get the "test" result to come back open for anything, I cant figure it out :(

---

### Post by repilce on 2010-08-30
Okay, I think i figured it out. Apparently on this westell dsl modem. Even though i have the firewall dummy button set to "allow all traffic" i still had to creat a port forwarding rule to my router, from there setup correctly i finally got it open.. and looks like transmission is responding accordingly! :D

---

### Post by wojox on 2010-08-30
Cool, glad to see you got it. ;)

---

### Post by repilce on 2010-08-30
Yes, and still thanks for that link.. definitely a book marker! cruising along at 300Kbs ish now :)

---

