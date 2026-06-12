---
title: "problem connecting to ftp in nautilus"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by mohawk.drummer on 2009-01-12
i recently purchased a D-link DNS-321 NAS (similar to DNS-323). I have it all set up and running. For some reason when i try to connect using nautilus ( Places > Connect to Server...) Ubuntu is unable to connect. I get a "The folder contents could not be displayed: Sorry, couldn't display all the contents of "/ on 74.12.153.xxx": Could not connect to host" (blocked out last three digits for security reasons:)). I've managed to connect via the network and i have also been able to access the ftp on other windows machines. Also i can access the ftp through firefox, fireftp (firefox plugin) and kind of lftp (although it never really makes a connection). I've been searching around and have found this [http://bugzilla.gnome.org/show_bug.cgi?id=556786](http://bugzilla.gnome.org/show_bug.cgi?id=556786) but am not sure whether this is the solution (can't find the files the patches are for). I know in order to connect with fireftp i have to have it set to passive mode so i'm not quite sure. If anyone could help me out as i would really like to have my ftp mounted like another drive in my Ubuntu (instead of having to go through a program) thanks

---

### Post by mohawk.drummer on 2009-01-14
bump. Anyone have any ideas? Or even if someone could tell me how to get a debug output from gvfsd-ftp as i try to connect...

---

### Post by HuaiDan on 2009-01-31
I'd like to know too. Same problem. I can connect internally no problem, and I can ftp using firefox no problem, but if I try to go external using nautilus, I get the same error message as the OP.


Nobody?


Edit:ports 20 and 21 are forwarded....

---

### Post by HuaiDan on 2009-02-03
I think it had something to do with trying to reach my FTP through the outside using Nautilus from the inside. This may be a Nautilus bug, not sure unless this error is consistent among other users.

I was able to use Filezilla quite nicely, an FTP client that rocks, from the inside and outside.


Mods, consider this a bug report or a fix.

---

