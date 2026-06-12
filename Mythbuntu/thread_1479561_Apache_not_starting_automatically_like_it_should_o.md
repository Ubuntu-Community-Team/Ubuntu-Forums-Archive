---
title: "Apache not starting automatically like it should on Lucid."
date: 2010-05-10
forum: Mythbuntu
---

### Post by bergqvistjl on 2010-05-10
So, for some reason (im using mythbuntu Lucid x64) apache doesnt start automatically like it should, so i cant access mythweb and the like. The command i used to start it was: sudo /etc/init.d/apache2 start
So, anyone else experienced this problem, and how can i get it to autostart, ive thought about adding it as a startup program, but i dont think it would because of the sudo. Any ideas?

---

### Post by cybertesla on 2010-05-28
Same problem here.  It used to work just fine for me.  However, at some point in the last couple weeks apache2 no longer automatically started at boot.  I tried directly restarting with:

/etc/init.d/apache2 restart

Then,

/etc/init.d/apache2 -k restart

It dies complaining about missing things that seems like they should be picked up from the config files.  Then I noticed that /etc/apache2/httpd.conf was empty.  That's as far as I've got so far.  I'll be back if I find out anything else.  Maybe someone that is much more familiar with this can be more helpful in the meantime.

---

