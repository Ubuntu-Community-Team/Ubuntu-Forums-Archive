---
title: "Modifieng startsequence - delay mythbackend start etc."
date: 2010-06-03
forum: Mythbuntu
---

### Post by Saubazi on 2010-06-03
I wonder where the mythtv-backend is started. I can not find it under /etc/rc*

I would like to delay it further on since initialization of video adapters etc. takes so long that there is a conflict. 

Additionally I would like to delay start of frontend and include a process check for backend as I get most of the time an irritating message that backend is not up yet. 

I had this kind of functionality in my old box where I manually installed mythtv on ubuntu-desktop version and used fluxbox. With xfce I do not know where the start of this stuff is defined...

---

### Post by bance on 2010-06-03
I'm not sure if it's what you're looking for but try this thread!

[http://ubuntuforums.org/showthread.php?t=1481488](http://ubuntuforums.org/showthread.php?t=1481488)

---

### Post by Saubazi on 2010-06-04
I think this will solve my backend problem. But where is it defined in the xfce that frontend is started automatically?

---

### Post by Saubazi on 2010-06-04
I think this will solve my backend problem. But where is it defined in the xfce that frontend is started automatically?

---

### Post by ian dobson on 2010-06-04
Hi,

Mythbuntu now uses upstart to start many of the startup processes (/etc/rcX.d/ is still supported for scripts that haven't been converted). The configuration files for upstart scripts are in /etc/init on Mythbuntu.

Upstart doesn't use a fixed start script 1 then 2 then 3, rather it uses an event system. When your network starts up start all processes that rely on network (dns, firewall etc).

Regards
Ian Dobson

---

### Post by Saubazi on 2010-06-04
Yes but that is not where start of frontend is defined?
I can see it in Application-Settings-Sessions and Startup.
I suppose I have to make my own shell script with necessary checks and so on for launching the frontend then...

---

