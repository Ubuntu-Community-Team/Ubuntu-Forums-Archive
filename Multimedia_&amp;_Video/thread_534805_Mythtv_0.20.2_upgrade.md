---
title: "Mythtv 0.20.2 upgrade"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by pulpinator on 2007-08-25
Is there a way to upgrade to Mythtv 0.20.2 (which supports the new data service) using apt-get? I've had really good luck upgrading everything with apt-get. I'd rather not download sources, compile, etc.

And a question that seems extremely newbie-ish, but I can't figure it out, how do I check which version of Mythtv I have installed?

---

### Post by napsilan on 2007-08-25
don't know about upgrading, but you can check your mythtv version using

dpkg --list | grep myth

---

### Post by PilotJLR on 2007-08-25
I found a forum posting (on gossamer-threads) saying that the new version will be in ubuntu repos early next week.

---

### Post by PilotJLR on 2007-08-28
In case you haven't seen this new update:
[http://ubuntuforums.org/showthread.php?t=536555](http://ubuntuforums.org/showthread.php?t=536555)

---

### Post by morgwon on 2007-08-28
that thread will not provide any help for those that dont have synaptic. Some of us have a barebone os and only use it for mythtv. 

The way I did it. 

Added these lines to sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main restricted universe multiverse

then I logged into the recovery mode since it would not allow me to update the backend portion otherwise (it would always say it was going to be held back when logged in as anything but root)

ran 

apt-get update
apt-get upgrade

and that was it.

Hope this helps.


Disclaimer: there maybe other things that will want to be updated. I do not know how to exclude things using apt-get but I allowed everything to update on my system and have not experienced any issues since the update.vc

---

### Post by superm1 on 2007-08-28
> **morgwon said:**
> that thread will not provide any help for those that dont have synaptic. Some of us have a barebone os and only use it for mythtv. 

The way I did it. 

Added these lines to sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main restricted universe multiverse

then I logged into the recovery mode since it would not allow me to update the backend portion otherwise (it would always say it was going to be held back when logged in as anything but root)

ran 

apt-get update
apt-get upgrade

and that was it.

Hope this helps.


Disclaimer: there maybe other things that will want to be updated. I do not know how to exclude things using apt-get but I allowed everything to update on my system and have not experienced any issues since the update.vc

That is the reason i was wary of describing the method in the command line setup.  Excluding you would have to choose each package that you had installed and be careful what you marked.  But what is described above is accurate :)

---

### Post by johnnyspire on 2007-09-02
I always use 'aptitude' instead of just apt-get. It allows me see what my options are.

---

