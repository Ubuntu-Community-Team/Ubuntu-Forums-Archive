---
title: "Slow Samba performance on Ubuntu 10.10"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by vishnumrao on 2010-11-03
I installed Maverick on my t60 laptop after wiping out Lucid. I notice that the samba performance is degraded significantly.

My NAS has two Samba Shares and file copy on 10.04 was about 10-15 MB/s over wired LAN connection. But now on 10.10, I see 1.8-2 MB/s speeds over the same LAN connection. As an experiment, I tried the 10.04 & 10.10 live cd on my desktop and tried file copy over wired connection. Same speeds as above.

Anyone else seen this problem? Any solutions?

---

### Post by swedski on 2010-11-05
Hello 
I have the same exact problem.  I upgrade my comhem internet to 100 service and my 10.04 wireless connection was around 25mb.  I then upgrade to 10.10 and am almost back to the identical configuration and yet my speeds are 1.5-2 mb.  My xp machine sitting next to this laptop comes in at 45mb wireless, so I am sure its not the router.
Any suggestions?

---

### Post by ndxtg on 2010-11-12
I too have this same problem on 10.10 (clean install)

Wireless Speed = 37Mbps

I download files at 10Mbps from the internet and access to LAN samba server at same time. The speed is ridiculous slow, cannot even watch a avi movie properly (the resolution of the movie is just 600x400px or so)

I used to do this in 9.04 and no problem at all.

---

### Post by steven6282 on 2010-11-12
I to am getting some pretty pathetic performance with Samba shares on ubuntu 10.10.

I came here hoping to get some fast answers, but considering the first post is 1 week old and there are no answers in this post I'm guessing that is not going to happen.

I'm building a NAS, my first one that I'm building myself and have been trying various solutions to see what gives me the best performance and reliability.

On FreeNAS using a ZFS file system and a Samba share, I was getting write speeds over the network of 65 MB/s to 75 MB/s.  That was descent for what I paid to build this NAS, but I wanted to see if I could etch out a little more speed.  Based on some other reviews that I read, Ubuntu was supposed to be faster than FreeNAS, and I also like the fact that I'm more familiar with Ubuntu since I'm running it on another web server box.  But I am by no means a linux guru, have just started using linux more in the past 6 months.

So anyway, I set up Ubunutu, did the software raid with a raid 5 setup, waited the 2 days for it to build the array (ugh), and then proceeded to start testing.

I've tried changing a lot of settings that I've read about in different places on the net, but the best speed I can get on this setup is 42 MB/s over the network.  That is pretty horrible compared to the speeds I was getting on FreeNAS.  

But even the write speeds directly to the raid array are worse.  On FreeNAS writing to the ZFS array I was getting 110 MB/s to 120 MB/s.  On Ubuntu, writing to the raid array I'm getting 90 MB/s to 100 MB/s.  Pretty pathetic speeds for a software raid 5 setup.  I knew ZFS would be slower than average due to it's integrity checks and higher memory usage, but why would ubuntu's software raid be so slow?

Anyway, hopefully someone can give me some advice soon.  I've got to get this NAS completed and in place this weekend, and if I can't figure out how to get the performance of Ubuntu and Samba share up to at least equal to the performance I had on FreeNAS and ZFS, I'll have to go back to using it.  I just really don't like FreeBSD :(

---

### Post by qva5 on 2011-01-06
Uncommenting those two lines in **/etc/samba/smb.conf** solved issue for me.

SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY

---

### Post by ottsm on 2011-01-06
I have the same issue, I did a clean install of 10.10 on a Dell Vostro 1500, it had XP before so I can't say what 10.04 would have done.

I have a Dlink DNS-323 with two 2T hard drives that I use for everything.  I have a spare 2T hard drive that I swap out and have used Fun_plug to setup an auto-backup every day.

When I try to access it with the Dell across a hard wire it works fine.

When I use the built in wireless N card to access the internet it is super fast and fine.

When I use the wireless to access my DNS-323 it crawls to the point it takes a entire minute just to load the directory.  XP accessed the DNS-323 just fine.

I tried editing the Samba file and un-commenting what was mentioned in the above link.  This did not fix my problem.

SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY

I hate windows and have switched over to linux on a lot of my machines, but, if I can't access all my photo's and movies I have on my DNS, thin I'm going to be forced to try 10.04 or go back to XP.

For me it looks like a driver issue versus a samba issue.  Although it works fine access the internet.

---

### Post by ottsm on 2011-01-07
OK, I setup the DNS 323 for NFS file transfer and it's still slow.  Not a SAMBA problem.

---

### Post by qva5 on 2011-01-08
> **ottsm said:**
>  
I tried editing the Samba file and un-commenting what was mentioned in the above link.  This did not fix my problem.

SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY


Try writing it in one line, ie.

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

---

### Post by qva5 on 2011-01-08
In fact below syntax is invalid (run testparm). 
[INDENT]SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY
[/INDENT]Therefore it seems that in my case was enough.
[INDENT]socket options = TCP_NODELAY
[/INDENT]

---

### Post by nelomh on 2011-01-09
i have a new ubuntu 10.10 install. that installed samba automatic when i shared a folder.

copy 50 mg to the machine or from the machine takes me almost 10 minutes. 

does any one had fixed this.?

---

### Post by steelsteel! on 2011-01-11
> **ottsm said:**
>  I tried editing the Samba file and un-commenting what was mentioned in the above link.  This did not fix my problem.

SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY



Same problem for me. Still existing. Exhausting.

---

### Post by avpap on 2011-01-12
Same problem here, slow transfer speed 3.0 MB/S in gigabit lan. What's wrong?

---

### Post by snakebob on 2011-01-14
Damn it...It's same to me.
 
I am sure I remeber that samba donwloading transfer speed was around 10Mb/s
in Ubuntu 9.04 and 10.04
 
But, now it's just around 3Mb/s in Ubuntu 10.10
 
What happend in Ubuntu team? It's getting more annoying for searching & tunning after new version of Ubuntu install.
 
Now, Ubuntu version is 10.10............
 
Anyway, please someone help this...

---

### Post by snakebob on 2011-01-14
> **qva5 said:**
> Try writing it in one line, ie.

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

For me above setting works!! 
thanks
I solved this !!!

---

### Post by qva5 on 2011-01-15
> **snakebob said:**
> Damn it...It's same to me.
 
I am sure I remeber that samba donwloading transfer speed was around 10Mb/s
in Ubuntu 9.04 and 10.04
 
But, now it's just around 3Mb/s in Ubuntu 10.10
 

Hi,
I have few questions regarding downloading speed you reported. I would really appreciate if you could give me some more details about it.

On what environment are you using samba? Is it mixture of linux/windows machines? Are transfering data through wireless or wired network?

---

### Post by ubuking on 2011-01-15
I have the same problem. I am using a dual boot 10.10 Meerkat / Windows 7 desktop machine, and copying to my NAS using windows I can reach 50 MB/s while copying the same file under Ubuntu speed only reaches 9MB/s at max. This shows that the problem really is in Ubuntu.
I have updated samba.conf as suggested but this did not do anything (visible) for me. I have added the parameter rsize=130048 and wsize=130048 to my CIFS mount command and that increased speed in Ubuntu to 11MB/s, still disappointing but nontheless slight improvement. 

So the /etc/fstab line looks like:
//NAS/Share /home/user/NAS/Share cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777,rsize=130048,wsize=130048 0 0   

Any other tweaks to increase speed?

---

### Post by ubuking on 2011-01-15
I have not solved the Samba issue yet, and still remain interested in a structural solution. 

However, I have installed NFS Server on my NAS, exported the shares in /etc/exports and have mounted the shares in 10.10 using nfs. The speed in copying files between shares and desktop has now increased to some 60 MB/s (on Gigabit LAN), similar to speed on W7, Works for me.

---

### Post by Qowjgej on 2011-01-15
I've run into the same problem. Getting a maximum of 7 megabytes per second using 10.10 64 bit. Tried two different gigabit interfaces using different drivers (forcedeth and r8169) with similar results.

---

### Post by snakebob on 2011-01-16
> **qva5 said:**
> Hi,
I have few questions regarding downloading speed you reported. I would really appreciate if you could give me some more details about it.
 
On what environment are you using samba? Is it mixture of linux/windows machines? Are transfering data through wireless or wired network?
 
I am using samba for Ubuntu file server.
I tested it between Windows7 and Ubuntu in Wired network.
 
The download speed was data transfering speed from Ubuntu to Windows7 in 100Mpbs wired network with over big files ( over 500Mbyes )

---

### Post by Qowjgej on 2011-01-16
I did some more testing. 

First I configured a SBM client on another Ubuntu 10.10 box and tested over a wired network, poor performance was the result, just a few megabytes per second.

Next I configured NFS on a Windows 7 client and mounted a file system from the server over a 300 megabit wireless network. The read performance was even worse than using SMB on the same machine.

Finally I SMB mounted a file system through the loopback interface on the server, Testing this showed good read performance (about 200 megabytes per second) which makes me think the problem is not samba, but likely to be a driver issue of some sort.

A bit of trawling through the internet shows many woeful stories of poor samba read performance and ubuntu going back several years. How representative these are I don't know.

I wonder if this problem is related to specific gigabit chip sets? One wonders how a problem like this could go unobserved and unfixed if it was widespread.

---

### Post by lunatico on 2011-01-17
I'm also having this problem. On that same machine it used to work fine on 10.04 and 9.10.
I tried changing the
```
SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY
```
options but that makes no difference.

This is pretty bad... Anyone has a solution?

---

### Post by lunatico on 2011-01-17
One more thing, I don't think it has anything to do with network card or drivers. I had an integrated Broadcom NetXtreme gigabit card, and I popped in a new Intel 82571EB gigabit card and it is the same with both cards.

---

### Post by andynz22 on 2011-01-17
Same issue here with transferring a file from an Ubuntu 10.10 to 9.04 Ubunutu server samba share.  Tried both on local machine:

[I]So the /etc/fstab line looks like:
//NAS/Share /home/user/NAS/Share cifs (my login and password),iocharset=utf8,file_mode=0777,dir_   mode=0777,rsize=130048,wsize=130048 0[/I] 0   

&

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

but still stuck at 2.5Mb/sec where as I normally get 10-11.  Booting into Windows 7 and transferring the same file gives me standard 11-12Mb/sec.

Cheers
Andy

---

### Post by qva5 on 2011-01-19
Do you think this issue matured enough to consider it as a bug and register it in launchpad?

---

### Post by lunatico on 2011-01-20
> **qva5 said:**
> Do you think this issue matured enough to consider it as a bug and register it in launchpad?

I'd say so... as it is it's just unusable.

---

### Post by Viciou§ on 2011-01-29
Just wondering, those of you that have slow transfer rates under ubuntu, do you have an nVidia card and proprietary drivers?

When I removed my GT210 card from my ubuntu box transfer rates jumped from ~3-4 Mb/s to 8-9 Mb/s over a wireless n network.

---

### Post by andynz22 on 2011-01-29
Both pc's I have this problem on are ATI cards.  Haven't tried on an Nvidia pc.

---

### Post by lunatico on 2011-01-30
> **Viciou§ said:**
> Just wondering, those of you that have slow transfer rates under ubuntu, do you have an nVidia card and proprietary drivers?

When I removed my GT210 card from my ubuntu box transfer rates jumped from ~3-4 Mb/s to 8-9 Mb/s over a wireless n network.

Not me. Some built-in Intel card... I don't see the connection between the video card and transfer rates... and if anything I would expect having a good card would make things better because there's more CPU available for other things... weird indeed. Try sticking it in again and see if the problem really comes back.

---

### Post by vdr60 on 2011-01-30
I have the same slow performances, it means max 3.3MB/sec
My configuration Hw is this:
1- Interface card is a MARVELL 88E8056 PCI-E Gigabit Ethernet
2- WRT610N Linksys router
3- To the router is attacched a NAS Iomega StorCenter Pro ix4 (with a Gigabit port...)

My **smb.cnf** is this:
```

[global]
   workgroup = MSHOME
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
**socket options = TCP_NODELAY SO_RCVBUF=32768 SO_SNDBUF=32768**
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

```

I tried many changes to *socket options* end *MTU* also, but with no results

---

### Post by kenmo on 2011-02-24
I'm having this issue as well..  I have a 1 gb network of 3 Windows 7 Home Premium  computers and 1 Ubuntu 10.10. Copying files between Windows 7 computers is around 60 MB. Copying from anyone of the Windows to the Ubuntu computer the best speed I get is 20MB...

Tried different 1gb nics in the Ubuntu but no performance gains....

Googling found this thread, so I'll post my query here...

PS: this is a 1gb wired network using an 1 gb unmanaged switch...

---

### Post by mbogevik on 2011-03-23
> **ottsm said:**
> 
SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY


Enabling this code in Samba also works for my Ubuntu 10.10-64 server.  I get close to 1000Mbit, but after a few seconds speed gets slower (770M file).  I think this is caused by a relatively slow HDD that do not handle the speed.  Changing above values from 8192 to 16384 seems to give me top speed a bit longer.
Thanks for tip !

---

### Post by sirtcp on 2011-04-19
have same issue non of the tweak helps. any idea i am stuck right now. i am learning Linux but facing error of those type may make my concept worst :P

---

### Post by bobwyajnr on 2011-05-10
> **sirtcp said:**
> have same issue non of the tweak helps. any idea i am stuck right now. i am learning Linux but facing error of those type may make my concept worst :P

Hmmm, yes how's about something that actually works!

I can stream stutter-free 1080p video and get 30 Mbyte/sec transfer rates (over Gb ethernet - with a switch that doesn't support Jumbo frames) Ubuntu 10.10 <-> 10.10. NB server machine has an updated 2.6.38 kernel (from a ppa - not sure if this is necessary). The transfer ~6Gb test file was *read* from an NTFS partition (using the latest NTFS-3G driver compiled from source). Using the **smb:** networking protocol (in XBMC) glitches constantly with even SD content streaming - requiring a lengthy re-buffering process (~5 seconds).

I am using **mount.cifs** to create local mounts of Samba shares and not the **smb:** mechanism which is decidedly flaky at the best of times. For ultra reliability I would recommend the use of a static IP address for your Samba server machine(s) (most routers can be setup to assign these by MAC address of your machines/devices). Large read/ write buffers are specified for the remote Samba shares to be mounted.

On your server machine(s) type:
```
gksu gedit /etc/modprobe.d/modprobe.conf
```
or for Kubuntu users:
```
kdesudo kate /etc/modprobe.d/modprobe.conf
```
Add this one line to the (hopefully/normally empty) file:
```
options cifs CIFSMaxBufSize=130048
```



A BASH script for mounting remote shares (assumes you are authenticating by **user** and **guest** user access is allowed):
```
#!/bin/bash

for cifs_share in "**SHARE NAME 1**" "**SHARE NAME 2**"
do
        sudo mkdir "/mnt/${cifs_share}/"
        sudo mount.cifs "//192.168.1.1/${cifs_share}/" "/mnt/${cifs_share}/" --verbose -o user='guest',password='',domain='WORKGROUP',ro,exec,noperm,uid=**UNIX USERNAME @CLIENT MACHINE**,gid=**UNIX GROUPNAME @CLIENT MACHINE**,rsize=130048,wsize=130048,directio
done

```
Ok so I won't win any awards for my BASH scripting skills! Replace the ****...**** items with something sensible. I put my mounts in **/mnt/** - to stop them getting messed up with Ubuntu removable media mounts. The script will ask for your **root** user password when starting.

If you want read/write user access to the shares put in your Samba Servers (share) username and password in (replacing: **guest**, and the blank password). Replace the **mount.cifs** mount option **ro** with **rw**. For (minimal) security reasons I would recommend giving the script **root** only access:
```
sudo chown root:root **SCRIPT NAME**
sudo chmod 700 **SCRIPT NAME**
```
Any security boffins point out a way to not use a plain text password in this script file?? :-k


Also in my **/etc/samba/smb.conf** file:
```
socket options = TCP_NODELAY SO_RCVBUF=65536 SO_SNDBUF=65536

```
Don't trust me on this - it goes against all the guides! (Lower values are considered optimal! Stick with 8192!) I did find a graph somewhere on the interwebs - once - with different values of the write and read buffers vs. throughput... :popcorn:

I am no networking expert - so Caveat Emptor!! :guitar:

Good luck!
Bob

---

### Post by futo on 2013-01-06
[SIZE=1]Same problem with 12.04 and Samba getting files from a NAS from Lacie.

Describing (and showing) the problem here also: [http://youtu.be/cSZ9X9y9_hc](http://youtu.be/cSZ9X9y9_hc)

             Have tried to add the&#65279; following two lines&#65279; ([/SIZE][SIZE=1][SIZE=1]placed under 'Misc'[SIZE=1], [/SIZE][/SIZE]all 3 combinations)&#65279; in /etc/samba/smb.conf:
           SO_RCVBUF=8192 SO_SNDBUF=8192
            socket options = TCP_NODELAY 

- First when I wrote them in ONE LINE, like this, it worked a little better:
socket options = TCP_NODELAY&#65279; SO_RCVBUF=8192 SO_SNDBUF=8192

- The speed jumped from 1MB or less to around 3 MB. Nice, but still not anything like 1000Mb/s


Checked eth0 with mii-tool and ethtool:

 mii-tool says half duplex and ethtool says full duplex. 
Tried to  change the setting 'in' mii-tool, but that didn't change anything. 
Don't  know&#65279; why the different results and what to try at this point to manage  these two different results.
            
I'll continue to search for a solution ... given no other options ... xD

------------------
[SIZE=1]Using testparm didn'[SIZE=1]t reveal anything interesting, as far as I can see:

[/SIZE][/SIZE] ```
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
```[/SIZE]

---

### Post by futo on 2013-01-06
[SIZE=1]Here the formulation of the problem from [SIZE=1]the YouTube page:[/SIZE]

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
[/SIZE]

---

### Post by jmate24 on 2013-01-06
Ubuntu 10.10 is End Of Life try upgrading to 12.04 or 12.10.

---

### Post by futo on 2013-01-06
Thanks, that helped a lot! :D ...
- oh, no, sorry, I just saw I'm already on 12.04 Long Term Support - and the problem persists. Well don't aks me to tell my opinion on 12.04 compared to 10.04, because that belongs somewhere else in different places  with all it's problems.

And my laptop is with the newest i7 3840qm 2.8 GHz for mobile units, ssd & ordinary hd, r8168 eth. card and a lot of other fine stuff.

:) More suggestions?....

Came on the idea to try a sftp session to the NAS from the 12.04-machine. Speed is around 4.7 MB/s.

Could this exclude Samba as reason?... Is it more in eth0 in generel I have to look?....

:)

> **jmate24 said:**
> Ubuntu 10.10 is End Of Life try upgrading to 12.04 or 12.10.

- Is it better if I moved my questions to the 12.04-part of this forum?....

---

### Post by overdrank on 2013-01-06
Hi and please start a new thread for your issues. Thread closed

---

