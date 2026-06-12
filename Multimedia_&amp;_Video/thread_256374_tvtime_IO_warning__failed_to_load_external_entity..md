---
title: "tvtime I/O warning : failed to load external entity...."
date: 2006-09-12
forum: Multimedia &amp; Video
---

### Post by 0okami on 2006-09-12
Im in the process of installing and configuring my notebook for video capture using dapper 6.06 and a PCMCIA saa7134 card... 

everytime i run TVTIME on my notebook, i get the following error: 

```
ookami@inspiron:~$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/ookami/.tvtime/tvtime.xml"
I/O error : Permission denied
Cannot change owner of /home/ookami/.tvtime/tvtime.xml: Permission denied.
videoinput: Cannot open capture device /dev/video0: No such file or directory
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O warning : failed to load external entity "/home/ookami/.tvtime/stationlist.xml"
station: No station file found, creating a new one.
I/O error : Permission denied
Thank you for using tvtime.
ookami@inspiron:~$

```

when looking at the folder .tvtime, it says im not the owner... 
Im not sure how to change that. sugestions?

I'd like to get tvtime working properly first and then later address the issue of my video capture card not being detected...

---

### Post by 0okami on 2006-09-12
I figured out a solution for my problem above... 
(in the steps below, replace "username" with your own username)


Remove tvtime...
```
sudo apt-get remove tvtime
```
 
Now, create a folder called .tvtime in the user's directory.
```
sudo mkdir .tvtime
```

Next, install tvtime. 
```
sudo apt-get install tvtime
```

go into the folder of tvtime (~/home/username/.tvtime) and change the owner of tvtime.xml like this: 
```
sudo chown username tvtime.xml
```

launch tvtime, and it should have no errors. 
```
tvtime
```

Atleast thats what worked for me. ^_^
now to fix tghe capture card to work properly... That will be a seperate thread...

---

### Post by Blixter on 2006-12-05
thank you! Had the same problem and tvtime seems to work properly now :)

---

