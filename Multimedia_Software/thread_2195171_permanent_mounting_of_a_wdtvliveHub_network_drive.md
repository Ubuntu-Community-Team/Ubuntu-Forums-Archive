---
title: "permanent mounting of a wdtvliveHub network drive"
date: 2013-12-22
forum: Multimedia Software
---

### Post by hornbutu on 2013-12-22
I am trying to permanently mount my wdtvliveHub so it connects automatically when I reboot. I have created a mount point "/home/will/wdtvlive"
and use "sudo
smbmount //192.168.0.18/WDTVLiveHub ~/wdtvlive -o guest,rw" everytime I reboot in order read and write to/from my WDTV box. 


As far as I have read, there are multiple ways of making this happen:


1. write "sudo smbmount //192.168.0.18/WDTVLiveHub ~/wdtvlive -o guest,rw" into a script (wdautostart.sh) and either;
     a) edit crontab to add the line "@reboot /home/will/Documents/scripts/wdautostart.sh"
     b) put that script in  /etc/init.d/rc.local, and it will execute upon boot.


2. Edit fstab to mount a network drive to a folder


Please help! Not a total noob but this is my first time attempting something like this so a breakdown step by step would be appreciated!




references: 
1.a) [http://stackoverflow.com/questions/6016713/how-to-run-command-at-startup-in-linux](http://stackoverflow.com/questions/6016713/how-to-run-command-at-startup-in-linux)
1.b)[http://ubuntuforums.org/showthread.php?t=1617799](http://ubuntuforums.org/showthread.php?t=1617799)
2. [http://ubuntuforums.org/showthread.php?t=1878244](http://ubuntuforums.org/showthread.php?t=1878244)

---

