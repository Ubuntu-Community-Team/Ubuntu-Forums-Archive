---
title: "i need help !!!!  update dont work!!"
date: 2008-03-24
forum: Michigan Team - US
---

### Post by atgreen1 on 2008-03-24
hey i keep getting the same error  how do i fix it ? E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.  

this only happens when i try to update i used the update manager there 41 updates i cant get right now hmm???  i am new to   ubuntu  but not dum . i looked in  files and found dpkg files but i dont know what to do with them .if i try reload the packages it stops. help please i love working with ubuntu  ....keith  in michigan

---

### Post by luisromangz on 2008-03-24
The error contains the solution...

Run 

sudo dpkg --configure -a

in a terminal.

---

### Post by atgreen1 on 2008-03-24
thank you for your help it worked fine . keith

---

