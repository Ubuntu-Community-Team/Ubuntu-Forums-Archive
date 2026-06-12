---
title: "[SOLVED] phpmyadmin install problem"
date: 2008-08-06
forum: Mythbuntu
---

### Post by newlinux on 2008-08-06
I just installed phpmyadmin, and I think that should be all I need to do to access it. However, when i try to go to:

[http://hostname/phpmyadmin/](http://hostname/phpmyadmin/)

I get:

The requested URL /phpmyadmin/ was not found on this server. I'm pretty sure in the past all I had to do was install it. I can access mythweb just fine on the same machine. any ideas?

---

### Post by newlinux on 2008-08-06
Never mind... 

sudo dpkg-reconfigure phpmyadmin

must have forgot to select apache2 when I installed it.

---

