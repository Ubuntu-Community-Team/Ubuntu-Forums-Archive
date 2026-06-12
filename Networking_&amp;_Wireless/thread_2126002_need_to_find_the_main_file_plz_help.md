---
title: "need to find the main file plz help"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by siddharthchauhan44 on 2013-03-15
hi guyz 
plz help me with this 
i installed NS2 and 
i have done some changes 
in smac.cc file 
i need to replace it with the original installed file can any one pls help me 

this is related to routing protocols and stuff 

ns2 only runs on UBUNTU

---

### Post by Bashing-om on 2013-03-15
siddharthchauhan44; Hi !

See if this works for you; Terminal command:
```
sudo find / -name  smac.cc
```
The use of sudo requires your pass word, repeating nothing to the screen on input (security reasons).
Will perform a search starting at the top "/" and search ALL directories for the file "smac.cc:. This may take a long while, depending on how fast your system is.[INDENT=4]
hth

[/INDENT]

---

