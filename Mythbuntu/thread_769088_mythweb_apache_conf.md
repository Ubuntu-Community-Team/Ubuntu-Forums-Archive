---
title: "mythweb apache conf"
date: 2008-04-26
forum: Mythbuntu
---

### Post by Kissell on 2008-04-26
okay, i got mythweb working fine on my localhost, then i tried to upload it to my web host.  

but my web hosting site doesn't allow me to get to the /etc/apache2/conf.d folder...  so i can't upload the mythweb.conf file.

is there anyway i can get around this?  can't I somehow tell mythweb what to do in my own folder instead of having to do it in the apache folder?

---

### Post by laga on 2008-04-26
Are you aware that MythWeb wants a working mysql server and a backend?

I doubt it's going to work on your webhost.

---

### Post by Kissell on 2008-04-26
:(

My web host has mysql, so i created a database and imported all my video metadata.  

I really wanted to get this to work, as a slingbox type solution, I don't use the MythTV part, but I modified mythweb's php pages to make it do nothing except easily search my sql database and browse video files and then play them embedded in the web page result.

but I mostly modified the existing system, I don't know enough  yet to modify it further to work with my webhost when I can't use extra apache conf files.  certainly there must be a way, mythweb the way i want to use it simply needs to do read-lookup searches on my sql database, and my web host allows me to create sql databases, so the only reason i'd want to create a sql database would be to use it in conjunction with php pages i'd created...  i've done this before, but it's been so long ago.

---

