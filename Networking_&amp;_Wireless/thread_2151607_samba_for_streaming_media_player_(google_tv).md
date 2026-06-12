---
title: "samba for streaming media player (google tv)"
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by 5mattyb5 on 2013-06-05
Why are permissions no longer automatically applied when creating a share through nautilus?  BTW I'm using 13.04 and this was always done on all previous versions I've used.  I have a shared folder on my computer full of movies to be seen from my Google TV device and this has always worked in the past.  I should add that although i can see the share on my google tv i cant access it.  I have no idea how to manually set these permissions and the files aren't even listed in /etc/samba/smb.conf, however i know they exist cause like i say they can be seen from google tv

---

### Post by 5mattyb5 on 2013-06-06
So im sure Im not the only one with this problem, so let me tell you how I got it all to work.  I turns out the only folders that were giving me trouble were on seperate drives, i learned this when i shared my /home/public folder and it all went seamless.  this got me investigating all the parent folders of the original folder I was trying to share.  The folder was located in /media/user/ , and /user did not have read permissions for guests.  after initiating "sudo chmod 755 /media/user"  all was well.

---

