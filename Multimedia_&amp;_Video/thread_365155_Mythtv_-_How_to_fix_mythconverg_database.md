---
title: "Mythtv - How to fix mythconverg database?"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by williammanda on 2007-02-19
I got one computer setup as a combined frontend, backend, and desktop (following superm1 instructions). I'm working on finishing another frontend. I have run into a problem. I got the 2nd frontend setup and working. Watched tv for about 10 minutes and the video and audio froze. Soon after that the masterbackend computer froze. I was able to reboot the 2nd frontend properly but I had to use the reset button on the masterbackend computer. When I restarted mythbackend and started viewing the 2nd frontend I got this error message in the terminal window (where I started the master backend):
2007-02-18 14:47:30.766 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1501' , '2007-02-18T14:47:27' , '75' , 9 , '5884400' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

How do you repair the database?
Also does superm1 have a quide for setting up a masterbackend? I followed all I know from the mythtv wiki.
Thanks

---

### Post by wjston on 2007-02-19
> **williammanda said:**
> 
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

How do you repair the database?
Also does superm1 have a quide for setting up a masterbackend? I followed all I know from the mythtv wiki.
Thanks

Go to post #5 using the following URL. I have explained how to repair mythconverg using a web browser.
[http://www.ubuntuforums.org/showthread.php?t=357927&highlight=MYTHTV](http://www.ubuntuforums.org/showthread.php?t=357927&highlight=MYTHTV)

---

### Post by williammanda on 2007-02-19
Thanks for the reply!
I didn't load PHP on this mythtv install. Can I install it now? If so, what file would I need to use?
Thanks

---

### Post by wjston on 2007-02-19
> **williammanda said:**
> Thanks for the reply!
I didn't load PHP on this mythtv install. Can I install it now? If so, what file would I need to use?
Thanks

Yes you can. Follow the directions here (scroll down about half a page to phpmyadmin):
[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)

---

### Post by williammanda on 2007-02-20
Thanks for he post! It worked great!
Thanks

---

### Post by wjston on 2007-02-20
> **williammanda said:**
> Thanks for he post! It worked great!
Thanks

Glad I could help.

---

