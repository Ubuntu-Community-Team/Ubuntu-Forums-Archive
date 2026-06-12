---
title: "Win7 can't see Ubuntu Server"
date: 2012-01-01
forum: Networking &amp; Wireless
---

### Post by iDeals on 2012-01-01
Admittedly I'm a newbie to Ubuntu.  I have install samba and verified it is running on my Ubuntu machine, but my Win7 laptop cannot see the server under networks.  Any ideas?

---

### Post by inobe on 2012-01-01
> **iDeals said:**
> I have install samba and verified it is running on my Ubuntu machine

samba needs configuring to get the best results.


we haveto to know if you need any sort of security, password and user name authentication, also if you wish to share a specific directory?

answer those two questions, then we can get you started.

---

### Post by collisionystm on 2012-01-01
> **iDeals said:**
> Admittedly I'm a newbie to Ubuntu.  I have install samba and verified it is running on my Ubuntu machine, but my Win7 laptop cannot see the server under networks.  Any ideas?

edit your smb.conf

the line that says wins server =

set it to your router

make sure your router has net bios enabled

---

### Post by iDeals on 2012-01-01
> **inobe said:**
> samba needs configuring to get the best results.


we haveto to know if you need any sort of security, password and user name authentication, also if you wish to share a specific directory?

answer those two questions, then we can get you started.


I configured a user and password for samba.  

so in smb.conf under authentication I changed it to:

security = user
username map = /etc/samba/smbusers

in directory smbusers I have:

<username> = <username>  

I'm just using <username> for reference, it isn't what it is set to.


wins server is set to

wins server = w.x.y.z.

---

### Post by iDeals on 2012-01-01
okay - I updated my firmware on my router and voila - I can now see the server.  The only problem is I can't access anything on it. 

My friend set up the following under [Share Definitions]


[Media]

path = /home/<servername>/Media
guest ok = yes
browseable = yes


this is what appears on Win7 computer.  I changed the casing of [Media] to make sure that is what it is pointed at and the change took affect on my win7 machine.  Any ideas why this wouldn't be accessable?

---

### Post by SeijiSensei on 2012-01-02
First, a simple question.  Is there indeed a Linux user named "servername" that owns the /home/servername directory?

If so, I'm guessing /home/servername has 700 permissions; that is, read/write/list for the owner "servername" and no permissions for anyone else.  Try running the command "sudo chmod 755 /home/servername" and see if that helps.  You can also give the "force user" and "force group" commands a try like this:

```

[Media]
path = /home/<servername>/Media
guest ok = yes
browseable = yes
force user = servername
force group = servername

```

That tells Samba to read and write to the resource as the user servername regardless of the Win7 username of the person mounting the share.

One other basic question... You're not including the [] characters in Windows, right?  You should be trying to mount \\servername\Media, not \\servername\[Media].  Also if you're getting a "not found" response when connecting, try using the IP address instead of servername like this, \\10.1.1.1\Media.

---

### Post by iDeals on 2012-01-02
> **SeijiSensei said:**
> First, a simple question.  Is there indeed a Linux user named "servername" that owns the /home/servername directory?

If so, I'm guessing /home/servername has 700 permissions; that is, read/write/list for the owner "servername" and no permissions for anyone else.  Try running the command "sudo chmod 755 /home/servername" and see if that helps.  You can also give the "force user" and "force group" commands a try like this:

```

[Media]
path = /home/<servername>/Media
guest ok = yes
browseable = yes
force user = servername
force group = servername

```That tells Samba to read and write to the resource as the user servername regardless of the Win7 username of the person mounting the share.

One other basic question... You're not including the [] characters in Windows, right?  You should be trying to mount \\servername\Media, not \\servername\[Media].  Also if you're getting a "not found" response when connecting, try using the IP address instead of servername like this, \\10.1.1.1\Media.


sorry, I was just using servername as a placeholder... but it all comes to the same.  I will try implementing the changes you suggested.  The other thing is I didn't have to mount the the network drive, the computer just appeared in my network.  Is that part of the problem?

---

### Post by iDeals on 2012-01-02
[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") you are awesome! that worked.  Thanks so much everyone for your help.

Cheers!

---

