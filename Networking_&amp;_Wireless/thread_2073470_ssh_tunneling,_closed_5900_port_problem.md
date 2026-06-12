---
title: "ssh tunneling, closed 5900 port problem"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by ziemowitzima on 2012-10-19
Dear Users of GREAT Ubuntu,

It happens that I am working remotely. To do this I like to use viritual desktop which I start via ssh tunneling. But sometimes (e.g. now :( ) after I connect to my server it does not work...
I found what is wrong, but I dont have any idea how to fix it remotely...
I think that the reason of tunneling feilure can be seen, when looking at open/listen ports on the server side:
***@***:~$ netstat -an | grep  "LISTEN "
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:3000            0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN   

BUT to work fine it should be:
tcp        0      0 127.0.0.1:3350          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:3389            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:13666         0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:56713           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:40970         0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:42251         0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::5800                 :::*                    LISTEN     
tcp6       0      0 :::5900                 :::*                    LISTEN 

NAMELY, it should LISTEN a 5900 port.

My question is:
why it does not LISTEN the 5900 port, and how to switch it on ?

Thanks
ZZ

---

