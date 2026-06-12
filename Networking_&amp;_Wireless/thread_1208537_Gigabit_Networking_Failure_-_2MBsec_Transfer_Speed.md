---
title: "Gigabit Networking Failure - 2MB/sec Transfer Speeds"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by starcraft.man on 2009-07-09
I'm at a complete loss, I need a networking expert. I'm not an idiot, I've read up and know quite a bit about networking and yet I'm at a complete loss, this problem almost seems to defy explanation. Guess I'll just explain.

I've got a lot of media on my main computer, around a Terabyte worth of vids and growing as I buy and rip more of my favourite shows to hard drive. I wanted basically to have a nice gigabit network in the house so I could stream to any of my hard wired PCs without trouble, and also be able to move very large files around for storage purposes. I didn't want to buy a NAS since they are very expensive, instead I just set up sharing on all my machines of all the drives/folders I wanted (through linux Samba, and Vista built in sharing, works fine).

My 3 hard wired machines all use built in networking from the mainboard. Two are nVidia 780i boards with dual gigabit jacks (I only use one each, no need for teaming), the third computer is a less powerful acer with an AMD 780G board also Gigabit capable to my knowledge. Each of my 3 machines is connected directly by ethernet to my router, a DGL4500 and are assigned IPs by DHCP reservation. I get the internet through a speedtouch 585 modem, it is out of this loop, I have it plug directly into the DGL's WAN port though. The only other component is my printer, a Brother 4040CN printer, it plugs into the Speedtouch and is assigned a fixed IP by DHCP reservation as well, I hook it to the modem since it doesn't require gigabit speed. All connections between machines and router, router and modem and even printer to modem are made with quality CAT 6 cables.

I've accounted for everything needed to my knowledge, and yet instead of getting gigabit speeds (i.e. 50-100MB/sec) consistently, it seems entirely random. Most of the time transferring files around I get a paltry 2-8MB/Sec, which is completely unacceptable. Sometimes, I get into the 20 range. Least often I have hit 50, and even 100MB/sec on a few large transfers of files exceeding 3GB. The speed I get seems to be based on no more than luck, I can't see any pattern. It doesn't matter if I transfer 1 file or many, if it's 100MB or 10 GB.

As to software, the AMD board is my full time linux box. I run transmission on it round the clock seeding torrents (linux CDs mostly) and the origami client (maxing my 4 cores). The other two machines mostly run Vista (one is a gaming machine for a relative in the house), the other dualboots between Vista and Ubuntu as I require.

Please help, this has really been driving me simply mad, I'm gonna go crazy if I don't get this sorted!](*,)

---

### Post by starcraft.man on 2009-07-09
Bump, anyone?

---

### Post by Het Irv on 2009-07-09
Alright, I one question about your setup, all three PC's are connected to a switch, and then the switch is connected to the internet.  I wonder if the switch is your choke point, and its not up to the amount of trafic going through it.

The easiest way to tell this is if you try a transfer while you are seeding alot... the transfer speed should be on the lower end, opposed to a time when you arn't seeding much, the speed should be higher.

If that isn't the case, I'm not sure what to tell you

---

### Post by starcraft.man on 2009-07-09
Nope, I terminated transmission and all other local programs that could be using up network bandwidth and still my speed averaged low, barely breaking 5MB on a single and batch file transfer from machine to machine. That's no faster than if I was on my old 10/100 cards/cables.

Thanks for the effort though. Anyone else got input?

---

### Post by bgiannes on 2009-07-28
I'm in the same boat, well sort off.

I have Three PC hard-wired one at 1G the others at 100M

I have a 1G router (wrt310n router running DD-WRT) which is connected to the internet (which is very stable).

There is one 1G switch (in another room, cable is ~10ft and Cat5e) which the two 100M servers are connected to one is (8.1 desktop) and the other a (9.04 server/proxy only for two windows machines) 


pings between any PC are ~ 0.15 to .25ms

i have never see a file tranfer faster then 9.9MB/s w/ scp
copying/moving from the desktop always runs at ~3MB/s or less.

funny this is that if i copy a number of files at the same time i can get 3MB/s per file, up to ~100M  [3Mbytes/s ~= 25Mbit/s]

somedays seem slower then others, (it does get very hot in that room maybe +100F)?  eg today scp is running at 2.9MB/s.  What gives, why should it change?

even if i move one of the servers into the same room and bypass the switch there is no change.

maybe 3Mbytes/s is as fast as SMB per transfer can go?

i was going to upgrade one of the old 100M cards to a 1G but is there any point?

:confused:

---

### Post by bgiannes on 2009-07-29
starcraft.man

have you try transfering files using different copy methods, what rates do you get?

stop all other LAN traffic, reboot LAN (all PC's and router/switchs). Then try copy one large file ie 1Gbyte between two points on your LAN using the following methods one at a time.

ftp
sftp
scp (fastest for me)
cp (cifs) mounts
cp (samba) mounts

I just did this; correct me if i'm wrong but it seems there is a 'SMB (cifs)' 3Mbytes/s ie 25Mbit/s cap Doh! :(  and for 'scp' i get 9.9Mbytes.s = 84Mbits/s {note 11.9MBytes/s is 100M max throughput} [for you 1000M the max is 119Mbytes/s]

i've read up on this, and others report a 3MB/s cap with samba as well.....

---

