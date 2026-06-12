---
title: "EASY scp question"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by brandon82 on 2009-01-26
Can anyone give me specefic instructions on how to connect to another linux machine via scp connection. As you can tell, I'm new... 

Thanks

---

### Post by Iowan on 2009-01-26
The **man scp** page will give much better instruction than I can - I don't use it often, and need to look up the directions each time...

---

### Post by kevdog on 2009-01-27
scp is old school.  I would use sftp in that its very similar to ftp, but still provides for all the encryption and security benefits as scp.

---

### Post by lastfrontier on 2009-02-22
here is the scrip needed how ever i will say i prefer it over sftp because there is no option that i am aware of to copy full directories with sftp but with scp you can use the -r option for recursive if you want to just copy one file like a picture or document sftp is quicker and easier 

scp -r terminal-junky@000.000.000.000:/home/terminal-junky/Desktop/"tims van crash"* ~/Desktop

in this scrip you can see that i am asking the remote host (terminal-junky) for the file tims van crash (" ") these were added because of the spaces in the file name i gave the path to the file and the location i wanted it to go to which was the Desktop hope this helps you.

---

