---
title: "Polkit1"
date: 2011-03-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Bobhuber on 2011-03-22
The settings in Polkit1 don't seem to have any effect on the system. Is this permanent ?
If so I won't be upgrading to Natty. The system asked me for a #$&^% password to do a simple file search.

---

### Post by mc4man on 2011-03-22
You do have  my curiosity - what policy relates to "file search"

---

### Post by Bobhuber on 2011-03-22
> **mc4man said:**
> You do have  my curiosity - what policy relates to "file search"

I needed to see system and hidden files in a search.

gksudo gnome-search-tool

---

### Post by mc4man on 2011-03-22
_IF you are the admin user_ i'd just take advantage of the sudo admin auth 'timeout' and if desired set it to unlimited (the life of the session) or some other time frame if the default (15 min?) is unsuitable

There are currently some differences in the current sudo in natty - the timeout only works on the current open instance so not that useful

Discussed here
[http://ubuntuforums.org/showthread.php?t=1648577](http://ubuntuforums.org/showthread.php?t=1648577)
Atm there are some ways to deal with, 2 ways shown in that thread

For the current 1.7.4X sudo in natty post 29

I don't ATM prefer that method for various reasons, (last several posts in thread), so instead here use what's shown in post 21

For use with gksudo I'd recommend post 21 ( download and downgrade to the 1.7.2 sudo using either the prior natty version or the preferred,( here), maverick security updated version

---

### Post by Bobhuber on 2011-03-23
> **mc4man said:**
> _IF you are the admin user_ i'd just take advantage of the sudo admin auth 'timeout' and if desired set it to unlimited (the life of the session) or some other time frame if the default (15 min?) is unsuitable

There are currently some differences in the current sudo in natty - the timeout only works on the current open instance so not that useful


I finally gave up and just removed the sudo password requirement for myself .

---

