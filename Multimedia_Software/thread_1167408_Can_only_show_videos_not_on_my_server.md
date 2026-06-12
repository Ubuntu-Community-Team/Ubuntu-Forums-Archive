---
title: "Can only show videos not on my server"
date: 2009-05-22
forum: Multimedia Software
---

### Post by Lakeside5 on 2009-05-22
Trying to get to the bottom of my problem here, I'm not sure if it's a linux issue, or a joomla issue, server etc. All I know is, if I embed a video from another source like youtube (using AllVideos:  {youtube}file_embed_code{/youtube} it shows and plays:  sasswebs.com  the car video, but when I embed a file(s) from my own server (var/www/images/stories/videos  they do not show, they are supposed to be under the car video. I'm wondering if it is a linux issue. thanks for any ideas.

---

### Post by pytheas22 on 2009-05-22
It looks like the URL of the missing video is [http://sasswebs.tzo.net/images/stories/videos/one.swf](http://sasswebs.tzo.net/images/stories/videos/one.swf).  When I put that URL directly into my browser, I get a message from your server saying I don't have permission to view the file.  Check the permissions on the file; you probably need to change ownership or add read permission.

---

