---
title: "Problem with networking."
date: 2006-05-18
forum: Networking &amp; Wireless
---

### Post by Eidar on 2006-05-18
Hi all,

I have a problem with my network.I think i've tried almost everything I can think of.

My hardware is:

Speedtouch 716g (adsl modem, router and wireless options)
WinXP box
Ubuntu (latest) box

My current network settings is a bridge between two NICs. I can ping Ubuntu box from WinXP box and vice-verse, I can browse the internet on both machines too.

However, from the WinXP box, I cannot access SSH or Apache using my WAN ip, only the lan IP of my Ubuntu box. That is the only problem.

I have tried forwarding the ports but it still won't work. Could somebody give a couple of hints, options or tips on how to access my Ubuntu server daemons through my WAN ip?

Thanks in advance. If anybody needs anything else please ask.

---

### Post by it.henrik on 2006-05-18
if you can ping the ubuntu box over wan from win xp then you prob have to set up the servers to listen on all nics.

---

### Post by Eidar on 2006-05-18
Could you please explain the procedure of doing so? I am pretty new to Ubuntu.

Thanks.

---

### Post by Eidar on 2006-05-18
Another thing which I forgot to mention is that I also configured Samba on my Ubuntu and the shares show up on my WinXP box and they are accessible.

Its just that I can access nothing on the Ubuntu box from using WAN ip, only local lan IP :/

[img]http://ubuntuforums.org/attachment.php?attachmentid=9669&stc=1&d=1147979123[/img]

That is how it looks when I try to SSH to the Ubuntu box using the WAN ip.

---

### Post by Eidar on 2006-05-21
I got it working correctly now, although I have to access my server's services (apache, ftp, ssh, etc,.) using a proxy. Why is that so? I don't quite understand why it must be like that.

---

