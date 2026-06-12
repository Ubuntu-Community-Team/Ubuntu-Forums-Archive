---
title: "What softare for syncing data windows &lt;&gt; ubuntu (over local network)"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by vcppp_p on 2010-07-07
Hi,
I'm looking for some software for syncing lots of data (about 60-90GB) over local network between two machines - Ubuntu and Windows XP home.

By syncing I mean at least the functionality of auto - copying both ways -> if some file / directory appears on one of the machines it'll be copied to the other.

we can assume that files are never modified nor deleted.

what would be your recommendation?

---

### Post by jonobr on 2010-07-08
Hello

Maybe [CWrsync]("http://www.itefix.no/i2/node/10650")
for the windows side . Its the rsync protocol bundled into a windows app that has client and server software.
You can use rsync on ubuntu itself it has a lot of options when doing the copy.
There is a man page and also tons of useful resources on the forum and the internet to describe how to use it on the linux side

---

### Post by Yarui on 2010-07-08
I don't know exactly what types of files you are using or what kind of behavior you want the program to have, but developers often use subersion software, or svn for short.  It is a system that does basically what you are talking about, but keeps backups of old file versions as well.  I have never configured a server before, I have just used a client, so I'm not sure how easy it is to set up.  It may be worth researching a bit, though.

---

### Post by vcppp_p on 2010-07-08
> **Yarui said:**
> I don't know exactly what types of files you are using or what kind of behavior you want the program to have, but developers often use subersion software, or svn for short.  It is a system that does basically what you are talking about, but keeps backups of old file versions as well.  I have never configured a server before, I have just used a client, so I'm not sure how easy it is to set up.  It may be worth researching a bit, though.
I know SVN (I'm also using it, my Ubuntu is running server) but this is not the case.
SVN is perfect for source files, while in that case it's about binary files.

Also, running SVN doubles the size of data, as the repository data are kept in some database file, then it needs to be checked out / exported to access the actual data.

Keeping both the repository and the actual data (up-to-date) on a single machine would take too much space.

Also, I'm afraid SVN wouldn't handle 90GB of data smoothly, when it comes to making diffs between commits etc.

---

### Post by Yarui on 2010-07-08
Hmm, in that case I don't really know what software you could use.  If it were me I would probably write my own program to do it for me, but I have had a hard time figuring out how to make a program properly utilize inotify.  Surely someone has already made a program for this purpose, though.  I just use dropbox to do what you are describing, but if you want to use over 2 GB in dropbox you have to pay a monthly fee, and that seems a bit silly if you only plan on using it over LAN.

---

