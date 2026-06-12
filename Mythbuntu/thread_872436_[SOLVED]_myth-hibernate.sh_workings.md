---
title: "[SOLVED] myth-hibernate.sh workings"
date: 2008-07-28
forum: Mythbuntu
---

### Post by GuiGuy on 2008-07-28
Hi,
Regarding the myth-hibernate.sh script, it seems to work OK up to a point for me. It hibernates the PC (ASUS M3A mobo), and it comes back pretty smartly. 

However, in the frontend settings even when selecting only the "SHUTDOWN" option the exit menu option is "EXIT and SHUTDOWN". In other words, the Frontend will exit and then the PC goes to hibernate. 

When it comes back from hibernate the frontend is, of course, no longer running. 

Is there a way around this so that the frontend will be running when the PC comes back from hibernate?

Or have I missed something altogether about putting the PC to sleep when it isn't in use?

Cheers

---

### Post by laga on 2008-07-28
That must be an annoying problem :)

You can either bind the hibernate script to a button on your remote using irexec, or you can add a button to frontend menu ([http://www.mythtv.org/wiki/index.php/Menu_theme_development_guide#Helpful_Tips](http://www.mythtv.org/wiki/index.php/Menu_theme_development_guide#Helpful_Tips) - also read the rest of the article to find out how to prevent your menu file from getting overwritten).

---

### Post by GuiGuy on 2008-07-28
> **laga said:**
> That must be an annoying problem :)

You can either bind the hibernate script to a button on your remote using irexec, or you can add a button to frontend menu ([http://www.mythtv.org/wiki/index.php/Menu_theme_development_guide#Helpful_Tips](http://www.mythtv.org/wiki/index.php/Menu_theme_development_guide#Helpful_Tips) - also read the rest of the article to find out how to prevent your menu file from getting overwritten).

Thanks.

---

### Post by ian dobson on 2008-07-28
Hi,

I just use the attached script to restart the frontend app when it's not running:-

```

#! /bin/bash
# Provides:          check if the Myth-Frontend is still running
# Short-Description: if it dies restart it
# Author:            Ian Dobson (i.dobson {at} planet-ian.com
sleep 30
while [ "1" != "0" ]; do
   Active=`ps -A| grep "mythfrontend"`
   if [ "$Active" == "" ]; then
      killall -15 gdm
      echo  "mythfrontend  Dead" > /var/log/mythtv/frontend.log
      sleep 5
      /etc/init.d/gdm start
     sleep 15
   fi
   sleep 30
done

```

Just save as /usr/bin/watch-frontend.sh and create a rc script that calls  watch-frontend.sh .

Regards
Ian Dobson

---

