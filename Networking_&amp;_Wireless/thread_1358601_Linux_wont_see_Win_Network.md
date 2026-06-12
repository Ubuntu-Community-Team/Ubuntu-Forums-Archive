---
title: "Linux wont see Win Network"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by kakashi_12 on 2009-12-18
Sometimes it will connect and other times it won't. Why only sometimes? I'm trying to connect to other computers for file sharing. Even if I type in the address exactly ( \\computername).

---

### Post by Iowan on 2009-12-18
[This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To *might* help - especially Problem 3.

---

### Post by kakashi_12 on 2009-12-19
Thanks so much!!!

I just realized one mistake I was making before. When typing in the address directly, I was using a double backslash then computername. In Linux, it's one forward slash. I forgot Linux switches around slashes (opposite of windows). Thanks. I typed in the address directly this time and it worked. I can browse easier and for surer too.

---

### Post by kakashi_12 on 2009-12-19
I just noticed two other things. First... I can't "see" the computers from the browser now. But I can "connect" to them by typing in the address directly. Until I share a folder on my own Ubuntu box here, THEN I can "see" the other computers in the file browser. Weird

Secondly, when I try to connect to the hidden c share, it prompts for a un and pw. I put both in (yes they're correct credentials of that computer), but it won't let me connect. I can connect to a normal shared folder, but not hidden shared. I do not get prompted for a un and pw on a normal share, but do on the hidden c share. Should I try including the computer name with a slash then username? I also tried getting to ubuntu box from windows, that worked great!

---

### Post by jpt266 on 2009-12-19
I think the fix as been found. Read some of these;


It seems caused by windows live sign-in assistant. I had exact same problem. [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/458637](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/458637)

[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)



Thanks to Yejun above.

Removing windows live sign-in assistant program has "fixed" it for me too - I can use my WIndows 7 printer and access shared folders using my windows user/password, whereas before Win 7 appeared to be refusing to accept the credentials.

Fixed it for me too. Could always go ubuntu to xp but not ubuntu to vista or windows7. Tried the system services tweak, no fix. So what is this windows live sign-in assistant doing that stops the share request?

---

