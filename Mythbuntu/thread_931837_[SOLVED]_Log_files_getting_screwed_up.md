---
title: "[SOLVED] Log files getting screwed up"
date: 2008-09-27
forum: Mythbuntu
---

### Post by myth01 on 2008-09-27
While trying to fix another problem (I'll mention it below in case anyone has a solution) I've discovered that the frontend and backend logs are getting...well...screwed up is about the only way I can describe it.  

Logging was working perfectly well until about 10 days ago, there was one backend log and one frontend log.  But while trying to fix a new problem, I found that the original logs (frontend.log and backend.log) are both empty and new ones have been created: frontend.log.1, frontend.log.2, frontend.log.3 etc up to 7 and up to 6 for the backend.

I assumed the logs had gotten too big and created new ones but each was between about 5 and 25 Kb big, and the logged events were not consecutive with big gaps and complete days missed out.

I deleted all of the logs and rebooted hoping that new ones would be created and I could start working on the other problem.  It worked fine again but only for a day, and now they're screwed up again.

Help!

The other problems:  unfortunately due to the lack of good logs this is the key parts from memory;

NVP prebuffering pause
WriteAudio: Buffer underrun 
WriteAudio: Buffer underrun 
WriteAudio: Buffer underrun 
WriteAudio: Buffer underrun 
WriteAudio: Buffer underrun 
WriteAudio: Buffer underrun 
WriteAudio: Buffer underrun 
NVP prebuffering pause
WriteAudio: Buffer underrun 
WriteAudio: Buffer underrun 
WriteAudio: Buffer underrun 
WriteAudio: Buffer underrun 
WriteAudio: Buffer underrun 
WriteAudio: Buffer underrun 
WriteAudio: Buffer underrun 

and
served busy frame D: AAUUUUUUUUUUUUUUULLLLLLLLLLL


Mythtv packages (master-backend and frontend) via synaptic on ubuntu hardy on HP NC6000 laptop.

---

### Post by myth01 on 2008-09-27
I meant to add that I'm still a newbie so be gentle :)

---

### Post by myth01 on 2008-09-28
Anyone?

---

### Post by ian dobson on 2008-09-28
Hi,

What rights have the log files? If you go to the terminal and type:-

cd /var/log/mythtv
ls -o

then copy the output to the forum. It could will be that the mythtv user doesn't have the rights to write to the log.

For your second problem maybe try to increase the audio buffer size.

Regards
Ian Dobson

---

### Post by myth01 on 2008-09-28
Cheers for your reply Ian.

Here's the output from your suggestion...

server@SERVER:~$ cd /var/log/mythtv
server@SERVER:/var/log/mythtv$ ls -o
total 24
-rw-r--r-- 1 mythtv 6789 2008-09-28 09:54 mythbackend.log
-rw-r--r-- 1 mythtv 1270 2008-09-27 12:50 mythbackend.log.1
-rw-rw-r-- 1 server    0 2008-09-27 12:50 mythfrontend.log
-rw-rw-r-- 1 server 2908 2008-09-27 12:50 mythfrontend.log.1
-rw-rw-r-- 1 server 7598 2008-09-26 18:18 mythfrontend.log.2
-rw-rw-r-- 1 server    0 2008-09-26 18:16 mythwelcome.log
server@SERVER:/var/log/mythtv$

---

### Post by ian dobson on 2008-09-28
Hi,

It looks as if the mythfrontend.log is owned by "server" rather than mythtv.

As what user does the frontend process run? If you go to the terminal and do:-

cd /var/log/mythtv
chmod 666 *

All logs will be read/writeable for all users. You need to restart the frontend to activate logging.

Regards
Ian Dobson

---

### Post by myth01 on 2008-09-28
Thanks I'll give that a go.  How can I find out what user a program is being run as?

---

### Post by myth01 on 2008-09-28
The chmod did the trick, I just hope it stays that way this time....

Thanks Ian for your help

---

### Post by ian dobson on 2008-09-28
Hi,

If this is really solved please mark the thread as solved using the thread tools option.

Regards
Ian Dobson

---

### Post by myth01 on 2008-09-28
Sorry, didnt know I could do that.

---

