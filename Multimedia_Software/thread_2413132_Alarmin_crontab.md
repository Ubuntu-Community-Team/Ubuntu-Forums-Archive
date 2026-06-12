---
title: "Alarmin crontab"
date: 2019-02-21
forum: Multimedia Software
---

### Post by Langstracht on 2019-02-21
I would like to have some audio alarms initiated in crontab.

I was under the impression that any legit CLI command could be used in a crontab file.

```
play whatever.wav
``` 

works just fine on CLI ... but I am unable to get it to perform in crontab.

Should I be able to?  

If yes, then what might I be missing in getting it to work?

If no, then can someone suggest another way I can get working alarms?

Thanks in advance.

---

### Post by #&amp;thj^% on 2019-02-21
Not sure if you have seen this yet: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
More info here: [https://askubuntu.com/questions/719590/help-using-crontab-to-play-a-sound](https://askubuntu.com/questions/719590/help-using-crontab-to-play-a-sound)
"gnome-schedule" can add a simple to use solution.

---

### Post by Langstracht on 2019-02-21
Thanks for taking the time to respond.

Maybe it's just my pea brain but I don't see how the url's you cited apply.

My crontab has perhaps a hundred lines ... all of which work fine.  So crontab syntax is not an issue.

I'm afraid I don't see the applicability of the "play-a-sound" url to my "play/crontab" issue.  

Unless you ARE saying that "play" does NOT work in crontab and that I should instead run a script from crontab ...

So I'm back to the question "should play work in crontab"?  And, if so what might/could be wrong?

Again thanks.

---

### Post by #&amp;thj^% on 2019-02-21
Play needs more: (Nor have I used the term "play" in any cron jobs)
Cron passes a minimal set of environment variables to your jobs. 
A common "gotcha" here is the PATH environment variable being different. Maybe your cron script uses the command somecommand found in /opt/someApp/bin, which you've added to PATH in /etc/environment? cron ignores PATH from that file, so runnning somecommand from your script will fail when run with cron, but work when run in a terminal. It's worth noting that variables from /etc/environment will be passed on to cron jobs, just not the variables cron specifically sets itself, such as PATH.

To get around that, just set your own PATH variable at the top of the script. E.g.
```

#!/bin/bash
PATH=/opt/someApp/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

# rest of script follows
```

Some prefer to just use absolute paths to all the commands instead. I recommend against that. 
Perhaps if you showed us the script your trying to use it would help us to help you.
Example of just one of my crontab -e......For just giving me the time every hour.
```
#!/usr/bin/env bash
my_date=$(date +'%I:%M:%S')
padsp espeak "$my_date"
```
My "crontab -e"reads as follows:
```
0 * * * * bin/say_hour
```
Enter the time (multiple times, days need to be separated with commas) and the script to execute for the alarm. The asterik can be used (*) to satisfy all variables. example for audacious:
```

07  21  *   *   1,2,3,4,5   env DISPLAY=:0.0 audacious /home/user/My\ Music/Other/Alarms/301gq.mp3
```

---

### Post by Langstracht on 2019-02-22
Thanks for your very complete response which has resulted in me now having a working alarm.  

I appreciate your help.

---

