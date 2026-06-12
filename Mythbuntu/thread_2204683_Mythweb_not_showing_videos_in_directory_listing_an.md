---
title: "Mythweb not showing videos in directory listing and streams not available"
date: 2014-02-09
forum: Mythbuntu
---

### Post by RadioDave_FM on 2014-02-09
I'm getting my mythbuntu setup to where it is nearly rock solid.  Backend and frontend both look good.  Recording is great and working well. The issue that I seem to be running into is running mythweb.  I've gotten mythweb up and running where I can pull schedule listings and set recording schedules.  However when I pull up the video directory, nothing is there.  I do confirm that my paths for recordings and videos are mapped correctly.  I will also have episodes show up in recorded shows, but when I go to stream them or even download the episodes, I get a 404 Error

VideoStartupDir is linked to /Spare/Recordings which has videos in it.

---

### Post by RadioDave_FM on 2014-02-15
Bump

---

### Post by newlinux on 2014-02-20
Are you using storage groups for your videos? Do you have slave backends? Answers to these questions may help me diagnose.

---

### Post by RadioDave_FM on 2014-05-31
Sorry, I haven't been on this forum in ages.  Appreciate you offering a hand to assist.  I do have storage groups set up that are mapped to my home drive on a separate partition.  The location for all the recordings is /home/dave/Recordings

My mythweb.conf looks like this for host setup.

# If you intend to use authentication for MythWeb (see below), you will
# probably also want to uncomment the following rules, which disable
# authentication for MythWeb's download URLs so you can properly stream
# to media players that don't work with authenticated servers.
#
    <LocationMatch .*/pl/stream/[0-9]+/[0-9]+>
        Allow from all
    </LocationMatch>

    <LocationMatch .*/music/stream.php>
        Allow from all
    </LocationMatch>


#
# CHANGE THESE PATHS TO MATCH YOUR MYTHWEB INSTALLATION DIRECTORY!  e.g.
#
#    /var/www
#    /home/www/htdocs
#    /var/www/html/mythweb
#    /srv/www/htdocs/mythweb
#
    <Directory "/var/www/html/mythweb/data">
        # For Apache 2.2
        # Options -All +FollowSymLinks +IncludesNoExec
        # For Apache 2.4+
         Options +FollowSymLinks +IncludesNoExec
    </Directory>

/var/www/html/mythweb/data leads to the links directory...video, recordings, etc.  I have linked all to /home/dave/Recordings, and I'm still having the Not Found problem.  

I don't have any slave backend setups.

---

### Post by khPWXxF on 2014-06-02
Have you tried this?
```
mythutil --scanvideos
```
Phil

---

