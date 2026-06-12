---
title: "Mythtv Authentication errors and other issues"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by minirx7 on 2007-03-19
I just wanted to help out those that have issues when following the guide for mythtv on 6.10 [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

First off:
Running mythtv-setup....

If you get an error saying mythv@localhost insufficient privileges or something of that nature.  Do what i did.

Install sudo apt-get install phpmyadmin.  Then from there go to your browser and go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

If you get an error saying cannot connect, you may have to install php5, search it in your synaptics package manager and isntall it.

When you log in, use root, and the blank for the password (unless you changed it).  Go to click on priviledges and reset the password for username mythtv with the password mythtv.

This will allow you get past the mythtv-setup phase.

RUNNING /etc/cron.daily/mythtv-backend
If you are having issues about some authentication issues or anything of that nature, then do this:
sudo nano /etc/cron.daily/mythtv-backend
inside you will find something like this:
su mythtv -c "mythfilldatabase blah blah blah
Change the mythtv to your own user name (the user name that you used following the guide for which you added to the group mythtv).
 
This should allow you to run this command with no issues.

RUNNING /etc/init.d/mythtv-backend
again if you run in ot the issues of authentication or anything, do this.
sudo nano /etc/init.d/mythtv-backend

in there you will find something like $USER=mythtv or something of that nature.  Change mythtv to the USERNAME that you added to the group mythtv.

This is how i resolved all my issues.  It seems that even though the setup adds the user mythtv, it doesnt add it in a way that you can run these commands as that user.  But since your current USERNAME is already added to the group mythtv, you should have no issues running these scripts as your own username.

I appologize for not being very specific, and i am a newbie, but i hope this helps other people.

Regards
ED

---

### Post by pulpinator on 2007-03-27
Another option is to not modify the username that the backend runs under. Instead, add the mythtv user to the mythtv group:

```

sudo usermod -a -G mythtv mythtv

```

That fixed the problem for me.

---

