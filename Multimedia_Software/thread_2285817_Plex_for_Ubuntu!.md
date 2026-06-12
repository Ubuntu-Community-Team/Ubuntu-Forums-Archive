---
title: "Plex for Ubuntu!"
date: 2015-07-08
forum: Multimedia Software
---

### Post by cmcanulty on 2015-07-08
Good news now youy can get 32 or 64 bit app for plex here

[https://plex.tv/downloads]("https://plex.tv/downloads")

I have a problem though starting it. I followed the directions here

[https://support.plex.tv/hc/en-us/articles/200264746-Quick-Start-Step-by-Step]("https://support.plex.tv/hc/en-us/articles/200264746-Quick-Start-Step-by-Step")

But I get these errors after successfully installing it with gdebi

```

cmcanulty@ubuntu1:~$ sudo /etc/init.d/plexmediaserver start
[sudo] password for cmcanulty: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service plexmediaserver start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start plexmediaserver
cmcanulty@ubuntu1:~$ service plexmediaserver start
start: Unknown job: plexmediaserver
cmcanulty@ubuntu1:~$  start plexmediaserver
start: Unknown job: plexmediaserver
cmcanulty@ubuntu1:~$
```

---

### Post by dino99 on 2015-07-08
is chmod +x helpfull ?

---

### Post by cmcanulty on 2015-07-08
well I installed it OK but what file should I set to x ? I couldn't find it in /usr/bin/

---

