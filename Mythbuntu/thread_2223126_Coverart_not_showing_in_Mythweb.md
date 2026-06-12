---
title: "Coverart not showing in Mythweb"
date: 2014-05-09
forum: Mythbuntu
---

### Post by jlatz on 2014-05-09
I am in the process of rebuilding my Mythbuntu system, after I thrashed my 12.04 LTS install recently trying to upgrade to 14.04 LTS.  Good news is that all of my data, all of my recordings, were safe on a separate spinning disk.  Bad news is all my hacks within on the OS disk are gone.

Here's my problem - I have coverart downloaded for some of my videos, and it displays just find using Mythfrontend, but it won't display using Mythweb.  Yes, I have storage groups enabled, yes I have "show video covers" set in Mythweb.  Tracking through the Perl (I am not a Perl programmer), I can see that $cover_url is being set correctly as it finds the source file.

Further, the resulting html from executing Mythweb shows this pattern:
[TABLE]
[TR]
[/TR]
[TR]
[TD="class: webkit-line-content"]        <div id="4022_img">                <img src="[pl/coverart/13062_coverart.jpg]("http://192.168.0.51/mythweb/pl/coverart/13062_coverart.jpg")" width="94" height="132" alt="Missing Cover"></div>[/TD]
[/TR]
[TR]
[TD="class: webkit-line-number"][/TD]
[/TR]
[/TABLE]

While the filename is correct, clicking the link results in a 404.  As far as I can tell, there is a symbolic link missing somewhere (mytweb/data?), but I can't figure it out.  I thought I had found and fixed a similar issue with my last install - but like I said, all that info is gone and I can't find any similar issue via google.

Can anyone help?

---

### Post by blm-ubunet on 2014-05-09
Isn't the problem to do permissions of mythweb user (www) having access to storage groups / folders outside /html..
I believe it is a serious mistake to allow www user to directly access outside folders/files especially if you plan to allow access from outside your LAN.

The symlink solutions make folders that has safe(r) www access.
[http://www.mythtv.org/wiki/MythWeb](http://www.mythtv.org/wiki/MythWeb)
(about 75% down the page)
Also have to allow
Options Indexes FollowSymLinks

---

### Post by jlatz on 2014-05-09
I am accessing via symlinks:

> ln -l /usr/share/mythtv/mythweb/data
lrwxrwxrwx 1 root root 22 May  3 19:12 video -> /data/videos
lrwxrwxrwx 1 root root 30 May  3 19:12 tv_icons -> /var/cache/mythweb/image_cache
lrwxrwxrwx 1 root root 26 May  3 19:12 recordings -> /data/recordings
lrwxrwxrwx 1 root root 21 May  3 19:12 music -> /data/music
lrwxrwxrwx 1 root root 30 May  3 19:12 cache -> /var/cache/mythweb/image_cache
lrwxrwxrwx 1 root root 14 May  9 15:03 video_covers -> /data/coverart


And yes, /etc/apache2/sites-enabled/mythweb.conf contains:

    <Directory "/var/www/html/mythweb/data">
        # For Apache 2.2
        #Options -All +FollowSymLinks +IncludesNoExec
        # For Apache 2.4+
        Options +FollowSymLinks +IncludesNoExec
    </Directory>

And I have restarted Apache several times...

---

### Post by jlatz on 2014-05-10
Okay - solved it:

sudo ln -s /data/coverart coverart

Once that link was created, good to go...

---

