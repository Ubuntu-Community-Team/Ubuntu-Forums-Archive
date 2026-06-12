---
title: "missing smbfs files"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by rsnow on 2011-04-06
I have two machines. Both with 10.10 installed and all updates current. I cannot get the lan connection between them to work. On checking, I found that one machine has 15 smbfs files and the other has only 7 smbfs files. 

Should I copy the missing files from the one machine and put them on the other machine or would it be better to try and get them from the web? 

Also, the machine with the 15 files will connect with my windows machine and the one with 7 files will not. I have tried to research this but not sure I understand what I'm reading.

Note: The one with 7 files does connect to the internet through the lan wiring.

---

### Post by nosebreaker on 2011-04-06
I'd never manually copy files, I always use a package manager of some sort.  "sudo apt-get install smbfs" for example.  Or "yum install smbfs".  I think cifs is used now instead of smbfs though, can you use that instead?

---

### Post by rsnow on 2011-04-06
That did the trick! I learned that sudo apt-get install smbfs actually gets both smbfs and cifs. Thanks for the response.

---

