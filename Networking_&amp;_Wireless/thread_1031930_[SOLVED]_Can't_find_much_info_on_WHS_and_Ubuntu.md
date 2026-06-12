---
title: "[SOLVED] Can't find much info on WHS and Ubuntu"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by Toady00 on 2009-01-05
I'm new to linux. Been a windows guy for a while. I have a mixed evironment at home. Windows XP Pro, Windows Vista Home Premium, Windows Vista Ultimate 64 bit, now Ubuntu 8.10 and the kicker is a windows home server. I love the Home server but I can't connect to any of the shares with Ubuntu. I came across this "How to"( [http://www.informit.com/articles/article.aspx?p=1021022&seqNum=5](http://www.informit.com/articles/article.aspx?p=1021022&seqNum=5) ) and it didn't work. When I click on my workgroup it doesn't show anything. I also tried using pyNeighborhood based on [http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734) . That didn't work either. Does anyone have any thoughts or come across this problem before? Thanks in advance for any help.

---

### Post by cariboo on 2009-01-06
I would suggest that in a Applications-->Accessories-->Terminal type:

```
smbclient -L <servername> -U%
```

If everything is working on your server you should get an output similar to this:

```
 smbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
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
	WINMCLEESE           Laptop

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

If you paste the result of the above command in your next post, it would be very helpful.

Jim

---

### Post by Toady00 on 2009-01-06
brandon@brandon-laptop:~$ smbclient -L server -U%
Domain=[THE POND] OS=[Windows Server 2003 3790 Service Pack 2] Server=[Windows Server 2003 5.2]

	Sharename       Type      Comment
	---------       ----      -------
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine server.  Error was NT_STATUS_ACCESS_DENIED
Error returning browse list: NT_STATUS_ACCESS_DENIED
Domain=[THE POND] OS=[Windows Server 2003 3790 Service Pack 2] Server=[Windows Server 2003 5.2]

	Server               Comment
	---------            -------
	SERVER               server

	Workgroup            Master
	---------            -------
	THE POND             SERVER

---

### Post by cariboo on 2009-01-08
Check the share permissions on your WHS are world read/writeable, I have no experience with WHS, but usually when sharing files with XP and you get the same error, it usually is a permission error. Also make sure you are using the same username and password on both your server and ubuntu computer.

One other thing to check is to alias the ip address to the server's name in /etc/hosts, like this

```
 cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	jack
192.168.1.1	router
192.168.1.200	willy
192.168.1.202	minibuntu
192.168.1.104	risky
```

In the above listing willy is my server.

Jim

---

### Post by WIVO_Riley on 2009-01-09
Well I have the same deal- I can see my network, but that's all  What I get is:

riley@UBUNTUBASE:~$ -L G33KSERVER -U%
bash: -L: command not found
riley@UBUNTUBASE:~$ smbclient -L G33KSERVER -U%
timeout connecting to 24.28.193.9:445
timeout connecting to 24.28.193.9:139
Connection to G33KSERVER failed (Error NT_STATUS_ACCESS_DENIED)
riley@UBUNTUBASE:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	UBUNTUBASE

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
riley@UBUNTUBASE:~$ 

I'm a linux newb, so any help you could give would be great.  I had 2 machines dual booting xp and ubuntu 2 distos ago, and was sharing on server 2003 that had an attached printer- everything was awesome.  I got some newer hardware and didn't install linux on them until now, and now I have nothing but problems and don't know enough to figure any of it out- have    internet access on this machine and that's all.  THANKS MUCH!!!!!

---

### Post by Toady00 on 2009-01-10
I figured it out. For some reason my server wasn't available by name but I could mount the shared folders by ip address. I used sudo mount -t smbfs -o username=<username>,password=<password> //<ip address>/<share name> /<mount point>

---

