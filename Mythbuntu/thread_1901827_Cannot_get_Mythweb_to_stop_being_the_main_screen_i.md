---
title: "Cannot get Mythweb to stop being the main screen in apache2"
date: 2011-12-29
forum: Mythbuntu
---

### Post by wpflum on 2011-12-29
I've tried the "dpkg-reconfigure mythweb" and answered no to the question "Will you be using this webserver exclusively with mythweb?" and restarted the server with "sudo service apache2 restart" but I still get the Mythweb screen when I use "localhost" in Firefox, in fact it adds on the /mythweb/ part all by itself.  in the /var/www all I have is the symlink "mythweb -> /usr/share/mythtv/mythweb/"  and nothing about an index.html or symlink to such.  I tried adding a symlink to the default in /usr/share/apache2/default-site/  but unless I specifically indicate it like localhost/default I still get the mythweb page.

What I want to do is put in a main page that will allow me to select mythweb or calibre or whatever else I'd like so I'll only need to remember one web site and not localhost/calibre and localhost/webtv and so on.  

What am I missing to get the default index.html in apache2 to show??

Help

---

