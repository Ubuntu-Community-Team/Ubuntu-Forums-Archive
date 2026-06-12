---
title: "samba not working in 8.10"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by snorkytheweasel on 2009-03-30
intrepid ibex:

From dapper through hardy samba has always worked perfectly after I tweaked smb.conf to id the workgroup (or domain) and to set security. 

In this case I'm using workgroup=surfrider and security=user.

I cannot see the windows side of the network. Error is
"failed to retrieve share list from server"

I've installed latest updates, but still get the error message.

What am I missing?

---

### Post by fmw on 2009-03-30
The same thing I'm misssing.  No one on the internet has been able to solve the problem.  I'm trying to decide whether or not to go down to 8.04.  Did you have 8.04 and did it work properly for you?

---

### Post by BFG on 2009-03-30
From searching on google / boards, this may be due to a recent update.

I've always been able to connect to samba shares, and can still access CIFS mounts, but as of the weekend I can no longer connect to samba shares on PCs on the network.

findsmb shows they are there, but I just can;t connect.  I get 
    failed to retrieve share list from server

---

### Post by Iowan on 2009-03-30
My aging Gutsy machine started having problems lately (update?), but shares still work with smb://<ipaddress>/sharename.

---

### Post by snorkytheweasel on 2009-03-30
Yes. from dapper through 8.04 samba worked with little effort (2 tweaks to smb.conf)

In the past I used Dolphin to access the samba shares. Now I'm using nautilus, but that can't be the problem (or can it...)

---

### Post by capscrew on 2009-03-30
> **BFG said:**
> From searching on google / boards, this may be due to a recent update.

I've always been able to connect to samba shares, and can still access CIFS mounts, but as of the weekend I can no longer connect to samba shares on PCs on the network.

findsmb shows they are there, but I just can;t connect.  I get 
    failed to retrieve share list from server

This is a Gnome/Nautilus problem, not Samba at all.  The CIFS mount and smbclient/findsmb use libs different than Gnome.

It would be interesting for you to try and make a new share.  All the Gnome/Nautilus shares are at /var/lib/samba.  If you can make a new share using Nautilus it will show up there.

---

### Post by snorkytheweasel on 2009-03-30
> **capscrew said:**
> This is a Gnome/Nautilus problem, not Samba at all.  The CIFS mount and smbclient/findsmb use libs different than Gnome.

It would be interesting for you to try and make a new share.  All the Gnome/Nautilus shares are at /var/lib/samba.  If you can make a new share using Nautilus it will show up there.

Hmmmmm. I (until now) use Kubuntu or Xubuntu with KDE or XFCE (and Dolphin). Perhaps that's why I haven't seen this problem. I'm surprised that mature products like Gnome and Nautilus would have such a big hole after all these years. Maybe that's why I switched to Ku- and Xu- way back when. Or maybe the barefoot adventure logo got athletes' foot.:wink: :wink:

Before switching to K- or X-, I'll try creating new shares using Nautilus. Problem: in KDE, the shares are at /var/lib/samba, but it's a binary file. If that's the same in Gnome, how would I view it? (I won't be at the Gnome computer for several hours, and my curiosity is overwhelming)

---

### Post by capscrew on 2009-03-30
> **snorkytheweasel said:**
> Hmmmmm. I (until now) use Kubuntu or Xubuntu with KDE or XFCE (and Dolphin). Perhaps that's why I haven't seen this problem. I'm surprised that mature products like Gnome and Nautilus would have such a big hole after all these years.

It's not a hole it's not even an error.  There has been a rewrite of the Gnome gvfs.  This backend is intended for both Gnome and others.  KDE is starting to use it.  The first parts became available in 8.04 and it is still going on.  The release of 8.10 has more gvfs updates and I believe 9.04 does also, but I am not sure.
> 
 Maybe that's why I switched to Ku- and Xu- way back when. Or maybe the barefoot adventure logo got athletes' foot.:wink: :wink:

Before switching to K- or X-, I'll try creating new shares using Nautilus. Problem: in KDE, the shares are at /var/lib/samba, but it's a binary file. If that's the same in Gnome, how would I view it? (I won't be at the Gnome computer for several hours, and my curiosity is overwhelming)

Yes they are binary.  So that only means you can add or remove them with a mouse click through the GUI interface.  I am running Hardy and my old /etc/samba/smb.conf file still works, but I see authorization changes.

I suggest making a test share and then try removing it.  If it works I would just rebuild the shares you had using the GUI and leave it at that.

Oldtimers (I'm one of them) generally resist this loss of control (not me).  If it works and I don't have problems making shares in an Ad Hoc environment, so much the better.  My headless servers; now that's another story.  At the present time I am having no problems with remote shares on my servers or mounting drives via CIFS mount.

---

