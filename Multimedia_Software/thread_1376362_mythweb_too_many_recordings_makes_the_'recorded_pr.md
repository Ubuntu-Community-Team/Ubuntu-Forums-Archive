---
title: "mythweb: too many recordings makes the 'recorded programs' page crash"
date: 2010-01-09
forum: Multimedia Software
---

### Post by &lt;mike&gt; on 2010-01-09
hi.

ok, so I have a lot of recordings on my mythtv box.

i can see/play them fine within the mythfrontend interface, and mythweb loads almost all pages ok (including schedules, guides, etc.), but when I click on 'recorded programs' at the top, I get

--------
<b>[html]
Fatal error:  Allowed memory size of 33554432 bytes exhausted (tried to allocate 88 bytes) in /usr/share/mythtv/mythweb/includes/translate.php on line 142
[/html]---------
I've had this error before, and it went away when I purged my list of recordings.

any suggestions (aside from the obvious 'delete some programs, fool!', or 'post this on mythtv.org, fool!')?

what logs should I check?

---

### Post by dowdy on 2010-01-18
Have a peek in your php.ini file and increase the setting for "memory_limit"

or 

In the settings page for MythWeb, goto "TV" on the left and change the value "Page recorded programs" to 10 or 25 for example.

---

### Post by &lt;mike&gt; on 2010-01-19
What's the path to php.ini? Is it /etc/php5/pache2/ ? And do I need to restart anything to make this work?
The settings 'page recorded programs' didn't fix it, by the way.

---

### Post by tzihad on 2010-03-27
I have same issue.
In /etc/php5/apache2/php.ini memory_limit = 1024M and in
 /etc/apache2/sites-enabled/mythweb.conf i have php_value memory_limit 256M.
Still i get 
Fatal error: Allowed memory size of 67108864 bytes exhausted (tried to allocate 79 bytes) in /usr/share/mythtv/mythweb/includes/translate.php on line 142
I have ~1500 recordings.

---

