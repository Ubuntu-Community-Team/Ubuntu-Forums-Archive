---
title: "Alternatives to slooow SAMBA for OS X and Win Clients?"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by ojobson on 2010-03-15
I set up ubuntu 9.10 to use as a file server for backing up and storing media files - so far so good apart from the terribly slow read speeds that I get from the server.

I've tried for two months now with all the tweaks I can find and 3 re-installs to overcome this, but I only get 7MBps from the server regardless of client, whereas writing is about 35 to 50 MBps depending on the clients.

The closest I got was disabling IPV6, where the read would start at 25MBps and then crash back down to 7MBps within about 5 seconds...

The client machines can talk to each other both ways at between 35 to 50 MBps. OS X clients can read / write to the server at about 40MBps - so it seems that samba is the problem on the server.

I have started a few threads / posted in other threads about this and got no where - 

So what alternatives can I use to share a resource from the server to OS X Leopard and Windows (7, Pro) client machines? Any ideas where I can go to read up on them or a how to? Apparently CIFS is SAMBA from what I can see - so that only leaves me with NFS as far as I know and I know nothing about that... (I've only been dabbling with linux for two months). I have been googling but haven't found much info about how to implement NFS at all.

Many thanks in advance.

---

### Post by RyanRahl on 2010-03-15
You may not need to use a different technology. It's not Samba/SMB that is slow. If you set up Ubuntu with all the defaults then you are using the an ext file system. the server can accept data fast because it caches it to memory but the write speed to the disk is probably significantly slower that the NIC traffic. What you may want to try is setting up a separate HDD on the server for file sharing and format it to XFS. I use XFS for Samba shares at my office (which is primarily XP machines) because I was having similar performance problems and it sped up significantly. XFS is a much faster file system but you may want to set up a daily backup because it is not crash proof. I've personally never had a problem (i do auto backup every night anyway) but just be warned. Let me know how it goes. All my LAN PCs are 10/100 and the server is 10/100/1000. Are you using any gigabit hardware?

---

### Post by Objekt on 2010-03-15
I'm eager to see some more information here.  Somewhat similar to your situation, I have a mixed home LAN, with machines running a mix of Windows and Ubuntu flavors.

I dual-boot Windows XP and Ubuntu 9.10 on my desktop machine, so the mix of OS's changes at times.  Sharing files & folders both ways is no big deal as long as I'm running Windows XP, but I have not been able to do the same thing while running Ubuntu.

Add to the mix: two netbooks running Ubuntu Netbook Remix.  At times, it would be useful to have them able to access stuff on the Windows machines.  Until I get that working, I have to transfer files using either an external HDD, or an 8 GB micro SDHC card.

I'm not sure what I need to do, to get sharing working both ways when I run Ubuntu.  NFS?  Samba?  Both?  I await informative responses here.

---

### Post by Objekt on 2010-03-15
> **RyanRahl said:**
> You may not need to use a different technology. It's not Samba/SMB that is slow. If you set up Ubuntu with all the defaults then you are using the an ext file system. the server can accept data fast because it caches it to memory but the write speed to the disk is probably significantly slower that the NIC traffic. What you may want to try is setting up a separate HDD on the server for file sharing and format it to XFS. I use XFS for Samba shares at my office (which is primarily XP machines) because I was having similar performance problems and it sped up significantly. XFS is a much faster file system but you may want to set up a daily backup because it is not crash proof. I've personally never had a problem (i do auto backup every night anyway) but just be warned. Let me know how it goes. All my LAN PCs are 10/100 and the server is 10/100/1000. Are you using any gigabit hardware?

Thank you for highlighting this important issue.  It is something I've wondered about, since in addition to having a mixed-OS network, I have mixed file systems on my PC because I dual-boot Windows and Ubuntu.

I've definitely noticed that copying from an NTFS volume, writing to an ext3 volume, can be really slow.  Like USB 1.0 slow, even though the NTFS volume is on an external SATA HDD, connected via eSATA to the target machine.  Moving data from an ext3 volume to an NTFS volume is also probably slower than NTFS to NTFS or ext3 to ext3.

Gigabit networking gear is only a part answer.  Regular SATA HDDs cannot sustain a full 1000 Mbit/s transfer rate (125 Mbyte/s).  In practice 60-70 Mbyte/s is more realistic (with my hardware at least).  So the bottleneck is no longer in the network, it's the hard drives.  And that's without even considering the overhead of translating between different file systems.

---

### Post by RyanRahl on 2010-03-15
My server runs 2 2TB drives using RAID1 and backs up to an off site location every night. The server hosts a lot of very large PDF files, system firmware for a variety of MFP devices and some video for my boss's personal use. Both the 2TB drives are specifically for file sharing to the internal office network and they run on SATA formatted to XFS. I get get speeds that are around 15-30mbps very consistently depending on current network load. I'm not sure if the slowdown everyone is experiencing is because of file 'translation' to a different file system, i believe that data is data and its all structured based on file format when it comes to most files so if you looked at it in hex or binary it would look the same regardless of the actual file system. I believe that the slowdown is in the write speed to the file system. File systems will read and write at different speeds depending on what kind of features it has (ie, journaling, encryption, compression, variable block size, etc.), the bottom line is the more features your file system has, the more work it has to do to keep your data. and the more work it has to do the slower it will go.

---

### Post by spyrule on 2010-03-15
[COLOR=#000000]To Objekt: [/COLOR] 

 [COLOR=#000000]At any given moment, these are the systems on my home network:[/COLOR]

 [COLOR=#000000]2 Windows 7 64-bit desktops[/COLOR]
 [COLOR=#000000]2 Windows Vista 32-bit desktops[/COLOR]
 [COLOR=#000000]1 Debian (Lenny) 32-bit desktop (used as a central file and streaming media server)[/COLOR]
 [COLOR=#000000]1 Ubuntu 9.10 (Karmic) 64-bit laptop[/COLOR]
 [COLOR=#000000]1 Ubuntu 9.04 (Jaunty) 64-bit laptop[/COLOR]
 [COLOR=#000000]1 Mac (Leopard) desktop[/COLOR]
 
 [COLOR=#000000]This is all done with a mixture of Ethernet and Wireless connections that are facilitated by one Linksys WRT54Gs running DD-WRT v24-sp2 (10/10/09) micro[/COLOR][COLOR=#000000]. The router handles all of the firewall (with iptables) as well as static and dynamic IP addressing and portforwarding. [/COLOR] 

 [COLOR=#000000]The Debian Server streams (via a LAMP intranet site) movies and TV shows through Divx webplayer, and also streams to iTunes via mt-daapd.[/COLOR]

 [COLOR=#000000]The file sharing, I suppose, is the trickiest part. All of the Linux based machines are running Samba. All of the Windows boxes are on the same workgroup, and my smb.conf lists the same workgroup name that the Windows machines are running on. Once Samba was installed on the Linux machines, and the name of the workgroup was entered in, network shares loaded just fine in Windows Vista, Mac, Ubuntu and Debian (and at other times, fedora, mint, red hat... you get the idea). The problem I'm having is with Windows 7. If browsing the network shares in Windows 7, it usually won't show the Linux boxes. But by typing the network path into the Windows Explorer address bar manually, it connects just fine and everything is just as accessible as anywhere else. Other than the annoyance, this works fine when you just add a shortcut to the share into the Explorer side panel. [/COLOR] 

 [COLOR=#000000]To share from a Linux machine, all you have to do is add something like the following to your smb.conf file (at /etc/samba/smb.conf):[/COLOR]

 ```
[Share]
     comment = Shared on Workgroup
     path = /path/to/Shared 
     read only = no 
     writeable = yes 
     guest ok = yes
```[COLOR=#000000]Most of the above code is pretty obvious I think (correct me if I'm wrong), but this can get a little more complex if necessary... You can look up, for example, 'valid users' or 'locking' from a Google search if you want a little more control over who has access and how.[/COLOR]

 [COLOR=#000000]As for speed issues, there's a plethora of variables that effect this. My network (like RyanRahl's) is a mixture of gigabit and 10/100. I have some cables that are Cat5, some Cat5e, and a couple of Cat6. Wireless maxes out at g, but some of the laptops are capable of running n. Some of the systems are ext3, some NTFS and some are Fat32. To maximize speed, without control over which filesystems the computers are running, or cards they have installed, is really about the logic of topology. For this reason, between my server and my what I use as a media player I have a dedicated gigabit switch that lets those two computers talk to each other without having to be bogged down by the router's capabilities. Cat6 cables makes them slightly faster, as do gigabit cards. But the reason my network is so fast is because I have virtually all of my time-sensitive information streaming. One can (and several do) sit in my back yard and watch the latest episode of House over wireless from my server in the attic.[/COLOR]
 
 [COLOR=#000000]Also, because of DD-WRT, I can give the operations that I think are the most important priority over other operations. My system is set up to slow down web browsing before slowing down file transfers between two laptops, for example.[/COLOR]

 [COLOR=#000000]If you want to maximize the speed at which files can be transferred between two computers, limit the hurdles between them. This means fiber (if you can afford it) or at least gigabit connections between those computers that are exchanging info. It also means experimenting with the fastest cards you can find, the fastest hard drives you can find and the best switch or router you can find. But, from my experience, Samba rocks!

Hope some of this helps.
[/COLOR]

---

### Post by ojobson on 2010-03-15
> **RyanRahl said:**
> You may not need to use a different technology. It's not Samba/SMB that is slow. If you set up Ubuntu with all the defaults then you are using the an ext file system. the server can accept data fast because it caches it to memory but the write speed to the disk is probably significantly slower that the NIC traffic.

It's not write speeds that are the issue - it is the read speed when pulling data form the server - I'm only geting 7MBps over samba regardless of the client setup. When using Appletalk I can pull data form the server at about 40 to 50 mbps - so I don't believe this is a hardware or file system issue. If I could get appletalk to work with Windows 7 then I would ditch samba in an instant.

I did consider XFS, but I wanted more reliability from my backup server. 

> **Objekt said:**
> Gigabit networking gear is only a part answer.  Regular SATA HDDs cannot sustain a full 1000 Mbit/s transfer rate (125 Mbyte/s).  In practice 60-70 Mbyte/s is more realistic (with my hardware at least).  So the bottleneck is no longer in the network, it's the hard drives.  And that's without even considering the overhead of translating between different file systems.

I have 3 hard disks in the server, a mix of sata and IDE - even the oldest gets read speeds way faster than 7MBps!

So any alternative protocols for sharing to OS X and Win 7?

---

### Post by RyanRahl on 2010-03-15
Well.... I know that in GNOME and Windows you can make a desktop icon that is a link to an FTP and it behaves visually just like a normal samba share and is MUCH faster. I'm not sure what you're doing with your file sharing or whether or not you are using software to call the shares that may or may not be FTP compatible. But for normal file sharing it works great. I've got FTP icons on my desktop for the few FTP servers I have. Just go to the 'Places' menu in GNOME and click 'connect to server.' If you want the shares to show up every time you boot you can add a mount command to your startup. I don't know exactly how to do this in Windows but I'm sure a Google search will give you some pretty quick answers. Hope this helps. :)

Looks like you can do this on OSX:
[http://www.blogiversity.org/blogs/willburns1/archive/2009/04/27/how-to-mount-ssh-and-ftp-file-systems-on-your-desktop.aspx](http://www.blogiversity.org/blogs/willburns1/archive/2009/04/27/how-to-mount-ssh-and-ftp-file-systems-on-your-desktop.aspx)

---

### Post by spyrule on 2010-03-16
> **ojobson said:**
> It's not write speeds that are the issue - it is the read speed when pulling data form the server - I'm only geting 7MBps over samba regardless of the client setup. When using Appletalk I can pull data form the server at about 40 to 50 mbps - so I don't believe this is a hardware or file system issue. If I could get appletalk to work with Windows 7 then I would ditch samba in an instant.

I'm kinda' confused by what you're saying here. Is Appletalk reporting rates in mbps? Or MBps? 

50 mbps = 6.25 MBps. So you're saying Samba is pulling faster, or at least similar to Appletalk?

---

### Post by ojobson on 2010-03-16
> **spyrule said:**
> I'm kinda' confused by what you're saying here. Is Appletalk reporting rates in mbps? Or MBps? 

50 mbps = 6.25 MBps. So you're saying Samba is pulling faster, or at least similar to Appletalk?

My bad there - should read MBps. - as in my first post, all speeds are megabytes per second (MB)

Reading from the samba share on the server is way slow over gigabit; 7MBps, whereas writing is 40 to 50 MBps. Appletalk gets 40 to 50 MBps each way (with identical hardware).

RyanRahl thanks for the tip about ftp - I think this may be a solution - although I don't know if this will work with the Windows 7 Backup software. I will have to have a look...

---

### Post by spyrule on 2010-03-16
I think you might find this thread useful:

[http://ubuntuforums.org/showthread.php?t=705431](http://ubuntuforums.org/showthread.php?t=705431)

---

### Post by ojobson on 2010-03-17
> **spyrule said:**
> I think you might find this thread useful:

[http://ubuntuforums.org/showthread.php?t=705431](http://ubuntuforums.org/showthread.php?t=705431)

This seems to suggest hardware is a problem - but I know I can transmit and receive at around the same speeds (approx 40 MBps) using appletalk - so could the hardware pose problems only for SAMBA?

Perhaps I will try a new network card and see if this helps...

---

### Post by RyanRahl on 2010-03-31
I don't think its a hardware problem..... I did some testing and I noticed that when I transfer large files with an FTP folder through GNOME it goes significantly slower than with an FTP client software. This made me question GNOME/Nautilus. I did some testing and discovered if you transfer SMB files with the standard 'cp' command to a Samba share mounted through the terminal you will notice there is not much of a slowdown. My conclusion is that Nautilus/GNOME is the bottleneck.

---

### Post by ojobson on 2010-05-17
Well, I've given up with Ubuntu - I needed something that was a bit more user friendly and I thought Ubuntu might have got to that stage, but no.

I am now the proud owner of an atom 330 powered hackintosh which is working beautifully and zipping along very nicely for what is required of it!!

---

