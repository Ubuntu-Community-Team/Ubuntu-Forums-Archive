---
title: "Having problems installing Mythtv?"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by Patrick Dixon on 2007-02-13
I've given up with it, but here's a few things I've learnt along the way which may help someone else.

If you follow the ubuntu howto's there are a few things you need to know and some that don't quite work as advertised.

1) Mythtv uses MySQL, and the installation will create both a mythtv linux user AND a mythtv MySQL user.  Both of these have passwords, which may or may not be the same, and which may or may not be set.

2) The ubuntu installation creates both a mythtv linux user and a MYSQL mythtv user with random passwords.  If you follow the instructions, you don't ever need to log on as mythtv, so the user password doesn't matter.  You may have to access MYSQL using mythtv's password though, so you have two options:

- check /etc/mythtv/mysql.txt for the random password and use that
- reset the password to "mythtv" and edit /etc/mythtv/mysql.txt to set it to the same.

**If you end up with different passwords in /etc/mythtv/mysql.txt and MySQL, mythfrontend will not connect to the mythtvbackend and you will not get very far.**

To reset the MySQL mythtv password to "mythtv":

# mysql -u root mysql
> UPDATE user SET Password=PASSWORD('mythtv') WHERE user='mythtv';
>FLUSH PRIVILEGES;
>quit;

(This assumes that you haven't set a 'root' MySQL password - if you did, you're on your own!)

[b]IF YOU DO THIS, THEN DO NOT DO

sudo dpkg-reconfigure --force mythtv-database

AS SUGGESTED BY THE TROUBLESHOOTING PAGE - IT WILL RESET THE PASSWORD BACK TO A RANDOM ONE!![/b]

2) The section of the HOWTO where it says:

"Right click the desktop and log out of the openbox session. At the gdm screen, switch the session to Mythtv. Login. When asked if you want mythtv as the default, hit yes. Now, when restarting your machine, mythtv should come right up."

doesn't seem to work.   What worked for me was, instead of doing

sudo /etc/init.d/gdm restart

a few steps earlier, do a complete reboot of the machine.  When the login screen comes up, select the 'Options' tab at the bottom left of the login screen, and then 'select session'.  From there, you should have the option to select the MythTV session, and when you then login, you'll get the option to make it the default.

Alternatively (if you didn't reboot), kill the openbox/X session (Cntrl, ALT, Backspace may work) to get back to the login screen, and follow the instructions from there.

3) For me, the screen power saving clicked in on mythtv after a 20minute (or so) time.  This was a bit of a PITA for TV watching, so to disable this I added the line 

xset -s noblank &

in the /usr/local/bin/mythtv.sh file that had been made.

In the same file, I also changed the line

mythfrontend&

to 

mythfrontend > /var/log/mythtv/mythfrontend.log 2>&1 &

which at least gives you a logfile for the frontend output, should you ever need to debug something or ask for help!

I'm not 100% sure the 'xset' command works, so if anyone has a better solution, please post it.

4) There seems to be some feeling that mythtv works better with ALSA sound that OSS.  To select ALSA, in mythfrontend > Utilities / Setup > Setup > General
set Audio Output Device to 'ALSA:default' and Mixer Device to 'default' (you will need to type these in the boxes).

HTH, and that you have more success than me.

Good luck!

---

