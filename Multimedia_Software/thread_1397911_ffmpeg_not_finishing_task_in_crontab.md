---
title: "ffmpeg not finishing task in crontab"
date: 2010-02-03
forum: Multimedia Software
---

### Post by Vinny_P on 2010-02-03
Hi all,

Hi all,

I have a script that I wish to use crontab to execute. When I run the script in a shell the line "ffmpeg -i ~/Record/Music/Flash* -f mp3  ~/Record/Music/$(date +"%a-%b-%d-%y-Time:%I:%M").mp3" command execute and completes. However when crontab runs the script the ffmpeg command does not complete its task. I know crontab executes the ffmpeg command in the script but must close the process before ffmpeg can finish.

Is there a workaround or reason? Limitation to crontab? Your help is appreciated :-)

This is another problem related to the same project from:
[http://ubuntuforums.org/showthread.php?p=8769027&posted=1#post8769027](http://ubuntuforums.org/showthread.php?p=8769027&posted=1#post8769027)

Thank you,
Vinny P

---

### Post by dingletec on 2010-08-13
I'm also having this problem.  Works perfectly on all video clips when run manually from command line.  Dies when run from cron.

--edit

Ok, did a bit more searching of the forums and found:

[http://ubuntuforums.org/showthread.php?p=9625890](http://ubuntuforums.org/showthread.php?p=9625890)

Solution is very simple, at the top of the crontab, put:

MAILTO=""

---

