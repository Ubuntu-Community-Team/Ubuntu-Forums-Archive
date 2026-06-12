---
title: "Workgroup Master Question"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by rcayea on 2010-10-15
Hi everyone,

I am wondering if I should change my WORKGROUP MASTER to my server or leave it as is? I know this is a confusing first line so let me explain and I will add info below.

I am not sure if the best way to setup my home network is to leave my wife's Vista computer (Vista 1) as the WORKGROUP MASTER. Or, should I switch the WM to my server (Server 1) or even my Ubuntu desktop (Ubuntu 1)?

I am simply trying to figure out what is best and maybe it will help me with some other problems. I get this info from smbclient -L command which was operated on the server side. Oddly enough, my Ubuntu desktop isn't listed. Should it be? Here is some info...

```

	Server               Comment
	---------            -------
	SERVER 1          server 1 server (Samba, Ubuntu)
	VISTA             wife_computer

	Workgroup            Master
	---------            -------
	WORKGROUP            Vista 1
```

---

### Post by pricetech on 2010-10-15
Are you referring to the Browse Master ??  If so, I've never had a need to specifically assign one, but if you think it might help something then go ahead.  There's a place in smb.conf for that.

---

### Post by rcayea on 2010-10-15
Yup, that was what I was referring to.

Thanks!

---

### Post by endotherm on 2010-10-15
you can also use the os level option in your smb.conf to rig the election, without having to specify a specific master (since what happens if that box is off?) just set the level to 65 for whatever box you want to be master, your second choice as fifty somthing and set the client desktops to 20. that shoudl get your server elected every time.

---

### Post by capscrew on 2010-10-15
> **rcayea said:**
> Hi everyone,

I am wondering if I should change my WORKGROUP MASTER to my server or leave it as is? I know this is a confusing first line so let me explain and I will add info below.

I am not sure if the best way to setup my home network is to leave my wife's Vista computer (Vista 1) as the WORKGROUP MASTER. Or, should I switch the WM to my server (Server 1) or even my Ubuntu desktop (Ubuntu 1)?

I am simply trying to figure out what is best and maybe it will help me with some other problems. I get this info from smbclient -L command which was operated on the server side. Oddly enough, my Ubuntu desktop isn't listed. Should it be? Here is some info...

```

	Server               Comment
	---------            -------
	SERVER 1          server 1 server (Samba, Ubuntu)
	VISTA             wife_computer

	Workgroup            Master
	---------            -------
	WORKGROUP            Vista 1
```

The term **Workgroup **is separate from the term **Master**.  The term Master refers to the Master Browser function.  Any host can be the Master Browser, but there is only one per LAN (or WINS server domain).  The Master Browser should be the host that has the greatest chance for remaining up (functioning), as the list of browsable shares is maintained on the that host. 

There is no entity called Workgroup Master.

---

### Post by pricetech on 2010-10-15
Best I recall it goes like this.

Server comes before Workstation.

Later OS comes before earlier OS.  Windows 7 would win over Vista which in turn would win over XP and so on, but none of them would win over Server.

If you set the option in your smb.conf, your Ubuntu box will win the election, but if it goes offline, a new election is forced, so you're never without a browse master unless you have disabled the function on other computers.

That's my best recollection of the way Microsoft defines it.

---

### Post by rcayea on 2010-10-18
Again, thank you for the information. I did have a rough understanding of the master browser from having read *Using Samba*, a little while ago, but I didn't know about the order and such. 

I will go with setting my Ubuntu Server as the Master in the smb.conf file.

Cheers!

---

