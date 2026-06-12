---
title: "Which smb.conf?"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by atwin on 2009-02-08
I am sharing a directory on Intrepid Ibex (ubuntu 8.10) and I need to know which smb.conf file ubuntu is using!

I know my way around smb.conf files and I can't find the one it is using to share my documents folder (i just used the right-click and share option dialog to set the share).

Where can I find that particular smb.conf file?


With thanks,

atwin.

---

### Post by FishRCynic on 2009-02-08
ubuntu default should be
 /etc/samba/smb.conf

---

### Post by madverb on 2009-02-08
/etc/samba/smb.conf?

---

### Post by atwin on 2009-02-08
Yes, I checked that file and it doesn't contain any reference to the [documents] share which appear on the network!?  That's what puzzling me!

Where is ubuntu putting the definition for that share?

---

### Post by capscrew on 2009-02-08
> ...i just used the right-click and share option dialog to set the share...

The above is the tipoff.  If you use the GUI (Nautilus) then the configuration is saved at:```
/var/lib/samba
```

The /etc/samba/smb.conf file is still used to set the workgroup.

---

### Post by cariboo on 2009-02-08
THe way Ubuntu has configured sharing, it doesn't use an smb.conf file, all the files and settings are located in /var/lib/samba.

Jim

---

### Post by capscrew on 2009-02-08
> **cariboo907 said:**
> THe way Ubuntu has configured sharing, it doesn't use an smb.conf file, all the files and settings are located in /var/lib/samba.

Jim

To expand on what Jim has said.  This is a Gnome convention rather that Ubuntu.  

In addition using CLI tools you might get differing results than using the GUI.  This is due to differing libs employed when viewing the share.

---

### Post by FishRCynic on 2009-02-08
yep tried it and it works - never shared that way before today.


out of curiousity if you boot in xbuntu or kubuntu are these gnome shares still used?

---

### Post by capscrew on 2009-02-08
> **FishRCynic said:**
> yep tried it and it works - never shared that way before today.


out of curiousity if you boot in xbuntu or kubuntu are these gnome shares still used?

I don't know for sure.  It depends on whether they use the Gnome libs.

---

### Post by atwin on 2009-02-09
Yep, /var/lib/samba/usershares is where everything is stored.

The format is smb.conf like except for one line.

path=/home/atwin/Documents
comment=
usershare_acl=S-1-1-0:R  <---- can anyone explain!?
guest_ok=y


Thanks loads everyone for all your help...Cheers.

---

### Post by capscrew on 2009-02-09
> usershare_acl=S-1-1-0:R <---- can anyone explain!?

Hahaha -- a little Googling reveals the following:
[URL="http://support.microsoft.com/kb/243330"][COLOR="RoyalBlue"]Well-known security identifiers in Windows operating systems[/COLOR]
[/URL]

Note the listing for "everyone"

Edit: > A sample usershare file

#VERSION 1

path=/home/jeremy

comment=This is a usershare

usershare_acl=S-1-1-0:R

guest_ok=Y

A sample usershare file

The first line allows file revisions (we'll never make that mistake again).

The &#8220;path&#8221; and &#8220;comment&#8221; lines are identical to the way they're used in the standard smb.conf.

The &#8220;path&#8221; parameter must be absolute (ie. start with &#8220;/&#8221;)

The &#8220;usershare_acl&#8221; entry specifies the ACL associated with the share.

Permitted values are &#8220;R&#8221; for read-only, and &#8220;F&#8221; for full access, D for deny access.

SID is used instead of UNIX uid/gid so smbd doesn't have to do uid -> SID mapping on parsing the file.

guest_ok determines guest access.

The above is from:
[http://http://209.85.173.132/search?q=cache:BQcjiDtUR7wJ:gd.tuwien.ac.at/infosys/servers/samba/slides/lwny2007.odp+usershare_acl%3DS-1-1-0:R&hl=en&ct=clnk&cd=2&gl=us]("http://http://209.85.173.132/search?q=cache:BQcjiDtUR7wJ:gd.tuwien.ac.at/infosys/servers/samba/slides/lwny2007.odp+usershare_acl%3DS-1-1-0:R&hl=en&ct=clnk&cd=2&gl=us")

---

