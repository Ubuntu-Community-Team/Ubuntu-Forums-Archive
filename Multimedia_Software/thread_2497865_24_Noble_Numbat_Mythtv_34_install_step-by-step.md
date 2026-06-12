---
title: "24 Noble Numbat Mythtv 34 install step-by-step"
date: 2024-05-21
forum: Multimedia Software
---

### Post by vidtek on 2024-05-21
**[SIZE=5][COLOR="#B22222"]mythtv 34 install to noble numbat[/COLOR][/SIZE]**
install:  ```
sudo apt-get install mythtv 
```  #add other add-ons later

open a web browser and goto: [http://localhost:6544/setupwizard]("http://localhost:6544/setupwizard")
This gives access to the websetup interface.

next page is the language setup

next page is backend ip's and security setup

next page is locale for tv frequencies

next page is misc settings  just go to next page

next pages are pretty much standard until add tuners
next page is capture cards, add your tuners

next page is recording profiles just go to next page

next page is add video sources

next page is connect tuners to video sources input connections
next page is scan for channels

next page is channel preferences, delete unwanted etc.
next page is adding your storage groups.

For storage groups ensure the user who starts mythtv (usually mythtv) has read and write permissions to that directory.
I usually create banners, coverart, fanart and screenshots in the mythtv user's home folder giving appropriate permissions.

next page is for programming stuff just save and exit restarting database

At this juncture just reboot.

When the machine has rebooted, add users to all of these groups **mythtv, video and audio groups**

eg: ```
sudo adduser root mythtv
```

If you have a combined backend/frontend machine as in an HTPC setup, I would recommend
changing the randomly generated password at install for one of youe own choosing.  I usually just make it mythtv.

To do so follow the following steps in a terminal copying and pasting each line one by one:
```
sudo mysql mythconverg
use mythconverg
CREATE USER 'mythtv'@'localhost' IDENTIFIED BY 'mythtv';
ALTER USER 'mythtv' IDENTIFIED BY 'mythtv';
GRANT ALL PRIVILEGES ON mythconverg.* TO 'mythtv'@'localhost';
ALTER USER 'mythtv'@'localhost' IDENTIFIED BY 'mythtv';

```

Then ctrl_d to exit mysql.

For those who wish to use acpi shutdown, these are the steps I take:
 in terminal type ```
sudo visudo
```

then paste the following:
```
%mythtv ALL=NOPASSWD: /usr/sbin/setwakeup.sh, /usr/sbin/checklogin.sh, /bin/systemctl, /usr/sbin/rtcwake, /sys/class/rtc/rtc0/wakealarm

```

then ctrl_o to write the entry, ctrl_x to exit the file.

This will allow the automatic shutdown to have correct permissions.

Then copy: checklogin.sh  and setwakeup to your /usr/sbin folder   Aquire the files from: [https://www.mythtv.org/wiki/ACPI_Wakeup]("https://www.mythtv.org/wiki/ACPI_Wakeup")

Then go to the web setup interface for mythtv: [http:/localhost:6544/setupwizard]("http:/localhost:6544/setupwizard")

and alter the enties on the shutdown/wakeup options page

idle shutdown time:                                             10secs
max wait for recording (secs):                                  60
startup before recording (secs):                                120
wakeup time format:                                             time_t
command to set wakeup time:                                     sudo /usr/sbin/setwakeup.sh
server halt command:                                            sudo /usr/sbin/poweroff
pre-shutdown-check-command:                                     sudo /usr/sbin/checklogin.sh

save and exit.

Don't forget if using this method when finished with the computer to always logoff do not shutdown.

---

### Post by mbliss2 on 2024-09-15
After upgrading to numbat, neither the Mythtv frontend, mythfilldatabase, nor [ttp:/localhost:6544/setupwizard]("http:/localhost:6544/setupwizard") is able to connect to the master backend. During the upgrade, their was a failure involving Mythtv, but I missed what it was, and the upgrade process then just quit. Any ideas where to go?

---

### Post by vidtek on 2024-09-16
> **mbliss2 said:**
> After upgrading to numbat, neither the Mythtv frontend, mythfilldatabase, nor [ttp:/localhost:6544/setupwizard]("http:/localhost:6544/setupwizard") is able to connect to the master backend. During the upgrade, their was a failure involving Mythtv, but I missed what it was, and the upgrade process then just quit. Any ideas where to go?

I would hope before starting the upgrade, you would have taken a full backup?   I use qt-fsarchiver, it is excellent.

I didn't do an upgrade, my several upgrade attempts failed too with many errors.    So I re-formatted and installed Noble Numbat from scratch (after a backup).   I did have issues with a combined audio sink not being created, and when I finally worked that issue out, migrated to Noble Numbat as my daily system.   The issue there was the Pipeline replacement of Pulseaudio and that took several weeks of painstaking fault-finding.   I needed a combined audio sync for my btooth headphones as I have imperfect hearing and the lovely Jane complains the sound is too high for her.   Everything else works fine, except I had to ditch VMware as my virtual package and install Virtualbox as VMware has been taken over by Broadcom and they make it just too hard.   That was nothing to do with Ubuntu's and Noble Numbat.

So my advice would be do a fresh install, the upgrade defeated me (and I tried 3 times after failures and re-installing the backups each time).

Best of luck Tony

---

### Post by mbliss2 on 2024-09-16
Thanks, and no I didn't do a backup, this machine is only used for MythTV and streaming. I'm not concerned about losing recordings, I just didn't want to have to start over. Looks like that may be my only option. Sigh ...

---

