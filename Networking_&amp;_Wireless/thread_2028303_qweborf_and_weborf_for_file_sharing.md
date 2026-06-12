---
title: "qweborf and weborf for file sharing"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by odinb on 2012-07-17
Hi!

Needed a quick and easy way to share files, and managed to find "weborf" in the repos.

Starting it using the GUI ("qweborf"), you can specify Authentication on the second tab. Perfect, just what I wanted!

But, I also want it running as a daemon, using the package "weborf-daemon", so I installed it. It works great, but I cannot figure out how to use authentication this way!
The Ubuntu manual ([http://manpages.ubuntu.com/manpages/maverick/man1/weborf.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/weborf.1.html)) refers to the author website ([http://galileo.dmi.unict.it/wiki/weborf/doku.php?id=authentication](http://galileo.dmi.unict.it/wiki/weborf/doku.php?id=authentication)) but I cannot grasp how to get it to work.

Anyone tried this?

Howto for dummies, please...

---

### Post by Lt_Worf on 2013-01-27
Hello,

I am afraid that you will need some programming to do so.

Open the file: **/usr/share/doc/weborf/examples/auth.py**
It is an example of authentication script for weborf. You can modify it according to your needs. For example if you need a certain username and password you can use the following condition (to replace the condition in the example file):

```
if not ('username' == data[3] and 'password' == data[4]):
    conn.send(' ')
conn.close()
```

Now save the new file somewhere like **/usr/local/sbin/weborf.auth** and give it exec permissions.

Also replace **/tmp/weborf_auth.socket** with **/run/weborf.auth**

Now you must edit **/etc/weborf.conf** and set

auth-bin=/usr/local/sbin/weborf.auth
auth-socket=/run/weborf.auth

After you did it, weborf will run with autentication.

---

