---
title: "How to uninstall or update Plexmediaserver"
date: 2013-09-06
forum: Multimedia Software
---

### Post by susja on 2013-09-06
Hello,
I'm running Ubuntu 12.04.3.
I'm runnning Plex Media Server Version 0.9.7.28
The problem happened when I try to update it. I've got this information:
Changes for the versions:
Installed version: 0.9.7.28.33-f80a4a2
Available version: 0.9.8.6.175-88ffbb2
Then when I try to update I've got the error:
**
W:Failed to fetch [http://shell.ninthgate.se/packages/debian/dists/squeeze/Release.gpg](http://shell.ninthgate.se/packages/debian/dists/squeeze/Release.gpg)  Could not connect to shell.ninthgate.se:80 (195.22.88.165). - connect (110: Connection timed out)
, W:Failed to fetch [http://www.plexapp.com/repo/dists/lucid/main/binary-i386/Packages](http://www.plexapp.com/repo/dists/lucid/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://shell.ninthgate.se/packages/debian/dists/squeeze/main/binary-i386/Packages](http://shell.ninthgate.se/packages/debian/dists/squeeze/main/binary-i386/Packages)  Unable to connect to shell.ninthgate.se:http:
, W:Failed to fetch [http://shell.ninthgate.se/packages/debian/dists/squeeze/main/i18n/Translation-en](http://shell.ninthgate.se/packages/debian/dists/squeeze/main/i18n/Translation-en)  Unable to connect to shell.ninthgate.se:http:
, E:Some index files failed to download. They have been ignored, or old ones used instead.
**

When I wanted to delete Plex I've got this error:
sudo apt-get remove plexmediaserver
......
Reading state information... Done
The following packages will be REMOVED:
  plexmediaserver
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 192593 files and directories currently installed.)
Removing plexmediaserver ...
Plex Media Server is not running (no process found)...
update-rc.d: /etc/init.d/plexmediaserver exists during rc.d purge (use -f to force)
dpkg: error processing plexmediaserver (--remove):
 subprocess installed pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 plexmediaserver
E: Sub-process /usr/bin/dpkg returned an error code (1)
*****
Well it looks I'm stuck with Plex: I can't update it and I can't remove it.
Could someone please advise?
Thanks

---

### Post by mikewhatever on 2013-09-07
> **susja said:**
> Hello,
I'm running Ubuntu 12.04.3.
I'm runnning Plex Media Server Version 0.9.7.28
The problem happened when I try to update it. I've got this information:
Changes for the versions:
Installed version: 0.9.7.28.33-f80a4a2
Available version: 0.9.8.6.175-88ffbb2
Then when I try to update I've got the error:
**
W:Failed to fetch [http://shell.ninthgate.se/packages/debian/dists/squeeze/Release.gpg](http://shell.ninthgate.se/packages/debian/dists/squeeze/Release.gpg)  Could not connect to shell.ninthgate.se:80 (195.22.88.165). - connect (110: Connection timed out)
, W:Failed to fetch [http://www.plexapp.com/repo/dists/lucid/main/binary-i386/Packages](http://www.plexapp.com/repo/dists/lucid/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://shell.ninthgate.se/packages/debian/dists/squeeze/main/binary-i386/Packages](http://shell.ninthgate.se/packages/debian/dists/squeeze/main/binary-i386/Packages)  Unable to connect to shell.ninthgate.se:http:
, W:Failed to fetch [http://shell.ninthgate.se/packages/debian/dists/squeeze/main/i18n/Translation-en](http://shell.ninthgate.se/packages/debian/dists/squeeze/main/i18n/Translation-en)  Unable to connect to shell.ninthgate.se:http:
, E:Some index files failed to download. They have been ignored, or old ones used instead.
**
These lines are unrelated to Ubuntu 12.04, in fact, they are for 10.04 and Debian Sqeeze. How did they even get there? Edit /etc/apt/sources.list and remove them.

> 
When I wanted to delete Plex I've got this error:
sudo apt-get remove plexmediaserver
......
Reading state information... Done
The following packages will be REMOVED:
  plexmediaserver
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 192593 files and directories currently installed.)
Removing plexmediaserver ...
Plex Media Server is not running (no process found)...
update-rc.d: /etc/init.d/plexmediaserver exists during rc.d purge (use -f to force)
dpkg: error processing plexmediaserver (--remove):
 subprocess installed pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 plexmediaserver
E: Sub-process /usr/bin/dpkg returned an error code (1)
*****
Well it looks I'm stuck with Plex: I can't update it and I can't remove it.
Could someone please advise?
Thanks

Not sure what's up with that, but try what it suggests:
```
sudo update-rc.d -f plexmediaserver remove
```

---

### Post by susja on 2013-09-07
- [**[COLOR=#000000]mikewhatever[/COLOR]**]("http://ubuntuforums.org/member.php?u=160645")
thanks for suggestion but it didn't work for me.
I ran sudo update-rc.d -f plexmediaserver remove and it removed system startup links for /etc/init.d/plexmediaserver ...
I checked that /etc/apt/sources.list has only one line : deb [http://www.plexapp.com/repo](http://www.plexapp.com/repo) lucid main and I commented it out. I didn't find anything else related to the error in that file.
Unfortunately it didn't make any difference and I still have exact same error as before.

---

### Post by mikewhatever on 2013-09-08
Hm..., interesting. I am not familiar with Plex, to be honest, but looking at the contents of the installation .deb, you might also check the "/etc/apt/sources.list.d/plexmediaserver.list" file.
As for removing it, perhaps everything has been removed exept the startup links.

---

### Post by susja on 2013-09-08
Thanks for suggestion.
You were right and I found in /etc/apt/sources.list.d/plexmediaserver.list" file line deb [http://shell.ninthgate.se/packages/debian](http://shell.ninthgate.se/packages/debian) squeeze main
I commented it out and now when I try to run Update Manager it states that nothing to update.
Well ... I suggest that I'm kind of OK now because I still have Plex Media Server installed and I'm using it but it won't be updated in the future.
I think it might be acceptable.
Thanks again.

---

### Post by mikewhatever on 2013-09-08
You could try downloading a .deb from their web site and installing it. For example:
```

sudo -i plexmediaserver_0.9.8.6.175-88ffbb2_i386.deb

```
The output might be informative.

---

