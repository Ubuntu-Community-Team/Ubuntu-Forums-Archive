---
title: "Cron Not Working"
date: 2012-09-22
forum: Mythbuntu
---

### Post by jamoody on 2012-09-22
After upgrading from Mythbuntu 11.04 to 12.03 cron does not appear to be working.  I have scripts in /etc/cron.daily and /etc/cron.weekly that aren't running.  I modified /etc/crontab from 
     25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
to 
     05 4    * * *   root    run-parts --report /etc/cron.daily
to eliminate anacron as the issue (though I didn't restart cron if that makes a difference).  If I run it manually via 
      sudo run-parts --report /etc/cron.daily
everything in that directory runs fine.

Ideas?

---

### Post by philled on 2012-09-23
> **jamoody said:**
> After upgrading from Mythbuntu 11.04 to 12.03 cron does not appear to be working.  I have scripts in /etc/cron.daily and /etc/cron.weekly that aren't running.
Ideas?
I recently had problems with scripts in /etc/cron.daily etc not running. The problem was caused by the script names having dot characters in them. Eg myscript.sh is not allowed by default and won't run, but myscript-sh is OK.

See this from man run-parts:
"If neither the --lsbsysinit option nor the --regex option is given then the names must consist entirely of ASCII upper- and lower-case letters, ASCII digits, ASCII underscores, and ASCII minus-hyphens".

---

### Post by Kantalias on 2012-09-23
> **jamoody said:**
>  If I run it manually via 
      sudo run-parts --report /etc/cron.daily
everything in that directory runs fine.

Ideas?

I had a problem with this after upgrading and it was an issue with the environment that cron runs in.  I was missing a few configuration files in root.  The cron utility does not get the environment of sudo -- for me the commands worked as sudo but not in the cron job because with sudo the script in question was getting the configuration files out of my user's folder whereas cron need them in /root.

See [http://stackoverflow.com/questions/2135478/how-to-simulate-the-environment-cron-executes-a-script-with](http://stackoverflow.com/questions/2135478/how-to-simulate-the-environment-cron-executes-a-script-with) for ideas about testing the cron environment.

---

