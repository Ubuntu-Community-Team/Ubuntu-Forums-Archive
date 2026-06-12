---
title: "Mythweb doesn't work after updates"
date: 2008-09-16
forum: Mythbuntu
---

### Post by daviding on 2008-09-16
I installed Mythbuntu 8.04 about six weeks ago, everything was working fine, including Mythweb.

I used Mythweb earlier today, and programmed a number of shows.  I then ran the update program, and now get the message ...

-- begin paste --

Database Setup Error
The database environment variables are not correctly set in the webserver conf or .htaccess file.  Please read through the comments included in teh file and set up the db_* environment variables correctly.
Some possible solutions are to make sure that the mode_env is enabled in httpd.conf, as well as having followed the instructions in the README and INSTALL files.

-- end paste --

Following the suggestions at [https://bugs.launchpad.net/mythbuntu/+bug/221532](https://bugs.launchpad.net/mythbuntu/+bug/221532) , I looked at ...
/etc/mythtv/mysql.txt , ... and ...
/etc/apache2/sites-available/mythweb.conf ...
... and found both of the passwords to be the same.

Looking on Synaptic Package Manager, the installed version of mythtv is 0.21.0+fixes18207-0ubuntu4~hardy1 .

Could someone please suggest additional diagnostics to restore the functionality in Mythweb?  Thanks.

---

### Post by oobe-feisty on 2008-10-14
i have the same problem could someone fix the updates before they post them

---

### Post by jbman on 2008-10-15
Looks like the backports is running since I think thats the same version i got from it. I am having avi playback issues after the update, mythweb working ok, so i guess i am lucky.

Backports is off now.

---

### Post by oobe-feisty on 2008-10-15
hi i figured out why i did not have my host name in mysql.txt and /etc/apache2/sites-available/mythweb.conf after my update's similar to another problem i have in another thread

---

### Post by danbodoh on 2008-11-15
Just to make this more clear:

To fix the problem, edit /etc/apache2/sites-available/mythweb.conf

and change line 

            setenv db_server        ""

to put the hostname of your myth machine in the quotes.

Dan Bodoh

---

