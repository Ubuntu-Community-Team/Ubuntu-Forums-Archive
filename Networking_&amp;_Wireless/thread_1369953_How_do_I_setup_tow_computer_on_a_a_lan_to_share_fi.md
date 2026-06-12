---
title: "How do I setup tow computer on a a lan to share files?"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by Scott O'Nanski on 2010-01-01
Hi, I'm trying to set up my Desktop (wired) and Laptop (wireless) so I can share files between the two. In windows, I normally just run the network wizrd and it sets everything up on both machines.

Ubuntu, not so easy...

I can't find a 'how to'. I'm looking for an easy GUI solution.

Anyone?

---

### Post by eddietours on 2010-01-01
look under network

---

### Post by Scott O'Nanski on 2010-01-01
> **eddietours said:**
> look under network

I did.


Anyone else?

---

### Post by VastOne on 2010-01-01
> **Scott O'Nanski said:**
> Hi, I'm trying to set up my Desktop (wired) and Laptop (wireless) so I can share files between the two. In windows, I normally just run the network wizrd and it sets everything up on both machines.

Ubuntu, not so easy...

I can't find a 'how to'. I'm looking for an easy GUI solution.

Anyone?

Are they both Ubuntu?

---

### Post by Scott O'Nanski on 2010-01-01
> **VastOne said:**
> Are they both Ubuntu?


Yep, both machines are running 9.10. I just installed Karmic on both in the past couple days.

Should I start over from fresh installs to make it easy to trouble shoot? Or, is that just added effort?

---

### Post by eddietours on 2010-01-01
can you ping the other computer

---

### Post by VastOne on 2010-01-01
> **Scott O'Nanski said:**
> Yep, both machines are running 9.10. I just installed Karmic on both in the past couple days.

Should I start over from fresh installs to make it easy to trouble shoot? Or, is that just added effort?

I would not think so if both are loaded OK.  

I am assuming you are using both machines connected to the same router?  Can you ping one machine from the other?

---

### Post by Morbius1 on 2010-01-01
I don't understand the question. Are you trying to share folders between two ubuntu computers?

Open Nautilus > Right click on a folder in your /home folder > Select "Sharing Options" > check all the boxes > Select "Create share"

It's exactly like it is in windows.

Go to the other Ubuntu machine , open nautilus , and select Network

---

### Post by VastOne on 2010-01-01
SSH is also an option and does not require a full blown samba install and I find it (SSH) faster

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by Scott O'Nanski on 2010-01-01
> **Morbius1 said:**
> I don't understand the question. Are you trying to share folders between two ubuntu computers?

Open Nautilus > Right click on a folder in your /home folder > Select "Sharing Options" > check all the boxes > Select "Create share"

It's exactly like it is in windows.

Go to the other Ubuntu machine , open nautilus , and select Network

I'm trying to setup both computer so I can access each from the other. They show up in the Network folder, but I can't browse their contents.

I keep getting this message from either machine;

Unable to mount location: Failed to receive the share list from the server.

I set the folders I want to share on both machines.

---

### Post by Scott O'Nanski on 2010-01-01
> **eddietours said:**
> can you ping the other computer

Yep.

From both machines.

---

### Post by Morbius1 on 2010-01-01
Please post the output of the following commands from the desktop PC:

Open **Terminal**
Type **smbtree**
Type **findsmb**
Type **nmap -sT 192.168.0.100/22**

[I]Change 192.168.0.100 to the ip address of the desktop.

[COLOR=Blue]EDIT: you may not have nmap installed but by issuing the command it will ask you if you want to install it - you do.[/COLOR]

[/I]

---

### Post by Scott O'Nanski on 2010-01-01
> **Morbius1 said:**
> Please post the output of the following commands from the desktop PC:

Open **Terminal**
Type **smbtree**
Type **findsmb**
Type **nmap -sT 192.168.0.100/22**

[I]Change 192.168.0.100 to the ip address of the desktop.

[COLOR=Blue]EDIT: you may not have nmap installed but by issuing the command it will ask you if you want to install it - you do.[/COLOR]

[/I]

```
smbtree
```

Returned

```

WORKGROUP
	\\SYSTEM-LAPTOP-X		system-laptop-x server (Samba, Ubuntu)
cli_start_connection: failed to connect to SYSTEM-LAPTOP-X<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\SYSTEM-DESKTOP-X		system-desktop-x server (Samba, Ubuntu)
		\\SYSTEM-DESKTOP-X\scott desktop  	
		\\SYSTEM-DESKTOP-X\IPC$           	IPC Service (system-desktop-x server (Samba, Ubuntu))
		\\SYSTEM-DESKTOP-X\Videos         	
		\\SYSTEM-DESKTOP-X\print$         	Printer Drivers

```

And

```

findsmb

```

Returned

```


                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.2.2     SYSTEM-DESKTOP-+[WORKGROUP] [Unix] [Samba 3.4.0]
192.168.2.3     SYSTEM-LAPTOP-X [	WORKGROUP     ]

```

And

```

nmap -sT 192.168.2.2/22

```

Returned

```

Starting Nmap 5.00 ( http://nmap.org ) at 2010-01-01 19:32 EST
Interesting ports on 192.168.2.1:
Not shown: 999 filtered ports
PORT   STATE SERVICE
80/tcp open  http

Interesting ports on 192.168.2.2:
Not shown: 994 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
5900/tcp open  vnc
9091/tcp open  unknown

Interesting ports on 192.168.2.3:
Not shown: 998 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1024 IP addresses (3 hosts up) scanned in 93.33 seconds
s


```

---

### Post by confusedstingray on 2010-01-01
from the out put \\SYSTEM-LAPTOP-X has nothing shared if it shared not accessable by the workgroup

---

### Post by Morbius1 on 2010-01-02
Your machine names in one case is at the legal length limit and in the other is beyond the limit. It must be 15 characters or less. The easiest way to fix this is like this:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

And all the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
netbios name = DESKTOP-X
```[COLOR=Blue]*It doesn't have to be DESKTOP-X, but it must have 15 characters or less with no spaces please.*[/COLOR]

Save the file, exit gedit, and back in the Terminal type:[B] sudo service samba restart

[/B]Wait a few minutes and see if sharing works.

---

