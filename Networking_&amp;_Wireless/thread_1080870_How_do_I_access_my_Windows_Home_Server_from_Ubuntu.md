---
title: "How do I access my Windows Home Server from Ubuntu Desktop?"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by bgriggs75 on 2009-02-25
Ubuntu NooB here, and not very good at Windows networking either, I'm afraid, so sorry on both counts.  

I just loaded Ubuntu 8.10 desktop and got things running very nicely with one exception.  I can't seem to figure out how to connect to my Windows Home Server.  Places->Network shows a windows network, and even the correct workgroup name when I click through.  But when I double-click on the workgroup name I get the message "Unable to mount location:Failed to retrieve share list from server"

I've also tried manually mounting the share with Places->Connect to server but also get the cryptic "failed to retrieve" message.  I've read a little bit about SAMBA but got about halfway through the instructions and decided I was over my head.  Plus, I thought: It can't be THIS hard, can it?  People have been running SAMBA on Ubuntu for several years so surely it should work nearly out of the box by now.  I could be wrong, though.

I was thinking about looking into Ubuntu as a possible netbook OS replacement for XP but if I can't get to my server then that kind of takes it out of the running.

Any thoughts, community? Thanks in advance.

---

### Post by cariboo on 2009-02-25
Open an Applications-->Accessories-->Terminal and type:

```
smbclient -L <servername> -U%
```

Where <server name> is the name of your server. The output from above command should look something like this:

```
smbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
	stuff           Disk      misc stuff
	images          Disk      iso images
	updates         Disk      Project Dakota
	data            Disk      Data directory
	music           Disk      Music library
	movies          Disk      TV Shows and Movies
	print$          Disk      Printer Drivers
	HP_LaserJet_5P_LPT_parport0_HPLIP Printer   HP LaserJet 5P
	
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------
	RISKY                Windows computer
	WILLY                willy server (Samba, Ubuntu)
	WINMCLEESE           

	Workgroup            Master
	---------            -------
	APLUS                WILLY 
```

if the shares on your server are setup properly.

Jim

---

### Post by bgriggs75 on 2009-02-25
Thanks for the starting point.  Looks like I may have a couple of issues.  When I try to execute the above command with hostnames, it times out.  I used IP address instead and got a response but shares were denied.

Domain=[DUM DOMAIN] OS=[Windows Server 2003 3790 Service Pack 2] Server=[Windows Server 2003 5.2]

	Sharename       Type      Comment
	---------       ----      -------
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine 192.168.x.2.  Error was NT_STATUS_ACCESS_DENIED
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.x.2 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[DUM DOMAIN] OS=[Windows Server 2003 3790 Service Pack 2] Server=[Windows Server 2003 5.2]

	Server               Comment
	---------            -------
	SOME-PC               
	SOMEROOM           
	SOME-SERVER        
	SOME-NETBOOK         

	Workgroup            Master
	---------            -------
	SOME HOME          SOME-SERVER

Trouble is, I didn't set up the shares.  Windows Home Server (based on server 2003) sets up the shares for you automatically based on the client software it installs on your machines.  So I'm not sure what "properly" means in this case.  I'm guessing that since this OS is based on windows server 2003 that it can be configured to work, though.

---

### Post by bgriggs75 on 2009-03-05
I was able to get the share set up properly.  My issue was more related to not having internal DNS set up properly, but once that was straightened out it was a matter of making sure the shares drive on the server was properly shared.  Thanks!

---

