---
title: "Ubuntu can't ping Windows, can half Samba, sort of (with diagram!)"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by mendhak on 2010-07-13
Hi, I'm still new to Ubuntu but I hope I'm providing you with all the right info.  I've also done a lot of searching but I haven't found any answers related to this problem.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=163326&stc=1&d=1279050358[/IMG]

The Windows7 machine can ping the Ubuntu machine (running 10.04) by name and IP address.
The Ubuntu machine cannot ping the Windows 7 machine by name, only IP address. (ping: unknown host aztec)

Via Nautilus, I cannot browse to a shared folder on the Win7 machine.

```
smb://aztec/Projects
(or)
smb://192.168.1.4/Projects

```
because I keep getting the password dialog repeatedly (entering the correct password of course).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=163327&stc=1&d=1279050631[/IMG]

However, I CAN mount a shared folder via /etc/fstab but only by IP address

```
//192.168.1.4/Projects /mnt/aztecprojects smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
```Using //aztec will not work in this case.

So I thought the Win7 machine wasn't visible by name, but then I tried using nmblookup and aztec does work!

```

$ nmblookup aztec
querying aztec on 192.168.1.255
192.168.1.4 aztec<00>

```I also did an smbtree and the output contains the Win7 machine.

```

WORKGROUP
    \\AZTEC                  
    \\ASHENVALE              ashenvale server (Samba, Ubuntu)
        \\ASHENVALE\IPC$               IPC Service (ashenvale server (Samba, Ubuntu))
        \\ASHENVALE\print$             Printer Drivers

```So as you can see, I'm confused.  Samba can sort of see the Win7 machine but I can't ping it.  I've seen the route -n requested in a lot of such threads, so here it is

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```The Win7 machine is 192.168.1.4 on the same subnet mask, the ubuntu laptop is 192.168.1.3.

I'd appreciate any pointers or help with getting these two machines to work together, please let me know if I've missed any other info.

---

### Post by mendhak on 2010-07-13
I also did an ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:22:19:db:29:e1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:23:4e:a2:35:41  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4eff:fea2:3541/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17519 errors:0 dropped:0 overruns:0 frame:1945
          TX packets:14974 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20219279 (20.2 MB)  TX bytes:2096793 (2.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51094 (51.0 KB)  TX bytes:51094 (51.0 KB)

```

And a cat /etc/network/interfaces

```

auto lo
iface lo inet loopback

```

TMI? :D

---

### Post by redmk2 on 2010-07-13
> **mendhak said:**
> Hi, I'm still new to Ubuntu but I hope I'm providing you with all the right info.  I've also done a lot of searching but I haven't found any answers related to this problem.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=163326&stc=1&d=1279050358[/IMG]

A picture is always worth a thousand words!  :-)> 

The Windows7 machine can ping the Ubuntu machine (running 10.04) by name and IP address.

The Ubuntu machine cannot ping the Windows 7 machine by name, only IP address. (ping: unknown host aztec)

Via Nautilus, I cannot browse to a shared folder on the Win7 machine.

```
smb://aztec/Projects
(or)
smb://192.168.1.4/Projects

```
because I keep getting the password dialog repeatedly (entering the correct password of course).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=163327&stc=1&d=1279050631[/IMG]

Did you add the user to the smbpasswd database?  You can do this with```
sudo smbpasswd -a [username]
```> 

However, I CAN mount a shared folder via /etc/fstab but only by IP address

```
//192.168.1.4/Projects /mnt/aztecprojects smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
```Using //aztec will not work in this case.

So I thought the Win7 machine wasn't visible by name, but then I tried using nmblookup and aztec does work!

There are 2 types of namesevices DNS (hostname) and NetBIOS.  Right now you can see NetBIOS only. > 

```

$ nmblookup aztec
querying aztec on 192.168.1.255
192.168.1.4 aztec<00> [COLOR="Red"]<-- this is a NetBIOS name[/COLOR]

```I also did an smbtree and the output contains the Win7 machine.

```

WORKGROUP
    \\AZTEC                  
    \\ASHENVALE              ashenvale server (Samba, Ubuntu)
        \\ASHENVALE\IPC$               IPC Service (ashenvale server (Samba, Ubuntu))
        \\ASHENVALE\print$             Printer Drivers

```So as you can see, I'm confused.  Samba can sort of see the Win7 machine but I can't ping it.  I've seen the route -n requested in a lot of such threads, so here it is

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```The Win7 machine is 192.168.1.4 on the same subnet mask, the ubuntu laptop is 192.168.1.3.

I'd appreciate any pointers or help with getting these two machines to work together, please let me know if I've missed any other info.

The first thing I would do is add the Samba *client *package to your Linux host (ashenvale) and see what works.  The package is "smbfs"

You can add it with ```
sudo apt-get install smbfs
```

---

### Post by mendhak on 2010-07-13
> **redmk2 said:**
> A picture is always worth a thousand words!  :-)Did you add the user to the smbpasswd database?  You can do this with```
sudo smbpasswd -a [username]
```There are 2 types of namesevices DNS (hostname) and NetBIOS.  Right now you can see NetBIOS only. 

The first thing I would do is add the Samba *client *package to your Linux host (ashenvale) and see what works.  The package is "smbfs"

You can add it with ```
sudo apt-get install smbfs
```

Thanks for responding! 

I added the user using smbpasswd, but Nautilus still keeps prompting with the password dialog.  I also tried installing smbfs but "smbfs is already the newest version", it says :D


So you mentioned NetBios - thank you for mentioning it, because that immediately got me searching and I chanced on this [thread here](http://ubuntuforums.org/showthread.php?t=88206), modified the nsswitch.conf file and now ping to the Win7 machine works (although there is a noticeable delay between pings)

```

hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4 

```

Does that look OK to you?  I added wins as the second entry.  I have no clue what mdns4 is.

So that leaves the Nautilus+Samba problem -  Trying to connect via Nautilus still gives me the password prompt, I enter the password, press enter, and it comes back again.  Any ideas there?

---

### Post by redmk2 on 2010-07-13
> **mendhak said:**
> Thanks for responding! 

I added the user using smbpasswd, but Nautilus still keeps prompting with the password dialog.  I also tried installing smbfs but "smbfs is already the newest version", it says :D


So you mentioned NetBios - thank you for mentioning it, because that immediately got me searching and I chanced on this [thread here](http://ubuntuforums.org/showthread.php?t=88206), modified the nsswitch.conf file and now ping to the Win7 machine works (although there is a noticeable delay between pings)

```

hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4 

```

Does that look OK to you?  I added wins as the second entry.  I have no clue what mdns4 is.

So that leaves the Nautilus+Samba problem -  Trying to connect via Nautilus still gives me the password prompt, I enter the password, press enter, and it comes back again.  Any ideas there?

I hope you did not add winbind.  That would be absolutely WRONG!!!!!

I believe you can modify just the /etc/nsswich file.  The order is very important.  You have it searching WINS before DNS.  Try putting wins AFTER dns.

For a good discussion on how this all works read [**_here_**]("http://ubuntuforums.org/showthread.php?t=1496488&highlight=netbios").  Read it all, and then read it again (slowly).  Let me know what you think.  How does it relate to your issues?

---

### Post by mendhak on 2010-07-14
Hi again,

After reading that, I think I'm actually dealing with two separate issues.  I've backed off from winbind for now, I'm going to spend more time reading up on this and using cifs as well.  What I should do is create a separate thread just for the Nautilus problem.  Thanks for your help, maybe I'll see you in that one too.  There doesn't seem to be a rating system on this forum, so just pretend I increased your forum reputation in some way.  :)

---

### Post by redmk2 on 2010-07-14
> **mendhak said:**
> Hi again,

After reading that, I think I'm actually dealing with two separate issues.  I've backed off from winbind for now, I'm going to spend more time reading up on this and using cifs as well.  What I should do is create a separate thread just for the Nautilus problem.  Thanks for your help, maybe I'll see you in that one too.  There doesn't seem to be a rating system on this forum, so just pretend I increased your forum reputation in some way.  :)

Thanks for the pat on the back.  :D

I think you should at least try and move the ***wins*** directive in the nsswitch.conf file and see what happens.  I'm not saying it would work but it is worth a try.

I think you should know that Nautilus (and therefore "smb://) is a routine developed by Gnome to address the Samba daemon (i.e. smbd).  It has nothing to do with this: **//netbios_name/share**, or **smbclient** calls other than it is ultamatly talking to the same smbd daemon.

---

### Post by bpsanborn on 2010-09-01
Hi,

I had the same "nautilus can't get to the Win7 shares" problem.  See this... starting at post #6 for the details:

[http://ubuntuforums.org/showpost.php?p=9789158&postcount=6](http://ubuntuforums.org/showpost.php?p=9789158&postcount=6)

Brian

---

