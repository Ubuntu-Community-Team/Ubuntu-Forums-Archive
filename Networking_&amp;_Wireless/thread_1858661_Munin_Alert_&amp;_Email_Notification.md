---
title: "Munin Alert &amp; Email Notification"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by mikaelcrocker on 2011-10-12
Hey All,

Using Munin and about ready to add a fist hole in the nearest object lol

Okay, so I used the contact command in the midst of some monitoring.

load.load warning 4
load.load critical 6
contact.mike.command mail -s "Munin Alert!! ${var:host}" [EMAIL="myemail@yea.com"]myemail@yea.com[/EMAIL]
contact.mike.always_send critical warning

I don't get an email, and I don't get anything.

Help! Objects are becoming perforated around me

---

