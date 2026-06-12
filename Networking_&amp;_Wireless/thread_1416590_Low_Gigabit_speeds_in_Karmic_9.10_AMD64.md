---
title: "Low Gigabit speeds in Karmic 9.10 AMD64"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by ganjaman2009 on 2010-02-26
I have a HP DC-7600 with the built-in nic [3f:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethe
rnet PCI Express (rev 01)] connected to a DLINK DGS-1008D switch.
Ethtool shows:
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x000000ff (255)
	Link detected: yes

My NAS is a DLINK DNS-323 (has a gigabit nic) and is also connected to the same switch, the firmware being 1.08 and the NFS APKG module loaded and I've shared out two filesystems (does not matter anyway ...).

My /etc/fstab contains these lines:
nas:/mnt/HD_a2/MP3 /media/MP3 nfs rw,nolock,rsize=32768,wsize=32768,timeo=14,intr,hard,tcp,async 0 0
nas:/mnt/HD_b2/MEDIA /media/MEDIA nfs rw,nolock,rsize=32768,wsize=32768,timeo=14,intr,hard,tcp,async 0 0

/proc/sys/net/ipv4/tcp_mem = 312480	416640	624960
/proc/sys/net/core/wmem_default = 129024
/proc/sys/net/core/wmem_max = 131071
/proc/sys/net/core/optmem_max = 20480
/proc/sys/net/core/rmem_max = 131071
/proc/sys/net/core/rmem_default = 129024


This was the best optimisation I could get, I did follow the NFS HOWTO.  Copying from my PC does not exceed 120Mbits/s (System Monitor).  My PC nic does not support jumbo frames.

I'm looking for any assistance to improve my network speed.  My PC has 4GB RAM.

I copied 74GB of average sized files between 4MB to 12MB (uh ... compressed audio) and it took 155 mins using tar:

pippin:/media/ALURATEK/MP3
> time tar cf - . | (cd /media/MP3 && tar xf -)
real	155m5.469s
user	0m16.520s
sys	6m16.170s

I also copied some more movies about 43GB and:
time tar cf - NEW-MOVIES | (cd /media/MEDIA && tar xf -)

real	131m46.220s
user	0m8.740s
sys	3m11.170s

So 73GB in 155m, and 43GB in 131m?

---

### Post by ganjaman2009 on 2010-02-26
Bizarre, using filezilla over FTP:

Response:	227 Entering Passive Mode (192,168,0,2,202,221)
Command:	STOR 2010.opening.cermony.720p.hdtv.x264-2hd.mkv
Response:	150 Accepted data connection
Error:	Connection closed by server
Response:	226-File successfully transferred
Response:	226 320.319 seconds (measured here), 13.98 Mbytes per second

Using NFS mounted filesystem:
pippin:/media/My Passport/DIVX
> time tar cf - Vancouver.Olympics.2010.Opening.Ceremony | (cd /media/MEDIA && tar xf -)

real	62m28.475s
user	0m0.870s
sys	0m18.660s

pippin:/media/My Passport/DIVX
> du -sh Vancouver.Olympics.2010.Opening.Ceremony/
4.4G	Vancouver.Olympics.2010.Opening.Ceremony/

---

### Post by ganjaman2009 on 2010-02-27
Well no thanks to anyone.  I figured out the problem and now I get decent speed.

Transferring a 4.4GB file
FROM (READ) the DNS-323:
pippin:/media/MEDIA/TV.SERIES
> time tar cf - Vancouver.Olympics.2010.Opening.Ceremony | (cd /home/user1/NEWS && tar xf -)

real	3m41.408s
user	0m1.410s
sys	0m42.670s

TO (WRITE) the DNS-323:
pippin:~/NEWS
> time tar cf - Vancouver.Olympics.2010.Opening.Ceremony | (cd /media/MEDIA && tar xf -)

real	6m12.169s
user	0m0.910s
sys	0m25.030s

---

### Post by jeebustrain on 2010-02-27
out of curiosity, what did you do to fix it? I am having the same sort of issue intermittently.

---

### Post by ganjaman2009 on 2010-02-28
First, set the DNS-323 to 1000 not auto - you will see a drastic improvement almost immediately.  The following will either not show any improvement or just tune your performance a bit.

In Ubuntu set autoneg off eth0 via ethtool.

Create a script: set_autoneg_off in /etc/init.d, you can call it whatever you wish - I just chose a logical name.  Insert the following:

#!/bin/sh
ETHTOOL="/usr/sbin/ethtool"
DEV="eth0"
OPTIONS="autoneg off"
case "$1" in
start)
	echo -n "Turning off autoneg ...";
	$ETHTOOL -A $DEV $OPTIONS;
	echo " done.";;
stop)
	;;
esac
exit 0

Make the script executable - i.e. chmod +x

Update your rc: 

# update-rc.d set_autoneg_off defaults

I now get 1GB/min READs and 500MB/min WRITES - not bad - but not great.  I think it peaks at 24MB/s READing from the DNS-323

---

