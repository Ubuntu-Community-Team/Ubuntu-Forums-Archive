---
title: "Run gnome-ppp as Normal User"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by undoIT on 2009-01-19
In Ubuntu 8.04 Hardy, I had my Samsung SPH-M610 cell phone with Sprint service tethered and working as a modem using kppp. Sprint provides detailed although somewhat dated instructions for getting this working in Ubuntu with kppp.

After installing Ubuntu 8.10 Intrepid I decided to try and get the M610 tethered using gnome-ppp and skip installing all of the KDE dependencies. The good news is that gnome-ppp works. The bad news is that it must be run as Super User, I have to open terminal and run sudo gnome-ppp

If I try to run gnome-ppp as a normal user I get the following error message in gnome-ppp log:

> Unable to run /usr/sbin/pppd.
Check permissions, or specify a "PPPD Path" option in wvdial.conf.

I have tried creating the user group "dip" with GUID 30 and adding my user account as suggested elsewhere on the internet. This did not work. I have also tried chowning pppd to my user rather than root. I can get connected after doing this but only for a split second and then gnome-ppp disconnects.

Is there any way to run gnome-ppp as a normal user in Ubuntu Intrepid?

---

### Post by ieee488 on 2009-01-19
[http://www.computechgroup.com/?p=539](http://www.computechgroup.com/?p=539)
even though they are talking about different commands, it worked for me

I also chmod /usr/sbin/gnome-ppp to 555

---

### Post by undoIT on 2009-01-19
/usr/sbin/gnome-ppp

file does not exist.

i tried running this command:

> sudo chmod u+s /usr/sbin/pppd

still getting the same error after relogin.

---

### Post by ieee488 on 2009-01-19
I first chmod /usr/bin/gnome-ppp to 555 did not work but the steps in section #2 in that linked website worked for me

I'm using gnome-ppp for my AirCard 860

---

### Post by undoIT on 2009-01-20
I found this fix on another thread:

[http://ubuntuforums.org/showpost.php?p=6011957&postcount=2](http://ubuntuforums.org/showpost.php?p=6011957&postcount=2)

I only needed the first two lines to get gnome-ppp working as a normal user:

```
sudo chown root:dip /usr/sbin/pppd
sudo chmod 4754 /usr/sbin/pppd
```

Hopefully this is more user-friendly in Jaunty :)

---

### Post by Trackieman on 2009-06-26
ieee488's (Posting #2) Using visudo to edit the /etc/sudoers file worked for me.
Now the icon I have on the desktop of my Dad's laptop executes sudo gnome-ppp as root but does NOT ask for the root password.

There's a good explanation (not to wordy and easy to understand (I hope))
of the sudoers file at [https://help.ubuntu.com/community/Sudoers]("https://help.ubuntu.com/community/Sudoers")

---

