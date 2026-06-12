---
title: "Sending emails at specific intervals"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by plletz on 2013-04-10
Hi, I have been trying to figure this thing out for a few days without much success. I want to send out emails from a folder 1 email at a time to a specified address, at a given schedule. How could this be done?

*hint: can cron be used to achieve this?

---

### Post by lisati on 2013-04-10
Yes, cron can be used. 

A code snippet in PHP showing one way where cron isn't an option but where you have a web page you can include your code can be found here: [http://stackoverflow.com/questions/4121263/how-to-send-schedule-emails-using-php-without-cron-job](http://stackoverflow.com/questions/4121263/how-to-send-schedule-emails-using-php-without-cron-job) - it should be easily adaptable to being part of a script that's run automatically by cron.

---

