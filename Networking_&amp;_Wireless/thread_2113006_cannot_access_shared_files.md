---
title: "cannot access shared files"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by sala1q on 2013-02-06
New to ubuntu (2 days). Just insalled 12.04 amd64 on server. I can see domain and can ping pc's and servers in network but I cannot see the samba server on any ms pc. I've read as much as i can in 2 days and cannot seem to locate problem.

---

### Post by PowerBarry43 on 2013-02-06
Hi

I'm assuming that you are trying to set up ubuntu as a samba server if so here is the guide... otherwise if you wis to have ubuntu as a samba client take a look at this

[http://askubuntu.com/questions/137011/how-to-mount-a-samba-shared-folder-ubuntu-x-ubuntu](http://askubuntu.com/questions/137011/how-to-mount-a-samba-shared-folder-ubuntu-x-ubuntu)

For setting up servers I'd recommend using Webmin to configure samba. Webmin is a web front end for configuring services on linux machines which can be done either locally or remotely from another pc on the lan, all through the browser.


I'm guessing you've done this already but just incase you haven't install the samba server:

```

sudo apt-get install samba samba-common
```

then download webmin

```

cd /tmp
wget http://prdownloads.sourcecforge.net/webadmin/webmin_1.610_all.deb
```

then install (which is meant to fail) and use apt to resolve dependencies.

```
sudo dpkg -i /tmp/wemin_1.610_all.deb
sudo apt-get install -f
```

from here just go into a browser, type https://<ip-of-server>:10000

log in as root or a user in the sudoers file and go to this page:

[http://www.linux.com/learn/tutorials/299651:samba-configuration-with-webmin](http://www.linux.com/learn/tutorials/299651:samba-configuration-with-webmin)

you can start about halfway down where it says "Using Webmin To Configure Samba"

Hope this helps!

Barry

---

