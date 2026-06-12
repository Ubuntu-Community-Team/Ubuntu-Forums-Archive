---
title: "HowTo continuously monitor MythBuntu MythTV logs"
date: 2008-08-18
forum: Mythbuntu
---

### Post by LarryJ2 on 2008-08-18
Frequently, I find myself doing  ***cat /var/log/mythtv/mythbackend.log | grep something*** as I fight my way through mythbuntu's configuration.  OK if you are searching (grepping) for a specific message,  but what if you want a continuously updated  display of the last say 60 lines in this log file? Then give this a try

1. Open a terminal click Applications ->Accessories -> Terminal

2. In the terminal enter
```
tail -n60 -f /var/log/mythtv/mythbackend.log
```

3. If you want to view the front end log at the same time, open another terminal and enter:
```
tail -n60 -f /var/log/mythtv/mythfrontend.log
```

4.  The -n60 says display the newest 60 lines in reverse (newest first) order and the -f says "don't close the terminal window but continue to print lines as they flow into the log file". Cntrl+C exits "tail" back to your terminal.

5.  Works for other files too.  For system messages, try
```
tail -n60 -f /var/log/dmesg
```

The display of these log files in the terminal windows will disappear  when you open mythbuntu frontend, but the changes will still be accumulated and available after you exit and return to the desktop.

---

### Post by ian dobson on 2008-08-18
Hi,

I usually use:-

watch tail -20 /var/log/mythtv/mythbackend.log

Watch calls tail every 2 seconds or so.

Regards
Ian Dobson

---

### Post by nickrout on 2008-08-18
watch is a great tool but not needed here.

One problem with tail -f is that when the logs are rolled over mythfrontend.log becomes mythfrontend.log.1 and a new mythfrontend.log is opened. However tail is still watching the old file. To get round this use tail -F (ie uppercase 'F').

---

### Post by nasha on 2008-08-19
Or to simplify it further, i've set up an alias to eliminate the need for typing all the garble all the time

> alias logsearch='tail -F /var/log/mythtv/mythfrontend.log'

I'd say this is almost worth a sticky... Most new users wouldnt know where to find their logs, yet its such a valuable troubleshooting tool.

---

### Post by managementboy on 2008-08-19
> **nasha said:**
> Or to simplify it further, i've set up an alias to eliminate the need for typing all the garble all the time



I'd say this is almost worth a sticky... Most new users wouldnt know where to find their logs, yet its such a valuable troubleshooting tool.

I like them both in one tail (alias mythlog='tail -F /var/log/mythtv/mythfrontend.log /var/log/mythtv/mythbackend.log')

---

### Post by LarryJ2 on 2008-08-19
Excellent!  I'm adding the alias logsearch entries now. For the benefit of others, open the /home/user/.bashrc file for editing using your favorite text editor. I prefer gedit:
```
sudo gedit ~/.bashrc
```

After the file opens in the editor gedit, I added the mythlog  alias line below the commented out alias.  Here's part of the edited file:
> # some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'
alias mythlog='tail -F /var/log/mythtv/mythfrontend.log /var/log/mythtv/mythbackend.log'

then log out and log back in again.  Open a terminal then enter the alias command  which will look something like this:
> lj@mythtv$  mythlog





Would this thread be appropriate for the "HowTo" closed "Sticky"?

---

### Post by nasha on 2008-08-19
I think so Larry. In my opinion there are many many other threads which should make it into the HowTo's sticky, yet the only thing thats in there is howto LVM which we dont even need since storage groups in 0.21!

---

### Post by JugeHuge on 2008-08-20
Does mythbuntu default use some of the log file rotation scripts??

Yesterday my mythbuntu got hosed up because mythbuntu logfiles filled root mount.

---

### Post by nickrout on 2008-08-20
looks to me as if they are rotated once a day with 7 days old logs kept. logrotate won't help if one days worth of logs fills up your filesystem as it only rotates once a day. You really need to sort out what is creating such huge log files and fix it :)

---

### Post by dannyboy79 on 2008-08-20
or he could change how many log files get saved for mythtv, wouldn't be change that in /etc/logrotate.d/mythtv-backend, then change the rotate 7 to something like rotate 3? don't know if that would work but it's a thought, or go to the /etc/logrotate.conf file and see if you can set up myth's log rotation differently by looking through man logrotate.

---

### Post by nickrout on 2008-08-20
If one days logs are filling the available space on the hard drive its not going to matter if he keeps 3 days or 7 days. Rapidly growing logs a symptomatic of a problem. The problem should be addressed at the top of the cliff, not the bottom.

---

### Post by JugeHuge on 2008-08-21
Thanks dannyboy79 for suggesting limiting daily log file count.. I think there should be also log file size limitation in use somehow..

Well i should look what was causing enormous log files but situation was new to me so deleted them instantly as soon as i found out.

I have used now one day to get all again back to track. Still some problems as i think that there is some setting files gone bad like i had mythtv config.xml emptied..

---

### Post by Archmage on 2008-08-21
Shouldn't we add a "; exit" at the end of the command, so that it will exit the terminal once we CTRL-C? At least I'm doing this will all my logs and I did never notice any problem.

---

### Post by tgm4883 on 2008-08-21
> **nasha said:**
> Or to simplify it further, i've set up an alias to eliminate the need for typing all the garble all the time



I'd say this is almost worth a sticky... Most new users wouldnt know where to find their logs, yet its such a valuable troubleshooting tool.

There is actually a program making it's way into intrepid right now that will gather MythTV related logs (stuff we think is relevant to troubleshooting) and automatically submit those logs to [http://mythbuntu.pastebin.com](http://mythbuntu.pastebin.com)  and present the link to the user.

---

