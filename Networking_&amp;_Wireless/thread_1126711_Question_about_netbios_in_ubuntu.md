---
title: "Question about netbios in ubuntu"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by linuxtorvalds on 2009-04-15
I was having problems connecting a wireless router set up as a wireless client to a wireless AP to DSL modem combo, details here:

[http://ubuntuforums.org/showthread.php?p=7054138#post7054138](http://ubuntuforums.org/showthread.php?p=7054138#post7054138)

Short version was that Win XP will work after I click "repair", and my Intrepid install won't.

Did some researching into what XP does, and discovered what fixes it are the
commands
**arp -d ***
**nbtstat -R**

Problem is, I can't find any info on how to do the equivalent in linux.  Ideas?

---

### Post by capscrew on 2009-04-15
> **linuxtorvalds said:**
> ...
Did some researching into what XP does, and discovered what fixes it are the
commands
**arp -d ***
**nbtstat -R**

Problem is, I can't find any info on how to do the equivalent in linux.  Ideas?

**arp -d ***  -- I assume that you want to delete an address.  The command is the same.  Use the command terminal.

**nbtstat -R** --  You need to install NBTscan.  To do that you need to use the terminal again and do this:
```
sudo apt-get install nbtscan
```

---

### Post by linuxtorvalds on 2009-04-15
Thanks..I'd figured out the arp one but didn't find any post on the internet that put nbtscan and nbtstat together...I'll give it a try...

---

