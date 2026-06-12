---
title: "I need to run a script with &quot;nohup&quot;?"
date: 2009-12-09
forum: Mythbuntu
---

### Post by larsolav on 2009-12-09
Hi there,
After my fresh install of 9.10 I have again a problem with "Could not find channel 26_1 in TVCT" as I chronicled _[here]("http://ubuntuforums.org/showthread.php?t=804252")_. Same channel, same program, same wife not happy with our wonderful mythbox...

Since then more people have seen the same problem, and someone came up with a script that monitors the backend log file for the "Warning: Recording will not commence until a PMT is set" message, and if found, restarts the backend process. The script can be found _[here]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/229797/comments/10")_.

My question: The poster mentions that "I start it [the script] from /etc/rc.local with nohup." I am not familiar with running nohup. Could anyone please tell me how I would have this script running in Mythbuntu?

Thanks in advance,

Lars

---

### Post by ian dobson on 2009-12-09
Hi,

Have a look here:- [http://en.wikipedia.org/wiki/Nohup](http://en.wikipedia.org/wiki/Nohup)

You just need to save the script as a file, set the execute bit then start the script with nohup script_name &.

You could add this script start to /etc/rc.local.

Also if your running 9.10 mythbackend has gone over to using upstart so you need to change the script to use start/stop mythtv-backend rather than /etc/init.d/mythtvbackend start/stop


Regards¨
Ian Dobson

---

### Post by larsolav on 2009-12-09
Thank you! Thank You, Ian!

Will give this a try after work tonight!

So if want to add this script start to /etc/rc.local, then should I put the script in the /etc/ folder? Then after saving it there do a  "sudo chmod 755 script_name"  to make it executable? (as you can tell I am new at this script stuff)

---

### Post by azmyth on 2009-12-09
You can put the script basically anywhere. Stuff like this I put in /usr/local/bin so you know where to go to make changes. Say you name it check.sh then you want to sudo chmod +x /usr/local/bin/check.sh

Then in your /etc/rc.local file add 

nohup /usr/local/bin/check.sh &

From looking at the check.sh file, you'll also want to make sure your backend log is in this directory. I'd also make sure you have the MYLOGFILE created by sudo touch /root/mythtvBugCheck.log

MYLOGFILE="/root/mythtvBugCheck.log"

MYTHLOGFILNAME="mythbackend.log"
MYTHLOGDIRNAME="/var/log/mythtv/"

---

### Post by larsolav on 2009-12-09
> **azmyth said:**
> You can put the script basically anywhere. Stuff like this I put in /usr/local/bin so you know where to go to make changes. Say you name it check.sh then you want to sudo chmod +x /usr/local/bin/check.sh

Then in your /etc/rc.local file add 

nohup /usr/local/bin/check.sh &

From looking at the check.sh file, you'll also want to make sure your backend log is in this directory. I'd also make sure you have the MYLOGFILE created by sudo touch /root/mythtvBugCheck.log

MYLOGFILE="/root/mythtvBugCheck.log"

MYTHLOGFILNAME="mythbackend.log"
MYTHLOGDIRNAME="/var/log/mythtv/"

Thank you for the detailed instructions!
I made the edits to the script (changed the way you stop and start the backend, and have the mythtvBugCheck.log go to /var/log/mythttv (just to have it with the other logs). I did the chmod command.

In in /etc/rc.local I added "nohup /usr/local/bin/check.sh &"
so now rc.local looks like this:
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

nohup /usr/local/bin/check.sh &

exit 0

I wasn't sure whether to put the new line before or after the "exit 0" line. Does it matter?
Also, was I correct in doing this after saving my edited rc.local: "sudo chmod +x  rc.local"  ?

after reboot, is there a way to make sure that the check.sh script is running?

Thanks again for your awesome help!

---

### Post by azmyth on 2009-12-09
looks good. Just reboot then do a

ps -A | grep check

to make sure the check script is running.

---

### Post by larsolav on 2009-12-09
Yes!!!!!!! I think I did it!

> husebo@mythbox:~$ ps -A | grep check
 2167 ?        00:00:00 check.sh


Thank you sooooooo much azmyth!

---

### Post by azmyth on 2009-12-09
Yup. Your welcome. Enjoy!

---

