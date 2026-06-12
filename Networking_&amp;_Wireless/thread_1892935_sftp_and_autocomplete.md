---
title: "sftp and autocomplete"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by Synoc on 2011-12-09
ok I am almost positive when I started sftp'ing into my server I had autocomplete on both sides of my "put" aka

```
 put ~/Docu {TAB fills out Documents} home/user/DocumentsB{TAB completes DocumentsBackup/} 
```

last time I tried it just completed MY side, THIS time it won't complete any of it. 

when I tab at /home/us... it gives me a space... which DOES fill in user... but don't print it to the screen, and on the other side it tried to fill in MY side instead of the server side. OR doesn't autocomplete anything at all any idea what is happening?

---

### Post by Synoc on 2011-12-09
here's a script file of the issue... 

```


user@user-NB3:~$ sftp 192.168.0.9
user@192.168.0.9's password: 
Connected to 192.168.0.9.
sftp> put /home/u Videos/     #tabbed after u it added space where "user/" is written apparently type Vid then tabbed, autocompleted "Vidoes/" then tabbed and got this avi's and the /Webcam"
a_movie1.avi                              b_movie2.avi             
c_movie3.avi                       Webcam/                                 

sftp> put /home/p Videos/c_movie3.avi /media/  # autocompleted "c_movie.avi" from tabbing after "c" however the autocomplete for /media spits out the PCs /media/ being the DVD as the tabbed autocomplete shows below
sftp> put /home/u Videos/movie3.avi /media/c_movie3.avi/
JACKET_P/  VIDEO_TS/  
sftp> exit

```

I would love help with this I want my autocomplete to work properly again. it works fine when I'm NOT connected via sftp

---

### Post by Synoc on 2011-12-09
it HAS come to my attention that I have not stopped staring at a CLI but to sleep or drive in over 3 weeks... so I may be blurring everything together between my server administration and my PC backups TO my server... if I am hallucinating... please please tell me so I can take a vacation?

---

### Post by SlugSlug on 2011-12-09
I'd book that holiday,

I've seen this myself with scp am thinking that auto tab is filling in server side paths only to find out that the path is also on the client so it's filling in using that 

eg both client and server have a /media/Music/Artists


if you see what I mean :)

---

### Post by Synoc on 2011-12-09
except that the server doesn't. it stops at media. there and the home directory stops at user/ beyond that there's a folder called File Share to back up all my work and such. and the movies go to a portable hard drive.

obviously tab autoccompletion works or iit wouldn't give me anything. but why is it chopping off the account's home page and feeding me the client computer on both sides?

---

### Post by Synoc on 2011-12-12
bump. Is there some security reason why autocomplete chops off the account name and won't work on server side at all or is it that the client computer simply doesn't scan the folders on the server side?

---

