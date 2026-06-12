---
title: "Setting up shell script to send email at regular intervals?"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by josephellengar on 2010-02-11
I'd like to set up a shell script that will send various emails at regular intervals through gmail.  I'm sure that there is some sort of text-based email client out there, but I'd like to do this with cron or anacron.  I know a little bit of shell scripting but am definitely not great at it.  Does anybody have a suggestion about how I would do this?

---

### Post by capybara! on 2010-02-11
The 'mail' command could do that, you have to have sendmail installed for that. I use 'mutt', because it is a bit easier to send attachments with it. You can install sendmail and mutt from the repositories. Then you can make a little script and add it to your cron, it should not be too complicated if you know a bit of shell scripting. I do not know exactly how to tell sendmail to send from your gmail account, just look in the manpages. It should be possible, since gmail is open to connect with any client to send and receive mail. Does this help you?
Greetings

---

### Post by josephellengar on 2010-02-11
> **capybara! said:**
> The 'mail' command could do that, you have to have sendmail installed for that. I use 'mutt', because it is a bit easier to send attachments with it. You can install sendmail and mutt from the repositories. Then you can make a little script and add it to your cron, it should not be too complicated if you know a bit of shell scripting. I do not know exactly how to tell sendmail to send from your gmail account, just look in the manpages. It should be possible, since gmail is open to connect with any client to send and receive mail. Does this help you?
Greetings

Yes, it does.  Thanks.  Those programs look perfect. :D

---

