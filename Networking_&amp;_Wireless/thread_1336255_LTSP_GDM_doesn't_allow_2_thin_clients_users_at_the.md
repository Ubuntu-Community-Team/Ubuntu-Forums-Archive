---
title: "LTSP: GDM doesn't allow 2 thin clients users at the same time..."
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by t0rtura on 2009-11-24
Hello,

I have a server with LTSP 5 configured, and I'm able to log into first thin client, see this picture:

[http://ubuntuforums.org/attachment.php?attachmentid=137440&stc=1&d=1259077916](http://ubuntuforums.org/attachment.php?attachmentid=137440&stc=1&d=1259077916)

Aluno1 is my user logged into the thin client, but when I type 'who' command it shows a blank tty field to the remote user. 

When I log at the second thin client at the same time, using Aluno2 account, Aluno1 is kicked and Aluno2 is showed in 'who' command, but it doesn't logout Aluno1, it just disappear in the 'who' command. See the pic:

[http://ubuntuforums.org/attachment.php?attachmentid=137441&stc=1&d=1259078487](http://ubuntuforums.org/attachment.php?attachmentid=137441&stc=1&d=1259078487)

When I use LDM in my lts.conf the tty field of remote users is showed up, but LDM doesn't read logon scripts like .profile, .bash_profile, and I need to use this scripts. GDM reads .profile but doesn't allow me to log two users at the same time.

Using LDM:
[http://ubuntuforums.org/attachment.php?attachmentid=137442&stc=1&d=1259078938](http://ubuntuforums.org/attachment.php?attachmentid=137442&stc=1&d=1259078938)


Thanks for any help
T0rtura

---

