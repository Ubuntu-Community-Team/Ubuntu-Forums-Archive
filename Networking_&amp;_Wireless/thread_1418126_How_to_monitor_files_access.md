---
title: "How to monitor files access??"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by robert.rosman on 2010-02-28
Hi guys.
 
I'm running server with couple of websites. I want to put on the server couple of flash games, and movies in flv format. I want to monitor files access to this files. I mean I want to be able to see if any other website didn't linked to these files.
 
Any suggustions where I can start looking?

---

### Post by Barriehie on 2010-02-28
inotifywait might can help you out.  If a watched dir./file is opened for reading, writing, closed, etc. it can do whatever.  I use it in a script that launches at boot to detect dl'ed files and then rename and move them.

HTH

---

### Post by amac777 on 2010-02-28
Sounds like you are concerned about "hot linking", which is where other websites will steal your bandwidth by linking to content on your website without your permission. There's lots of information about detecting and preventing hotlinking on google. Here's a brief intro and some information on how you can use .htaccess on apache to prevent it.

[http://www.tamingthebeast.net/articles6/hotlinking-protection.htm](http://www.tamingthebeast.net/articles6/hotlinking-protection.htm)

---

