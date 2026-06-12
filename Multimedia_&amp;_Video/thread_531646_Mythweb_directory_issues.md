---
title: "Mythweb directory issues"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by jjohns63 on 2007-08-21
I am having issues using Mythweb, I had it working before but uninstalled it and now the mythweb directory no longer appears. 

When I list /var/www I can see two directories, one is apache2-default which as far as i can tell is just a test folder, the other is a symbolic link named mythweb, which points to /usr/share/mythtv/mythweb:

[IMG]https://netfiles.uiuc.edu/jjohns63/pics/mythweb.jpg[/IMG]

However, when I point my browser at [http://localhost/](http://localhost/) the only directory listed is apache2-default:

[IMG]https://netfiles.uiuc.edu/jjohns63/pics/mythweb2.jpg[/IMG]

And I get a 500 Internal Error when trying to access [http://localhost/mythweb](http://localhost/mythweb)

Does anybody have any ideas? I'm pretty new to linux so you'll have to walk me through it if its complicated, I've tried uninstalling and reinstalling multiple times using sudo apt-get install/autoremove mythweb.

---

### Post by jjohns63 on 2007-08-23
I figured it out, turns out I had to use ```
apt-get autoremove --purge mythweb
``` to get the installation to completely remove

---

