---
title: "Zoneminder 1.23X Apache and Ubuntu Intrepid -----No Video Output"
date: 2009-01-14
forum: Multimedia Software
---

### Post by metallica1973 on 2009-01-14
I have install Ubuntu Intrepid and Zoneminder 1.23X. I have setup all of the all of the cameras and every time I try and run the cameras is cycle or montage mode I get no picture and I see a little emblem that resembles a broken connection. I checked /var/log/apache2/error.log and I can see that that there is an error with finding /htdocs

[PHP][Tue Jan 13 15:08:30 2009] [error] [client 127.0.0.1] File does not exist: /htdocs, referer: http://localhost:12444/zm/index.php?view=cycle&group=0&mid=3&mode=stream
[Tue Jan 13 15:09:00 2009] [error] [client 127.0.0.1] File does not exist: /htdocs, referer: http://localhost:12444/zm/index.php?view=cycle&group=0&mid=4&mode=stream
[Tue Jan 13 15:09:30 2009] [error] [client 127.0.0.1] File does not exist: /htdocs, referer: http://localhost:12444/zm/index.php?view=cycle&group=0&mid=5&mode=stream
[Tue Jan 13 15:10:00 2009] [error] [client 127.0.0.1] File does not exist: /htdocs, referer: http://localhost:12444/zm/index.php?view=cycle&group=0&mid=1&mode=stream
[Tue Jan 13 15:10:30 2009] [error] [client 127.0.0.1] File does not exist: /htdocs, referer: http://localhost:12444/zm/index.php?view=cycle&group=0&mid=2&mode=stream[/PHP]

I checked apache.conf and I can see that all is pointing to /usr/share/zoneminder. I checked the directory and see no reference of htdocs.I created the file and gave it the same permissions as the other files in the directory{root} and still no success. Can someone help?

---

### Post by metallica1973 on 2009-01-15
problem solved. It turned out to be an configuration issue with apache and the virtualhosts. I had changed the listening port 80 to 12444 in apache2.conf and also needed to do so under the /etc/apache2/site-enabled/000-default{virtualhost}. After that is all work fine.

:guitar:

---

