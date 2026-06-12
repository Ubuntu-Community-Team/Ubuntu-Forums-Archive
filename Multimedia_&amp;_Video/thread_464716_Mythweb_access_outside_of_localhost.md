---
title: "Mythweb access outside of localhost"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by dyoung418 on 2007-06-05
I have MythTV and MythWeb installed on my Feisty Fawn AMD64 setup.  I can sucessfully access mythweb from the local machine (localhost), but I haven't been able to figure out how to access mythweb from other machines on my local network.
My Feisty Fawn box has a fixed IP address and apache works fine from machines in my local lan (I can see the "It works!" page from other machines), but when I try to look at mythweb, I get nothing.
So far, I've tried adding an entry in /etc/apache2/httpd.conf to "AllowOverride", but I'm not sure how to modify the .htaccess file in /var/www/mythweb.  At one point I modified the .htaccess host entry to read as my fixed IP address instead of localhost, but then I got an access error from both outside and inside localhost when trying to access mythweb.
Can anyone give me pointers?
Thanks,

---

