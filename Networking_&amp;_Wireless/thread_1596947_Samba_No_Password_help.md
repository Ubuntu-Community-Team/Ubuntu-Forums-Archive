---
title: "Samba No Password help"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by granade on 2010-10-14
Hello all,


I recently finished installing 10.10 64bit desktop and im trying to get samba setup. I have had it configured on 9.04 server with no password and working great.

I keep getting this error message from my Win 7 laptop:

Windows cannot access \\share\share

Check the spelling of the name...blah blah

error code 0x800070043

Here is my smb config:


[global]
        workgroup = tuxnet
        netbios name = tuxbox
        security = share
	guest account = nobody


  
[Repository]
	path = /media/Share
        available = yes
	browseable = yes
	public = yes
	writable = yes
	force user = nobody
	force group = nogroup
	create mask = 0777
	directory mask = 0777


Am i missing anythgin?


Thanks

G!:popcorn:

---

### Post by granade on 2010-10-15
Im going to try to do a fresh install again. Since i just installed it last night anyway...

---

### Post by luvshines on 2010-10-15
> **granade said:**
> Hello all,
Windows cannot access \\share\share

Check the spelling of the name...blah blah

error code 0x800070043


Can you post the exact address you are trying to access it with from Win7 and the error is reports ?

---

### Post by sikander3786 on 2010-10-15
Are you able to ping the Ubuntu box from Windows machine?

Are you sure there are no firewalls involved?

---

### Post by granade on 2010-10-15
Thank you both for you responses!


I have resolved the problem...


WIN 7 is the issue!


If you follow the steps below it should work for you:

[b]Control Panel - Administrative Tools - Local Security Policy

Local Policies - Security Options



Network security: LAN Manager authentication level
Send LM & NTLM responses

Minimum session security for NTLM SSP (there are 2 of these-disable both)
Disable Require 128-bit encryption[/b]


I was able to connect to the shares once i changed the above settings. 

:guitar:

---

### Post by pimpys on 2010-10-16
> **granade said:**
> Thank you both for you responses!


I have resolved the problem...


WIN 7 is the issue!


If you follow the steps below it should work for you:

[B]Control Panel - Administrative Tools - Local Security Policy

Local Policies - Security Options



Network security: LAN Manager authentication level
Send LM & NTLM responses

Minimum session security for NTLM SSP (there are 2 of these-disable both)
Disable Require 128-bit encryption[/B]


I was able to connect to the shares once i changed the above settings. 

:guitar:
Thanks I had the same errors ! You rocks.

---

### Post by gordintoronto on 2011-01-20
What version of Windows contains that option?

---

