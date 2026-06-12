---
title: "PHP send mail problem"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by Black Mage on 2008-12-12
I am having a problem sending mail with PHP. I think my problem lies in the fact that my mail server is different from my web server. I am using the PHP-PEARL to send mail and I set my php.ini to this:

sendmail_path = /usr/sbin/sendmail -i -t

But could it be because the path is on the web server than it is preventing me from sending mail?

And there error I recieve is: unable to connect to smtp server [email]ddixon@my-lan.us[/email]:25

Thanks

---

### Post by albinootje on 2008-12-12
But does /usr/sbin/sendmail exist ?

I recommend to install postfix, and configure it to only accept emails from localhost.
Postfix will provide the /usr/sbin/sendmail binary.

---

