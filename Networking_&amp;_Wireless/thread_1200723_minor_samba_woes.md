---
title: "minor samba woes"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by johnh10000 on 2009-06-30
Hi gang

Have a ubuntu jaunty desktop, one winxp, and a partcialy upgraded jaunty server box.

Can "see" and connect to them on jaunty desktop.

On windoz, it clames the share I am trying to connect to, on ubuntu is :

\\Tux is not accessible. You might not have permission yo use this network resourse contact admin.

On ubuntu I can connect to it fine.

---

### Post by superprash2003 on 2009-06-30
have you tried accessing via ip instead of local hostname

---

### Post by johnh10000 on 2009-06-30
> **superprash2003 said:**
> have you tried accessing via ip instead of local hostname

sorry gang, this is via samba

Oh and from the tux box to win it's fine. the other way round is the problem.

don't ask about tux2, it says it's not on any network but can connect to the inet.

---

### Post by Boondoklife on 2009-06-30
> **johnh10000 said:**
> sorry gang, this is via samba

Oh and from the tux box to win it's fine. the other way round is the problem.

don't ask about tux2, it says it's not on any network but can connect to the inet.

Yea we know it is samba, but did you try to browse to the share on your doz box using the ubuntu box's IP? \\192.168.1.2

---

### Post by johnh10000 on 2009-06-30
> **maletek said:**
> Yea we know it is samba, but did you try to browse to the share on your doz box using the ubuntu box's IP? \\192.168.1.2

I hadn't but.. I tried //192.168.1.3 that came back with my web page
\\192.... send you can't spell

---

### Post by swerdna on 2009-06-30
Two things to check:
The workgroup name in [global] stanza of smb.conf must be the same as the workgroup name on all the other machines.
You might have a share on Ubuntu that requires username/password to enter but no Linux users enrolled in the Samba user database.

---

### Post by Boondoklife on 2009-06-30
> **johnh10000 said:**
> I hadn't but.. I tried //192.168.1.3 that came back with my web page
\\192.... send you can't spell

On the windoes box try `\\192.168.1.2` Pay special attention to the direction of the slashes for if you try it like you wrote, that Explorer will think it is a website.

What web page came up by the way, and is that a page hosted on the ubuntu box? Make sure you replace the 192.168.1.2 with the ip of your ubuntu box.

---

### Post by johnh10000 on 2009-06-30
> **swerdna said:**
> Two things to check:
The workgroup name in [global] stanza of smb.conf must be the same as the workgroup name on all the other machines.
You might have a share on Ubuntu that requires username/password to enter but no Linux users enrolled in the Samba user database.

I know the workgroup name is correct, because it works the otherway round.  I have a share on the windoz box of the dvd and that works.  

To check out your other theroy I removed all the shares on this box bar the print$, and the same result.

Considering uninstalling samba and reinstalling it.  As for another problem I have, I installed the server version of ubuntu on an another box on the net and windoz can see and enter the workgroup fine.

For win I do reinstall samba, is it needed to have samba users, as I want the shares visible network wide (local).  the other box will be returning to a winxp, after sorting out my other problem.

---

### Post by johnh10000 on 2009-06-30
> **maletek said:**
> 

What web page came up by the way, and is that a page hosted on the ubuntu box? Make sure you replace the 192.168.1.2 with the ip of your ubuntu box.
 I did close 192.168.1.3 ;)  my one hosted on that Ip

---

### Post by johnh10000 on 2009-06-30
Setting up samba (2:3.3.2-1ubuntu3) ...
--------- IMPORTANT INFORMATION FOR XINETD USERS ----------
The following line will be added to your /etc/inetd.conf file:

#<off># netbios-ssn	stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/smbd

If you are indeed using xinetd, you will have to convert the
above into /etc/xinetd.conf format, and add it manually. See
/usr/share/doc/xinetd/README.Debian for more information.
Suggested entry (automatically converted using itox):

-----------------------------------------------------------

 * Starting Samba daemons                                                [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba

And its always worked b4 :(

---

### Post by superprash2003 on 2009-07-01
you have to enter smb://192.168.x.x under places->COmputer ( near location )

---

### Post by johnh10000 on 2009-07-01
> **superprash2003 said:**
> you have to enter smb://192.168.x.x under places->COmputer ( near location )

thanks I will.

the bit I don't get is it works one way not the other

---

### Post by johnh10000 on 2009-07-01
> **johnh10000 said:**
> thanks I will.

the bit I don't get is it works one way not the other

It works on tux2 between windoz and it self, tux don't work there either.

So im going to copy the config from tux2 to tux, if not try an reinstall again...

---

