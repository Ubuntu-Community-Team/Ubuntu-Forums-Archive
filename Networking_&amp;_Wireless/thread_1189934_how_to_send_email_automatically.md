---
title: "how to send email automatically ?"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by shva on 2009-06-17
I would like to do this thing: every time when I turn on my Ubuntu (before I log in), system will get the ip address of this computer, record it in a log file and send it to [email]user@domain.com[/email] . Can anybody help me figure out how to do it? Thank you.

---

### Post by MaindotC on 2009-06-17
YOu'd have to write a script and add it to the startup configuration.  Now, I am not a developer, I don't know anything about scripting except a few simple sed & awks I did in this Unix book I'm reading, and I'm only able to give you a high-level, broad understanding that you may have figured already.  But, here's one suggestion I have for you.

Write a script that uses lynx, the console-based web browser, to go to something like [http://www.whatismyip.com](http://www.whatismyip.com) and pulls the ip address from the page source.  Then the script would probably invoke the sendmail program and send an email with that ip address to they email account of your choice.  Then place this script in your /etc/init.d/r* directory (not sure which of the r's you put it in) and you'll need to delay the script so that it executes after your machine has fully booted and is connected to the network - I believe that's the "sleep" command.

---

