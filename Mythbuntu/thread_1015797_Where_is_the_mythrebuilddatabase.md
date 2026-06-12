---
title: "Where is the mythrebuilddatabase??"
date: 2008-12-19
forum: Mythbuntu
---

### Post by axelsvag on 2008-12-19
I have read a lot about the command mythrebuilddatabase.pl. But when I try the command mythrebuilddatabase.pl I get the message that the command is not found. What am I missing?

I use mythtbuntu 8.04 on a amd64

---

### Post by ian dobson on 2008-12-19
Hi,

It appears to be in /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl.gz. you can expand it using gunzip.

Regards
Ian Dobson

---

### Post by axelsvag on 2008-12-19
Thank you I found it and unpacked it. But still the command line says that the command does not exist. There must be something more I have to do?

---

### Post by ian dobson on 2008-12-20
Hi,

You need to move it to somewhere on your path and set it to executable with chmod +x filename.

or just call it directly (after seting it to be executable)

/usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl

Regards
Ian Dobson

---

### Post by axelsvag on 2008-12-21
I still get  command not found. Maybe I am doing something else wrong. For example in which folder should I put the script? Should I use sudo command to make it execute? Do I have to be in the right folder in terminal to make it work?

---

### Post by SiHa on 2008-12-21
I generally put my scripts in **/usr/local/bin**
```
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

``` Will display the list of directories that will be searched for an executeable - you can put it in any of these.

---

