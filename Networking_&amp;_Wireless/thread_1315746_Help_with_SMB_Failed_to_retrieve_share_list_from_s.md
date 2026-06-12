---
title: "Help with SMB: Failed to retrieve share list from server"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by sb73542 on 2009-11-05
Hi,

I am running Ubuntu 9.10.  Another user on my network is running Ubuntu 8.10.  The two are on the same workgroup, connected wirelessly via a dd-wrt router.  When I try to access the other computer's network shares, it just tells me "Failed to retrieve share list from server".  This is the output of smbtree:

WORKGROUP
	\\COMPUTERNAME   		computername server (Samba, Ubuntu)
cli_start_connection: failed to connect to COMPUTERNAME<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\LAPTOPNAME           		laptopname server (Samba, Ubuntu)
		\\LAPTOPNAME\Deskjet-3900   	HP Deskjet 3900
		\\LAPTOPNAME\print$         	Printer Drivers
		\\LAPTOPNAME\Public         	
		\\LAPTOPNAME\IPC$           	IPC Service (LAPTOPNAME server (Samba, Ubuntu))

Any ideas?  Thanks!

---

### Post by Iowan on 2009-11-05
Can you **ping** the machine (hostname or address)?
Does [this]("http://ubuntuforums.org/showthread.php?t=1169149") one help?

---

### Post by sb73542 on 2009-11-05
> **Iowan said:**
> Can you **ping** the machine (hostname or address)?
Does [this]("http://ubuntuforums.org/showthread.php?t=1169149") one help?

Thanks for the reply!  I can ping the IP address but not the hostname "COMPUTERNAME".  Any idea which of those suggestions in the link you sent me might be the most appropriate?

EDIT:  I just realized now what the problem is:  The error says "failed to connect to COMPUTERNAME<20> (0.0.0.0)", so obviously it doesn't know the IP address of COMPUTERNAME.  So, how do I make it know the COMPUTERNAME?  I'd like to do this correctly, instead of just adding it to the hosts file.  Thanks!

---

### Post by Iowan on 2009-11-05
Dunno if dd-wrt router uses **dnsmasq** (or something similar). if it does, [this]("http://ubuntuforums.org/showpost.php?p=8245959&postcount=14") may help.

---

### Post by sb73542 on 2009-11-09
Hmmm, yes, my router is running dnsmasq.  But it must not be configured correctly.  It can't resolve the IP addresses of COMPUTERNAME.

---

### Post by sb73542 on 2010-04-05
Well, turns out this is the simple solution:

[http://www.adamsmash.com/?p=345](http://www.adamsmash.com/?p=345)

If you want to see this fixed, you can mark this bug as affecting you: [https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/555916](https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/555916)

---

### Post by l.clayton.parker on 2010-05-03
Find the line in smb.conf

    name resolve order = lmhosts host wins bcast

and change it to:

    name resolve order = lmhosts wins bcast host

That solved the problem for me. YMMV

Lee Parker
chief cook, bottle washer and sometime sysadmin

---

### Post by stanley82 on 2011-04-23
> **l.clayton.parker said:**
> Find the line in smb.conf

    name resolve order = lmhosts host wins bcast

and change it to:

    name resolve order = lmhosts wins bcast host

That solved the problem for me. YMMV

Lee Parker
chief cook, bottle washer and sometime sysadmin

Thanks fixed it for me.  Been bugging me for ages.:)

---

### Post by studiogrynn on 2011-06-30
> **l.clayton.parker said:**
> Find the line in smb.conf

    name resolve order = lmhosts host wins bcast

and change it to:

    name resolve order = lmhosts wins bcast host

That solved the problem for me. YMMV

Lee Parker
chief cook, bottle washer and sometime sysadmin

Freaking genius! I have been dealing with this for months, and have invested countless hours. Sweet and simeple - Thank you!:popcorn:

---

