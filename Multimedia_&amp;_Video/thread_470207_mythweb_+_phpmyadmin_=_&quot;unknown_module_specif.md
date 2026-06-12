---
title: "mythweb + phpmyadmin = &quot;unknown module specified&quot;"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by tha_toadman on 2007-06-10
I'm running 7.04 alternate with MythTV installed...I also installed 'phpmyadmin' as well. It's seems as if when I went to install 'mythweb', it broke my 'phpmyadmin'. Now when I visit my phpmyadmin page, all it says in "An unknown module was specified". I looked at apache's log and it said something about "favicon.ico" wasn't found but other than that, it was still running fine (and other pages displayed).

After typing that last paragraph, I ran apt-get remove mythweb, restarted apache2, and there was phpmyadmin again..!? It seems like this must be a bug or need some form of documentation? I guess I'll wait for further assistance if someone else has either experienced this or could shed some light on it. Thanks!

---

### Post by tha_toadman on 2007-06-15
seeing that no one replied to this one...i'll update you all as to what i did to solve it.

once i had apache2 and phpmyadmin installed, was editing the 'DocumentRoot' in the "default" apache2 file. for some reason, this would break phpmyadmin when i called for **/var/www/mythweb** as the 'DocumentRoot'. I was misusing (so i think) the DocumentRoot, and instead, saw the 'redirect' section a few lines below. i uncommented this line out, called for **/mythweb** and there ya go! phpmyadmin and mythweb were working!

---

