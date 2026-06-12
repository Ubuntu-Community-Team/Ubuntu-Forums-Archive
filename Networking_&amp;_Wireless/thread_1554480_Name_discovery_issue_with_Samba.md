---
title: "Name discovery issue with Samba"
date: 2010-08-16
forum: Networking &amp; Wireless
---

### Post by Marcelo Ruiz on 2010-08-16
Hi,

I have a small network configured over a wireless linksys router.
I'm trying to use Samba to share documents between linux and Win PCs.

I configured Samba to use:

name resolve order = wins lmhosts hosts bcast

but it works randomly. Sometimes I can see the server using findsmb and sometimes I can't.

smbclient -L [Host Name] never works, but smbclient -L [IP Number] does.

I would like to set up a network in which any of my friends with a laptop could share documents as we do under Windows: no editing text files for each new friend that comes with a different computer.
I would like to click Places->Network and find the computers and shares offered by any computer connected to the network.
Is this possible?

Thanks!

---

### Post by capscrew on 2010-08-16
> **Marcelo Ruiz said:**
> Hi,

I have a small network configured over a wireless linksys router.
I'm trying to use Samba to share documents between linux and Win PCs.

I configured Samba to use:

name resolve order = wins lmhosts hosts bcast

but it works randomly. Sometimes I can see the server using findsmb and sometimes I can't.

smbclient -L [Host Name] never works, but smbclient -L [IP Number] does.

I would like to set up a network in which any of my friends with a laptop could share documents as we do under Windows: no editing text files for each new friend that comes with a different computer.
I would like to click Places->Network and find the computers and shares offered by any computer connected to the network.
Is this possible?

Thanks!

Samba will by default convert host names to NetBIOS names.  There is no reason to modify the smb.conf in that way.

---

### Post by Marcelo Ruiz on 2010-08-17
Hi,

Thanks for your answer.
Are you talking about "name resolve order = wins lmhosts hosts bcast"?
What is the way to achieve what I am looking for?
Thanks!

---

### Post by bab1 on 2010-08-17
> **Marcelo Ruiz said:**
> Hi,

Thanks for your answer.
Are you talking about "name resolve order = wins lmhosts hosts bcast"?
What is the way to achieve what I am looking for?
Thanks!

Capscrew is correct.  There is no need to add any "name resolve order".  The default is:```
name resolve order = lmhosts host wins bcast
```
This will provide the needed name resolution in most Samba setups.

My system works exactly as you stated you want in  your first post.  I have not added "name resolve order" directive in my smb.conf file.  I can see any Windows share that is hosted on a machine that is attached to my network.

I do have DNS running on my router.  I'm not sure that your Linksys has that ability.  

The question is:  Why did you feel you needed to modify the smb.conf file?  What problems were you having?  What other modifications to the system have you made?

---

### Post by Marcelo Ruiz on 2010-08-17
Hi bab1,

Thanks for your answer.

I initially modified the name resolve order because I read in a different website that it might help the problem, but it hasn't. You mentioned that this is the default:
```
name resolve order = lmhosts _host wins_ bcast
```
but if I use swat and hit the set default I get:
```
name resolve order = lmhosts _wins host_ bcast
```
Which one should I use?

The problem I am having is that they see each other randomly just for a very short period of time: if I click refresh in Nautilus they disappear, and that even is true for the same machine I am working with. This random behavior also shows up when I try:

```
smbclient -L [Host Name]
```

I initially modified the name resolve order because I read in a different website that it might help the problem, but it hasn't.

About the router, I don't think it has the DNS service. What I don't get is that if I boot in windows everything works as expected with the very same router... so it must be a Samba configuration problem.

Any ideas?

Thanks!

---

### Post by Marcelo Ruiz on 2010-08-17
This is an example of what happens randomly when I try in 2 computers running Ubuntu Lucid + Samba:


```
marcelo@marcelo-laptop:~$ smbclient -L //erin-laptop
Enter marcelo's password: 

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (erin-laptop server (Samba, Ubuntu))
	music           Disk      
	pictures        Disk      
	backup m        Disk      
	2010            Disk      

	Server               Comment
	---------            -------
	ERIN-LAPTOP          erin-laptop server (Samba, Ubuntu)
	MARCELO-LAPTOP       marcelo-laptop server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	FREEBIRD             MARCELO-LAPTOP
marcelo@marcelo-laptop:~$ smbclient -L //erin-laptop
Enter marcelo's password: 
Connection to erin-laptop failed (Error NT_STATUS_UNSUCCESSFUL)
marcelo@marcelo-laptop:~$
```

I issued the second command right when the first returned...

---

### Post by Marcelo Ruiz on 2010-08-17
From the other computer, I can get things like the following (also issuing the commands with almost no waiting time between them):

```
erin@erin-laptop:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.101   MARCELO-LAPTOP [	FREEBIRD      ]
192.168.1.106   ERIN-LAPTOP   +[FREEBIRD] [Unix] [Samba 3.4.7]
erin@erin-laptop:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.101   unknown nis name
192.168.1.106   ERIN-LAPTOP   +[FREEBIRD] [Unix] [Samba 3.4.7] 
erin@erin-laptop:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.106   ERIN-LAPTOP   +[FREEBIRD] [Unix] [Samba 3.4.7]
erin@erin-laptop:~$

```

---

### Post by bab1 on 2010-08-17
Marcelo,

My guess is that the name resolve issue is not your problem.  At least not by what you have posted below. Have you checked the logs to see what is the the reason for the error: "Connection to erin-laptop failed (Error NT_STATUS_UNSUCCESSFUL)"


> **Marcelo Ruiz said:**
> This is an example of what happens randomly when I try in 2 computers running Ubuntu Lucid + Samba:

```
marcelo@marcelo-laptop:~$ smbclient -L //erin-laptop
Enter marcelo's password: 

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (erin-laptop server (Samba, Ubuntu))
	music           Disk      
	pictures        Disk      
	backup m        Disk      
	2010            Disk      

	Server               Comment
	---------            -------
	ERIN-LAPTOP          erin-laptop server (Samba, Ubuntu)
	MARCELO-LAPTOP       marcelo-laptop server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	FREEBIRD             MARCELO-LAPTOP
marcelo@marcelo-laptop:~$ smbclient -L //erin-laptop
Enter marcelo's password: 
Connection to erin-laptop failed (Error NT_STATUS_UNSUCCESSFUL)
marcelo@marcelo-laptop:~$
```

I issued the second command right when the first returned...

---

### Post by Marcelo Ruiz on 2010-09-12
Hi,

Thanks for your message! 
Sorry for the late reply, but the notification e-mail went straight to the spam folder, which I checked today.
I don't see the reason in the log files for the infamous NT_STATUS_UNSUCCESSFUL.
I some threads I read, they explain that is a general error that can mean anything...
What is weird is that it seems to work randomly under Ubuntu, but it works fine in this very same computer with Windows 7.
Thanks again!

---

