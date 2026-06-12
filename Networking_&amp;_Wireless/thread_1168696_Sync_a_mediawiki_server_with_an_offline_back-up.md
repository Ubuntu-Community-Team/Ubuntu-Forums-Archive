---
title: "Sync a mediawiki server with an offline back-up"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by monsterstack on 2009-05-24
I've been having some troubles with my server lately, and I want to back up a wiki I've been developing. But rather than just back it up, I'd like some way to sync it to my desktop computer's localhost, because it might be a few weeks before I can get round to fixing my server and I'd rather not lose any data in the meantime. Once I've fixed the server, I would like to republish the wiki from my desktop. Can anyone point me in the right direction as to what I'd need to do to get this done, if possible?

Thanks in advance. :)

---

### Post by Kareeser on 2009-05-24
You'll need to play with the commands "mysqldump", "tar", and "rsync".

I use those three commands in a script to export the SQL table, compress it, and send it across the network to a directory on my backup computer.

Simply reply back if you need help on any of the three. Try "man *<command>*" first.

---

### Post by monsterstack on 2009-05-25
> **Kareeser said:**
> You'll need to play with the commands "mysqldump", "tar", and "rsync".

I use those three commands in a script to export the SQL table, compress it, and send it across the network to a directory on my backup computer.

Simply reply back if you need help on any of the three. Try "man *<command>*" first.

Thanks a lot. That's pretty much everything I need to do, I just didn't know where to start. I'm going to set up a cron job once I've hosed down the server to make sure I don't get burned again in case the worst happens.

---

