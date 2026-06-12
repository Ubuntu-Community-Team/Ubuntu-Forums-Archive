---
title: "Idea for sharing files via webpage on LAN.  Feasible?"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by Objekt on 2010-10-07
I have banged my head against the Samba sharing problem off and on for months now, with little progress and minimal success.  It is way, way, way harder than it should be, and I have been unable to determine whether it's the fault of Windows 7, Ubuntu 9.10, or some combination of the two.  All I want to do is make some volumes on my Ubuntu machine browsable by the Windows 7 machine and any other Windows machine which may connect to my LAN, but apparently that is too much to ask.

All this time, the Windows 7 machine has had no trouble at all accessing the Apache server that I apparently installed on my Ubuntu 9.10 box, then forgot about.  I can browse to the Ubuntu machine's local IP address in the Windows 7 machine's browser, and I get the default "It works!" page.

Is there a fairly easy way to share files via that Web interface?  Couldn't I somehow share the desired volumes?  I know I've been to websites before where I could browse through a file system, very similar to what I would see in Windows Explorer or Ubuntu's Nautilus, but it all happened inside the Web browser.

Are there any reasons why I would not want to do that?  What is the most easily-configured software for serving up files that way?

Note that I am mostly interested in a one-way, read-only connection.  My Ubuntu 9.10 machine has a ridiculous amount of storage, so it acts as a pseduo-server to all other machines on my LAN.

I don't think there are any security issues here.  As far a I know, my Ubuntu machine's Apache server will only be visible to machines on my LAN.  If I'm missing any security considerations, please point them out.

---

### Post by SeijiSensei on 2010-10-07
Try WebDAV using Apache's mod_dav.  Here's one fairly extensive explanation on how to set this up: [http://www.nubae.com/webdav-with-ubuntu-and-moodle](http://www.nubae.com/webdav-with-ubuntu-and-moodle)

---

### Post by Objekt on 2010-10-07
Thanks, but that really wasn't any good.  I didn't see any way to share drives (ex. stuff in /media), only how to make folders in /var/www.  

Also it didn't work, perhaps because the walkthrough is 2 years old.  This "webdav" stuff is way too complicated.

---

### Post by SeijiSensei on 2010-10-07
> **Objekt said:**
> ```
Syntax error on line 6 of /etc/apache2/httpd.conf: DAV not allowed here
```
What on earth does that mean?!

Usually it means you placed an Apache directive in a location where it isn't allowed.  I looked in one of my .conf files where I had enabled DAV, and the "DAV on" directive is within a <Directory> container like this:

<Directory /path/to/the/DAV/resource>
DAV        on
</Directory>

If you want to require a password to access the share, you'll need to put the directives like AuthUserFile in the <Directory> container as well.

You should also read [http://httpd.apache.org/docs/2.2/mod/mod_dav.html](http://httpd.apache.org/docs/2.2/mod/mod_dav.html) which has some examples.  

If you're still stuck, post your httpd.conf file so we can take a look.

DAV is only valuable if you want to enable people to post files as well as download them.  If you just want to enable downloads of files you put there yourself, try something like this:

```

Alias /music /media/music
<Directory /media/music>
Options +Indexes
</Directory>

```

Now restart Apache and try [http://my.web.server.address/music/](http://my.web.server.address/music/).  You should see a list of your files.  Make sure the directory and files are either world-readable, or readable by the Apache user www-data.

---

