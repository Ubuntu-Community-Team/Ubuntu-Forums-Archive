---
title: "connection refused for mythtv@127.0.0.1 after 0.27+fixes upgrade"
date: 2014-05-04
forum: Mythbuntu
---

### Post by dannyboy79 on 2014-05-04
i was running mythbuntu 12.04.4 which had 0.26+fixes on it and I wanted to upgrade the server to 14.04 as well as MythTV to 0.27+fixes as well as change all the hardware (CPU, ram, psu, motherboard, and hard drives). I had the other machine already running with xubuntu 14.04 on it, i just needed to install my 2 2TB SATA drives in it and turn it into a mythtv server. It was a tall order that's for sure. 
I first ensured I had a good backup of my mythconverg database in case I needed to return to 12.04.4 and 0.26+fixes
I then backed up all content that was on any IDE drive onto a new SATA drive using rsync -a -v --progress
Then I swapped all the hardware that was going from the old server to the new one like the capture cards and 1 hard drive
then I tried using mythbuntu-control-center to convert the machine from a frontend only to a master backend and I am not sure it worked because I was getting an error.
i then used the restore database option within mythbuntu-control-center which again didn't seem to work so I ended up just using mythconverg_restore.pl directly. 
at some point I had to apt-get install mythtv-backend-master which is did install that. 
i had to ensure my /etc/mysql/my.cnf file bind-address was set to my external IP (ie: 192.168.0.5, the servers IP)
i had installed phpmyadmin and used it to add user 'mythtv' for localhost, 127.0.0.1, dell (the hostname of the server), 192.168.0.5 and my frontend IP's also.
i had to ensure that all the various locations that config.xml was located all had the same info in it.
and I was still getting connection refused and I couldn't figure out why, i could run mythtv-setup but when it would try to run mythfilldatabase it said connection refused for 127.0.0.1 and I could't figure it out. 
I now realized that for some reason I have to upstart script to start the backend so everytime i want to start it I need to run mythtv-setup which then starts it after I exit the setup.
still error'ing out, so then I just tried calling it directly with /usr/bin/mythbackend and it was showing me that a frontend (specifically my original apple tv running crystalbuntu) was trying to access the backend repeatedly so I went and unplugged the apple tv and all then I double checked all my settings, all my mysql permissions, etc etc and finally the backend started up.
I had to reinstall mythweb for it to work but I finally did it after trying for 11+ hours to get it working. It must have been the appletv cmyth plugin that kept mysql tied up or something. I don't know, I am just glad its finally all backup running perfectly

So, does anyone know why I don't have a mythbackend service script that I can run to stop and start the server?

---

