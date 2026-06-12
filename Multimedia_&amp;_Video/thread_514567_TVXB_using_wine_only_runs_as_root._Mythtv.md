---
title: "TVXB using wine only runs as root. Mythtv"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by ptipton on 2007-07-31
I am trying to use the listing grabber TVXB running under wine to provide the program guide for Mythtv. If I run the command wine /usr/local/share/TVxb/bin/TVxb.exe as root it works fine, if I try to run as any other user it brings up the console and then just stops and returns to the command prompt. I have checked the permissions on TVxb.exe and they seem fine. Any help much appreciated, this is  an anoying problem in what has otherwise been a relativly simple Mythtv install.

---

### Post by Andrew-buntu on 2007-08-01
Although the permissions on TVxb.exe may be fine, it's likely trying to write somewhere (or start another program) that requires permissions other than what you have.
Are you logged in as the "mythtv" user when you try running this program?  I haven't used Myth for years but I remember that it had a special user associated with it.  If you're logged in as "ptipton" and you're trying to write to "/home/mythtv/.myth/somefile", that's going to fail unless you're root or you're the mythtv user.

---

### Post by ptipton on 2007-08-02
Andrew, thanks. Have tried running as user mythtv and also as user administrator which is a member of the mythtv group. Let me check the permissions on the files it writes to. Dont suppose there  is a log that would tell me what the error is? DMSG doesnt show anything and cant find a log for wine.

---

### Post by Andrew-buntu on 2007-08-02
There are some logs in /var/log/mythtv.  Maybe the stuff in there will give you a clue as to what's going on.

---

