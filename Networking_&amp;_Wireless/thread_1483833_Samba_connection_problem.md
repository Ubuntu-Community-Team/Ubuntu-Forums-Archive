---
title: "Samba connection problem"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Zanven on 2010-05-15
I am new to network sharing all together really but I want to set up a  connection with my laptop running Xubuntu and both of my desktop  partitions running Win 7 and xubuntu.

I went here:  [https://help.ubuntu.com/community/SettingUpSamba#Samba%20Client%20-%20Manual%20Configuration](https://help.ubuntu.com/community/SettingUpSamba#Samba%20Client%20-%20Manual%20Configuration)  and in typing:
smbclient -L //server -U user
I tried substituting "server" with ip and I get 
> Domain=[XEEFLAA-PC] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]

    Sharename   Type        Comment
    ---------                ----             -------
    ADMIN$                 Disk           Remote Admin
    B                                 Disk       XHITACHI (B:)
    B$                              Disk            Default share
    Back-up                Disk      
    C$                 Disk            Default share
    IPC$                         IPC              Remote IPC
    Users                      Disk      
session request to 192.168.1.100 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available
So I try to substitute  server with "Windows & Professional 6.1" instead and I get 
> Connection to Windows 7 Professional 6.1 failed (Error NT_STATUS_BAD_NETWORK_NAME)So do I need to change that name in windows 7 somehow/how do I? or am I doing this wrong all together?

---

### Post by Eiríkr on 2010-05-15
Hello there Zanven --

The "Server" listing here is not the name of the server machine, but rather the name of the application doing the serving.  My results when using my Samba server IP address look like this:

```

eirikr@Boreas:~$ smbclient -L //192.168.10.10 -U eirikr
Enter eirikr's password: 
Domain=[WOLKENHAFEN] OS=[Unix] Server=[Samba 3.0.26a]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (Zephyrus server (boreas; 192.168.10.11))
	Music           Disk      
	Margvís's Docs  Disk      
	Eiríkr's Docs   Disk      
	shared          Disk      Shared directory with forced group.
Domain=[WOLKENHAFEN] OS=[Unix] Server=[Samba 3.0.26a]

	Server               Comment
	---------            -------
	ZEPHYRUS             Zephyrus server (nmbd; 0.0.0.0)

	Workgroup            Master
	---------            -------
	WOLKENHAFEN          ZEPHYRUS
eirikr@Boreas:~$ 

```

I notice that your output doesn't list the last two groupings.  From the header line in your results, it looks like you're connecting *from* your Linux machine *to* your Win 7 machine, which might be why.  However, here we're wandering into waters where I might not be able to help much, since I have zero familiarity with Win 7 (still happily chugging along with XP when I need Windows stuff).  

That said, I might still be able to help clarify some things, with a few questions for you.  

[LIST]
[*]How many machines are you sharing between?
[*]What OS(es) does each machine run?
[*]On which machine(s) are the files that you want to share?
If possible, you're best off if you can find **one** place where all your shared files will live, and then set up sharing to serve the files *from* that machine to all the others.  
If you simply cannot consolidate your files into one location, things are messier and trickier, but still potentially doable -- but then you need to properly configure sharing from **all** the machines that have files you need to access.
[/LIST]

By way of example, I've got three or four computers I regularly share files between -- Zephyrus (Ubuntu), Boreas (Ubuntu), Odysseus (the MacBook I share with my wife), and Mistralis (Win XP running in a VM).  I learned the hard way that it was the least confusing and the easiest to keep all data files in one place (not just in terms of server setup but also just in terms of sorting out duplicates and which versions of what files I actually mean to keep), so I set up Zephyrus as my file server.  This way I only need to worry about the Samba configuration on one machine.  

Anyway, think through your particular needs and get back to us with the answers to the above questions, and we'll go from there.

Cheers,

-- Eiríkr

---

### Post by Zanven on 2010-05-16
To answer the questions: 

[LIST]
[*]I am running two machines.
[*]My laptop is running Xubuntu and my Desktop runs both Win 7 and Xubuntu.
[*]I got an external drive and I was trying to set it up to run it as a drive shared between them (in my two machine network).
[/LIST]

I was trying to accomplish two things really. I was trying to set up this drive as a share drive to more easily move files between machines and to make a place I can make backups. The latter I figured falls in the same category as the former though really.
I was trying to set this up doing more work now so I can be lazier later because I could probably just unplug my drive every time.
Between the linux partitions I set this up just fine after posting the above but without success on the Win7 set up.

Win 7 sees my laptop in the network but can't see any folders but I'm pretty sure its because I haven't set up share files on my laptop or at least not using windows method but that's okay because I want files going the other way. It seems my laptop sees my desktop but can't connect as by what I posted earlier.

I suppose I could just log into my Xubuntu partition on my desktop every time in the meantime but I'd rather not have to interrupt what I'm doing to do other things.

---

### Post by Iowan on 2010-05-16
Just for more resources, the [Ubuntu Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") has a [Samba]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html") server section - dunno if anything in there will help with your problem...

---

