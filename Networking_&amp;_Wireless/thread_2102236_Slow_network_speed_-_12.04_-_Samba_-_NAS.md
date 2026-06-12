---
title: "Slow network speed - 12.04 - Samba - NAS"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by futo on 2013-01-06
Problem originally described and shown on YouTube [http://youtu.be/cSZ9X9y9_hc](http://youtu.be/cSZ9X9y9_hc) .

Downloading from my NAS to Ubuntu 12.04 with Samba on my home network is horrible slow.

Here the formulation of the problem from the YouTube page:

The NAS and the Ubuntu 12.04-laptop are connected to the same switch - and these three parts run a 1000 Mbit/s-network.

The Ubuntu 10.04-PC is connected to the internet-routeren with a 100 Mbit/s-network - and this internet-routeren feeds also the switchen where the NAS and the Ubuntu 12.04-laptop is connected to.

THE PART OF THE NETWORK WITH 1000 Mbit/s:
The NAS can deliver op to 100 MByte/s = 800 Mbit/s (losely calculated)
The network of the switch can deliver 1000 Mbit/s = 125 MByte/s (losely calculated)
The Ubuntu 12.04-laptop runs with 1000 Mbit/s and a test shows that it downloads from the NAS with around 8.0 MByte/s = 16 Mbit/s (losely calculated). (THIS SLOW SPEED IS A PROBLEM!)

THE PART OF THE NETWORK WITH 100 Mbits/s:
The network of the internet-router delivers 100 Mbit/s = 12.5 MByte/s (losely calculated)
The Ubuntu 10.04-PC runs 100 Mbit/s and a test shows that it downloads from the NAS with around 4.7 MByte/s. (only half of the possible speed, but not the problem right here)

As I was chatting on a IRC channel next to testing the download from the NAS I came on the idea to isolate the switch from the router - not that this interfered with the download between the NAS and the Ubuntu 12.04-laptop. The speed dropped to far under 1 MByte/s !!! even thou it is supposed to be between 50 MByte/s and 100 MByte/s !!! ...

... thus confirming the original test (from when the video was uploaded) described in the following:



First I store from the Ubuntu 10.04-PC some bulky files around 14 GB on the LaCie. This runs with 9.3 MByte/s. This speed fits perfect into the capacity of the 100 Mbit/s ethernet card of this computer.

When the files are completely transferede to the NAS server I go on with the next steps.

From the Ubuntu 12.04-laptop (a brand new laptop by Okt. 2012 with all of the best) I now drag and drop the same files from the NAS server to the desktop. The transfer rate is now ONLY 1 - 2 MB/s !!! - What happens?... This is actually a computer with a 1.000 Mbit/s ethernet card!!! A card ten times faster than that on the other computer.


NO COMES THE FUNNY PART: While the Ubuntu 12.04-laptop is fetching the data from the NAS, I now start to fetch another big bulky file from the same NAS to the desktop on same computer. When these two cuncurrent transfers are running from the same NAS to the same computer, then the transfer rate jumps to what ist expected: around 50 - 100 MByte/s. ... Thats weird!

As soon as the second transfer stops, the speed of the first transfer drops to 1 - 2 MByte/s again.

Crazy stuff! - What happens?... Is it Lacie, Ubuntu or Samba?...

--------------------------------------------------------------------

My laptop is with the newest i7 3840qm 2.8 GHz for mobile units, ssd & ordinary hd, r8168 eth. card and a lot of other fine stuff. The driver for the network card is r8168 and not r8169 which comes with a Ubuntu/kernel installation.

Have tried to add the&#65279; following two lines&#65279; (placed under 'Misc', all 3 combinations)&#65279; in /etc/samba/smb.conf:
SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY

- First when I wrote them in ONE LINE, like this, it worked a little better:
socket options = TCP_NODELAY&#65279; SO_RCVBUF=8192 SO_SNDBUF=8192

- The speed jumped from 1MB or less to around 3 MB. Nice, but still not anything like 1000Mb/s

----------------------------------------------

Checked eth0 with mii-tool and ethtool:

mii-tool says half duplex and ethtool says full duplex.
Tried to change the setting 'in' mii-tool, but that didn't change anything.
Don't know&#65279; why the different results and what to try at this point to manage these two different results.

------------------------------------------------

Came on the idea to try a sftp session to the NAS from the 12.04-machine. Speed is around 4.7 MB/s.

Could this exclude Samba as reason?... Is it more in eth0 somewhere I have to look?....

---------------------------------------------------
Using testparm didn't reveal anything interesting, as far as I can see:
```
laila@laila:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
```

I hope the font isn't to small nor to big for reading. At my home/laptop I have a very big font right now - being able to read it from 2 meters distance of the screen. Not anything I'm used to on the internet.

---

### Post by tgalati4 on 2013-01-06
You are getting better speeds than me.  I can transfer a 1 GB ISO from my freenas server to my Ubuntu laptop (wired or wireless) in 5 minutes.  That's 3.33 MB/sec.  SAMBA has always been a slow protocol.  I have a gigabit switch that my freenas server is hooked to and the wireless is 100BaseT.  SAMBA was designed for compatibility and not performance.  It does a lot of packet header checking and that overhead reduces throughput.  You are not the first to notice this.

True throughput speeds on TCP/IP is roughly 1/10 of the maximum burst speed.  So a 1 Gigabit/sec switch would really only deliver 100 Mbits/sec or 12.5 MBytes/sec sustained throughput.  Put other machines on the network and SAMBA overhead and you are lucky to get 4.7 MBytes/sec throughput.

Show me a faster network protocol in linux.

---

### Post by futo on 2013-01-06
> **tgalati4 said:**
> You are getting better speeds than me.  I can transfer a 1 GB ISO from my freenas server to my Ubuntu laptop (wired or wireless) in 5 minutes.  That's 3.33 MB/sec.  SAMBA has always been a slow protocol.  I have a gigabit switch that my freenas server is hooked to and the wireless is 100BaseT.  SAMBA was designed for compatibility and not performance.  It does a lot of packet header checking and that overhead reduces throughput.  You are not the first to notice this.

True throughput speeds on TCP/IP is roughly 1/10 of the maximum burst speed.  So a 1 Gigabit/sec switch would really only deliver 100 Mbits/sec or 12.5 MBytes/sec sustained throughput.  Put other machines on the network and SAMBA overhead and you are lucky to get 4.7 MBytes/sec throughput.

Show me a faster network protocol in linux.

If all your words are right, why then have I had throughput of up to more than 80 MB/s (megabyte per second) on the same 1 Gigabit/s switch as I'm now using? ... If you watch the video I linked to [http://youtu.be/cSZ9X9y9_hc](http://youtu.be/cSZ9X9y9_hc) you can see at 0:50 that the speed is at more than 30 MB/s....

The NAS is capable of read from the disk and feed a network with up to 100 MB/s - and as said; I have been at 80 MB/s - with Samba and with my laptop.

The crazy things is, next to the low speed, that the speed changes UP-wards when two downloads competes OR if I download from the internet at the same time (same switch, same laptop, same NAS).

In the video on YouTube I have showed a faster network than 4.7 MB/s. 
- So, other suggestions?...

---

### Post by futo on 2013-01-06
> **tgalati4 said:**
> ...SAMBA was designed for compatibility and not performance.  It does a lot of packet header checking and that overhead reduces throughput. ...

Read this link from the Samba people:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html)

 ... which says: "... Generally, you should find that Samba performs similarly to ftp at raw transfer speed. It should perform quite a bit faster than NFS, although this depends on your system. 

Several people have done comparisons between Samba and Novell, NFS, or Windows NT. In some cases Samba performed the best, in others the worst. I suspect the biggest factor is not Samba versus some other system, but the hardware and drivers used on the various systems. Given similar hardware, Samba should certainly be competitive in speed with other systems...."

---

### Post by futo on 2013-01-06
> **tgalati4 said:**
> ... 4.7 MBytes/sec throughput.... 

Sorry; Your mixing the facts. 

4.7 MB/s is a fair speed on a 100Mbit/s network. 12,5 MB/s is theoretical. 10 MB/s is practical possible. When it's only the half, 4.7 MB/s, is probably because the data has to go "forward and backward" on the same cable - something like half duplex.

But as I sad: That's not the problem here. 

The problem is that the speed of the 1 Gigabit/sec, alias 1000 Mbit/s, alias 125 MB/s (theoretical) network is only at around 1 MB/s.

Practical the speed should be around, or up to 100 MB/s.

---

### Post by futo on 2013-01-06
I checked the driver for updates. Since october I used 8.032.00, but a new where available: 8.035.00. - I updated: no changes on the long run, but noticed how mii-tool now says that duplex is 'full' where is earlier said 'half'. Anyway; no speed changes.

---

### Post by futo on 2013-01-06
Tried some hardware changes: Unplugged everything except laptop and NAS - and placed them both on the internet-router with the 100Mbit/s network. No speed changes. Download is at 1 MB/s more or less. - But should actually be around 4.7 MB/s.

---

### Post by futo on 2013-01-06
Tried to download from another machine with Ubuntu 10.04 - same speeds for download with sftp via terminal.

Is the problem the internet-router, the switch or the Lacie NAS ?...

... I'm open for suggestions ... and will stop post anything until the higher powers gives some hints...

---

### Post by tgalati4 on 2013-01-07
If you search the net and these forums for file transfer speed, you will find many posts and many similar stories.  Everything from tweaking TCP parameters, kernel parameters, routers/switches, cable types, folks have demonstrated that each network is unique with its own performance bottlenecks.

Because TCP/IP is a network protocol that allows multiuser and multistream for a single user, there is an overhead associated with using it.  

On my network, it takes 5 minutes to move a linux ISO (~1 GB) from one machine to another.  That's 3.33 MB/sec, regardless of which machine I use or wireless vs wired.

On your network, try a test of two simultaneous transfers of a large file from one machine to another.  Try two different users, each transfering one large file.  Try transfering a large file in one direction, while simultaneously transfering another in the opposite direction.

If all you cared about was one-directional, single-file speed, then you would use fiberchannel, or some other proprietary protocol that is optimized for that task.

Regarding SAMBA:  It is a great protocol that solves a lot of connectivity problems and has so for a long time.  Some folks have experienced performance problems.  They expected dd raw write performance over a network and they get coffee-can-and-string performance.  It might be a SAMBA problem or it might be something else.  Each network is unique.

The common notion:  "I bought a gigabit router and all my stuff is gigabit, I should be getting gigabit speeds."  underestimates the complexity of the network problem.  Your network delivers whatever speeds it delivers.  You can try to make some changes to improve it (usually only slightly), but it is what it is.

I couldn't find any reviews on the LaCie 2big NAS on the web.  Perhaps others are satified with it?  I have a 1997 PC, 256 MB RAM (maximum), Pentium I, 188 MHz (overclocked from 166 MHz) with a SATA card and several TB of disks.  I run [http://freenas.org](http://freenas.org) on it.  I get 3.33 MB/sec transfer out of it. I'm running a zfs RAID pool on it, but that doesn't affect network speed.  It uses ~35 watts.

"The 2Big NAS has a 2GHz ARM processor that, LaCie claims, helps boost read speeds from 60 MBps to 100 MBps. It&#8217;s running LaCie&#8217;s latest version of NAS OS software which was updated last year to offer more features and make easier to set up and use. The 2Big NAS is also more environmentally friendly, using 90 percent less power in deep sleep mode.

Available without any drives ($299) or with 6TB ($699) of storage" 

So I am satisified that my old, crappy NAS can do as well as the new and shiny stuff.  Show me consistent 60 MB per second transfers.  Even the reviewers could only get around ~12.7 MB/sec with 10 GB of small files.

---

### Post by futo on 2013-01-08
Thanks very much for all the time you spend on this. :) I've read a lot  of different stories on the internet of how network can behave. Yes,  each network has it's soul. And each wireless have more than one soul.  And sometimes both of them are female. xD

Yes, be happy about  your 60 MB/s. That's a quite fine speed. Mostly the inside of a computer  can't deliver more, unless you start use prof equipment with minimum  some other buses and RAID with 5 disks - and a lot other stuff. (=  bigger costs)

After this "show" with Lacie I will never again buy  Lacie. I promise! - I tend try other labels or build my own. (A tip for  my self - find articles about what other users want. They might have  experience with exactly NAS: [http://lifehacker.com/5968677/five-best-nas-enclosures](http://lifehacker.com/5968677/five-best-nas-enclosures) )

I've done *several* tests the last days.

Always  when I use the Lacie File Browser I have the best (and full)  performance - through out Ubuntu 12.04, 10.04 or Windows 7. On a 100Mb/s  network that's around 10 MB/s as transfer rate. 

Ubuntu+Samba,  being 10.04 or 12.04, can't manage to get a higher speed than between 1  and 3 MB/s. Here it doesn't matter if the network is 100 Mb/s or 1000  Mb/s (without additional software from Lacie).

With seconds  between the test I've tested first Samba download and then Lacie File  Browser. File Browser ran with full speed and Samba was slow as always.  (Samba - graphical network connection through Ubuntu)

I have done  several test the last days on a different router, with different cables  where only NAS and a laptop was connected. No better results with  Ubuntu+Samba than 1 to 3 MB/s while Lacie File Browser ran full speed.

I have reformatted the NAS. I have reloaded the Operating System on the NAS according to Lacie instructions. Nothing helped.

Right now I'm tending to investigate Samba on Ubuntu more.

Just  as I bought the NAS I had speeds at 10 MB/s on a 100 Mb/s network. Back  then I had some software from Lacie on a 32-bit-pae Ubuntu 10.04. Now  I'm running 64 bit Ubuntu 12.04 and can't install that software.

Well,  I actually just tried the software from Lacie in a virtual machine  running 32-bit Ubuntu 10.04. No gain in speed: Still only 2 MB/s.

Just as I got the 1000 Mb/s network switch I had speeds over 70 MB/s.  They disappeared somehow - and I can't remember or don't know the  circumstances when that happened.

The searcher ... :/

Thanks for the help so far. Your the best! :)

---

### Post by futo on 2013-01-08
- Oh, yes, and I've been using 3 different computers - and the same tests again and again on all those 3 ...

... by the way, MOST CHOCKING: Windows 7 didn't have any problem with a direct Samba-connection: It ran full speed!

So, I could tend to look at the problem in Samba AND on Ubuntu laptop-OS-side ... but on the other hand, why there?... could also be Lacie?... I have to test with another Samba-server one day ... no, the NAS hadn't changed anything until 4 days ago, so it must be Samba/Ubuntu-laptop-side. ...

Here later, I'm noticing the following.
All the time I tested the transfer speed with a big file of 1 GB. As I now download 1.500 files of together only 24 mb the transfer speed is less than 0.1 MB/s. Even the preparation of the file operation takes a hell of a time. 

- What can that indicate?....

---

### Post by tgalati4 on 2013-01-08
Windows 7 doesn't use SAMBA, per se, it uses its native, network file sharing system.  Ubuntu needs a translator to go from ext4 to Windows and uses SAMBA to perform that function.  It takes time, especially with lots of small files.  That is why you are seeing a performance hit with many, small files.

I wonder how the speeds are with a Mac?  I don't know what operating system the LaCie NAS uses, but it was probably developed and optimized for Windows.  If you had a linux or BSD-based server you would probably get faster transfer speeds.  Try setting up another Ubuntu instance and share a folder.  Measure the speed a large file from Ubuntu-to-Ubuntu and a directory with several small files.

You can put a "hard share" in your /etc/fstab.  I find they are faster than temporary mounts done through Nautilus.  I'm not sure why, unless there is a user versus system performance penalty. There are several examples on the forums, search fstab.

The LaCie doesn't appear optimized for transfers for linux machines.  There could be extra, redundant traffic that slows down such transfers.  Send an email to LaCie documenting your performance testing.  Like I said, the few reviews I found for the LaCie NAS noted the crappy throughput--regardless of the hype printed on the box.

Without reading the Lifehacker article that you posted, I was going to recommend Synology.  What operating system does it run?

Here are some performance numbers:

[http://forums.freenas.org/showthread.php?9884-FreeNAS8-performance-vs-Synology&highlight=synology](http://forums.freenas.org/showthread.php?9884-FreeNAS8-performance-vs-Synology&highlight=synology)

And, only Windows machines tested:

[http://www.synology.com/products/performance.php?lang=us#tabs-2](http://www.synology.com/products/performance.php?lang=us#tabs-2)

---

### Post by bab1 on 2013-01-09
> **tgalati4 said:**
> Windows 7 doesn't use SAMBA, per se, it uses its native, network file sharing system.  Ubuntu needs a translator to go from ext4 to Windows and uses SAMBA to perform that function.  It takes time, especially with lots of small files.  That is why you are seeing a performance hit with many, small files.
This is not quite how things work.  Both *Windows File Sharing* and *Samba* use the same basic protocol (SMB/CIFS) in the implementation of file sharing.  The underlying file system (EXT or NTFS) has nothing to do with SMB/CIFS either.  But...  The mounting of the share has everything to do with the performance.> 

I don't know what operating system the LaCie NAS uses, but it was probably developed and optimized for Windows. 
It uses Linux (2.6 kernel)> 
 If you had a linux or BSD-based server you would probably get faster transfer speeds.  Try setting up another Ubuntu instance and share a folder.  Measure the speed a large file from Ubuntu-to-Ubuntu and a directory with several small files.

You can put a "hard share" in your /etc/fstab.  I find they are faster than temporary mounts done through Nautilus.  I'm not sure why, unless there is a user versus system performance penalty. There are several examples on the forums, search fstab.
Nautilus uses what the Gnome dev's felt would work best for most users.  I have used both command line mount scripts or fstab for better results.> 

The LaCie doesn't appear optimized for transfers for linux machines.  There could be extra, redundant traffic that slows down such transfers.  Send an email to LaCie documenting your performance testing.  Like I said, the few reviews I found for the LaCie NAS noted the crappy throughput--regardless of the hype printed on the box.

Without reading the Lifehacker article that you posted, I was going to recommend Synology.  What operating system does it run?

...
Synology also uses Linux as an OS.  My own take is that the versions of Samba is older and can cause problems.  It might even be v2 Samba for all I know.  

Neither of these devices have a CPU worth talking about or an optimized HDD I/O that will bring any real improvements.  But both devices have had folks develop Debian install packages.  Hmmm...

---

### Post by tgalati4 on 2013-01-09
Bab1, you make some excellent points.  But why are there so many stories of poor file transfer performance with linux machines with these NAS devices?

I don't think CPU performance should make a difference if these devices show high transfer speeds to Windows boxes but low transfer speeds to linux boxes, unless there are some software overhead associated with talking to linux machines that would cause the slow downs.  Could it be the different (more complex) permission system that linux utilizes that causes extra checking and would also explain the poor small-file performance?

---

### Post by Thee on 2013-01-09
I had problems with network speed with Ubuntu > NAS, with Windows > NAS it worked like it should, so I followed this guide:
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

And it doubled my network transfer speeds and solved everything.
So check it out.

---

### Post by bab1 on 2013-01-09
> **tgalati4**
I don't think CPU performance should make a difference if these devices show high transfer speeds to Windows boxes but low transfer speeds to linux boxes, unless there are some software overhead associated with talking to linux machines that would cause the slow downs.

I agree here.  The CPU is forced to work harder because the embedded Linux ususally uses earlier (non-optimized) Samba code, > 
 Could it be the different (more complex) permission system that linux utilizes that causes extra checking and would also explain the poor small-file performance? 
No, more like the CIFS or gvfs drivers.  There are no NTFS aspects to the mount or file transfer. Look at the mount of a share.  You will see it uses mount.cifs or gvfs rather than NTFS.  Here is a mount of one of my shares (note that this is gvfs)
```
gvfs-fuse-daemon on /home/bab/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bab)
```
If you were to mount this directly using mount.cifs you could optimize the mount.

Another point is that userland file systems (i.e. gvfs-fuse) are never as fast as kernel file systems.

> **@Thee**
And it doubled my network transfer speeds and solved everything.
So check it out. 
There are numerous errors in that posting.  In addition there have been many updates since that post. This includes MS loosing a lawsuit and having to disclose how they implement CIFS.  Glad to hear that it has worked for you.  Did you mount the share directly using mount.cifs (mount -t cifs)?

---

### Post by Thee on 2013-01-10
> **bab1 said:**
> In addition there have been many updates since that post. This includes MS loosing a lawsuit and having to disclose how they implement CIFS.

That may be so, but the speed was not good out of the box using just Nautilus to mount SMB shares. And every other effort to boost the speed that I found on the net, failed.

I made a permanent mount in fstab using the following command:

```
//netbiosname/sharename    /media/sharename        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

And from ~6 MB/s the speed jumped to ~11 MB/s (100 Mbps network).

---

### Post by tgalati4 on 2013-01-10
So we have at least one datapoint that shows kernel space mounting is faster than user-space mounting with SAMBA/CIFS shares.  I have noticed the same trend, but I don't have detailed test cases.

The problem for a NAS is that a casual user is moving stuff back and forth to the NAS so fstab or console mounts are inconvenient.  It's OK between machines where you can permanently mount a "Share" directory on each machine and put stuff into that directory that you want to show up on the other machine.  I suppose you could make permanent fstab mounts to a NAS with similar "Share" or "Public" directories, but that requires a more in-depth level of linux knowledge.

---

### Post by bab1 on 2013-01-10
> **Thee said:**
> That may be so, but the speed was not good out of the box using just Nautilus to mount SMB shares. And every other effort to boost the speed that I found on the net, failed.

I made a permanent mount in fstab using the following command:

```
//netbiosname/sharename    /media/sharename        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

And from ~6 MB/s the speed jumped to ~11 MB/s (100 Mbps network).

As I said, using a mount of the share from the CLI or fstab will get you the speed you wanted.  This is how I mount shares for users who need that.  There are also other parameters that help some apps like Libre Office perform better  when data is stored on Samba shares.

---

### Post by bab1 on 2013-01-10
> **tgalati4 said:**
> So we have at least one datapoint that shows kernel space mounting is faster than user-space mounting with SAMBA/CIFS shares.  I have noticed the same trend, but I don't have detailed test cases.

The problem for a NAS is that a casual user is moving stuff back and forth to the NAS so fstab or console mounts are inconvenient.  It's OK between machines where you can permanently mount a "Share" directory on each machine and put stuff into that directory that you want to show up on the other machine.  I suppose you could make permanent fstab mounts to a NAS with similar "Share" or "Public" directories, but that requires a more in-depth level of linux knowledge.

You can also script the mount of the shares.  It's not for a "casual user", but it sure helps me admin the user that only intermittently needs access to Samba shares.  I use Zenity to  provide prompts for the user (yes I have Samba user on Ubuntu machines).  The same script both mounts and unmounts the share.  I provide the user an icon on the on the desktop that they click to mount and click to unmount the share.  Simple for the user.  maybe not so simple for the Linux noob though.

---

### Post by tgalati4 on 2013-01-10
Can you post that Zenity script?  That would be most helpful.

---

### Post by bab1 on 2013-01-11
> **tgalati4 said:**
> Can you post that Zenity script?  That would be most helpful.

Sure.  There are a few things that are checked in the script.  I will explain...  

First  I check to see that the host with the Samba server is up (but not that the smbd daemon is running) using PING.  I've never had Samba fail in 5 years so I just ping the host,

Second is that I check to see if the Samba share is mounted or not by checking for a specific file that is only available when the share is ***not*** mounted (e.g the readme.smb file is in the directory /media/samba_data),  If you can see the readme.smb file then the share is not mounted.

Lastly, if the ping is false (no ping returns) then notify the user.

In addition you need to add the mount line to the fstab file.  In most cases the user can be the admin (UID 1000) and the group should be a common samba users group.  You control permissions via the group rather than the owner (e.g 775).

If you want to use a common group for your Samba users you need to set the GID bit (SGID) to provide group inheritance for all files and subdirectories (e.g 2775).  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for more info.  On earlier versions of Ubuntu the umask also needs to be set to umask=002 in the /etc/profile file.  This provides file creation permissions of 664 and directory creation permissions of 775.  In the end this is how BSD or OpenSolaris (UNIX) handles permissions, so it is not that strange.

Below is the script:```
#! /bin/bash
#
# A script to mount/unmount a Samba share by an mortal user 
#
# The remote host (Samba Server) = 192.168.1.2
#
# 1. Test to see of the Samba Server is up is up
# 2. Test to confirm that the share is not mounted
# 3. Mount the share
# 4. Notify the user   

SMB_SERVER=192.168.1.2

ping -c 1 "$SMB_SERVER" > /dev/null

if [ "$?" -eq 0 ] ; then
    if [ -f /media/samba_data/readme.smb ]; then
#     We need to>> mount<< the share (via fstab) and inform the user
      mount /media/samba_data
      zenity --info \
                --text="Samba_Data is now available"
    else
#    We need to >>unmount<< the share and inform the user
     umount /media/samba_data

      zenity --info \
                --text="Samba Data is now un-available"
    fi
else
# Failed to find the host via pinging IP address
  zenity --error \
                --text="The Samba Server is unavailable at this time"
fi
```

...and here is the line for the /etc/fstab file```
# Manual mount of Samba Share (samba_data) to /media/samba_data
#
//192.168.1.2/DATA /media/samba_data cifs user,noauto,username=<username>,credentials=/home/<username>/.smbcred,uid=100x,gid=100x,nobrl 0 0
```

You will have to change the variables to match your system so don't cut 'n paste.  ;-)

You might ask; why use Samba on a Linux to Linux share?  The answer is; it started out as a Linux to Windows client share.  That user is long gone, But I have found that there is little or now performance loss compared to NFS (which is also running on the server).  

I have also combined the script and fstab entry into a text file that I have attached.  Please ask questions if you need help.

---

### Post by futo on 2013-01-11
Just a short follow up of the original problem: It's not solved.
There was a new update of the OS from Lacie for the NAS here the 9th of Jan. but this update didn't solve the problem either.

I did something like the work around of bab1 on how to connect to the NAS. I extracted the procedure from this link [http://www.swerdna.net.au/susesambacifs.html](http://www.swerdna.net.au/susesambacifs.html) .

SECURITY RISK!: The following is a public share with a public password! Do not use your passwords this way - everybody will know them then.

After testing the settings for a spontaneous connection I made it permanent in fstab.

I used the following command in Ubuntu 12.04 for a spontaneous connection just to TEST that it works (with a public password):
```
sudo mount -t cifs -o username=myuser,password=mypassw //192.168.1.52/your_share_on_the_nas /the_mountpoint_on_your_pc
```SECURITY RISK: Passwords entered directly in commands will be revealed in the logs! - And can be read by others afterwards!

To open fstab in Ubuntu 12.04 use the following command:
```
sudo gedit /etc/fstab
```Enter the following new line with your own data:
```
//192.168.1.52/public   /mnt/public   cifs username=guest,password=guest,_netdev   0 0
```SECURITY RISK: Again, this is an unsafe way to use the password - you have to HIDE this username and password in a file that's NOT readable by any except of the root!

:popcorn:
SUCCESS!!!: With this configuration I managed to get 80 MB/s in download permanently!!!! - The same speed I had just when I bought the NAS.
This type of connection is much easier to work with in everyday than 'open folder'->'press Network'->'press NAS-name'->'press share-name' etc.

While the above solution works with 80 MB/s the Lacie File Browser only downloads with between 10 and 20 MB/s. - And sftp is running with only 4.7 MB/s.

FAIL: I'm disappointed by the combination Lacie-Samba-Ubuntu. To much work (if you ain't a expert) just to get what the producer promises.

I presume there is a problem with files bigger then 4 GB (???). 
- They are stored on the NAS but they can't be shown with the above method, only with the Lacie File Browser. Any information on this issue?...

TO DO on the 'solution': Find out how to hide/secure a password in a permanent manner.

> **bab1 said:**
> ...  Please ask questions if you need help.

How are the file permissions of /home/<username>/.smbcred? ... How du you ensure that it's not read by other people than the owner and the root?... (That the pw is not misused)

---

### Post by bab1 on 2013-01-11
> **futo said:**
> How are the file permissions of /home/<username>/.smbcred? ... How du you ensure that it's not read by other people than the owner and the root?... (That the pw is not misused)
I assume what you mean is:  What is the format of the .smbcred file?  It is a text file with this information in it```

username=<your_user>
password=<your_pass>
domain=<DOMAIN>

```

The security is that it both a hidden file and second it is only readable readable the user who is the owner (e.g. permissions are 0600).  I advise my users to set the permissions on their home directory to 0600.  Then no other user on the system can see anything in that users home directory.

---

### Post by futo on 2013-01-11
> **bab1 said:**
> I advise my users to set the permissions on their home directory to  0600.  Then no other user on the system can see anything in that users  home directory

Is that done by performing the following command (for the user laila)?: 

```

laila@laila:/home$ ls -l
total 32
drwxr-xr-x 67 laila laila 16384 Jan 11 16:55 laila
drwx------  2 root  root  16384 Oct 19 22:30 lost+found
laila@laila:/home$ sudo chmod 0600 laila
```?

---

### Post by bab1 on 2013-01-11
> **futo said:**
> Is that done by performing the following command (for the user laila)?: 

```
laila@laila:/home$ sudo chmod 0600 laila
```?If the this command ```
pwd
```...returns this```
/home/laila
``` then you would be setting the permissions on the that users home directory.

If you wanted to be absolutely sure you could use this```
sudo chmod 0600 /home/laila
```
...do you understand the difference between relative and absolute paths?

---

### Post by futo on 2013-01-11
> **bab1 said:**
> ...do you understand the difference between relative and absolute paths?

Yes :)

Was just unsure about the execute-bit as had the impression it was necessary to open a folder. But this impression could come from the Lacie File System. So, I just wanted to be sure on the details. :)

Thanks a lot! :D :guitar: :popcorn:

---

### Post by bab1 on 2013-01-11
> **futo said:**
> Yes :)

Was just unsure about the execute-bit as had the impression it was necessary to open a folder. But this impression could come from the Lacie File System. So, I just wanted to be sure on the details. :)

Thanks a lot! :D :guitar: :popcorn:
Actually I went and looked at the users folder and it is 0700.  It's a directory.  My mistake, I was thinking of the files in the home directory which should be 0600.

Sorry :-(

---

### Post by futo on 2013-01-11
> **bab1 said:**
> ```
sudo chmod 0600 /home/laila
``` 

Well, if you only use the graphical interface to walk around in your folders, there is no problem with 0600 as permissions, but when I go to the folder through a terminal, I just got rejected without the execute-bit...

So if you are using terminal in your pc-life, better do it with 0700, as far as I can see, right?

:)

EDIT: Wrote as you answered -  we agreed.

---

### Post by bab1 on 2013-01-11
> **futo said:**
> Well, if you only use the graphical interface to walk around in your folders, there is no problem with 0600 as permissions, but when I go to the folder through a terminal, I just got rejected without the execute-bit...

So if you are using terminal in your pc-life, better do it with 0700, as far as I can see, right?

:)

Yes. I live in the terminal The perms 0700 work for both terminal and Nautilus.

---

### Post by futo on 2013-01-11
> **bab1 said:**
> ...Please ask questions if you need help.

:)

I have some trouble with hiding the username and password. I'm testing the commands in the terminal as this seems quicker for me than rebooting all the time.

```
laila@laila:~$ sudo mount -t cifs //192.168.1.52/backup /mnt/backup -o username=chief,password=test
laila@laila:~$ sudo umount /mnt/backup/
```When I use a command with the username and password inside, this works fine and the connection is established very quickly, but when I try to use the hidden file this comes out:

```
laila@laila:~$ sudo mount -t cifs //192.168.1.52/backup /mnt/backup -o credentials=/home/laila/.nascred
mount: wrong fs type, bad option, bad superblock on //192.168.1.52/backup,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```The content of the file '.nascred' is this:
```
username=chief
password=test
domain=Workgroup
```It doesn't mater if I have the 'domain=Workgroup'-line with or not, the result is the same. Either with everything in one line. I've even tried the 'workgroup with small 'w'.

Some metadata:
```
laila@laila:~$ ls -l .nascred
-rwxr----- 1 laila laila 46 Jan 11 20:00 .nascred

```dmesg | tail returns this:
```
laila@laila:~$ dmesg | tail
[ 2340.322030] CIFS VFS: No username specified
[ 2395.135947] CIFS VFS: No username specified
[ 2403.506337] CIFS VFS: No username specified
[ 2437.056216] CIFS VFS: No username specified
[ 2454.454478] CIFS VFS: No username specified
[ 2639.538100] CIFS VFS: No username specified
[ 2932.428714] CIFS VFS: No username specified
[ 3076.612487] CIFS VFS: No username specified
[ 3089.064885] CIFS VFS: No username specified
[ 3308.769153] CIFS VFS: No username specified
```Does anybody have a hint?...

---

### Post by bab1 on 2013-01-11
> **futo said:**
> :)

I have some trouble with hiding the username and password. I'm testing the commands in the terminal as this seems quicker for me than rebooting all the time.

```
laila@laila:~$ sudo mount -t cifs //192.168.1.52/backup /mnt/backup -o username=chief,password=test
laila@laila:~$ sudo umount /mnt/backup/
```When I use a command with the username and password inside, this works fine and the connection is established very quickly, but when I try to use the hidden file this comes out:

```
laila@laila:~$ sudo mount -t cifs //192.168.1.52/backup /mnt/backup -o credentials=/home/laila/.nascred
mount: wrong fs type, bad option, bad superblock on //192.168.1.52/backup,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```The content of the file '.nascred' is this:
```
username=chief
password=test
domain=Workgroup
```It doesn't mater if I have the 'domain=Workgroup'-line with or not, the result is the same. Either with everything in one line. I've even tried the 'workgroup with small 'w'.

Some metadata:
```
laila@laila:~$ ls -l .nascred
-rwxr----- 1 laila laila 46 Jan 11 20:00 .nascred

```dmesg | tail returns this:
```
laila@laila:~$ dmesg | tail
[ 2340.322030] CIFS VFS: No username specified
[ 2395.135947] CIFS VFS: No username specified
[ 2403.506337] CIFS VFS: No username specified
[ 2437.056216] CIFS VFS: No username specified
[ 2454.454478] CIFS VFS: No username specified
[ 2639.538100] CIFS VFS: No username specified
[ 2932.428714] CIFS VFS: No username specified
[ 3076.612487] CIFS VFS: No username specified
[ 3089.064885] CIFS VFS: No username specified
[ 3308.769153] CIFS VFS: No username specified
```Does anybody have a hint?...
This usually happens when you don't have the package cifs-utils installed (Ubuntu > 10.10).  This package used to be named smbfs (Ubuntu < 10.04).

What version of Ubuntu are you using?  Is this package installed on your system?

---

### Post by futo on 2013-01-11
> **bab1 said:**
> This usually happens when you don't have the package cifs-utils installed (Ubuntu > 10.10). This package used to be named smbfs (Ubuntu < 10.04).

With the hammer on the nail! :D Just installed it and it works! - Great! Smashing! Capital!!

:guitar:

It's Ubuntu 12.04 - And the package wasn't installed by default! :)

Tested the download, and it runs with 75 to 80 MB/s. Very nice! After, all in all, one week of more than full time work I have a solution that is worth living with. ;) - Wonderful! :D

:popcorn:

A "traditional Samba" connection is still just running below 5 MB/s even thou everything else is the same (hardware and software, computer, NAS, router etc.). Somehow I'm still curious why it is so. If anybody should come up with some guesses, I would definitely be interested.

---

### Post by bab1 on 2013-01-11
> **futo said:**
> With the hammer on the nail! :D Just installed it and it works! - Great! Smashing! Capital!!

:guitar:

It's Ubuntu 12.04 - And the package wasn't installed by default! :)

Tested the download, and it runs with 75 to 80 MB/s. Very nice! After, all in all, one week of more than full time work I have a solution that is worth living with. ;) - Wonderful! :D

:popcorn:

A "traditional Samba" connection is still just running below 5 MB/s even thou everything else is the same (hardware and software, computer, NAS, router etc.). Somehow I'm still curious why it is so. If anybody should come up with some guesses, I would definitely be interested.
Glad to see you have had success.

Everything will be a guess unless you look at the source code.  What you are calling a traditional Samba connection is really Nautilus' version of mounting the SMB/CIFS share.  There is no specific way of creating these routines.  The RFC only states the results desired.  It's up to the developer to write routines that meet the goal.  This of course creates interoperability problems and differences in performance right off the bat.  The cifs-utils package (specifically the mount.cifs routine) may not be used by Gnome devs (Nautilus) at all.  There is no reason that they couldn't write there own mount routines.  An example of this is OpenSolaris (SUN/Oracle).  They have a completely separate CIFS package for their OS.  No Samba needed.  Apple has done the same thing with their latest version of OSX.

All of this is "navel gazing" anyway.  I find a lot of lint but not much solid knowledge.   :-)

---

### Post by futo on 2013-01-11
Just enough information to have an idea. I've had a great experience with your help! Thanks a lot bab1! :D

---

