---
title: "Apache Web Stats"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by apjone on 2006-07-10
Sorry, couldnt find a server thread so I though networking was next best place to post this question.

What stats package would you advise me to use for an apache hosted website on the web?

---

### Post by mpvano on 2006-07-10
This isn't really an Ubuntu issue, but personally, I feel that all the commonly available "automated" packages are security risks at the moment. Most of them have holes that are exploited regularly to break into systems.

This means that the safest thing to do is make your own custom implementation. That way hackers have no idea where to find files to exploit, or how to exploit them.

I use the package called analog myself to do this, and run it from a userspace cron job in a separate user account (with no logins allowed via properly configured password file) used just for such purposes. I then use carefully controlled read only access to a "user" apache documents directory for that account to read the reports.

Be aware of three things, however:

1) analog is very powerful, but it's REALLY a nuisance to configure.

2) DO NOT use any online forms, etc to configure web statistics - they're often exploitable.

3) Be careful what you allow public access to as far as statistics go. Some common report summaries can either be a security risk in themselves, expose you to privacy lawsuits, or provide hacker's with invaluable "how am I doing" feedback.

4) as with anything you install in a public web server you should very carefully examine the installed files for any packages (such as analog) you install to make sure they don't do things you don't want done or install services or configurations that are dangerous to your security by default. Security is still YOUR problem, not the package distributer's!

Good luck,

Mario

---

### Post by tturrisi on 2006-07-10
I use Webalizer for all my deb servers.  It works out of the box.  If want high security with it use .htaccess & .htpasswd so the dir is not accessable to all viewers.
[http://www.mrunix.net/webalizer/](http://www.mrunix.net/webalizer/)

---

