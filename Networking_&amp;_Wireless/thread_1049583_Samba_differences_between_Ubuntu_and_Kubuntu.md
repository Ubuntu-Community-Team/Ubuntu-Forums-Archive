---
title: "Samba differences between Ubuntu and Kubuntu"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by aj7360 on 2009-01-24
Can someone please explain why Samba works so differently on Kubuntu versus Ubuntu?

I've been using Ubuntu for a while, editing some files on an XP box. The folder on the XP box is set up appropriately for sharing and changing.

Thought I'd try out Kubuntu as I like the appearance and the way it works.

BUT... while I can browse and open files on the XP box from within Kubuntu, I can't save them.  Kubuntu sees them as "read only".

I install Ubuntu twice, the second time to upgrade hardware and this time I goofed and ended up putting it into the "WORKGROUP" workgroup instead of "MSHome". I'm thinking this might be why Kubuntu won't write, but can for the life of me figure out how to change it to MSHome... at least not in Kubuntu.

For the time being I'm back in Ubuntu until I can get this sorted out.

Any help would be appreciated immensely.

Thanks

AJ

---

### Post by jimv on 2009-01-24
Probably will be easiest to just change the config file for samba and put your workgroup in there.

The file is /etc/samba/smb.conf

The line is Workgroup =

---

### Post by aj7360 on 2009-01-24
> **jimv said:**
> Probably will be easiest to just change the config file for samba and put your workgroup in there.

The file is /etc/samba/smb.conf

The line is Workgroup =

Thanks. That did work. And now I can see the Kubuntu/Ubuntu machine in the MSHOME group from the XP box.

But I still can't write any of the XP files from Kubuntu while I CAN from Ubuntu. 

Very strange.


Thanks again.

---

### Post by cariboo on 2009-01-24
Try installing **smb4k**, to see if that makes any difference. Smb4k is in the repositories.

Jim

---

### Post by aj7360 on 2009-01-24
> **cariboo907 said:**
> Try installing **smb4k**, to see if that makes any difference. Smb4k is in the repositories.

Jim

Thank you!!!

That worked AND it is smoking fast browsing the Windows network.

Sweet!!

\\:D/

---

