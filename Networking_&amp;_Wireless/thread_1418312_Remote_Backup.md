---
title: "Remote Backup"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by taffy2010 on 2010-02-28
Apologies in advance for the newbie questions.  I have trawled around the forum, found parts of what I think I need but not entirely sure, I am after a little advice on the following and any help would be greatly appreciated.
   
  Following a discussion in the pub the other night it became apparent that my mates, some with businesses some home users had absolutely no backup systems at all (I back up with Goodsync to my NAS, but if the house burnt down I would be in trouble), anyway to cut to the chase I told them leave it with me I will get it sorted (things seem so easy when you have had some beers).  My thoughts are to take on a dedicated server with someone e.g. fasthosts, adequate specification with 2 IP addresses etc running Ubuntu 9.04.  My thoughts then were to create folders for each of us (secured with authentication) with a limit of lets say 500mb and somehow with software set up overnight backup.
   
  I guess I have now hit a bit of a brick wall as I’m not sure where to go as there are so many software packages, one idea I had was to use Open VPN to create a secure network drive that would show up in “My Computer” and then use software such as Goodsync to synchronise overnight.  There seems to be so many software packages such as “Deltacopy” which could do it.
   
  The PC’s to be backuped up all run Windows XP or Vista.
   
  Any help would be greatly appreciated.

---

### Post by spikyjt on 2010-02-28
Do you really mean to limit them to 500MB each? If so, save yourself the effort (and cost) and use [Dropbox]("http://dropbox.com/") - you get 2GB online storage which is autosynced onto as many computers as you like, with a web interface too, for free.
If you mean 500GB, then you must be very rich! A dedicated server with enough capacity for that, for you and your mates, will cost loads. In that case you can afford to buy someone's ready to rock offsite backup solution and save yourself the bother.
If you really want to have a go, I'd suggest looking at ssh and rsync for the server. There are several GUI backup apps that use these for the clients.

---

### Post by taffy2010 on 2010-02-28
Hi, thanks spikyjt for your reply, the server's capacity is 500Gb so could give us over 50GB each, i just used 500mb as an example, will look into rsync. I am also thriving on the challenge of something new. Thanks again.

---

### Post by gfuggs on 2010-02-28
It sounds like you're looking for rsync.  I've only used it locally, but I believe it can backup over ssh.  It's smart in the sense that after the initial backup, only changes are sent in subsequent backups.

---

