---
title: "mythtv &quot;frontend only&quot; changes channels by itself"
date: 2008-01-12
forum: Mythbuntu
---

### Post by mkalracuesl on 2008-01-12
Hello everyone

installed a combined backend + frontend -> works like a dream.

then I set up a second box with a frontend only. configured everything and it seemed to work very well with the remote backend.  but then I noted that the "frontend only box" switches channels without beeing told! (about every 3 minutes)

is this a feature or a bug? :)  
or maybe some special mode to automatically zap through all channels??

what did I miss? any ideas?
rgds
Marcel

---

### Post by tgm4883 on 2008-01-19
Are you using a STB that feeds into your backend with IR blasting?

---

### Post by mkalracuesl on 2008-01-23
nope - but I found the problem: 
had nxtvepg running in daemon mode to collect program information :)

after I killed that process the channel switching stopped. found an entry in the logs where it said something about another process using the tv-card ... 

the frontend that runs on the same system as the backend didn't get any signal at all (black screen) ...

guess this is solved :)

thanks for your answer anyway!

---

