---
title: "MythTV on my home network with home server"
date: 2008-05-27
forum: Multimedia Software
---

### Post by garethsimpsonuk on 2008-05-27
Hi,

I've just got a PCI TV card for my server. I was thinking I could set it up to record / play digital tv from any networked box in the house (and the net using web gui).
I was just wondering if this is a good idea for my home server. All together it will be running:

-TorrentFlux
-aMule
-Lamp
-Webmin
-rSync (or similar)
-Samba
-A family website & forum / + other scripts to access it all.

I haven't got all this sorted yet but do you think I'm asking a lot of my Athlon XP 2000+ (1.7ghz 256mb - upgrading ram v.soon, will 512 mb be enough or shall I get 1 gb)

Will it be very slow? It wont be under much stress so I hope it will be ok.

Cheers

Gareth

p.s. does anyone have any alternatives + cool things I can do with my TV card

---

### Post by thorgal on 2008-05-27
the issue won't come from CPU usage but from disk usage and network bandwitdh traffic. I have a MythTV LAN based setup as well. You need a dedicated hard disk formatted with a filesystem that can write and delete large chunks of data very fast (like JFS or XFS - I personaly use xfs and never had issues with it, unlike other users who have complained a lot so YMMV). You should tune your NFS server (wsize and rsize options). 

In my setup, the NFS and mysql servers are on two different boxes. I use the NFS server for other things than just MythTV so my MythTV box can sleep when idle without bringing down NFS. Of course, you don't absolutely need NFS with MythTV but if you plan to use mythVideo or mythMusic with your won collection of mp3s, avi's, etc, it becomes necessary.

---

### Post by garethsimpsonuk on 2008-05-27
well I have 300 gb spread over 3 IDE drives in the box. I also have an NTFS 500gb USB drive (cant be taken out of cradle). It says Myth TV saves recordings etc in th /var/ path, van I change it to a different disk (my os is on a 4 gb and the rest are for storage.)
I do have another box that's a till from a shop which is quite powerful but it has loads of noisy fans and since it's in a small box I'm gonna carpet it and make it into a 'carputer'. Take a Nubuntu live cd with me and I can 'borrow' wifi wherever I park up!

---

### Post by EndPerform on 2008-05-27
CPU usage will depend on the type of TV card you have.  If it's one that has a hardware encoder (PVR250/350 I believe), then it shouldn't be too big a strain.  The biggest thing, though, is going to be the network connection.

You've got a bittorrent client, a web server and if you intend on streaming video from the server, you're asking a lot of your network connection, so it might be a good idea to migrate at least the bittorrent stuff to another machine.

For streaming, you can configure your other computers as MythTV frontends only, then point them at the backend (your server), which is what I did.  I had a small backend server, and used a modified XBox running Xebian as my frontend.  It worked quite nicely.  As far as NFS and sharing your media goes, Samba works rather well, too.

---

### Post by eldragon on 2008-05-27
ive installed mythtv last week in order to be able to stream tv to my laptop through the wireless network...

having a fair connection (18Mbps) it works ok. 

im using an analogue card, so stream rate might be more network friendly.

---

### Post by garethsimpsonuk on 2008-05-27
That's it! I'll put an xbox in the living room connected to the plasma. Kinda like a thin client that's a great idea, and it looks nice to. Have you had any experience with LinuxMCE? They have an iso that installs kubuntu and  linuxmce I could put this on an xbox maybe. 
I think I'll go with myth TV just for now because it's a lot less to setup (eventually I do want everything integrated - lights, kettle etc. lol) 
The thing is we have 5 windowes boxes in the house how well will MythTV work with windows?

---

### Post by garethsimpsonuk on 2008-05-27
Yea most will be hardwired but upstairs they will be wireless (54mbps) I'll just have to stop the torrents while at home and use it when I'm out ( control with a pocket pc + edge + web gui )

---

