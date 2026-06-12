---
title: "Update broke mythfrontend 0.27"
date: 2015-08-10
forum: Mythbuntu
---

### Post by hugh4 on 2015-08-10
Hi,
I had some spare time today and decided to update mythbuntu/mythtv via the apt-get update and apt get-upgrade commands.
Now mythfrontend won't start, just get continuous loop stating code 130.... 
Have googled and found myth music may be problem so removed all add ons like mythmusic mythweb etc..
Also found problem with upgrade with "following packages have been kept back" mythfrontend being one of them. 
Running command apt-cache policy mythtv I get:

mythtv: installed 2.0.27+fixes.....
candidate: 2.0.27+fixes.....(as above)
version table : *** 2.0.27.5+fixes....(as above) 0
500 [http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/) trusty/main amd64 Packages
100 /var/lib/dpkg/status 2.0.27.0+fixes........

Backed up database and restored but did not fix.
Am thinking of executing mythfrontend --reset to see if that helps.
Have checked files ~/.mythtv/config.xml and /etc/config.xml and both have same settings.

It has been some time since I have done the command line stuff...
Any help in getting my system working again would be very much appreciated.
Cheers,
Hugh

---

### Post by hugh4 on 2015-08-11
Solved.
I ran this to fix
sudo apt-get -u dist-upgrade

All good.

---

