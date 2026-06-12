---
title: "How to set workgroups?"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by shade5 on 2009-05-23
Hello.



Where do I set my workgroups?



When I use 



```
smbclient -L //myIP/

```


there are two workgroups listed. But I do not know where to set these.



I already set in /etc/samba/smb.conf 



```
workgroup = myworkgroup
```



But smbclient -L //myIP/ told me that myworkgroup is actually my domain. Here is the output



> Domain=[MYWORKGROUP] OS=[Unix] Server=[Samba 3.0.28a]



	Server               Comment

	---------            -------



	Workgroup            Master

	---------            -------

	MYWORKGROUP2             Laptop

	MYWORKGROUP            Desktop



As you can see I also joined my Laptops Workgroup. But I never set this by myself. Did it happen automatically when I accessed data from my lap?



I also found this command: smbclient -W. The man said it would set workgroups. However 



> smbclient -W myworkgroup3 //myip/



did not work.



How do I set my workgroups and how does the -W parameter work? 



Thanks.

---

### Post by capscrew on 2009-05-23
> **shade5 said:**
> Hello.

Where do I set my workgroups?

In the /etc/samba/smb.conf file, just like you say.
> 

When I use 

```
smbclient -L //myIP/

```

there are two workgroups listed. But I do not know where to set these.

On the other hosts that are sharing files.
> 

I already set in /etc/samba/smb.conf 

```
workgroup = myworkgroup
```


Only on the local host.
> 

But smbclient -L //myIP/ told me that myworkgroup is actually my domain...
The DOMAIN is your COMPUTER NAME> 

As you can see I also joined my Laptops Workgroup. But I never set this by myself. Did it happen automatically when I accessed data from my lap?

Workgroups are just used to associate all the shared hosts.  It its done by the browsing routines by the host that is the browsing master.> 

I also found this command: smbclient -W. The man said it would set workgroups. However did not work.

How do I set my workgroups and how does the -W parameter work? 

You don't.  The -W is to define the workgroup for the session only.  It is defined as the netbios name of the host for that session.
> 



Thanks.

---

