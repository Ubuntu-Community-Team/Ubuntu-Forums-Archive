---
title: "Close/Open port 21 using command line"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by bgabga on 2011-03-12
I would like to Close/Open port 21 using command line. I have an FTP server and I don't want to have the port open all the time. I need only two hours by week to be open port 21 from outside to inside.
So I need to know the command line for opening and closing the port 21 then I will implement this in a script into cron.hourly.

Thank you,

---

### Post by Iowan on 2011-03-12
One option might be to start/stop the FTP server that uses the port...

---

### Post by gmargo on 2011-03-12
What are you using for firewall software?  If it's **ufw( 8 )**, then it should be easy:

```

ufw allow ftp        # Open port 21

ufw deny ftp         # Close port 21

```

---

