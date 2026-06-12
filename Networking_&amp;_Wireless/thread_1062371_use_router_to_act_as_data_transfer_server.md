---
title: "use router to act as data transfer server"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by Stargazer989 on 2009-02-06
hey guys/girls, i want to use my Linksys wireless router to connect to my Ubuntu laptop from my Windows XP desktop so i can grab some files(anime) from it. 
the files are contained on an external hard drive.
the only point where both my desktop and laptop "connect" is the linksys router.
would it be possible to connect to the laptop(ubuntu 8.10) and grab those files(or just watch them from there(stream)) and drop them onto my desktop(WinXP) ?

---

### Post by dburnett77 on 2009-02-06
Yes, there is.  icecast is a package and I believe they have a server that will automate this.  Also, try any of the programs from the apache-lite suite, they'll do it.

---

### Post by Stargazer989 on 2009-02-06
is there anything i should know about ? like if i have to set something up on the windows side... or if i have to regulate something in icecast or apache-lite suite so nothing will be leaked to the outside ?

---

### Post by Spherical on 2009-02-06
doesn't the external disk have a UUID?
if it does, you can add it to fstab
all you have to do then is activate and mount it, add it to your samba shares (the mountpoint that is)

works for me, when I boot my home-server, I might be able to tell you more (I'm too lazy to get up now, sorry)

---

### Post by Stargazer989 on 2009-02-06
how do i find this UUID ? (it's a USB external)

and what's this Samba shares ?

---

### Post by Stargazer989 on 2009-02-06
ok, so, um, i right-clicked on Disk(the ext hdd) and clicked "share folder" or w/e it was... but when i map network drive on XP i keep getting "...Does not accept remote requests..." "...do not have permissions..." etc. i have the guest thing enabled.

any ideas ?

---

### Post by cariboo on 2009-02-06
You have to install Samba. Have a look at this [howto]("http://ubuntuforums.org/showthread.php?t=202605").

Jim

---

### Post by Stargazer989 on 2009-02-15
ok, so... i edited /etc/samba/smb.conf
i edited the example at the bottom of the file(the one for CD-ROM) to fit my needs. > [externalDriveAnime]
   comment = Adam's Drive
   read only = no
   locking = no
   path = /media/disk
   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
   preexec = /bin/mount /media/disk
   postexec = /bin/umount /media/disk didn't use the /etc/fstab part. but this *should* suffice, right ?

---

### Post by Stargazer989 on 2009-05-20
gonna bring back the dead and ask something else:

I'm trying to connect to a vista machine... used cariboo907's link but i'm stuck on "Step 2," the part where i go on vista and tinker with things. I cannot find an 'LAN Connections' menu or 'Internet Connections' menu, either.

any ideas?

---

### Post by lisati on 2009-05-20
> **Stargazer989 said:**
> gonna bring back the dead and ask something else:

I'm trying to connect to a vista machine... used cariboo907's link but i'm stuck on "Step 2," the part where i go on vista and tinker with things. I cannot find an 'LAN Connections' menu or 'Internet Connections' menu, either.

any ideas?

(Lisati turns on Vista machine and shares some thoughts while waiting for it to boot, whoops distracted by trying to think of an answer and missed Grub)
On my laptop with Vista there is a "Network" option on the "Start" menu which shows the machines that Vista recognizes as being available for connection. It also has some options for tinkering with the settings.
I might have to come back to this one, Mrs Lisati wants to talk....anyone else?

---

### Post by lisati on 2009-05-20
OK. I've got my Vista machine up and running, and the link open in another tab..
I think the link is aimed more at XP than Vista.
Sorry about the delay.... I had to go looking for how to do it on my machine
To tinker with WINS support (this sounds a little long-winded and if anyone has a quicker way, suggestions would be appreciated! I haven't tinkered with Vista's settings much): On your control panel, look for "Network and Internet". Click on "Network and Sharing Center". Then click on "view status" for your local area connection (LAN). Click on the "properties" button. You might be asked permission to continue. Select "Internet Protocol v4 (TCP/IPv4)" and click on the "properties" button. Click on the "advanced" button then the "WINS" tab. You can then choose an appropriate setting and close the dialog boxes - the default on my system is to use the NETBIOS etting from the DHCP server....

---

### Post by Stargazer989 on 2009-05-21
something new: instead of windows just idling when i try to connect, it's actually given me something! a [Network Error]("http://ubuntuforums.org/attachment.php?attachmentid=114586&stc=1&d=1242946322")

---

