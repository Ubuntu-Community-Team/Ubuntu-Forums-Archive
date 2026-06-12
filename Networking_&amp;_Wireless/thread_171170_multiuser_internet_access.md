---
title: "multiuser internet access"
date: 2006-05-06
forum: Networking &amp; Wireless
---

### Post by teeleef on 2006-05-06
Ladies & Gents,  I have installed Dapper Beta.   As administrator/sudo I can access the internet however when I log out or my daughter logs on, she cannot access the internet?  I'm sure it is just a setting thing but I don't know where to look.
I have a ADSL router which was set up automagically.


Teeleef

---

### Post by Jussi Kukkonen on 2006-05-06
[QUOTE=teeleef]Ladies & Gents,  I have installed Dapper Beta.   As administrator/sudo I can access the internet however when I log out or my daughter logs on, she cannot access the internet?  I'm sure it is just a setting thing but I don't know where to look.
I have a ADSL router which was set up automagically.
[/QUOTE]

That really should Just Work...  [Wired ethernet troubleshooting guide](http://ubuntuforums.org/showthread.php?t=87643) may help, although most of it is probably not relevant to you.

You could do to this to help someone help you:
Run the following commands logged in as your daughter
```
cat /etc/network/interfaces
ifconfig
route -n
```
Save the output, and send it here.

---

### Post by Iowan on 2006-05-06
[QUOTE=teeleef] however when I log out or my daughter logs on, she cannot access the internet? [/QUOTE]Congratulations, you've discovered the ultimate "parental control..."  ;) 
Sounds like a permissions problem, but I don't have any useful suggestions.

---

