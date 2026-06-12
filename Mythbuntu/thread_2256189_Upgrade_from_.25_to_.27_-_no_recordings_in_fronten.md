---
title: "Upgrade from .25 to .27 - no recordings in frontend"
date: 2014-12-10
forum: Mythbuntu
---

### Post by newlinux on 2014-12-10
hi, this morning I upgraded from .25 to .27 (v0.27.4-26-gea73ed3). It seemed to go okay, but none of my frontends can access the recordings (they can access videos and stream them). I can watch live TV. The watch recordings screen never loads (tries for a while) but eventually fails back to the previous menu. I have a number of these errors in my master backend when trying to load the recordings:
```

mythbackend[29778]: C ProcessRequest mythcorecontext.cpp:699 (GenMythURL) MythCoreContext::GenMythURL(192.168.1.20/7301_20141202040000.mpg): Given IP address instead of hostname (ID). This is invalid.

```

The frontend gives me  the following errors

```
2014-12-10 11:01:05.766709 E  MythSocket(7f0574012c90:57): ReadStringList: Error, timed out after 30000 ms.
2014-12-10 11:01:05.766815 E  MythSocket(7f0574012c90:-1): No response.
2014-12-10 11:01:05.766821 N  Connection to backend server lost
2014-12-10 11:01:05.767017 N  Event socket closed.  No connection to the backend.
2014-12-10 11:01:05.773338 I  MythCoreContext: Connecting to backend server: 192.168.1.109:6543 (try 1 of 1)
2014-12-10 11:01:06.267815 E  MythSocket(7f0560002e20:57): WriteStringList: Error, invalid string list.
2014-12-10 11:01:06.267847 E  MythSocket(7f0560002e20:57): Failed to send command.
2014-12-10 11:01:06.268010 C  Reconnection to backend server failed
2014-12-10 11:01:06.268089 I  MythCoreContext: Connecting to backend server: 192.168.1.109:6543 (try 1 of 1)
2014-12-10 11:01:06.394284 W  PlaybackBox: SortedList is Empty
```

The frontend errors seem to simply tell me it can't get the list of recordings, and then loses connection to backend. It keeps connection fine, however, when streaming livetv. 
Any ideas. sucks to not have my recordings.

---

### Post by Mythological on 2014-12-10
My understanding has always been that you must run the same point version of MythTV on both the backend and the frontends.  So if you have not updated any of the frontends to .27 yet, you might want to give that a try.  The necessity of doing that is the big reason I'm still on .25; it works so I don't want to touch it!

If you do update your frontends, please post back and let us know if that fixes the problem.

---

### Post by newlinux on 2014-12-10
> **Mythological said:**
> My understanding has always been that you must run the same point version of MythTV on both the backend and the frontends.  So if you have not updated any of the frontends to .27 yet, you might want to give that a try.  The necessity of doing that is the big reason I'm still on .25; it works so I don't want to touch it!

If you do update your frontends, please post back and let us know if that fixes the problem.

Yes, I had already updated all frontends, and all slave backends. I went switched to a recording group that had fewer recordings and that loaded. So I think the longer listings of shows (I have hundreds of recordings) are timing out for some reason. Still investigating. 

I've been using myth since .19 (I think, or somewhere around there) I usually upgrade every 2 years or out of necessity. I agree with the if it ain't broke don't fix it.. I just plan on going to 14.04 soon for some machines so I figured now is the time.

I'm curious where I should be specifying a hostname where I am specifying an ip address.

---

### Post by newlinux on 2014-12-10
i decided to reboot all of my slave backends. That helped. The recording screens load, but they are much slower than they used to be. the used to load almost instantaneously regardless of recording group. Now they take 3-7 seconds. Still would like to get to the bottom of the IP issue since that floods my master backend log whenever I go to a recording screen, and may be tied to the slowdown.

---

### Post by aelfric55 on 2014-12-11
I had a very similar issue happen to me, not when moving to 0.25 to 0.27(.2), but rather when I moved the master backend from 0.27.2 to the then newly-released 0.27.4. I could never get the recordings data to load at all on 0.27.4, but when I returned the master backend to 0.27.3, the issue disappeared. I never migrated the slave backends to 0.27.4, so this appeared to be a pure master backend/mariadb thing.

---

### Post by newlinux on 2014-12-11
> **aelfric55 said:**
> I had a very similar issue happen to me, not when moving to 0.25 to 0.27(.2), but rather when I moved the master backend from 0.27.2 to the then newly-released 0.27.4. I could never get the recordings data to load at all on 0.27.4, but when I returned the master backend to 0.27.3, the issue disappeared. I never migrated the slave backends to 0.27.4, so this appeared to be a pure master backend/mariadb thing.

Thank you for the information. I took a look at the code that actually produces this the line I get in my master backend log file about hostname/ip issue:

line 699 in this file:

[https://github.com/MythTV/mythtv/blob/master/mythtv/libs/libmythbase/mythcorecontext.cpp](https://github.com/MythTV/mythtv/blob/master/mythtv/libs/libmythbase/mythcorecontext.cpp) 

It helped me understand a little bit, but I still don't know what's passing this function the IP address. My understanding was that mythbackend got the hostnames directly from /etc/hostname. It could be this is a bug, but then I don't know why it doesn't happen to everyone. Ironically, it looks like the purpose of this code is resolve ip/hostname issues in the myth code, but I think it's causing delays in my recordings loading. I have been able to research much beyond that. Maybe I'll look into downgrading the master to .27.3. Is that the same protocol as .27.4? Don't want to have to downgrade all my slave backends. Hopefully it's an easy process. I've never rolled back.

---

### Post by aelfric55 on 2014-12-11
It's the same protocol for all the minor revs. 0.27.0 to 0.27.4+ The machines of your network are indifferent to which mythtv minor rev. backend or frontend is running on which machine: moving up or down a minor revision generally consists of nothing more than stopping the backend, changing the mythtv version, and starting the backend. The only issue tends to be whether and how much the package manager in use interferes with rolling back a package. I personally use Ubuntu and its derivatives only on frontend machines --the master backend was Slackware, and so the stop, rollback, and restart of mythbackend took under a minute.

---

### Post by newlinux on 2014-12-12
Back when I used to update mythtv more frequently I was bit by a minor version upgrade having a protocol change, so I know it has happened before, just wanted to make sure the fixes branch are all on the same protocol now. The package management part of it is what I'm concerned about in rolling back. But really, I'd rather just get the problem identified and fixed. Still holding out a little hope.

---

### Post by newlinux on 2014-12-16
bump in case anyone else has ideas. I don't want to roll back as I'm not sure that will fix the problem, and eventually I want to keep up to date anyway. I've looked through the database for where a IP address may be used in a hostname field, but I couldn't find any. I really don't know what this error is about. I looked through the code as indicated by the error, but that didn't help either.

---

### Post by newlinux on 2015-01-21
Couple updates:

More info in case this helps someone figure out what's going on (also posted to mythtv-users).

This has been getting worse, often leading to the recordings screen timing out and not showing any recordings. This looks to be possibly some kind of networking problem, although I haven't changed anything about how my network works in years. I have my router running dnsmasq and as my DHCP server it assigns the same IP to all machines based on MAC and it resolves local domain names. I have 4 backends. In my master, on a whim I decided to add entries for the the slave backend hostnames in /etc/hosts. Keep in mind that from the commandline my master has no problems resolving the slaves with nslookup so I didn't think this would help. Well, it did. The load time sped up quickly, but the problem is still there a bit. I used to get one of the "MythCoreContext::GenMythURL(192.168.1.108/5091_20110203100000.mpg): Given IP address instead of hostname (ID). This is invalid." lines for what I believe is every single recording (around 600 or so I believe) on a slave backend. After adding the /etc/hosts entries the messages dropped down to 200 and screen went from taking 20 seconds (sometimes timing out) to load to 1-2 seconds. I still get this message in the master backend log for various recordings on each slave backend (none for recordings on the master backend), but I can find no rhyme or reason to why some recordings give this message and some don't or why adding entries to /etc/hosts helped reduced the number of recordings (seems to me it should have done nothing, or fixed them all). This one is a head scratcher for me. I never had this problem until updating the backend to .27.4, however at the same time I did update the OS to current (still Ubuntu 12.04), so maybe something changed there. I still don't understand where I would be giving it an IP when it is expecting a hostname in the OS or in myth.

I did file a bug a month ago, and it appears from the additional comment that I'm not the only person with this issue. This person is running Fedora and I'm on Ubuntu for my backends. Still not sure what it is, but haven't had time to look into much further...

[https://code.mythtv.org/trac/ticket/12340](https://code.mythtv.org/trac/ticket/12340)

---

