---
title: "Myth frontend will not automatically start"
date: 2010-08-14
forum: Mythbuntu
---

### Post by androne on 2010-08-14
Hi

Since an upgrade to 10.04 ive had a number of issues with upstart [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554172](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554172) low graphics mode etc..

Ive gotten most things working fine including commenting out /dev/console in number of files as described in bug above.

The only thing left is getting mythfrontend to automatically start.  I have mythwelcome configured and it works to power on to record and power off when complete.  I just have to manually start mythfrontend each time I want to watch some content.
It has been set in MCC to autostart.  my .config/autostart/mythtv.desktop  is

```


[Desktop Entry]
Name=MythTV Frontend
Comment=A frontend for all content on a mythtv-backend
GenericName=MythTV Viewer
Exec=mythfrontend --service
Type=Application
Encoding=UTF-8
Icon=/usr/share/mythtv/themes/MythCenter-wide/ui/mythtv_logo.png
Categories=GNOME;Application;AudioVideo;Audio;Video
X-AppInstall-Package=mythtv


```I can start mythfrontend fine from command line or from menu.  Another thing i have noticed is i no longer have any content in /var/log/mythfrontend/log

I tried to delete this to see if myth would recreat it but no joy.

Im also using JYA's repo's 

Does anyone have any suggestions?

Thanks

---

### Post by androne on 2010-08-15
ok so from .config/autostart/mythtv.desktop

Exec=mythfrontend --service  - does not start the fronted automatically
Exec=mythfrontend                - starts the frontend automatically
Exec=/usrbin/mythwelcome    - starts mythwelcome automatically 

starting mythwelcome is the prefered option however, I still dont have any mythfrontend logs 

Ive tried from .config/autostart/mythtv.desktop using :

Exec=mythfrontend -l /var/log/mythtv/mythfrontend.log
but again mythfrontend doesnt automatically start.  It works fine from the cli and even writes to the mythfrontend.log

so as mythfrontend was originally being called with --service I edited /etc/mythtv/session-settings and commented out MYTHFRONTEND_OPTS="--verbose all,nodatabase"

still mythfrontend fails to automatically start and no frontend log file.

so under from .config/autostart/mythtv.desktop it works fine with Exec=/usr/bin/mythwelcome but would be nice to have some frontend logs.  

Therefore in the mythwelcome setup screen under "command to start frontend" instead of just /usr/bin/mythfrontend, ive added /usr/bin/mythfrontend -l /var/log/mythtv/mythfrontend.log

I dont think this is the standard way of doing it but it works

---

