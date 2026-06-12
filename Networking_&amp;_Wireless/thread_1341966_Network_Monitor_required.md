---
title: "Network Monitor required"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by stevebond001 on 2009-11-30
Hi
Hopefully this is a question with a simple answer.

Can anyone tell me of a simple network monitoring tool which will display the upload and download totals from my 64 bit Ubuntu PC?
I used to use an application called netmeter on my XP PC which provided totals for the day, week and month, so I'm looking for a linux alternative for this.  Preferably this needs to be a GUI which I can just leave running whilst logged on, rather than a command line utility

Any ideas?  

Many thanks in advance

---

### Post by ajgreeny on 2009-11-30
Use **vnstat** together with a shell script file as I have.  My vnstat script is as follows
```
#!/bin/bash
vnstat -d > /tmp/$
gedit /tmp/$
rm /tmp/$
```
which runs vnstat, produces a file called $ in/tmp, then displays it in gedit, and then deletes it.  You do not necessarily need to add the delete (rm /tmp/$) line if you want to keep the file between runs of the script.

---

### Post by stevebond001 on 2009-11-30
Thanks for the prompt reply.
Will this keep a tally of my download and upload totals for the month?

---

### Post by ajgreeny on 2009-11-30
Yes, the -d option will give you daily downloads and uploads for the last month, ie back to the same date last month from when you run it.

---

### Post by doas777 on 2009-11-30
and if you want to see it in realtime, check out iftop

---

### Post by H4F on 2009-11-30
> **doas777 said:**
> and if you want to see it in realtime, check out iftop

iftop really coooool. was looking for something like that. ti will be nice also to have there a list of progrmms related to traffic . and a way to limit the network speed of those.

---

### Post by stevebond001 on 2009-11-30
Brilliant
Many thanks for the replies. I've managed to get netmeter running under Wine, but I'll also look at using the others suggested here.

Thanks once again.

---

