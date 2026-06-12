---
title: "Samba does not reach Windows"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by yc2 on 2009-04-24
I have been upgrading since Feisty and I am very satisfied. I just upgraded to Jaunty and all seems to be well.

However, I have Samba problems. (I am not sure if it is the upgrade or if it is just that I haven't used Samba for a while.)

I usually only click (Gnome) Places > network to reach my Windows XP computer in my small home network.

When I do this now, I first see correctly my Windows group name, but when I click that icon I get

"Failure to retrieve share file list from server"

(Hardware seems OK, since I can reach across to my Windows computer if I start the *Windows-system* on the same computer as the Ubuntusystem - it is dual boot)

Please help me reach my other computer :)

I just followed this simple and good guide, but to no avail
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

(I thought when it came to reaching Windows from Ubuntu it should not be necessary to do any setup.)

EDIT:
The situation has improved a little: I can now reach Ubuntu from Windows, but this is less convenient for me. I still have problems reaching Windows XP from my Ubuntu Desktop.

Thanks for any help.

---

### Post by Another Monkey on 2009-04-24
I had Samba blow up in a bad way during the upgrade.  I found that forcing a full re-install of all Samba modules and then a reboot fixed some of the issues.  (Back-up your smb.conf first)

I also installed system-samba-config and used that to check my settings.  They seemed fine, I changed nothing.  

After doing this I can browse from Jaunty to the Windows network, open shares on Windows machines etc.  Browsing from Windows to Linux still does not work though.

Linux can't even navigate tp istelf, I just get "Unable to retrieve share list from server".

How did you get Windows -> Ubuntu working again?

Is it just me being stupid, or is setting Samba up a bit like black magic?

---

### Post by weather15 on 2009-04-24
I think it is a bug with 9.04 because I just did a fresh install last night and I am having this very same problem. How ever it does work without a problem on ubuntu 8.10 why?

---

### Post by weather15 on 2009-04-24
After reinstalling samba I still get the same error how ever I can now see the workgroup but can't access it. Also I have a network printer that is shared over the windows network but I also can't access it.

---

### Post by hvralpha on 2009-04-24
Same result on Kubuntu with 9.04. When samba is not installed, DFolphin can actually see the linux shares. The moment anything is shared with samba, nothing works although it is shown as shares.

Must be a bug and will report

---

### Post by Another Monkey on 2009-04-24
It's not me being stupid?  :eek:
Now there's a first.....

If there's anything I can do to help, let me know (logfiles, whatever)

I think I'll keep 8.10 on my other boxes for a while longer!

---

### Post by Deamos on 2009-04-24
Same issues here.  It gets as far as showing the Workgroup and then does not allow me to go any deeper.  I can connect manually by IP address, however it does not recognize the NETBIOS Names.

---

### Post by yc2 on 2009-04-24
Thanks a lot for the support, guys. It always feels good to come here and meet all the knowledgable, friendly, humorous, helpful people. I am sorry to say that I cannot be very logical on this one. What has made the connection start working a little better was maybe reinstallation and update.

I also think maybe I was careless during the Jaunty upgrade. ("install the package maintainers version of smb.conf" - I chose yes), maybe also the upgrade process reset the Ubuntu shared files access-rights to a higher level. At first I could only read Ubuntu files from Windows.

Now it is possible to mount the Windows-share ("coprde") in Ubuntu:
sudo mount -t smbfs //192.168.1.201/coprde /mnt/yl_tst

(Which was not possible before. I agree with several of your hints. - Especially the ones about black magic and a possible samba 9.04 bug, that maybe has been at least partly cured by update? :)

But at first even this did not work. I could only access the Windows-share by writing straight into the Nautilus addresswindow:
smb://192.168.1.201/coprde/
(NetBIOS name could not be used.)

The Gnome method - clicking the network icon still gives the same error as I described in my first post. It gets the group-name right but nothing more after that.

It seems I can reach the Ubuntu computer from the Windows computer for both reading and writing now. Even without entering a password! I haven't seen that before! (I didn't do anything in the Windows machine. I just click "my network locations" and it just opens for read/write without entering the Ubuntu pwd!) I tried removing the "public=yes" in smb.conf, but that only made the folder inaccessible. I still haven't found out how a password is asked for. But it is not a big issue in my situation now. I have used the smbpasswd of course.

I also agree with the "staying with the LTS-version" or at least "not upgrade too quickly" -thinking. I have continuosly upgraded since Feisty and I am not sure this is the right way. Maybe one should save the package information (dpkg) and home-partition and start over some now and then?

Sorry for not being able to be very specific. I have spent long hours upgrading over a slow connection and my mind is even duller than usual.

Thanks for all advice and support.

---

### Post by sl0t3g on 2009-04-24
Having the same type of problem.  I am able to access windows shares via Nautilus; however, I can't add SAMBA Printers.

I access Printing under System -> Administration and try to Add a printer via SAMBA, a dialog box pops up with a list of all the computers on the network, when i click the arrow to get a list of available devices for the computer, both windows close without warning, no errors.  :confused:

however i am able to set it up with smb://192.168.x.x/PrinterName  

bah

---

### Post by weather15 on 2009-04-24
I happen to think that this is a bug with ubuntu 9.04 because samba works fine on ubuntu 8.10. I have tried to re-install samba returning the same results. Also printers do not work unless the printer is directly connected to the network. There for I believe that this is a bug with ubuntu 9.04.

---

### Post by pearl298 on 2009-04-24
I had the same problem: I have 2 Linux machines, two Win XP machines, and one Vista machine on the LAN.
All of the "non-Ubuntu" machines could "see" and access my "Ubuntu 9.04" machine, but IT could only detect the other Linux machine and not the three Windows machines!

Sadly the traditional "Windows" solution worked: power down the Ubuntu machine for 30 seconds and restart! 

Everything then works fine. SIgh.

I think I am going to wait for a week or so before I upgrade my second Linux machine to Ubuntu 9.04 LOL

UPDATE

This seems to come and go! 

I could see all my Windows machines this morning, now they are gone again! 

I can still access them by IP address or by smb://xyz/

---

### Post by weather15 on 2009-04-24
I think thats a case of being lucky LOL! I have just reinstalled ubuntu 9.04 this does not fix the problem also have re-installed samba. Maybe one of the other samba packages needs to be present? Also I tried going to places connect to server windows share and this also doesn't work.

---

### Post by Iowan on 2009-04-24
Samba seems to have "changed" with Hardy.  If I remember correctly, that's when GVFS started "helping". 

BTW, **smbfs** is deprecated in favor of **cifs**. [Here]("http://ubuntuforums.org/showthread.php?t=288534") is a How-To for mounting **cifs**.

---

### Post by Linux.man on 2009-04-24
Hi, I install Ubuntu 9.04 with the same problem.

I believe that I found the solution.

Please try this...

```
sudo apt-get install fusesmb
```

Reboot and tell me.

---

### Post by weather15 on 2009-04-25
No installing that package does not work.

---

### Post by Another Monkey on 2009-04-25
At home I have 8.10 Intrepid in a VirtualBox image, I made totally sure Samba was working (Ubuntu -> Ubuntu, Ubuntu -> Windows and Windows -> Ubuntu).  All was fine, no warnings or error messages in the logs.

I took a snapshot and did the upgrade to 9.04 Jaunty.

Windows -> Ubuntu works.  My XPsp3 host is more than happy to access the Samba shares.

9.04 Jaunty won't even open the network in Nautilus.  If I use the IP address, it will let me see the Windows shares and access them, so something is working.  I am also now seeing errors in the logs.  From /var/loga/samba/log.smbd:
```
[2009/04/25 17:32:56,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/04/25 17:32:56,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/04/25 17:44:18,  0] lib/util_sock.c:get_peer_addr_internal(1676)
  getpeername failed. Error was Transport endpoint is not connected
```

And from /var/loga/samba/log.winbind-idmap:
```
[2009/04/25 17:44:18,  0] winbindd/idmap.c:idmap_alloc_init(587)
  ERROR: Initialization failed for alloc backend, deferred!
[2009/04/25 17:44:18,  1] winbindd/idmap_tdb.c:idmap_tdb_alloc_init(341)
  idmap uid or idmap gid missing
[2009/04/25 17:44:18,  0] winbindd/idmap.c:idmap_alloc_init(587)
  ERROR: Initialization failed for alloc backend, deferred!
[2009/04/25 17:44:20,  1] winbindd/idmap_tdb.c:idmap_tdb_alloc_init(341)
  idmap uid or idmap gid missing
[2009/04/25 17:44:20,  0] winbindd/idmap.c:idmap_alloc_init(587)
  ERROR: Initialization failed for alloc backend, deferred!
```
I've seen this before, but being no expert I have no idea how to fix it.  All I know is that it means Samba is broken.

"testparm" gave me this:
```
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Pictures]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = MGROUP
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Pictures]
	path = /home/monkey/Pictures
	valid users = monkey
	read only = No
```

SO there is deffo something about Samba on Jaunty that is goosed.  Does anyone have Samba working on Jaunty?

---

### Post by Another Monkey on 2009-04-25
Doing a bit more reading, it looks like something has changed in Samba.  [http://blog.loftninjas.org/2009/03/09/sambawinbind-331-on-ubuntu-jaunty/](http://blog.loftninjas.org/2009/03/09/sambawinbind-331-on-ubuntu-jaunty/)

I think what I'll try and do is get a hold of the default smb.conf for Jaunty and do a manual compare (the compare during the install is, frankly, useless and I just retained my working file).

I took a copy of the file that was working on Intrepid, did a full reinstall of Samba and allowed it to overwrite smb.conf.  There were a few changes, but nothing that seemed important.  I then copied over my user and share info and restarted Samba.  The result was the same as before - WIndows -> Ubuntu is fine, Ubuntu -> Windows is just not happening.

I am seeing this in /var/loga/samba/log.smbd:
```
[2009/04/25 18:31:55,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/04/25 18:33:19,  0] lib/util_sock.c:get_peer_addr_internal(1676)
  getpeername failed. Error was Transport endpoint is not connected
```

I followed this [http://kbase.redhat.com/faq/docs/DOC-2339;jsessionid=B3427A500A9C9E95BFCF8054D027B7C7.ab46478d](http://kbase.redhat.com/faq/docs/DOC-2339;jsessionid=B3427A500A9C9E95BFCF8054D027B7C7.ab46478d) and it was no help either, although that error appears to have gone away.

Whatever the sodding problem is, it is restricted to listing the contents of the workgroup/domain.  Going direct to the other PC by name (so NETBIOS etc don't seem to be an issue) or IP works fine.  This is all very strange.

---

### Post by Linux.man on 2009-04-25
Work for me !!!

[IMG]http://farm4.static.flickr.com/3322/3473960574_ca38e9eb86.jpg[/IMG]

[http://www.flickr.com/photos/linuxman/3473960574/](http://www.flickr.com/photos/linuxman/3473960574/)

---

### Post by Another Monkey on 2009-04-25
Hi Linux.man - was yours a fresh install or an upgrade?

---

### Post by Linux.man on 2009-04-25
It's a fresh install.

i like try the ext4 filesystem.

---

### Post by Another Monkey on 2009-04-25
That might be the difference, I think it is people with upgrades that are suffering.

Seems a pretty critial bug to release with though, if it is a bug.

---

### Post by jed4czar on 2009-04-25
[SIZE="4"]I had fresh install with similar symptoms - Window closes unexpectedly on browsing to shared printer. It seems to be a function of browsing rather than SAMBA itself.

I just manually typed the path / URI of the SMB printer... i.e. for me it is: 

*smb://mshome/your-9638769703/Printer2*

Just find the path in Nautilus (via network) and append the printer share-name from the WinBox {eg *Printer2*}[/SIZE]

---

### Post by Another Monkey on 2009-04-26
> Just find the path in Nautilus (via network)
That the problem the original poster and I are having, this does not work in Jaunty.

---

### Post by Another Monkey on 2009-04-26
Yet more fiddling and I think I am now seeing what is causing the fault.

I brought up Firestarter and tried "smbtree" in the terminal.  Whenever I issue this command, I see a bunch of hits in the Firestarter console.  Ports 6646, 35911, 35993, 44101 and 56837.

I think one of those is my McAfee firewall on Windows, the others I think are responses to Samba on differnt ports and are getting blocked.  When I tell Firestarter to drop the firewall, it works.

As this was all working in 8.10, I can only assume that Jaunty has done something to iptables and is now blocking stuff.

I am not able to check on the other box which is also failing.

yc2, are you seeing anything similar?

---

### Post by Another Monkey on 2009-04-26
And...***solved***!  For me anyway....

For me it was the response to Samba being blocked that was causing the issue (I will need to check on the other PC, but it does not have a firewall IIRC).  And I am damned sure I was not seeing the blocked response yesterday, but I had been fiddling about with smb.conf (see earlier posts) so maybe that changed something.

I followed post #2 in this thread by "dsmalley" [http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542)

Very, very frustrating but it is working at the moment.  I'll keep an eye on it and see what happens.  Hope this is of some help to you yc2.

---

### Post by yc2 on 2009-04-26
Thanks for many good suggestions.

I think the problems may the netBIOS names. (Like suggested above.)

I entered the Win box into /etc/hosts:

192.168.1.201 yl-portable-2

```
 sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...   

```

I can now click my way in gnome:
locations > network > ... into my Win box.


```
~$ nbtscan 192.168.1.0/24
Doing NBT name scan for addresses from 192.168.1.0/24

IP address       NetBIOS Name     Server    User             MAC address      
------------------------------------------------------------------------------
192.168.1.0	Sendto failed: Permission denied
192.168.1.101    UBUNTU           <server>  UBUNTU           00:00:00:00:00:00
192.168.1.201    YL-PORTABLE-2    <server>  <my name>       00:0b:ad:89:0b:ed
192.168.1.255	Sendto failed: Permission denied

~$ ping yl-portable-2
PING yl-portable-2 (192.168.1.201) 56(84) bytes of data.
64 bytes from yl-portable-2 (192.168.1.201): icmp_seq=1 ttl=128 time=0.348 ms
64 bytes from yl-portable-2 (192.168.1.201): icmp_seq=2 ttl=128 time=0.312 ms
64 bytes from yl-portable-2 (192.168.1.201): icmp_seq=3 ttl=128 time=0.322 ms
64 bytes from yl-portable-2 (192.168.1.201): icmp_seq=4 ttl=128 time=0.326 ms
^C
--- yl-portable-2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.312/0.327/0.348/0.013 ms


```
Maybe not a bug after all? (At least not in my case?) But it should not be necessary to modify /etc/hosts ??

Thanks for all the good advice and support. I always like coming here.

---

### Post by Another Monkey on 2009-04-27
Got access to the other upgraded box now.  A restart of Samba seemed to cure whatever the problem was.

Then I added "smb ports = 139" to smb.conf and retsarted; the problem came back.

I restarted again and I still had the same problem.

Anyway, I tried the same trick that worked at home.  I installed firestarter, allowed the Samba ports and applies the fix dsmalley's fix from here [http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access](http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access)

Now it seems to work without error.

Can anyone explain to me why Samba now requires Firestarter?  Or is Firestarter doing something that is solving the problem for me?

I don't think Samba is very stable these days.

---

### Post by bacardiandwatermelon on 2009-04-27
Yeah installing Firestarter solved my issues with samba. Before I couldn't get a vista machine to write to my samba share folder. Thanks for the fix.

---

### Post by Another Monkey on 2009-04-28
I wouldn't call it a fix - Samba should not require Firestarter.  I am going to guess that many people will run desktop Ubuntu without a firewall configured using Firestarter, so I think they'll find that Samba does not work.

I still have no idea what Firestarter is doing to fix the problem an being a newb, I have no idea where to look.

It's definitiely a fault in Jaunty though, as I did not need this in Intrepid.

---

### Post by celem on 2009-04-28
The bug is, in my opinion, not in SAMBA but in SMBclient. I submitted a bug report (see link below). If any of you experience the same issue please vote and or comment on the bug to elevate its priority.

FYI - SAMBA does not need to be loaded for your Linux machine to see your Windows shares. SMBclient is there by default and it is what accomplishes this connectivity. You load SAMBA if you want Windows to see your Linux shares.

See:
[http://tinyurl.com/djekwp](http://tinyurl.com/djekwp)

---

### Post by Another Monkey on 2009-04-28
You are, of course, correct celem.  Samba is a server and, as I come from a Windows background, I probably don't separate them in my head as I see sharing folders out to the network and accessing folders on said network as all part of the same "thing".

The symptoms I had we, as you'd expect, Windows was happy enough to root around the shared folders, Ubuntu not so.

The big mystery to me is why Firestarter "fixes" it.

I saw this also about printers and Samba: [https://bugs.launchpad.net/samba/+bug/330883](https://bugs.launchpad.net/samba/+bug/330883)

---

### Post by Robsteranium on 2009-04-28
I'm also receiving the "Transport endpoint is not connected" error message.  The share does mount initially but eventually drops.  I'm able to ping the share successfully even though I can't pick it up through Thunar (Fusesmb) or ls.

Neither installing Firestarter nor adding the share to /etc/hosts appears to make a difference.

[This thread]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572") suggests that this is a Samba mutex problem - which would explain it's intermittent nature.

I jumped from 8.04 to 9.04 so I can't tell if this problem relates to Jaunty.  I'm using Xubuntu.  The NAS is a WD MyBook - effectively a Windows share.

Incidentally my NetworkManager Applet says "No valid active connections found!" apparently because there are no managed connections.

---

### Post by Another Monkey on 2009-04-29
It's not enough to add Firestarter, you need to configure it and edit the inbound config file to allow NEW connections to UDP.  Did you do that?  It's dsmalley's fix if post #2 here [http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access](http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access)

I have messed around and that was the bit of "magic" that sorted it for me.  After that smbclient (nods to celem :)) was able to connect without issue.

The NetworkManager thing just means you are not allowing it to manager the  connection, it's nothing to worry about.  If it annoys you, just edit "/etc/network/interfaces" so that the connection is not defined in there.

---

### Post by pearl298 on 2009-04-29
> **Linux.man said:**
> Hi, I install Ubuntu 9.04 with the same problem.

I believe that I found the solution.

Please try this...

```
sudo apt-get install fusesmb
```

Reboot and tell me.

Ok this worked for me!

THANK YOU!

---

### Post by Robsteranium on 2009-04-30
EDIT: Uninstalling Dolphin didn't solve the problem.

dmizer: I've tried changing workgroups, but to no avail.
Another Monkey: I've configured firestarter, no luck here either.

I realised that, while thunar/ terminal were dropping the connection after 40 seconds of use, the Dolphin filemanager manages to maintain the connection.

This appears to be a fuse problem.

```

$ ls -l /media/ | grep network
ls: cannot access /media/network: Transport endpoint is not connected
d????????? ? ?     ?        ?                ? network
$ fusesmb /media/network
fuse: bad mount point `/media/network': Transport endpoint is not connected

```

Creating a new mount point works for about 40 seconds!

I've got two samba configs, but I don't now why:
```

/etc/samba/smb.conf
/usr/share/samba/smb.conf

```

The fuse module is missing on this kernel.  Reverting to a previous kernel does not give the following error but it doesn't solve my problem either.
```

$ modprobe fuse
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
FATAL: Module fuse not found.

```

I can't see anything in the logs.  Any ideas?  Ta in advance.

---

### Post by dmizer on 2009-04-30
For more information on this problem (as well as solutions): [http://ubuntuforums.org/showpost.php?p=7157868&postcount=12](http://ubuntuforums.org/showpost.php?p=7157868&postcount=12)

---

### Post by Robsteranium on 2009-05-01
Okay.  Solved now.  I think...

libsmbclient isn't thread safe.

[https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351](https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351)

---

### Post by bdhrsa on 2009-05-01
Hi All. Check this Post. It sorted my 9.04 Samba

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Good Luck

---

### Post by dmizer on 2009-05-01
> **bdhrsa said:**
> Hi All. Check this Post. It sorted my 9.04 Samba

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Good Luck

That thread is for allowing Windows to connect to Ubuntu. This thread is about connecting to Windows from Ubuntu. :)

---

### Post by RealG187 on 2009-05-01
[http://ubuntuforums.org/showthread.php?t=1145775](http://ubuntuforums.org/showthread.php?t=1145775)

I cannot connect to Windows via Samba, but I can connect to my other Ubuntu machine via samba, anyone else have this problem?

---

### Post by dmizer on 2009-05-02
> **RealG187 said:**
> [http://ubuntuforums.org/showthread.php?t=1145775](http://ubuntuforums.org/showthread.php?t=1145775)

I cannot connect to Windows via Samba, but I can connect to my other Ubuntu machine via samba, anyone else have this problem?
Have a look here ...

> **dmizer said:**
> For more information on this problem (as well as solutions): [http://ubuntuforums.org/showpost.php?p=7157868&postcount=12](http://ubuntuforums.org/showpost.php?p=7157868&postcount=12)

---

### Post by RealG187 on 2009-05-04
My computers are the the same workgroup. I turned off DMZ so my computer had a normal IP and not a DMZ one and I can connect to one Windows machine but still not the other. I rebooted and renewed the IP lease on the server and I still cannot connect to it.

---

### Post by celem on 2009-05-04
I suspect that the solutions at the link below will solve your problems. My final post at that link was #125, wherein my problem was fully solved.

[http://ubuntuforums.org/showthread.php?t=784259](http://ubuntuforums.org/showthread.php?t=784259)

---

### Post by RealG187 on 2009-05-04
I think my router automatically reserves the IPs, I always have the same IP Addresses.

I figured something out, when I booted XP on this computer I was able to access the shares, but when it's running Server 2003 I can't :(

---

### Post by jpt266 on 2009-12-19
Solved.

This fixed for me too! I could always go ubunto to xp but not ubuntu to 
vista or windows 7.

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/458637](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/458637)

Removing windows live sign-in assistant program has "fixed" it for me too - I can use my WIndows 7 printer and access shared folders using my windows user/password, whereas before Win 7 appeared to be refusing to accept the credentials.

---

