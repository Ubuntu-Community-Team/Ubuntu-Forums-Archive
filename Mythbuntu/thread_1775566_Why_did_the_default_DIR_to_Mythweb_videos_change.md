---
title: "Why did the default DIR to Mythweb videos change?"
date: 2011-06-04
forum: Mythbuntu
---

### Post by nhtrader on 2011-06-04
myth v0.24.1-9
ubuntu 10.10 (32bit)
xfce 4.8.0


Something changed when I applied the upgrade this week. First, Mythweb failed. So I uninstalled it and then reinstalled it to get it working again. 

But now a new problem has arisen. I've always used the default settings for storage directories, so when I use mythweb the path to the videos was 
[http://10.10.10.12/mythweb/videos/MyMovie.mpg](http://10.10.10.12/mythweb/videos/MyMovie.mpg)

Now it's [http://10.10.10.12/mythweb/data/video/MyMovie.mpg](http://10.10.10.12/mythweb/data/video/MyMovie.mpg)

Notice that there's a new sub-directory "/data/video" not simply "mythweb/videos" in the path. I'd like to remove it. How do I remove this sub-directory? Or how do I reset the path that mythweb uses?

I've checked:
1. /etc/apache2/apache2.conf
2. /etc/apache2/sites-enabled/mythweb.conf (this is linked file)
3. Using MythTV Backend Setup, I've checked the storage path and it is 
/home/mythtv/videos

I don't know where else to look. Again, how do I set mythweb to use the storage directory as defined within "MythTV Backend Setup"? Secondly, why does MythWeb's change the default path?

Is there a known problem with the new upgrade?


In summary, Mythweb is working in so far as the web browser sees the list of movies, but I can't play any of the movies b/c of the following error message: 

Not Found - The requested URL /mythweb/data/video/MyMovie.mpg was not found on this server.

Note that the path is wrong. It should be /mythweb/videos/MyMovie.mpg

---

### Post by nhtrader on 2011-06-05
More Info:

I just used the following commands in terminal mode:
sudo su <E>
cd / <E>
find . -name "myth*.*" -exec grep "/data" '{}' \; -print <E>

and found these responses:
CLEANUP="/usr/share/mythtv/mythweb/data"
./var/lib/dpkg/info/mythweb.prerm

datadir=/usr/share/mythtv/mythweb/data
./var/lib/dpkg/info/mythweb.postinst

What are the files cited above for? Do they affect mythweb's default path?


Here's another curiousity in the hunt for DIR "/data/video" ...

Why does the following path exist (/var/lib/mythtv/videos) which is empty?
This contrasts with /home/mythtv/videos which contains the movies.

I also found /usr/share/mythtv/mythweb/data/video which is linked to an empty DIR /var/lib/mythtv/videos  What is purpose of this link? 

This is another DIR that I found which points to the same empty DIR:
 /var/www/mythweb/data/video is a symbolic link to /var/lib/mythtv/videos


How are all of these files related?

---

