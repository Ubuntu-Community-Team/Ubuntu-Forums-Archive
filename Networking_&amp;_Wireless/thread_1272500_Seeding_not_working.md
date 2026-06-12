---
title: "Seeding not working"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by eaglemob on 2009-09-22
I all,
I am nooob on linux.

I installed ubuntu 9.04 desktop, so far a manage to make it work as i want.
The only think that i can not fix is to seed torrents. I have a download like 2,3mb/sec.

But wen starts to seed it just doesn't work, I try vuze/azureus,deluge,transmission.
And have the same problem.

My hardware is:Q6600 quadcore 2,41mhz,6gig ram, etc
Internet connection 24mbits/1mBits, Modemswitch  *Inteno xavi  x5222r-p3* (NO router in it), DHCP (i get the ip from the provider), Not static ip.

I tryed FTP server,webmin,gadmin-proftpd.

I got acess to all the windows system.. wel in other words all is working except the damn torrents seeding.

I want to seed to tvtorrents.com (i got a acount there ), i don't know if they have anything special that i should know.

Wen i look on devices information i have this, using NETWORK TOOLS.
Loopback interface (lo)
Ipv6::1  128     host
Ipv4 127.0.0.1   255.0.0.0

Ethernet interface (eth1)
Ipv6 :FE80 etc etc etc    64    Link
Ipv4 (my ip)      255.255.254.0

Ethernet interface (eth0)
All on 0    Unknown

ETH0 not active i got 2 network cards on the motherboard

Wen in check net stats i get this, allso using NETWORK TOOLS.

Tcp 127.0.0.1   631   Listen
tcp6 ::1            631   Listen
Udp   0.0.0.0      68

Sorry but i don't know what to do.
Any help is apreciated.

Thx :)

---

### Post by cbugsubunt on 2009-09-22
Maybe its a firewall problem and blocks the seeding procedure connections.coz seeding its tryin share itself to other clients

---

### Post by eaglemob on 2009-09-22
Not using any firewall.
I think i am missing some configuration.
I am on DHCP DSL  Dynamic ip it's quite confusing for me.
I have loop back (lo), eth0 and eth1.
I don't understand how to configure (lo)Ipv4 and Ipv6.
I am not familiar with that :(


I did a netstat with de torrent program on here is what i got:

netstat -anp --tcp --udp | grep LISTEN

tcp        0      0 0.0.0.0:55555           0.0.0.0:*               LISTEN      4409/transmission
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::55555                :::*                    LISTEN      4409/transmission
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               

Port 55555 i open in transmission, the rest i don't understand.
Port 10000 can be webmin.. port 631 i have no idea

Thx for the replay.  :)

---

### Post by Charles Kerr on 2009-09-23
> **eaglemob said:**
> But wen starts to seed it just doesn't work, I try vuze/azureus,deluge,transmission.
And have the same problem.

Sorry but i don't know what to do.
Any help is apreciated.

Thx :)

If it's not working in any of those clients, my first thought is that maybe you've got torrents that have a lot more seeders than leechers, so that it's easy for you to download but difficult to upload.

In transmission, go to the Properties dialog for one of your torrents, look at the peers tab, and on the bottom it'll say how many seeders and leechers your tracker thinks are in the swarm.  If the seeder-to-leecher ratio is high, you'll find it difficult (or impossible) to upload.

If that's not the problem, you might want to read this checklist of common problems: [http://trac.transmissionbt.com/wiki/SlowSpeeds](http://trac.transmissionbt.com/wiki/SlowSpeeds).

---

### Post by eaglemob on 2009-09-23
> **Charles Kerr said:**
> If it's not working in any of those clients, my first thought is that maybe you've got torrents that have a lot more seeders than leechers, so that it's easy for you to download but difficult to upload.

In transmission, go to the Properties dialog for one of your torrents, look at the peers tab, and on the bottom it'll say how many seeders and leechers your tracker thinks are in the swarm.  If the seeder-to-leecher ratio is high, you'll find it difficult (or impossible) to upload.

If that's not the problem, you might want to read this checklist of common problems: [http://trac.transmissionbt.com/wiki/SlowSpeeds](http://trac.transmissionbt.com/wiki/SlowSpeeds).

Thx Charles.

Using Deluge,
I tested to download a torrent via the ubuntu tracker and i had a speed 2.3MiB/sec and uploading allso was about 100KiB/sec, all that was normal.

And on Tvtorrents.com it doesn't work.
I see that is seeders 34  peers 10, and nothing happens.

Can be something to do with the client settings on network extras in deluge ?
UpnP,Nat-PMP,Peer Exchange, LSD and DHT ?

very strange that works on other trackers :(
I am loosing upload credits on tvtorrents.com each time i download using Ubuntu.

Greethings

---

### Post by Charles Kerr on 2009-09-27
> **eaglemob said:**
> Can be something to do with the client settings on network extras in deluge ?
UpnP,Nat-PMP,Peer Exchange, LSD and DHT ?
If it's help with Deluge you're looking for, you'll have to ask someone else.  [-(

---

### Post by eaglemob on 2009-10-13
Solved.
I upgrade my linux to 9.10 together with Vuze 4.2.0.8.
And allso followed up the instructions/settings in advanced mode from:

[http://www.azureuswiki.com/index.php/AdvancedNetworkSettings](http://www.azureuswiki.com/index.php/AdvancedNetworkSettings)

Anyway thx a lot for your replays

---

