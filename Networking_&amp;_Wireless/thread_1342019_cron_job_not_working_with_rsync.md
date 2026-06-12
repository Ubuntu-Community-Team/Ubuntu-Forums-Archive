---
title: "cron job not working with rsync"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by ahounsome on 2009-11-30
I used to have a simple cron job that ran an rsync backup routine to back my /home/user directory to another box in the office. I've rebuilt my machine and the cron job with Crontab -e but its not working. I've added >> to the rsync script to get output and it seems that the job gets as far as adding the date and time and then falls over at the rsync string. I've actually watched the machine processes with top and I can see that its not running rsync and ssh. The machines authenticate to each other with root permissions with ssh using rsa keys that I have generated. Running the script manually works fine. Any suggestions welcomed.

---

