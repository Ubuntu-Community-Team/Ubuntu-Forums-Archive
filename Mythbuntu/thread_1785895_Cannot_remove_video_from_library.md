---
title: "Cannot remove video from library"
date: 2011-06-18
forum: Mythbuntu
---

### Post by chipppy on 2011-06-18
Good Morning

I made a new mythbox for a friend using 11.04.  Install went perfect.
I put a few kids cartoons into the Videos directory to test and all worked great.  Deleted the kids videos

We then install a 500GB second hard drive to hold the video and my mate then put his video collection onto the second hard drive, modified the backend to look for the second drive.

When we scanned for changes it found all the videos in the second drive, but all the kids videos are still shown in the library???????

The kids cartoons dont work as the file has been deleted but it is still shown.  I tried to use the delete function from the library but that dosent work either.

How do I get these removed kids cartoons to disappear???

Cheers
chipppy

---

### Post by Senkoboy on 2011-06-19
> **chipppy said:**
>  mate then put his video collection onto the second hard drive, modified the backend to look for the second drive.


Did you delete the path for the first hadrdrive? You might try putting the path for the cartoons back into the backend, scan for changes and see if that works.

---

### Post by chipppy on 2011-06-19
Good Morning

We had both the original /var/lib/mythtv/videos and the 2nd harddrive /var/lib/mythtv/HDD2 in storage directories when the problem occured

I tried removing /var/lib/mythtv/videos and scanning for changes
didnt help

I put /var/lib/mythtv/videos back in and scanned for changes and still didnt help.

Any other ideas

Help please

Cheers
chipppy

---

### Post by ktmom on 2011-06-20
For me, the simplest answer if you have a webserver installed is to install phpMyAdmin (sudo apt-get install phpmyadmin).  Make sure you do a mythtv database backup before starting.

The installer will walk you through the setup.  Then use your browser to your boxes ip address/phpmyadmin.  Log in using the mythtv user and the password (grep DBPassword /etc/mythtv/config.xml).  Then go to mythconverg -> videometadata  The links are on the left.

Now click the tab "search" at the top and you have a page that will help you search
on every field in the videometadata table.  Find the row for filename.  In the "operator" column, select "LIKE %...%"  and in the text field enter "/var/lib/mythtv/videos".  Go to the bottom of the page and hit "go".  This will return a list of every entry that was on the old drive.  You can delete them by hitting the red X in the third column of the results page.

It seems like a lot of work, but phpMyAdmin is the easiest way to engage with a SQL database.  You could do this on the command line if you'd rather not install another app.

---

### Post by nickrout on 2011-06-23
you could manually delete the rows concerned from the videometadata table.

---

### Post by larsolav on 2011-06-23
Forgive my ignorance, but could you not just highlight the offending videos in the mythvideo menu and press "d" to delete? I know it will not actually delete the non-existing files, but maybe it would delete the entry in the database?

---

