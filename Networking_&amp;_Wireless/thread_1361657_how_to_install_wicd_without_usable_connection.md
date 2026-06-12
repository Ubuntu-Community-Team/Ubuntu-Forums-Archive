---
title: "how to install wicd without usable connection"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by Tobias Mahaler on 2009-12-22
Hi there!
here's my sad story:
I've removed network manager for wicd and for a while everything went ok. BUT soon showed up problems getting the IP. Because I'm a noob things went out of controll and now I have to find a way to install wicd again, this time without connection (no apt-get for me!)
I've tried to download the package from here [http://sourceforge.net/projects/wicd/files/](http://sourceforge.net/projects/wicd/files/)
and follow the instruction but it still wicd don't show up.
(if I try to remove it get:
 
wicd is not installed, so not removed
 
ok, good!
 
can someone please help me getting my connection?

---

### Post by chenxiaolong on 2009-12-22
Download the version from the Ubuntu repository: [http://mirrors.kernel.org/ubuntu/pool/universe/w/wicd/wicd_1.6.1-3ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/w/wicd/wicd_1.6.1-3ubuntu1_all.deb)

FYI, all the Ubuntu packages can be downloaded at [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by Tobias Mahaler on 2009-12-23
thanks a lot!
hope this will work..
merry xmas, if you care about it!

---

### Post by Tobias Mahaler on 2009-12-25
ok, I've downloaded the .deb archieve and opened with GDebi package installer. still I haven't wicd working. it appears on applications->internet->wicd but doesn't do anything at all, even if i run it in terminal, only ask for pasword the first time
 
I've removed the old directory /etc/wicd but still wicd seems to be alive. and now gives the Dbus error.
How can I delate it completely?

---

### Post by chenxiaolong on 2009-12-25
You can remove it completely by opening Synaptic and selecting [COLOR="SeaGreen"]Remove Completely[/COLOR] for [COLOR="DarkOrchid"]Wicd[/COLOR] or you can run:

```
sudo apt-get -y remove --purge wicd
```

---

### Post by shredder12 on 2009-12-25
deleting /etc/wicd will only remove the config files of wicd nad probably that's why you are getting the error
follow the above post to completely remove it.

---

### Post by HobbitTR on 2010-04-10
> **Tobias Mahaler said:**
> Hi there!
here's my sad story:
I've removed network manager for wicd and for a while everything went ok. BUT soon showed up problems getting the IP. Because I'm a noob things went out of controll and now I have to find a way to install wicd again, this time without connection (no apt-get for me!)
I've tried to download the package from here [http://sourceforge.net/projects/wicd/files/](http://sourceforge.net/projects/wicd/files/)
and follow the instruction but it still wicd don't show up.
(if I try to remove it get:
 
wicd is not installed, so not removed
 
ok, good!
 
can someone please help me getting my connection?
I had a similar dbus error problem which you did not discuss very well. I found a solution here:
[http://ubuntuforums.org/showthread.php?t=1243485](http://ubuntuforums.org/showthread.php?t=1243485)
code:
sudo wicd -foe

Should reveal a parsing error in /etc/wicd/wired-settings.conf -- 
There will probably be a line with an empty "[]" on it, remove that line.
Then run wicd-client again, your daemon should start and connect immediately.

---

