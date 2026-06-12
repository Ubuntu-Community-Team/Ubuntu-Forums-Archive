---
title: "Update Manager &quot;Hits&quot; Files"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by thomas144 on 2010-08-01
When I check for updates in Update Manager, instead of downloading the files, it goes through the files very quickly and says "Hit" for every file. If I try to update this information manually by running sudo apt-get update, I get this:
```

thomas@THOMAS-PC:~$ !!
sudo apt-get update
Get:1 http://www.club.cc.cmu.edu lucid Release.gpg [189B]
Ign http://www.club.cc.cmu.edu/pub/ubuntu/ lucid/main Translation-en_US
Ign http://www.club.cc.cmu.edu/pub/ubuntu/ lucid/restricted Translation-en_US
Ign http://www.club.cc.cmu.edu/pub/ubuntu/ lucid/universe Translation-en_US
Ign http://www.club.cc.cmu.edu/pub/ubuntu/ lucid/multiverse Translation-en_US
Get:2 http://www.club.cc.cmu.edu lucid-updates Release.gpg [189B]
Ign http://www.club.cc.cmu.edu/pub/ubuntu/ lucid-updates/main Translation-en_US
Ign http://www.club.cc.cmu.edu/pub/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://www.club.cc.cmu.edu/pub/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://www.club.cc.cmu.edu/pub/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:3 http://www.club.cc.cmu.edu lucid-security Release.gpg [189B]
Ign http://www.club.cc.cmu.edu/pub/ubuntu/ lucid-security/main Translation-en_US
Ign http://www.club.cc.cmu.edu/pub/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://www.club.cc.cmu.edu/pub/ubuntu/ lucid-security/universe Translation-en_US
Ign http://www.club.cc.cmu.edu/pub/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://www.club.cc.cmu.edu lucid Release
Hit http://www.club.cc.cmu.edu lucid-updates Release
Hit http://www.club.cc.cmu.edu lucid-security Release
Hit http://www.club.cc.cmu.edu lucid/main Sources
Hit http://www.club.cc.cmu.edu lucid/restricted Sources
Hit http://www.club.cc.cmu.edu lucid/main Packages
Hit http://www.club.cc.cmu.edu lucid/restricted Packages
Hit http://www.club.cc.cmu.edu lucid/multiverse Sources
Hit http://www.club.cc.cmu.edu lucid/universe Sources
Hit http://www.club.cc.cmu.edu lucid/universe Packages
Hit http://www.club.cc.cmu.edu lucid/multiverse Packages
Hit http://www.club.cc.cmu.edu lucid-updates/main Packages
Hit http://www.club.cc.cmu.edu lucid-updates/restricted Packages
Hit http://www.club.cc.cmu.edu lucid-updates/restricted Sources
Hit http://www.club.cc.cmu.edu lucid-updates/main Sources
Hit http://www.club.cc.cmu.edu lucid-updates/multiverse Sources
Hit http://www.club.cc.cmu.edu lucid-updates/universe Sources
Hit http://www.club.cc.cmu.edu lucid-updates/universe Packages
Hit http://www.club.cc.cmu.edu lucid-updates/multiverse Packages
Hit http://www.club.cc.cmu.edu lucid-security/main Packages
Hit http://www.club.cc.cmu.edu lucid-security/restricted Packages
Hit http://www.club.cc.cmu.edu lucid-security/restricted Sources
Hit http://www.club.cc.cmu.edu lucid-security/main Sources
Hit http://www.club.cc.cmu.edu lucid-security/multiverse Sources
Hit http://www.club.cc.cmu.edu lucid-security/universe Sources
Hit http://www.club.cc.cmu.edu lucid-security/universe Packages
Hit http://www.club.cc.cmu.edu lucid-security/multiverse Packages
Fetched 567B in 4s (113B/s)
Reading package lists... Done

```
I know it's not downloading anything because my Internet connection isn't very fast, so if the files were downloaded, it would take a minute or two. I want Update manager and apt-get to actually download this  information. This problem just started yesterday, or maybe the day  before. Running sudo apt-get clean and sudo apt-get autoclean doesn't help. Neither does rebooting. Can anybody help me?

---

### Post by chili555 on 2010-08-01
I believe this is the expected behavior if there are no updates available. What happens when you run:```
sudo apt-get upgrade
```When there are no available updates, it should read:> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by thomas144 on 2010-08-02
Actually, when this problem occurred, there were already two packages to upgrade. I ran sudo apt-get upgrade and it seems that everything worked. Here's the output of the command:
```

thomas@THOMAS-PC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libdbusmenu-glib1 libdbusmenu-gtk1
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 44.2kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://www.club.cc.cmu.edu/pub/ubuntu/ lucid-updates/main libdbusmenu-glib1 0.2.9-0ubuntu3.1 [29.1kB]
Get:2 http://www.club.cc.cmu.edu/pub/ubuntu/ lucid-updates/main libdbusmenu-gtk1 0.2.9-0ubuntu3.1 [15.1kB]
Fetched 44.2kB in 1s (28.5kB/s)      
(Reading database ... 185342 files and directories currently installed.)
Preparing to replace libdbusmenu-glib1 0.2.9-0ubuntu3 (using .../libdbusmenu-glib1_0.2.9-0ubuntu3.1_amd64.deb) ...
Unpacking replacement libdbusmenu-glib1 ...
Preparing to replace libdbusmenu-gtk1 0.2.9-0ubuntu3 (using .../libdbusmenu-gtk1_0.2.9-0ubuntu3.1_amd64.deb) ...
Unpacking replacement libdbusmenu-gtk1 ...
Setting up libdbusmenu-glib1 (0.2.9-0ubuntu3.1) ...

Setting up libdbusmenu-gtk1 (0.2.9-0ubuntu3.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```
sudo apt-get update gives the same result of hitting files. If it discovers updates in the next few days, I never had a problem.

---

### Post by chili555 on 2010-08-02
This is from *man apt-get*:> update
           update is used to **resynchronize** the package index files from their sources. 

--- snip ---

       upgrade
           upgrade is used to **install** the newest versions of all packages currently installed on the system from the sources enumerated in /etc/apt/sources.list.

--- snip ---I have added emphasis. As I said, the behavior you experienced is normal.

---

### Post by Cavsfan on 2010-08-02
I totally agree!
You don't even need update manager except to see if there are any updates.
You just need these three commands:
**sudo apt-get update**         (what **chili555** said above)
**sudo apt-get upgrade**       (lists what will be upgraded, installed, removed, not upgraded like in **chili555**'s post)
**sudo apt-get dist-upgrade** (this will get any kernel if there is one to install)

But the upgrade command is especially useful as it tells you if something is going to be removed with nothing to replace it.
In this case, you want to just wait and come back later and check again.

And there will be days when there are no updates to be had.

---

