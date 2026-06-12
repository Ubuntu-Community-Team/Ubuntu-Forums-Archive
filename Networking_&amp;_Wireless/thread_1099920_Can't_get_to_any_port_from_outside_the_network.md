---
title: "Can't get to any port from outside the network"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by pkulak on 2009-03-18
This is really odd, but all of a sudden I can't get to my 8.10 box from outside the network. And it's not a network issue, because I forwarded port 22 on my router to my laptop to test and then it worked fine. All of a sudden everything is closed off, but only from the outside. Does anyone have any idea about how I can figure out what's going on? Thanks!

---

### Post by ktrnka on 2009-03-18
It looks like it is possible to ssh to your box. I just tried. Are you not getting past the password prompt? (I would suggest removing your dns name as this thread will eventually show up in google.)

---

### Post by pkulak on 2009-03-18
> **ktrnka said:**
> It looks like it is possible to ssh to your box. I just tried. Are you not getting past the password prompt? (I would suggest removing your dns name as this thread will eventually show up in google.)

Wow, that's really weird. I've tried SSH from three places (including my phone over 3G) and every ssh try just times out. You just did "ssh mydomain.com" and you got a password prompt?

---

### Post by ktrnka on 2009-03-18
Yep, just have to wait about 5 seconds then Password: comes up.

Here's your RSA fingerprint

38:6a:3b:1c:58:7a:15:11:00:64:9a:84:87:bb:f0:f0

just to double check.

Your ip is:

67.189.*.* (don't want to give our too much)

You should see 2 fails from user test and 1 from user pkulak in your auth.log

Could be a DNS resolve issue.

---

### Post by pkulak on 2009-03-20
Just for the sake of Google:

It was moblock. I thought I had it configured properly, but apparently not. Which, of course, explains why it was blocked only from certain places.

---

### Post by ktrnka on 2009-03-20
Ahhh ok, good to know.

---

