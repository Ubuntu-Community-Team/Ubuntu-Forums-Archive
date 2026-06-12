---
title: "Mythbuntu 8.04 install fails at 83%"
date: 2008-04-26
forum: Mythbuntu
---

### Post by Grodesh on 2008-04-26
I'm trying to install Mythbuntu 8.04 on my computer but it somehow fails to complete the installation. Regardless of the way I start the installation (from the Live CD or directly from the option "Install Mythbuntu" in the boot menu), when it reaches 83% - "Configuring MythTV", the window disappear without any error message.

I already know about a similar problem caused by spaces or certain special characters in the mysql password: [http://ubuntuforums.org/showthread.php?t=671186](http://ubuntuforums.org/showthread.php?t=671186) but my mysql password doesn't have any weird character; it only consists of numbers, lowercase and upercase letters.

Any ideas about what could be the culprit? I had to leave home before doing more testing and looking for log files, but any help would be appreciated so that once I'm back home I'll be prepared to either give you more information about my bug or simply fix my problem! What log file should I look into?

---

### Post by tgm4883 on 2008-04-26
Is this a standard install or advanced install?  FE, BE, FE/BE?  What options did you pick during install?

---

### Post by Grodesh on 2008-04-26
> **tgm4883 said:**
> Is this a standard install or advanced install?  FE, BE, FE/BE?  What options did you pick during install?


It's an advanced installation for a Primary Backend with Frontend with the following options (I suppose most will be irrelevant but I'll just throw them all in case):

Plugins:
[INDENT]Myth Web
Myth Archive
Myth Controls
Myth Game
Myth Video[/INDENT]

Themes:
[INDENT]Since I don't have a widescreen TV, I deselected all the wide themes[/INDENT]

Additional Services:
[INDENT]VNC
SSH
Samba
NFS[/INDENT]

MythTV Related Passwords:
[INDENT]I set up a password for both Mythweb and MySQL. As said before, the MySQL password consist of only number and letters (lower and uppercase) for a length of 12 characters.[/INDENT]

Remote control:
[INDENT]Windows Media Center USB (Philips)[/INDENT]

Transmiter:
[INDENT]Windows Media Center for Scientific Atlanta[/INDENT]

Frontend drivers:
[INDENT]Nvidia drivers for Geforce4 MX 440, with composite out enabled (NTSC-M)[/INDENT]

Backend drivers:
[INDENT]XMLTV Guide Data[/INDENT]

---

### Post by Grodesh on 2008-04-27
I've got the debug file from the installer and I attached it to this post. There seems to be a problem with my locale (fr_CA) as there are a lot of warnings about it.

Also, the installer tries to write files in the /root/ directory but it lacks the permissions.

I'll try to setup an en_US installation to see if it makes any difference.

---

### Post by grannyw on 2008-04-27
when you install from the live cd during the installation unplug the internet cable!!!:KS

---

### Post by Grodesh on 2008-04-27
Neither using en_US or unpluging the network cable changed anything... I'm running out of ideas...

---

### Post by superm1 on 2008-04-27
Hi Grodesh,

Can you please post an entire /var/log/syslog after it fails?  This log contains a more informative traceback where things are failing.

---

### Post by Grodesh on 2008-04-27
Here's my syslog. Thanks for looking at it.

I scanned it rapidly and saw new information: For my /home, I'm mounting a partition I was using on my old installation, Since I'm using the same account name (and there already is a home dir for a user called mythtv from my old installation). I suppose there might be a problem with either the uid or the gid which may cause some permission problems. I'll experiment once more by renaming the old home directory names and check what happens when the home directory are recreated from scratch.

---

### Post by Grodesh on 2008-04-27
That was it. Now that the directories didn't exist on the /home partition, the installation has passed the 83% mark and is about to finish.

THanks a lot superm1, you indirectly showed me the path to a successful installation! :)

---

