---
title: "Cannot log into system after upgrade to 9.1"
date: 2009-11-18
forum: Mythbuntu
---

### Post by nunrgguy on 2009-11-18
AS the title suggests - just upgraded b/e to 9.1 and am now unable to get in and do anbything. am prompted with log inscreen on boot. TYHpe in the password and it tries to start (myth logo seen) and then loops back to log in screen.

---

### Post by nunrgguy on 2009-11-18
Right, after about 30 attempts have actually managed to log in but it's not looking good - mythconverg is down.
Here's the error log:
[http://mythbuntu.pastebin.com/f64cdf98]("http://mythbuntu.pastebin.com/f64cdf98")

---

### Post by nunrgguy on 2009-11-19
Right, this seems to have fixed it:

First I checked the hostname which is now Mythtv.
Previously I had 127.0.0.1 in the f/e as hostname didn't used to work, I changed it to hostname.

Then I opened a terminal and did the following:

cd /etc/mysql
sudo mv my.cnf my.cnf.9.04
sudo cp my.cnf.dpkg-dist my.cnf

Followed by 
sudo mysql-upgrade

Then reboot

You will be prompted re the upgrade - click upgrade when asked (this will happen a couple of times).

Live TV etc will then work.

Also of interest is, I'm ALMOST certain (though not completely) that I had another user 'mythtv' on the system, this is now gone so hopefully system permissions issues of the past will be gone fingers crossed.


This isn't a total fix I don't think as phpmyadmin shows that additional features for linked tables are disabled and connection for controluser failed.

---

### Post by chipppy on 2009-11-19
Good Evening

Take a look at [http://ubuntuforums.org/showthread.php?t=1308845]("http://ubuntuforums.org/showthread.php?t=1308845").

This seems to be a bit of an known issue

Cheers
chipppy

---

### Post by nunrgguy on 2009-11-19
That wasn't it at all in this instance, the problem seems to have been that the front end would try to load, couldn't find the backend, because it wasn't there and then crash out to the login screen again

---

