---
title: "SOLVED smb password with punctuation (@ and !)"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by dannyboy79 on 2009-08-05
i was having a difficult time getting the smb:// protocol to accept my password when entering it in the smb:// string because my password has punctuation in it. i tried using single quotes around password as well as double quotes, nothing was working. I use xbmc and I looked at the log today and found out how to turn an "@" symbol as well as a "!" mark into something the smb:// protocol is acccepting. So the string is as follows:
smb://jeff:jeff%4005%21@ubuntu/500gb1/

jeff is the username
jeff@05! is the password
ubuntu is the servername
500gb1 is the smb share

so as you can see instead of entering jeff@05!, i have to enter jeff%4005%21 for the password instead

%40 must equal the "@" symbol
%21 must equal the "!" mark

there you have it. now I just need to figure out the rest of the punctuation. bye now

---

