---
title: "PS3 doesn't detect mediatomb at all"
date: 2009-10-23
forum: Multimedia Software
---

### Post by v1nsai on 2009-10-23
I've seen a few people with mediatomb problems, but none seem to have trouble simply getting mediatomb to be detected by the PS3.  I can't even get that far.  I followed the instructions [here]("http://linuxowns.wordpress.com/2008/04/28/stream-media-from-ubuntu-to-your-ps3/") and I'm sure I've followed them as described.

When starting mediatomb in the terminal, it gives the IP: port address that the server can now be reached at.  With mediatomb running in the terminal, I used a portscan on localhost and discovered that my system is listening on the power that mediatomb specified (the port goes away when mediatomb is shut off so it's not a port conflict) but when I scan my network with my ipod touch I don't see this media server even though it has it's own IP address.

/stumped

---

### Post by dubs65401 on 2009-11-17
> **v1nsai said:**
> I've seen a few people with mediatomb problems, but none seem to have trouble simply getting mediatomb to be detected by the PS3.  I can't even get that far.  I followed the instructions [here]("http://linuxowns.wordpress.com/2008/04/28/stream-media-from-ubuntu-to-your-ps3/") and I'm sure I've followed them as described.

When starting mediatomb in the terminal, it gives the IP: port address that the server can now be reached at.  With mediatomb running in the terminal, I used a portscan on localhost and discovered that my system is listening on the power that mediatomb specified (the port goes away when mediatomb is shut off so it's not a port conflict) but when I scan my network with my ipod touch I don't see this media server even though it has it's own IP address.

/stumped
 yeah me too i have done everything this [site]("http://linuxowns.wordpress.com/2008/04/28/stream-media-from-ubuntu-to-your-ps3/") (click on it) told me to do but still my ps3 won't detect mediatomb what am i doing wrong.

---

### Post by megadave on 2010-01-06
I know you posted a while ago, but are you still having the problem?

I ran into the same issue, and the cause was a blocked port by the firewall.

[B]
To resolve[/B]

[LIST=1]
[*]Install firestarter (firewall manager) using synaptic
[*]Start firestarter (answer the DHCP and internet sharing questions)
[*]On your PS3, do a "Search for MediaServers"
[*]Look @ the events tab.  You should see an entry for port 49152.  Right click on it and choose either "allow service for everyone" or "source" depending on your security needs.  If your PS3 IP changes, i'd add for everyone.  If it does not, you can do "for source".
[*]Re-run the "Search for Mediaservers" on your PS3
[/LIST]

And now you should see Mediatomb

---

### Post by kokonobs on 2010-01-18
Thanks megadave, i spent all day looking for a solution.  I figured firestarter was the reason although i had it off.. Works fine now.

---

### Post by willie001 on 2010-01-25
I also have issues getting PS3 to detect MediaTomb.

Last year November I installed MediaTomb on one of my Ubuntu boxes, configured it, and it worked fine. My PS3 system immediately detected the server and all worked perfectly.

Some time during the new year, my PS3 system simply stopped detecting the media server. I am stumped.:confused: I did not change anything, not my router settings, not the Mediatomb settings, not the PS3 settings, nothing!! I did not install any updates or firmware upgrades or anything else. It just stopped working.

I searched Google and can not find any real solutions. I checked my firewall, the router settings, the PS3, everything. I even went as far as setting up a new box with only Ubuntu server and Mediatomb. Nothing!!

I am desperate for help!!:???:

Please, anyone.

---

### Post by autogarsas on 2010-01-28
Heya. Im in the same situation that wille, solution i found is reinstalling whole ubuntu ](*,) Its not working now too, and im pissed loosing all data. Any help?

P.S. I rebooted router to try if this help, and now mediatomb is asking for username and password even i never typed anythink...

---

### Post by llawwehttam on 2010-01-28
Did you guys enable that port? If not install GUFW (in the repos) which stands for 'gui for uncomplicated firewall'. You can then use that to enable the ports.

---

### Post by autogarsas on 2010-01-28
I tryied with that firewall manager, not hellping. Btw before i tryied with firestarted like someone above mentioned, and i didnt saw that ps3 is trying connect at all. I mean there wasnt anythink with that port in events.

---

### Post by autogarsas on 2010-01-28
hehe, solved it somehow. (not sure which part helped)

Note, that everythink worked for me before any of those steps...
1. edit config file:
sudo gedit /etc/mediatomb/config.xml
Changed to yes:
 <protocolInfo extend="yes"/><!-- For PS3 support change to "yes" -->

uncommented those two lines:
<!-- Uncomment the line below for PS3 divx support -->
        <map from="avi" to="video/divx"/>
        <!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
        <map from="avi" to="video/avi"/>


2. Runed firestarter, and search for media servers on ps3, then saw in firestaster ps3 is trying to connect @ port 1900, right click and allow connections.
3. Search for server again and walla 1 server found. 


P.S. Frankly i knowed only about 30% what im doing, so i dont know what helped. Hope it help you some.

---

### Post by badrock on 2010-04-02
I was having the same problem where the PS3 would not even see my mediatomb and firestarter showed no activity from it. The problem ended up being that I had two network cards in my computer, so I had to specify which network interface to do when starting mediatomb. This is what I did (ra0 is my nic):

```
mediatomb -e ra0
```

I also did the other tips in this thread (uncomment the lines in the mediatomb config, opened port 1900 in firestarter, and after the first time I tried to scan for media servers on the PS3 I went back to firestarter and allowed those connections). The PS3 and mediatomb are finally playing nicely together.

---

### Post by philipz on 2011-01-24
Try to add interface tag in Server tag, like the below.
<interface>eth0</interface>

---

### Post by Gecko483 on 2011-02-05
> **philipz said:**
> Try to add interface tag in Server tag, like the below.
<interface>eth0</interface>
 
I just wanted to say THANKS! This was my problem ( I had just upgraded to a dual NIC motherboard).

---

### Post by motla68 on 2012-10-07
I struggled with this for a while too and resolved:

UFW firewall - set a new rule

Allow - in - service - TCP - From: [ps3 ip address] 
                               To: [mediatomb ip adress] port: 49152

Then restart media server scan on ps3.

:popcorn:

---

