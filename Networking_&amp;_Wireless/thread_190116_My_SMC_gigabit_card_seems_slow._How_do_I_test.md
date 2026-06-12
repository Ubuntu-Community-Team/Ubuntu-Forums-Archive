---
title: "My SMC gigabit card seems slow. How do I test?"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by MetalMusicAddict on 2006-06-05
I have a SMC EZ 1000 (SMC9452TXV.2). I think the chipset is Marvell Technology 88E8001.

Ok so heres how I noticed. Of the 6 PCs in the house only 1 still dual-boots with windows. I encode movies over there. :) It takes less that 2 mins to move a 1.5gig file on the win-side. I moved that same file in linux and it took over 5. :-k 

The box (my server that I havnt upgraded yet) I moved the file to has the same card running Breezy. Everything else is Dapper.

Any ideas? Not the best driver? Any way to test the connection?

---

### Post by d.j.schroeder on 2006-06-05
I tested mine using a 670MB iso image of a CD, and then timed it with the second hand on my watch.  It took 50 seconds (670 x 8)/50 = 107 Mbits/s.  Unfortunately for me that is the same as what it took before I upgraded to gigabit switches.  On my Windows boxes that time dropped immediately to a little less than 15 seconds when I upgraded (limited by hard drive read/write speeds).

The switch recognizes that it is connected to a fast adapter, something about 6.06 won't let it go that fast.  I am a total linux noob so I have no clue what to do about it.  The adapter is on an ASUS A8N-SLI board with an Nvidia Nforce 4 chipset and, I think, a Marvell ethernet adapter. 

Anyone have a suggestion?

---

### Post by d.j.schroeder on 2006-06-05
ok that smiley face in that equation was an 8 when I typed it, for 8 bits in a byte.  Don't know why that happened, sorry.

---

### Post by MetalMusicAddict on 2006-06-06
[QUOTE=d.j.schroeder]ok that smiley face in that equation was an 8 when I typed it, for 8 bits in a byte.  Don't know why that happened, sorry.[/QUOTE]
"Disable smilies in text" is what you needed to do. You can edit your other post. ;)

Can anyone help me out? Any commands I can run?

---

### Post by MetalMusicAddict on 2006-06-07
[IMG]http://www.aaliyah.com/forum/attach.aspx/15724/Boxer%20Bump.JPG[/IMG]

---

### Post by MetalMusicAddict on 2006-06-09
Anyone? :)

---

### Post by MetalMusicAddict on 2006-06-10
Bump..... :) Somebodys gotta know something.

---

### Post by MetalMusicAddict on 2006-06-12
Maybe I should start a "Waaa, I'm leaving" thread to get help? :)

---

### Post by MetalMusicAddict on 2006-06-13
I wonder how many time I can bump this without getting help? :)

---

### Post by netztier on 2006-06-14
Well, you can bump it 'till your head hurts ;-)

Or you can try [**iPerf**]("http://dast.nlanr.net/Projects/Iperf/"). It should be available in the universe or multiverse repositories.

Running it as a "server" (receiving data) with **iperf -s** and a "client" (sending data) with **iperf -c <server-ip>** can give you a rough estimate of what your network, NICs and TCP stacks are capable of. 

Playing around with the command line options can be quite fun, and you can really put some stress onto your switches and routers. We use it at work to do some "sanity checks" on our network: any full duplex mismatch somewhere on the path between server and client is easily spotted that way.

On Gigabit links, using single connections and no optimisations (receive window an the like), you should get somewhere between 400 and 600 Mbps. To fill a Gigabit pipe, you should increase the receive window and use multiple streams simultaneously - at the price of noticeable CPU load on the end systems. Don't try this at work, kids! (unless you know what you are doing) ;-)

Beware: this tool will *only* measure raw TCP or UDP throughput. It won't say anything about the performance of your server programs - which will be file servers in this case, probably using samba.

I for myself have been disappointed by the performance of samba. This goes for both the "classic" Windows filesharing style with NetBIOS over IP (udp/137+138, tcp/139) and the newer CIFS style (tcp/445). Either way, it won't go beyond ~7,5 MByte/sec (peak, 5Mbyte/sec sustained) for a single connection (on 100Mbps full duplex links).  

Samba gets dwarfed by NFS which does 11.5MByte/sec from the same file server serving the same file to the same client, with noticeably less CPU load on the file server. So upgrading to 1Gbps might just not be the thing that helps here. Serving multiple concurrent clients however showed that samba can indeed fill a 100Mbps link.

Check your network with iPerf - if there's no bottlenecks, you'll have to start investigating with the services you are using.

kind regards

Marc

---

### Post by MetalMusicAddict on 2006-06-27
Now that Ive played with it this is a driver issue Im sure. Anyone know how to go about getting a resolution or definant answer on this? How to let a dev know?

---

