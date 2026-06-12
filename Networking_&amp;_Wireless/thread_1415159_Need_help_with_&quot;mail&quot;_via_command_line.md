---
title: "Need help with &quot;mail&quot; via command line"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by jonnale on 2010-02-24
I have postfix configured and running properly, and I have it delivering mail to /home/$user/Maildir.

I also have mailx installed, because some users need to send mail over the terminal. This also delivers the mail to /home/$user/Maildir.

However, some users need to check their mail via command line, but when the user types in:

$: mail

It says the user has no new mail. I believe it is checking for mail in the folder /home/$user/mbox

However, the following works (consider the user name is claire):

claire@server $: mail -f /home/claire/Maildir

This command will show all of the mail.

Is there a way to set the default directory that the mail command looks for mail in? For example, how do I get it so that when the user types "mail", it searches in /home/$user/Maildir?

Cheers!

---

