---
title: "TVtime I/O error."
date: 2008-03-29
forum: Multimedia &amp; Video
---

### Post by OisinT on 2008-03-29
tvtime worked ok for me for a long time and I didn't change anything, but it stopped working.
I searched around to fix the errors, but it didn't fix it.  I'll just post the log so you can see what went wrong.

```
oisint@OisinT1:~$ sudo chown oisint /etc/tvtime/tvtime.xml
oisint@OisinT1:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/oisint/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/oisint/.tvtime/tvtime.xml: Permission denied.
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O warning : failed to load external entity "/home/oisint/.tvtime/stationlist.xml"
station: No station file found, creating a new one.
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O warning : failed to load external entity "/home/oisint/.tvtime/stationlist.xml"
station: No station file found, creating a new one.
I/O error : Permission denied
I/O error : Permission denied
Thank you for using tvtime.
oisint@OisinT1:~$ 


```

---

