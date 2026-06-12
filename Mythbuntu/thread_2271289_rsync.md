---
title: "rsync"
date: 2015-03-28
forum: Mythbuntu
---

### Post by deanie44 on 2015-03-28
Hi everyone.  I am trying to run rsync as a cronjob.  I can run rsync from the terminal, but the cronjob will not run.
The cronjob is as follows: 17 22 * * *[B] [COLOR=#a52a2a]/usr/share/doc/rsync -av --delete /home/sakkie56/ /media/home/test/
 [/COLOR][/B]Can anyone give me a few suggestions of what I am doing wrong.  Should sudo be used to run the job?
Any help will be appreciated.  sister5091

---

### Post by mikewhatever on 2015-03-28
Try /usr/bin/rsync instead.

---

### Post by papibe on 2015-03-28
Hi deanie44.

The proper path for rsync is /usr/bin/rsync

I would also log rsync's output so you can better debug it:
```
17 22 * * * /usr/bin/rsync -av --delete /home/sakkie56/ /media/home/test/ > /home/sakkie56/rsync.log 2>&1
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by deanie44 on 2015-03-28
papibe and mikewhatever, thank you for answering my post.  I have tried your suggestions and they did not work. I did get a log file in my home directory.  The cronjob is --[COLOR=#a52a2a]**05 23 * * * /usr/bin/rsync -av --delete /home/sakkie56/ /media/home/test/ > /home/sakkie56/rsync.log 2>&1**[/COLOR].  I must be doing something wrong?  More ideas will be appreciated.  sister5091

---

### Post by SeijiSensei on 2015-03-28
What "didn't work?"

---

### Post by deanie44 on 2015-03-28
Hi SeijiSensei.  I am talking about using a cronjob for rsync.  I am trying to use the rsync command to backup my home directory daily with a cronjob.  I used the suggestions from mkewhatever and papibe, but unfortnately it did not work. Here is the cronjob:
-[COLOR=#a52a2a]**05 23 * * * /usr/bin/rsync -av --delete /home/sakkie56/ /media/home/test/ > /home/sakkie56/rsync.log 2>&1**[/COLOR].  I must be doing something wrong?  More ideas will be appreciated.  sister5091

---

### Post by deanie44 on 2015-03-29
Thank you gentlemen.  I figured it out.  I'm good.  sister5091

---

### Post by ajgreeny on 2015-03-29
And the solution was??

---

