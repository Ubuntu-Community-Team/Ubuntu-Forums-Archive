---
title: "mythweb direct download doesn't work"
date: 2014-06-28
forum: Mythbuntu
---

### Post by itlarson2 on 2014-06-28
I am trying to get the mythweb "direct download" button to work.  The "recorded" page looks normal, and shows a listing of the recordings with thumbnails as usual.   In 12.04 I could use "direct download" to copy recordings onto a portable drive, but now when I click on it I just get:

Not Found
The requested URL /mythweb/mythweb.pl/pl/stream/1111/1403920860 was not found on this server.
 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at localhost Port 80

I have tried modifying the paths in /var/www/mythweb/data/ and /var/www/html/mythweb/data/ since my storage directory is in a non standard location:

$ ls -l /var/www/mythweb/data/
total 0
lrwxrwxrwx 1 root root 30 May 31 21:10 cache -> /var/cache/mythweb/image_cache
lrwxrwxrwx 1 root root 21 May 31 21:10 music -> /var/lib/mythtv/music
lrwxrwxrwx 1 root root 12 Jun 28 18:50 recordings -> /home/.store
lrwxrwxrwx 1 root root 26 May 31 21:10 recordings.bad -> /var/lib/mythtv/recordings
lrwxrwxrwx 1 root root 30 May 31 21:10 tv_icons -> /var/cache/mythweb/image_cache
lrwxrwxrwx 1 root root 16 Jun 28 18:58 video -> /home/itl/Videos
lrwxrwxrwx 1 root root 22 May 31 21:10 video.bad -> /var/lib/mythtv/videos
lrwxrwxrwx 1 root root 22 May 31 21:10 video_covers -> /var/lib/mythtv/videos

This is not something I have had to do before, and it didn't have any effect on the problem.  I also tried replacing /var/lib/mythtv/recordings with a link to my storage directory, but nothing has worked.  Any Ideas?

---

### Post by senator32 on 2014-07-01
I had the same issue on a DVR I recently installed. After a lot of looking I managed to fix it. Here is how: 

Fix mythweb downloads:
- sudo ln -s /etc/apache2/mods-available/cgi.load /etc/apache2/mods-enabled/cgi.load
- nano /etc/apache2/mods-available/mime.conf
- AddHandler cgi-script .cgi .pl
- Restart Apache2

I hope this helps!

---

### Post by itlarson2 on 2014-07-01
Thanks, that did it.

---

### Post by senator32 on 2014-07-01
Glad to help! :)

---

