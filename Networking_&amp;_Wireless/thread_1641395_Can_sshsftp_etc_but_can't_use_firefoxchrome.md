---
title: "Can ssh/sftp etc but can't use firefox/chrome?"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by pjlfield on 2010-12-09
Hi all,

I am struggling with what I think is a very strange issue (however my networking experience is quite limited).  

We are running Ubuntu 10.04 on a new workstation, and are having troubles with the internet connection.  It was working for some time, then, without any memorable changes, no longer connects to the internet through firefox/chrome etc...  The connection itself seems fine, as we can ssh/sftp/ping other computers around the building.  Perhaps it is an issue with html?  I am out of ideas, so any help would be much appreciated - Thanks!!!

 -Peter

---

### Post by pjlfield on 2010-12-10
back to the top

---

### Post by pjlfield on 2010-12-10
Additional information:

It now appears that HTTP is probably not the issue.  I can connect to some sites through their IP addresses (e.g. google ip 72.14.213.147).  However, connecting to [www.google.com](www.google.com) still does not work.  Does this sound like a DNS issue?

---

### Post by pjlfield on 2010-12-10
Solved!  Turns out the computer was not getting the proper DNS locations from /etc/resolv.conf.  No idea how this file was edited (there were only two lines in the file), but giving it appropriate DNS IP's for my location fixed all the issues.

---

