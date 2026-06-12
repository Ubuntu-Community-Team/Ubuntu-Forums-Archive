---
title: "just upgraded to karmic, possible xmltv problem"
date: 2009-10-29
forum: Mythbuntu
---

### Post by bergqvistjl on 2009-10-29
Hi guys, im in the UK and everything works ok with regards to setting up the channels EXCEPT mythfilldatabase/xmltv. This is the output i get when running xmltv (latest version, .xmltv is set up exactly as it was before (radio times grabber), when it would run sucessfully)
```
john@john-mythbuntu:~$ mythfilldatabase
2009-10-29 20:17:06.598 Using runtime prefix = /usr
2009-10-29 20:17:06.599 Using configuration directory = /home/john/.mythtv
2009-10-29 20:17:06.599 Empty LocalHostName.
2009-10-29 20:17:06.599 Using localhost value of john-mythbuntu
2009-10-29 20:17:06.604 New DB connection, total: 1
2009-10-29 20:17:06.606 Connected to database 'mythconverg' at host: localhost
2009-10-29 20:17:06.607 Closing DB connection named 'DBManager0'
2009-10-29 20:17:06.607 Connected to database 'mythconverg' at host: localhost
2009-10-29 20:17:06.609 Current MythTV Schema Version (DBSchemaVer): 1244
2009-10-29 20:17:06.610 New DB connection, total: 2
2009-10-29 20:17:06.611 Connected to database 'mythconverg' at host: localhost
2009-10-29 20:17:06.611 Updating source #1 (XMLTV) with grabber tv_grab_uk_rt
2009-10-29 20:17:06.611 Found 43 channels for source 1 which use grabber
2009-10-29 20:17:06.943 Grabber has capabilities: baseline manualconfig cache preferredmethod tkconfig apiconfig 
2009-10-29 20:17:07.365 Grabber prefers method: allatonce
2009-10-29 20:17:07.365 New DB connection, total: 3
2009-10-29 20:17:07.366 Connected to database 'mythconverg' at host: localhost
2009-10-29 20:17:07.366 XMLTV config file is: /home/john/.mythtv/XMLTV.xmltv
2009-10-29 20:17:07.366 New DB connection, total: 4
2009-10-29 20:17:07.366 Connected to database 'mythconverg' at host: localhost
http://xmltv.radiotimes.com/xmltv/1542.dat: Cannot decode string with wide characters at /usr/lib/perl/5.10/Encode.pm line 182.
2009-10-29 20:18:59.421 FillData, Error: xmltv returned error code 2304
2009-10-29 20:18:59.777 Error in 55614:15: unexpected end of file
2009-10-29 20:18:59.837 IconData: Updating icons for sourceid: 1
2009-10-29 20:18:59.837 New DB connection, total: 5
2009-10-29 20:18:59.911 Connected to database 'mythconverg' at host: localhost
ICE default IO error handler doing an exit(), pid = 5286, errno = 32

```
any ideas? is this an xmltv, radio times, or perl problem?

---

### Post by bergqvistjl on 2009-10-29
anyone?

---

### Post by nickrout on 2009-10-29
> **bergqvistjl said:**
> anyone?

what do you mean "Anyone" - you posted a bump message an HOUR after the original message?

Do you think people on here somehow OWE you a reply?

---

### Post by bergqvistjl on 2009-10-30
> **nickrout said:**
> what do you mean "Anyone" - you posted a bump message an HOUR after the original message?

Do you think people on here somehow OWE you a reply?
no, but it would be nice if someone acknowleged or gave some generic advice if possible. There must be more than just me who's trying to use xmltv with the radio times grabber out of the box.

---

### Post by caribo on 2009-10-30
I suspect this is a problem related to the RT data.

Try running "mythfilldatabase -v all"  to identify the channel which is causing the problem.

I had this same issue myself and found that the problem was related to program listings for the community channel, so i just removed it from my xlmtv channel file which is great as I do not have this channel in my line up anyway!

Good luck.

---

### Post by bergqvistjl on 2009-10-30
> **caribo said:**
> I suspect this is a problem related to the RT data.

Try running "mythfilldatabase -v all"  to identify the channel which is causing the problem.

I had this same issue myself and found that the problem was related to program listings for the community channel, so i just removed it from my xlmtv channel file which is great as I do not have this channel in my line up anyway!

Good luck.

yeh that was it, it was the community channel. Thanks!

---

### Post by uncle hammy on 2009-10-30
> **nickrout]what do you mean "Anyone" - you posted a bump message an HOUR after the original message?

Do you think people on here somehow OWE you a reply?[/QUOTE]
[QUOTE=bergqvistjl said:**
> no, but it would be nice if someone acknowleged or gave some generic advice if possible. There must be more than just me who's trying to use xmltv with the radio times grabber out of the box.
I think you missed the point completely....as in it sailed right over your head, and you were staring at the sidewalk.

You don't bump a post ONE HOUR after the original post.  It's not like this is a live board, and "operators are standing by to address your every need".  Try waiting 24 hours before posting an "anyone?" like you've somehow been slighted.

Or, I suppose you could keep trying the one hour tactic, only to find that ALL your post invariably get ignored. ;)

---

