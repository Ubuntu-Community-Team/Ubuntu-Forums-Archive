---
title: "mpd + mpdscribble"
date: 2008-07-26
forum: Multimedia Software
---

### Post by dgel on 2008-07-26
Hi,

I can't get mpdscribble to work, the logs keep saying: 'md5 challenge incorrect, wrong username or password?'
even though i computed the right ckecksum using:
echo -n 'mypassword' | md5sum
did I do something wrong?
Also, maybe unrelated, but the logs report a time 2 hours earlier than the actual time my clock gives me.
(also, what is the correct way to get mpd to start when i login?)


*btw, I know this is not strictly about ubuntu, but mpdscribble doesn't have a forum or irc channel..

---

### Post by dgel on 2008-07-27
*bump*..

---

### Post by beeman on 2008-08-13
I have the same problems with mpdscribble... I noticed they [filed a bug]("http://code.google.com/p/mpdscribble/issues/detail?id=9"). 

At first I thought it maybe had something to do with the recent changes at the last.fm site, but imho it would be strange if they'd changed something low-level like this, and the bugs at the site above are older too...

---

### Post by wbdigi.com on 2008-08-13
I have the same problems with mpdscribble....



support @ [www.wbdigi.com](www.wbdigi.com)
support @ wbdigi.com

---

### Post by beeman on 2008-08-26
Although I didn't change anything (afaik), it seems to work fine for me now... :)

(Ubuntu Gutsy/32bit)

---

### Post by aslok on 2010-12-18
Same

---

### Post by aslok on 2010-12-18
Solved!

[aslok@3r]2010.12.18-14:10:06:~$ sudo cat /etc/mpdscribble.conf | grep -E '^(user|pass)'
username = aslok
password = %%%%%MY PASS NOT MD5%%%%%
[aslok@3r]2010.12.18-14:10:24:~$

---

