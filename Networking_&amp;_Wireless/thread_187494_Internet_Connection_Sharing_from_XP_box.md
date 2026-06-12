---
title: "Internet Connection Sharing from XP box"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by dadioflex on 2006-06-03
I installed Breezy about 3 days ago (doh!) and it worked fine leeching the internet off my XP box (after switching to One Care from Zone Alarm). I did a clean install of Dapper after my upgrade bummed out over Cream/Vim of all things and suddenly my Linux box is persona non grata. 

I don't know if it's relevent but with Breezy it asked questions about ip addresses and wotnot during installation but Dapper doesn't. But I'm not entirely stupid so I configured a fixed ip address (and mask) and used the ip of the XP box as the gateway - identical to the way it was under Breezy. (EDIT: I already changed the default settings in One Care to allow ICS). I can pull data off the XP box no problem but can't get the internet connection working at all.

Being cavalier with my safety I even turned off the One Care firewall briefly to see if it made a difference (though it worked fine with Breezy and, as mentioned, I can browse the XP box.). But no.

So I tried the blacklist tulip and ip6 fixes just in case but they didn't make a difference. The XP box hasn't changed from when I was using Breezy but something just isn't clicking. And ideas where to look next?

On a side note - One Care is locking up my XP box something rotten. Yeah, I know, go figure. However even when disabled I'm getting the same problem.

To be honest I'll probably reinstall Breezy just to double check it isn't XP playing up. Though last time when I installed Dapper I had to re-format my hard drive with a Windows rescue disk because Dapper was crapping out during installation.

So so far Breezy 1   Dapper 0.

---

### Post by dadioflex on 2006-06-04
Okay, so I did a fresh install of Breezy and automatically got the upgrade options this time. Went through the upgrade and the ICS seems to be working. Perhaps something I installed during my 2 or 3 days with Breezy initially (Cream/Vim, gdesklets and frozen bubble - as far as I can remember that was it.) broke the upgrade procedure or the network connection. Still it's all an education innit?

---

