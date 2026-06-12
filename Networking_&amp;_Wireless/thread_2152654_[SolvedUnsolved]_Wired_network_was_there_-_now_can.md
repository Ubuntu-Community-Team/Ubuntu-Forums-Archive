---
title: "[Solved/Unsolved] Wired network was there - now cannot connect"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by WB0HYQ on 2013-06-08
Hi.  LINUX new guy here (UBUNTU 12.04 - 64-bit).

When I first installed the OS about three weeks ago, I could connect to my local network (COMNET) just fine.  A bunch of updates got installed and now I a member of "WORKGROUP" and not my original of "COMNET".  Most of the time, using Home Folder - Browse Network, I can see an entry for COMNET (and WORKGROUP) but when I try to connect, I'm told:

"Unable to mount Location"
"Failed to retrieve share list from server"

What does all this mean?  Why would I get kicked out of COMNET and back to the default of WORKGROUP?  I feel it may be a simple command using Terminal, but it is beyond me to figure out what command to issue to get me back into COMNET.

Bill

---

### Post by WB0HYQ on 2013-06-08
More information:

Output of "smbtree" shows that I have been changed to "WORKGROUP" followed by a list of items.  There is a lone "COMNET" at the bottom, but nothing below it at all.

Inside smb.conf:

```

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP


```

Results of smbtree:

```

WORKGROUP
    \\NETGEAR67BC72          Netbios 2.2.12
    \\BILL-UBU               bill-UBU server (Samba, Ubuntu)
        \\BILL-UBU\Music              
        \\BILL-UBU\IPC$               IPC Service (bill-UBU server (Samba, Ubuntu))
        \\BILL-UBU\print$             Printer Drivers
COMNET

```


I have found that /etc/samba/smb.conf contains (in the Global area) Workgroup = WORKGROUP.  I think that is my problem.  Somehow that got changed in the mass of updates.  How can I get Gedit to open the file for changing?  I can open it for Read-Only, but don't have the ability to change it.

Bill

---

### Post by steeldriver on 2013-06-08
That file will belong to root - so you will need to do 

```
gksudo gedit /etc/samba/smb.conf
```

You will probably need to reboot after for the change to take effect

---

### Post by WB0HYQ on 2013-06-08
Hmmmm.  workgroup = COMNET has been established, but now I get nothing for "smbtree'.  Nothing at all.

I am using the computer to post here, so my Internet access is still there, but under Browse Network/Windows Network I get nothing either.

Bill

---

### Post by bab1 on 2013-06-08
> **WB0HYQ said:**
> Hmmmm.  workgroup = COMNET has been established, but now I get nothing for "smbtree'.  Nothing at all.

I am using the computer to post here, so my Internet access is still there, but under Browse Network/Windows Network I get nothing either.

Bill

The Samba worgroup is not the same as you networks name.  I assume that Comnet is your ISP.  The Samba workgroup is only for visual association.  On the other hand the system will update the Master Browse List and you should see the machines appear later on.

Post the output of ```
smbtree -d3
```...this will show what Samba is really doing.

---

### Post by WB0HYQ on 2013-06-08
Okay.  the name COMNET is the workgroup that all my Windows machine are in.  Up until a couple of days ago, that's what I saw when I looked into the Windows Network (under Browse Network).  If I double-clicked on COMNET, I could get access to all the shared items on each of my computers.  But now, I get nothing under Windows Network.

I can 'see' my UBUNTU computer from all my Windows machines (and access the shared directories), but not the other way around.


Output from smbtree -d3:

```

tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name COMNET<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name COMNET<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name COMNET<0x1d>
Got a positive name query response from 192.168.1.151 ( 192.168.1.151 )
Connecting to host=192.168.1.151
Connecting to 192.168.1.151 at port 445
Connecting to 192.168.1.151 at port 139
failed negprot: NT_STATUS_INSUFFICIENT_RESOURCES
Connecting to host=PRINSERVER
Connecting to 192.168.1.151 at port 445
Connecting to 192.168.1.151 at port 139
failed negprot: NT_STATUS_INSUFFICIENT_RESOURCES

```

Bill

---

### Post by bab1 on 2013-06-08
> **WB0HYQ said:**
> Okay.  the name COMNET is the workgroup that all my Windows machine are in.  Up until a couple of days ago, that's what I saw when I looked into the Windows Network (under Browse Network).  If I double-clicked on COMNET, I could get access to all the shared items on each of my computers.  But now, I get nothing under Windows Network.

I can 'see' my UBUNTU computer from all my Windows machines (and access the shared directories), but not the other way around.

I just recently had an Ubuntu update to Samba.  I had to select to keep the original smb.conf file.  Do you remember anything like that?  I've never had any problems with Windows hosts not seeing my Samba servers.

> 

Output from smbtree -d3:

```

name_resolve_bcast: Attempting broadcast lookup for name COMNET<0x1d>
Got a positive name query response from 192.168.1.151 ( 192.168.1.151 )
Connecting to host=192.168.1.151
Connecting to 192.168.1.151 at port 445
Connecting to 192.168.1.151 at port 139
failed negprot: NT_STATUS_INSUFFICIENT_RESOURCES
Connecting to host=PRINSERVER
Connecting to 192.168.1.151 at port 445
Connecting to 192.168.1.151 at port 139
failed negprot: NT_STATUS_INSUFFICIENT_RESOURCES

```

Bill

I see that the Ubuntu machine is able to find the host that is the master browser ```
name_resolve_bcast: Attempting broadcast lookup for name COMNET<0x1d>
Got a positive name query response from 192.168.1.151 ( 192.168.1.151 )
```...but that it fails at: failed negprot: NT_STATUS_INSUFFICIENT_RESOURCES.  This is very unusual.

It the host 192.168.1.151 named NETGEAR67BC72?    If so, you should note that this host is running Samba2 and might be causing the problem.  I would turn this host off and reboot the Ubuntu and windows hosts.  The first machine up will become the Master Browser and shuld be able to respond correctly.  I would boot the Ubuntu machine first myself.  In any event leave the host NETGEAR67BC72  off for now.

---

### Post by WB0HYQ on 2013-06-08
I cannot turn off the NetGear machine -- that's my router!!!!  If I turn it off then none of my wireless users will be able to connect, and my wired users won't get to the Internet.

Note, in the above code section, that the second time "Connecting to host = " appears it has matched the IP address of 192.168.1.151 to PRINSERVER - which is correct.  That is my 32-bit Windows 7 machine and at the moment it and one more machine (192.168.1.100 - SCANNER) are the only ones fired up.

I am bothered by the lack of response from my 'smbtree' command.  I get nothing but the return of the prompt.  Is there a way to command a complete reload of the smb stuff?  Maybe it will default into a state I can work with.

Bill

---

### Post by bab1 on 2013-06-08
> **WB0HYQ said:**
> I cannot turn off the NetGear machine -- that's my router!!!!  If I turn it off then none of my wireless users will be able to connect, and my wired users won't get to the Internet.
Then you need to turn off the file sharing for a short period of time.  At the present time that host is the master browser by election and it uses an ancient version of Samba (2.2.12).  The latest version of Samba is 3.6.4.  Version 3 has been used for at least the last 5 years or so.  In the past, has the Ubuntu host stayed up for extended periods of time?> 

Note, in the above code section, that the second time "Connecting to host = " appears it has matched the IP address of 192.168.1.151 to PRINSERVER - which is correct.  That is my 32-bit Windows 7 machine and at the moment it and one more machine (192.168.1.100 - SCANNER) are the only ones fired up.

What are the other host OS's?  Windows versions?
> 
I am bothered by the lack of response from my 'smbtree' command.  I get nothing but the return of the prompt.  Is there a way to command a complete reload of the smb stuff?  Maybe it will default into a state I can work with.
Bill
The smbtree command is the terminal version of browsing the network.  When you add -d3, you have turned on debug.  It clearly shows that the machine as run out of resources.  This is Samba resources not hardware resources.  It can be name handles of WORKGROUPS or COMPUTER NAMES.  The only reference I can find is for problems with SambaV2.  This is why I want to remove the the Samba server on the router from the equation.  At the present time it is in control as the Master Browser (the mapping between the IP address and the NetBIOS name). 

Reloading the smb.conf and electing a new Master Browser is what we're trying with what I suggested.

---

### Post by WB0HYQ on 2013-06-08
Now I am really confused.  The "netgear67BC72" is a wireless access point.  My router (Linksys) is also wireless (and the DHCP server).  How can an access point (which doesn't have DHCP turned on) act as a Master Browser?  Is that possible?

That particular device just today appeared in the Windows Network panel along with WORKGROUP and (occasionally) COMNET.  I had never before seen it.  But now, nothing at all appears in that panel.

Bill

---

### Post by bab1 on 2013-06-08
> **WB0HYQ said:**
> Now I am really confused.  The "netgear67BC72" is a wireless access point.  My router (Linksys) is also wireless (and the DHCP server).  How can an access point (which doesn't have DHCP) act as a Master Browser?  Is that possible?

The Samba?Windows sharing (SMB/CIFS) is a separate network ***sharing*** the physical hardware.  The Master Browser registers NetBIOS names and matches it to IP addresses.  It has nothing to do with DHCP at all.   The AP has a Samba server in it (\\NETGEAR67BC72 Netbios 2.2.12).  Look at your first post with smbtree to see it.  It appears that you have no shares at \\NETGEAR67BC72, but at the present time is is functioning as the MB.  Any SMB/CIFS server (yes, Windows too) can be the MB.
> 

That particular device just today appeared in the Windows Network panel along with WORKGROUP and (occasionally) COMNET.  I had never before seen it.  But now, nothing at all appears in that panel.

Bill
So let's turn it off for a few minutes and reboot the machines that have wired connections.  Is the Ubuntu machine wired?  Give it 10 or 15 minutes for the election to be held and the new MB to populate the list.  Then tell me what happens with smbtree.

[COLOR="#0000FF"]Edit:  You can continue to ask questions and I will answer them while we wait, but  we do need to do this to move forward.[/COLOR]

---

### Post by WB0HYQ on 2013-06-08
Okay.  I get it.  Let me give the users a moment to log into the router wireless instead of the access point and then I'll shut it down.

Be back with further info in a bit after I reboot the various wired machines.  Yes, the UBUNTU machine is wired.  It is a desktop and doesn't have wireless available unless I get one fo those USB to wireless thingies (which I hate).

Bill

---

### Post by WB0HYQ on 2013-06-08
Well, that was it.  Five minutes after I turned off the access point and rebooted PRINSERVER (which is on 24/7) I got back COMNET and all the machines in it.  I can see their shared folders just fine.

Now, what could have occurred at the AP that made it 'take over' as a master browser?  Any idea what I should look for to uncheck or turn off inside the various AP menus?  Or is it something that just naturally happes if the current Master Browser machine is rebooted?  This is a new AP that I bought to replace one that began to malfunction.  I've explored all the various setup menus, but may have missed something.


smbtree:

```

COMNET
    \\PRINSERVER             Printer Server
        \\PRINSERVER\Supercomp Backup    
        \\PRINSERVER\Samsung CLP-310 Series    Samsung CLP-310 Series
        \\PRINSERVER\Public_F           
        \\PRINSERVER\Public_C           
        \\PRINSERVER\Public             
        \\PRINSERVER\print$             Printer Drivers
        \\PRINSERVER\P$                 Default share
        \\PRINSERVER\iTunes             
        \\PRINSERVER\IPC$               Remote IPC
        \\PRINSERVER\F$                 Default share
        \\PRINSERVER\D$                 Default share
        \\PRINSERVER\Compak Backup      
        \\PRINSERVER\Canon imageCLASS D300    Canon imageCLASS D300
        \\PRINSERVER\C$                 Default share
        \\PRINSERVER\Billvaio Backup    
        \\PRINSERVER\Baby Backup        
        \\PRINSERVER\ADMIN$             Remote Admin
    \\BILL-UBU               bill-UBU server (Samba, Ubuntu)
        \\BILL-UBU\Music              
        \\BILL-UBU\IPC$               IPC Service (bill-UBU server (Samba, Ubuntu))
        \\BILL-UBU\print$             Printer Drivers

```


Bill

---

### Post by bab1 on 2013-06-08
> **WB0HYQ said:**
> Well, that was it.  Five minutes after I turned off the access point and rebooted PRINSERVER (which is on 24/7) I got back COMNET and all the machines in it.  I can see their shared folders just fine.
> Great.  I'm glad that this worked out.  :D

Now, what could have occurred at the AP that made it 'take over' as a master browser?  Any idea what I should look for to uncheck or turn off inside the various AP menus?  Or is it something that just naturally happes if the current Master Browser machine is rebooted?  This is a new AP that I bought to replace one that began to malfunction.  I've explored all the various setup menus, but may have missed something.
-Bill
As I said before, when the host that is currently the MB leaves the network (reboots or is shut down) the rest of the hosts in the SMB/CIFS network hold an election and another machine becomes the MB.  In you case the AP won but it is not equipped to handle multiple NETBIOS names so it choked.

You need to disable the Samba server in  the AP so I can't be involved in subsequent elections.


[COLOR="#0000FF"]Edit:  Look at all those file handles (shares).  No wonder SambaV2 couldn't handle it.[/COLOR]

---

### Post by WB0HYQ on 2013-06-08
You got that right.  I'll do some searching inside the AP to find out how to do that.

Thanks very much for your help Bab1

bill

---

### Post by bab1 on 2013-06-08
Glad I could help.

Mark the thread solved please.  The easy way is broken.  You can mark it solved by following [**[COLOR="#FF8C00"]this how to[/COLOR]**]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by WB0HYQ on 2013-06-27
I know this thread is marked 'solved' but I am back to the same problem and this time the solution (turn off the access point and reboot everything BUT the AP) didn't fix it.

Here are the results of smbtree -d3:

```

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::8e89:a5ff:fe6c:6fd9%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.24 bcast=192.168.1.255 netmask=255.255.255.0
Enter bill's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name COMNET<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name COMNET<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name COMNET<0x1d>
Got a positive name query response from 192.168.1.151 ( 192.168.1.151 )
Connecting to host=192.168.1.151
Connecting to 192.168.1.151 at port 445
Connecting to 192.168.1.151 at port 139
failed negprot: NT_STATUS_INSUFFICIENT_RESOURCES
Connecting to host=PRINSERVER
Connecting to 192.168.1.151 at port 445
Connecting to 192.168.1.151 at port 139
failed negprot: NT_STATUS_INSUFFICIENT_RESOURCES

```

I have done a check on smb.conf and find I am still in the proper workgroup (COMNET) but when I go to Browse Network -> Windows Network is see nothing at all.  I currently have just one computer, identified in the code above as 'PRINSERVER' but I don't see any of the shared directories on it (and there are several).

The Windows machine (PRINSERVER) can see my shares on the Ubuntu computer just fine.

Where do I go from here?

Bill

---

### Post by bab1 on 2013-06-27
> **WB0HYQ said:**
> I know this thread is marked 'solved' but I am back to the same problem and this time the solution (turn off the access point and reboot everything BUT the AP) didn't fix it.

Here are the results of smbtree -d3:

```

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::8e89:a5ff:fe6c:6fd9%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.24 bcast=192.168.1.255 netmask=255.255.255.0
Enter bill's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name COMNET<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name COMNET<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name COMNET<0x1d>
Got a positive name query response from 192.168.1.151 ( 192.168.1.151 )
Connecting to host=192.168.1.151
Connecting to 192.168.1.151 at port 445
Connecting to 192.168.1.151 at port 139
failed negprot: NT_STATUS_INSUFFICIENT_RESOURCES
Connecting to host=PRINSERVER
Connecting to 192.168.1.151 at port 445
Connecting to 192.168.1.151 at port 139
failed negprot: NT_STATUS_INSUFFICIENT_RESOURCES

```

I have done a check on smb.conf and find I am still in the proper workgroup (COMNET) but when I go to Browse Network -> Windows Network is see nothing at all.  I currently have just one computer, identified in the code above as 'PRINSERVER' but I don't see any of the shared directories on it (and there are several).

The Windows machine (PRINSERVER) can see my shares on the Ubuntu computer just fine.

Where do I go from here?

Bill

This is still showing that the host 192.168.1.151 is the 

Now I'm confused.  I asked if 192.168.1.151 was the Netgear router and you responded that it was not but it was the AP.  Now it appears that this is really a host named PRINSERVER.  What is PRINSERVER?  The OS is...?  The version of Samba is...?  The error definitely points to a lack of file handles (names) available.

---

### Post by WB0HYQ on 2013-06-27
192.168.1.151 is a Windows 7 Ultimate desktop computer with the name "PRINSERVER".  The wireless accesspoint is turned off and will remain turned off until I can get a handle on this problem.

Thanks, sorry for the delay in getting back.

EDIT:  Up until this morming, the network was running just fine.  I could transfer files and whatnot between Windows and Ubuntu at will.  I allowed some Ubuntu updates and suddenly this happened again.  I think that some default or other got set and I don't know to unset it.

Bill

---

### Post by bab1 on 2013-06-27
> **WB0HYQ said:**
> 192.168.1.151 is a Windows 7 Ultimate desktop computer with the name "PRINSERVER".  The wireless accesspoint is turned off and will remain turned off until I can get a handle on this problem.

Thanks, sorry for the delay in getting back.

EDIT:  Up until this morming, the network was running just fine.  I could transfer files and whatnot between Windows and Ubuntu at will.  I allowed some Ubuntu updates and suddenly this happened again.  I think that some default or other got set and I don't know to unset it.

Bill

Reboot the host 192.168.1.151.  Don't do anything else.  Did that fix things?

---

### Post by WB0HYQ on 2013-06-27
Unfortunately, I can't reboot it right at this moment.  I am running a complete scan (find bad sectors and all that) on a recalcitrant laptop hard drive (160G) and it's only about halfway done.  This may take a while.  I will post immediately after it finishes and I reboot.

Bill

---

### Post by WB0HYQ on 2013-06-27
I did the next-best thing.  I started up another computer on the network.  Apparently, it challenged PRINSERVER and they decided that PRINSERVER was boss.  Now I can access things from Ubuntu.  I just wish I could disable the OS in the access point because, somehow, it keeps taking over the network and I don't want it to.  Netgear support is sadly lacking as I've had no response from them at all.  Maybe someone in their forum can help.

Thanks --- again.

Bill

---

### Post by redmk2 on 2013-06-28
My mistake :oops:

---

### Post by bab1 on 2013-06-28
> **WB0HYQ said:**
> I did the next-best thing.  I started up another computer on the network.  

I'm sorry that you did that.  I have a different take on this problem now and I wanted to prove my hypothesis.  :(
> 
Apparently, it challenged PRINSERVER and they decided that PRINSERVER was boss.  Now I can access things from Ubuntu.  


You would have to prove that to me ( that PRINTSERVER is the current Master Browser).  We can look and see if this is so.  What do you get from this command from the Ubuntu host```

smbclient -L bill-ubu

```
This should return something like the following: In this instance the host *rincon* is the host responding to the **smbclient** request while the host *malibu* is the Master Browser```

smbclient -L rincon
Enter red's password: 
Domain=[BEACH] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	public          Disk      Shared Data
	IPC$            IPC       IPC Service (rincon server (Samba, Ubuntu))
	PDF             Printer   PDF
	HP-LaserJet-2200 Printer   LaserJet 2200
Domain=[BEACH] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	RINCON         rincon server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	BEACH                 MALIBU


```

> 
I just wish I could disable the OS in the access point because, somehow, it keeps taking over the network and I don't want it to.  Netgear support is sadly lacking as I've had no response from them at all.  Maybe someone in their forum can help.

Thanks --- again.

Bill

Here is what I think is happening.  The host PRINTSERVER ( a Windows host mind you) has a memory leak causing it to fail as a Master Browser while remaining elected to that position.  This causes the network browsing to fail and no automagic way for it to repair itself.  You reboot the host and it either elects a new Master Browser or, if the host PRINTSERVER is fast enough, it wins the new election and has no problems because all the pointers to data (in RAM) are fresh.

Why do I think that?  Because we had the AP off when this problem reoccurred, plus NT_STATUS_INSUFFICIENT_RESOURCES is apparently  Windows specific problem now and I believe that 192.168.1.151 is not the AP but rather, it is PRINTSERVER!  At this point however, I can't corroborate  these thoughts other than with this  ```

Connecting to host=**[COLOR="#FF0000"][B]PRINSERVER**[/COLOR][/B]
Connecting to 192.168.1.151 at port 445
Connecting to 192.168.1.151 at port 139
failed negprot: NT_STATUS_INSUFFICIENT_RESOURCES

```
At this point it's all just a theory that I would like to verify.   It would be helpful if you provided a list of the hostame to IP address mapping in your LAN.  It would go a long way towards nailing down the root answer answer to the problem.  The format could be something like this```

printserver <ip address>
ubu-bill  <ip address>
<The AP> <ip address>
<The Router> <ip address>

```...the items in the < > are variables that I don't know the correct name or number of.

I just need to see who all the players are in your network.  If my suspicions are correct the AP is not the problem, The Windows host PRINTSERVER is. but I don't know that for a fact just yet, so I would do as you say; leave the AP off for right now.  Are there any other devices with hostnames that I should know the mapping of?

---

### Post by WB0HYQ on 2013-06-28
Here is the output of smbclient:

```

 smbclient -L bill-ubu
Enter bill's password: 
Domain=[COMNET] OS=[Unix] Server=[Samba 3.6.3]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    IPC$            IPC       IPC Service (bill-UBU server (Samba, Ubuntu))
    Music           Disk      
Domain=[COMNET] OS=[Unix] Server=[Samba 3.6.3]

    Server               Comment
    ---------            -------
    BILL-UBU             bill-UBU server (Samba, Ubuntu)

    Workgroup            Master
    ---------            -------
    COMNET               


```

Apparently, when I booted up the Ubuntu machine, it assumed the Server duties.  My desktop (PRINSERVER) was turned on and running as well as my AP.

EDIT:

Here are the IP addresses of the network:

PRINSERVER:  192.168.1.151 (Manually assigned)
bill-UBU: 192.168.1.24 (assigned by the Router DHCP)  <-- when running in Windows as COMPAK, 192.168.1.160 (manually assigned)
AP: 192.168.1.200 (Manually assigned)
Server: 192.168.1.1 (connected to DSL modem)

There are others that can come alive on the network, but they are all off right now.  All IP addresses (except laptops) are manually assigned.  Laptops are assigned from DHCP pool.

Bill

---

### Post by bab1 on 2013-06-28
> **WB0HYQ said:**
> Here is the output of smbclient:

```

 smbclient -L bill-ubu
Enter bill's password: 
Domain=[COMNET] OS=[Unix] Server=[Samba 3.6.3]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    IPC$            IPC       IPC Service (bill-UBU server (Samba, Ubuntu))
    Music           Disk      
Domain=[COMNET] OS=[Unix] Server=[Samba 3.6.3]

    Server               Comment
    ---------            -------
    BILL-UBU             bill-UBU server (Samba, Ubuntu)

    Workgroup            Master
    ---------            -------
    COMNET               


```

Apparently, when I booted up the Ubuntu machine, it assumed the Server duties.  My desktop (PRINSERVER) was turned on and running as well as my AP.

> Not at all.  The above output shows that.  The entry for the Master Browser is empty so bil-ubu is not the MB.  Samba sometimes has difficulty collecting the info from Windows hosts (in this case PRINTSERVER.  What this proves is that some other host (it could be PRINTSERVER) is the MB.  

EDIT:

Here are the IP addresses of the network:

PRINSERVER:  192.168.1.151 (Manually assigned)
....

This really proves my hypothesis.  The host PRINTSERVER is 192.168.1.151.  It is the root of you problems.  Te simple cure is: Every time find you can't browse your network for shares, you have to reboot PRINTSERVER.  Since this host is on 24/7 you will have to either have to live with this or find a way to auto reboot PRINTSERVER every night.

---

### Post by WB0HYQ on 2013-06-28
Okay, I can see there is no entry under Master.  At the moment, I am still under a huge learning curve with Ubuntu and, because of this, I only reboot into LINUX when I have a few hours free to delve into something interesting.  This machine is also my gaming machine, and I use it extensively in Windows for my virtual trains and flight sim.

Since this strange behavior doesn't seem to affect anything on the Windows side, I'll have to just check when I boot up Ubuntu and see what happens to the network.  If it is borked, then I'll take action only if I need something from on of my Windows boxes.

Thanks for your help - again.

Bill

---

### Post by bab1 on 2013-06-28
> **WB0HYQ said:**
> Okay, I can see there is no entry under Master.  

Thats because smbclient can't retrieve it from the Windows machine.
> 
At the moment, I am still under a huge learning curve with Ubuntu and, because of this, I only reboot into LINUX when I have a few hours free to delve into something interesting.  This machine is also my gaming machine, and I use it extensively in Windows for my virtual trains and flight sim.

Since this strange behavior doesn't seem to affect anything on the Windows side, I'll have to just check when I boot up Ubuntu and see what happens to the network.  If it is borked, then I'll take action only if I need something from on of my Windows boxes.

Thanks for your help - again.

Bill
That sounds like a plan.  At least you know sort of understand what the problem is and how to resolve it for that moment.

---

