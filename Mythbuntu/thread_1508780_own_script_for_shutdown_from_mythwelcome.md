---
title: "own script for shutdown from mythwelcome"
date: 2010-06-13
forum: Mythbuntu
---

### Post by Saubazi on 2010-06-13
Hopefully my final challenge is getting my own shell script to run instead the standard shutdown. I have a shell script that shutdowns some services and then suspends for instance.

Now the beginning of the script is as follows:
$ head -15 scripts/suspend2ram.sh 
```
#!/bin/sh

date > /home/jykke/scripts/beforesuspend.log
echo "Myth processes before suspend:" >> /home/jykke/scripts/beforesuspend.log

ps -e | grep myth >> /home/jykke/scripts/beforesuspend.log
ps -e | grep CCcam >> /home/jykke/scripts/beforesuspend.log
ps -e | grep sasc >> /home/jykke/scripts/beforesuspend.log

echo "Stopping backend..." >> /home/jykke/scripts/beforesuspend.log

sudo stop mythtv-backend

echo "Backend should not show now in ps:" >> /home/jykke/scripts/beforesuspend.log

```

for shutdown command I have in mythwelcome "sudo suspendscript.sh"

All that happens is that mythtv-backend is stopped but somehow, for example the next echo is not written into the log file anymore...

At the same time from command-line my script runs through and machine suspends so I do not understand why it goes differently from mythwelcome?!?

---

### Post by Saubazi on 2010-06-13
Hmmm...could this be because the script is maybe executed by backend and the execution is interrupted when backend is stopped? I'll try with & and nohup...

---

