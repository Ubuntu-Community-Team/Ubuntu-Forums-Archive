---
title: "Samba share frustrations"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by gundo on 2009-10-26
Hello all...

Im hoping someone can help..

Ive set up an old PC with ubuntu 9.04 server edition, and during setup chose to install the samba server...

I have put the following in my /etc/samba/smb.conf

[public]
path = /home/mark/public
available = yes
browsable = yes
public = yes
writable = yes
create mask = 0777
directory mask = 0777
guest ok = yes

Other computers on my LAN can see the public share, but when I double click the icon i get an error saying that public could not be mounted...

Would appreciate any help...

Thanks a lot,
Mark

---

### Post by Iowan on 2009-10-26
I presume you set up **mark** as a Linux user and a Samba user and that you're logging in (connecting) as **mark**.

---

### Post by gundo on 2009-10-26
Hi, 

mark is the user I made during setup, im not sure how I make sure mark is a samba user?

On my desktop installation samba shares just seem to work when I set them up with the same config as above, is there something extra I have to do on the server installation?

Thanks a lot,
Mark

---

### Post by Iowan on 2009-10-26
I just tried from my server (via SSH terminal): **sudo smbpasswd -e myuser**
Machine responded: myuser enabled.
When I tried: **sudo smbpasswd -e nonexist**
Machine responded: Failed to find user nonexist in passdb backend.

---

### Post by swerdna on 2009-10-27
Just for your interest: "public = yes" is a duplicate of "guest ok = yes".

Guests should be able to mount because access for guests is allowed. -- unless there's a problem in the [global] stanza. Can you post an abbreviated smb.conf by running this command and posting the result:[LIST]
[*]testparm -s
[/LIST]

Oh and just to be thorough, what's the results for these two commands as well please:

[LIST]
[*]ls -l /home/mark | grep public
[*]sudo pdbedit -L
[/LIST]

---

