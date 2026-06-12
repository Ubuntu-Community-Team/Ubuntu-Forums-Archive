---
title: "netatalk stopped working, can't update to latest version"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by rubicks on 2011-07-30
so i followed this guide to get netatalk and it was working fine until a few days ago, we've had some storms and lost power a few times and i think that might have messed it up.  I didn't install avahi, but in my attempts to fix it i tried installing avahi and it didn't help at all.

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

from what i've seen, a lot of people have used this guide, but none of the of the fixes have worked for me.

i think the problem is in my afpd.conf file.  Right now, when i try to use the connect to server option in Mac (which is how i've always done it) it'll ask me for a username and password.  the password and username are correct, but it says its invalid.

This is the current line i have at the end:
- -transall -uamlist uams_randnum.so,uams_dhx.so -nosavepassword -advertise_ssh

When i try this,
- -transall -uamlist uams_randnum.so,uams_dhx2.so -nosavepassword -advertise_ssh
it won't ask for a username and password, but just endlessly tries to connect.

in my /etc/netatalk/AppleVolumes.default i have this:
/home/downloads downloads allow:myusername,downloads cnidscheme:cdb options:usedots,upriv

downloads is a second account i have setup.

Netatalk is version 2.0.5-3, and i'm running 10.04.3.

now the latest stable version according to netatalks website is 2.1.5, when i followed the guide it had me compile my own version and put a hold on the package.
```
echo "netatalk hold" | sudo dpkg --set-selections
```

i think i got the hold removed, but it won't update.  i tried uninstalling, but i think it is reusing the package i made, even after i deleted what i had in my folder. i saved a copy of the files, but i renamed the folder so i could remake it if i need to.

suggestions? i'm not that great with ubuntu/command line. but i'm great at following directions.

---

### Post by rubicks on 2011-07-30
i'm also getting this error sometimes:
There was an error connecting to the server.  Check the server name or IP address, and then try again.

---

### Post by rubicks on 2011-07-31
got 2.1.4-1 of netatalk running by adding the natty repos to apt and then removing it after i installed it.

i still can't connect to the ubuntu box using AFP though, i'm getting the invalid username/password no matter what changes i make to the conf files.

---

