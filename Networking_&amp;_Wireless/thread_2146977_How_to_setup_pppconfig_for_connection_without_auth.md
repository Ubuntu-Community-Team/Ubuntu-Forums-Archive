---
title: "How to setup pppconfig for connection without authentication?"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by drofart on 2013-05-20
[TABLE]
[TR]
[TD="class: votecell"]              
[/TD]
              [TD="class: postcell"]               When i am trying to setup a connection to my 3g dongle with an isp that does not need authentication, but pppconfig seems to not have that no authentication option. How to do? 

Thanks for ur time :)

      

[/TD]
[/TR]
[/TABLE]

---

### Post by praseodym on 2013-05-20
[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

Check this. Do you really want/need pppconfig?

---

### Post by drofart on 2013-05-20
Well, after viewing the checklist, it seems i can't connect through 3g dongle as i am tring yo do it in ubuntu server minimal installation! Right? I don't have any other device/modem to connect to web :(

---

### Post by praseodym on 2013-05-20
So try
```

sudo pppconfig
```

---

### Post by drofart on 2013-05-20
Tried but it is asking for an authentication type but my connection does not need any authentication and there is no option for "no authentication" just stuck there.

---

### Post by drofart on 2013-05-20
[ATTACH=CONFIG]242830[/ATTACH]

---

### Post by alexfish on 2013-05-20
Hi

if  no password required try PAP

ppp is front end to pppd /  pppd will try to negotiate the protocol required , if err have a look in the syslog

BR

Alex

---

