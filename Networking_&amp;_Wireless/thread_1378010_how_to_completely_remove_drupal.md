---
title: "how to completely remove drupal?"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by gfunkera on 2010-01-10
i need to completely remove drupal and reinstall it, i would also like to completely remove phpmyadmin and reinstall it.. does anyone know how to do this?

---

### Post by dFlyer on 2010-01-10
If they were installed as a dep file just start symaptic, do a quick search for the programs, right click on them and select complete removal or just mark for reinstall. That should work for both programs. Another way is to use sudo dpkg --purge (insert program name). I believe synaptic would be easier.

Gary

---

### Post by tgalati4 on 2010-01-11
sudo apt-get reinstall phpmyadmin
sudo apt-get reinstall drupal5

If you downloaded drupal from drupal.org, you can just delete the appropriate drupal directory from (for example) /var/www/drupal.

If something is broken, sometimes you can just reconfigure:

sudo dpkg-reconfigure phpmyadmin
sudo dpkg-reconfigure drupal5

---

