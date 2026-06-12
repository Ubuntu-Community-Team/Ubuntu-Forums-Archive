---
title: "Weekly upgrade fails for mythtv-database"
date: 2009-06-08
forum: Mythbuntu
---

### Post by bcg30506 on 2009-06-08
I just ran an sudo apt-get dist-upgrade to get the latest builds for mythbuntu 9.04 to include the new nvidia 185 drivers.  All went well except for this during the installs:

Setting up mythtv-database (1:0.21.0+fixes-20674-openglvdpau-0ubuntu0) ...
Failed to connect to database (incorrect admin password)
Failed to create or modify database (incorrect admin username/password?)
Try:
sudo dpkg-reconfigure mythtv-database

I've changed nothing since the last update and can access my database just fine.  Why was it trying to reconfigure this package?  Did the DB structure change in this release?

---

### Post by ian dobson on 2009-06-08
Hi,

I've been seeing this for sometime but the backend seems to run without any problems.

I think when the backend needs the database updated/changed the backend process updates the database structure by itself.

Regards
Ian Dobson

---

### Post by mpp on 2009-10-31
I've just upgraded from Jaunty to Karmic.  The mythtv database upgrade did not apply during the dist-upgrade process due to problems with my mysql configuration so I had to come back later and apply this.

When trying to run ```
sudo dpkg-reconfigure mythtv-database
``` I was seeing these errors about no permissions to the database: ```
Failed to create or modify database (incorrect admin username/password?)
```.

The solution was to start up mythtv-frontend.  When you start it up it prompts you to update some of the database tables - say yes and it will do this for you.  I assume it applies all the changes that the dpkg-reconfigure would/should have done!

have fun()
mike

---

