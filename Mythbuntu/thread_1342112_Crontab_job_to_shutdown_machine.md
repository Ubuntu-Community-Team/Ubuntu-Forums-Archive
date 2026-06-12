---
title: "Crontab job to shutdown machine"
date: 2009-11-30
forum: Mythbuntu
---

### Post by gwagchunks on 2009-11-30
Hi

Hope someone can help. I have setup a quick script to shutdown the box at a set time. 
```

#!/bin/bash
shutdown -h now

```
I made the script executable by: chmod +x cronpower.sh

If I run cronpower.sh from a terminal window it works, but when I add to my crontab file (or roots, or mythtv) it does not work. Here is the crontab:

```

sudo crontab -u gwagchunks -l
# m h   dom mon dow    command
05 30 * * * /usr/local/bin/cronpower.sh

```

Just to confirm I have been changing the time to 5 mins in the future to test (not just using the same time!)

Any ideas?

Many thanks

---

### Post by azmyth on 2009-11-30
Probably need to add the user to your visudo file and then add to your script.

sudo shutdown -h now

---

### Post by gwagchunks on 2009-11-30
> **azmyth said:**
> Probably need to add the user to your visudo file and then add to your script.

sudo shutdown -h now

Hi azmyth

Thanks for the reply. I did a visudo and added:

%gwagchunks ALL = NOPASSWD: /usr/local/bin/cronpower.sh

I also added a line for mythtv and amended both crontab files for myself gwagchunks and mythtv and still nothing?

---

### Post by gdonwallace on 2009-11-30
An easier way to cause cron to shutdown your system is have it execute the program directly.  To ensure that the shutdown executes properly, I would suggest taking the line that you currently have in your crontab, put it in the root crontab, and instead of executing your script file, execute shutdown with the options that you want.

May look something like this:

05 30 * * * shutdown -r now

Or to use the command directly:

05 30 * * * /sbin/shutdown -r now

In either case, the shutdown command will shutdown the machine and reboot afterwords.  If you only want the machine brought down, remove the -r, as that is the reboot flag.

Hope that helps.

---

### Post by gwagchunks on 2009-11-30
> **gdonwallace said:**
> An easier way to cause cron to shutdown your system is have it execute the program directly.  To ensure that the shutdown executes properly, I would suggest taking the line that you currently have in your crontab, put it in the root crontab, and instead of executing your script file, execute shutdown with the options that you want.

May look something like this:

05 30 * * * shutdown -r now

Or to use the command directly:

05 30 * * * /sbin/shutdown -r now

In either case, the shutdown command will shutdown the machine and reboot afterwords.  If you only want the machine brought down, remove the -r, as that is the reboot flag.

Hope that helps.

Thanks gdonwallace

I used the second one and this works perfectly! 

Thanks again, that'll save some money off the electricity bill until I get a chance to look at ACPI.

---

