---
title: "SCP: Can I list the contents of a directory on a computer at some IP address?"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by test_tube_baby on 2011-07-15
Can I list the contents of a directory on a computer at some IP address from my terminal?

If so.. what is the command?

Suppose I know the username and the password and the IP address.

I want to list the contents of the home folder i.e. /home/...


How do I do that?

---

### Post by doas777 on 2011-07-15
well, instead of scp specifically, I would just connect via ssh, and run 'ls -al <path>' .

I remember I used to remote into a solaris box for school, using kshell and vi commands for cli editing. I personally hate VI so I always used winscp for accessing and editing files, but to create a file initially, I had to hop to a ssh session and run 'touch filename'

---

