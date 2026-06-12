---
title: "Mutt and sending via cron"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by potgietdl on 2009-02-18
Hi Guys,

I need help...again.

I`ve setup mutt to use gmail via one of the ubuntu ariticals. I only use this to send mails out of the server. It works great in user mode, but if i use sudo to run the script that sends the mail. i get an exception stating .msmtprc has to be owned by root. Now i know this is not the right procedure but if a change the owner to root and run the script again as sudo it works.

The problem is that when the script triggers via cron it doesnt work, nor do i get an exception.

any ideas how to be able to send mail when cron calls a script

Rgds
D

---

### Post by andrew.46 on 2009-02-19
Hi,

You could try using the -C option to call another msmtp configuration file:

> 
              -C, --file=filename
                     Use the given file instead of ~/.msmtprc as the user con-
                     figuration file.




Andrew

---

