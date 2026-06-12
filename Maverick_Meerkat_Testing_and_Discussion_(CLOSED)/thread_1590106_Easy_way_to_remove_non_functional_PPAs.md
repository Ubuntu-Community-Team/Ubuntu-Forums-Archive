---
title: "Easy way to remove non functional PPAs"
date: 2010-10-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by xircon on 2010-10-07
Just upgraded, re-ticked all my PPAs most work but some are reporting:
```
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
```

Is there a quick way to isolate?

---

### Post by viralmeme on 2010-10-07
> **xircon said:**
> Is there a quick way to isolate?

Use the [RepositoriesCommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine") ..

---

### Post by xircon on 2010-10-07
> **viralmeme said:**
> Use the [RepositoriesCommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine") ..

There is nothing there about isolating PPAs that do not work (or am  I going blind?)

---

### Post by philinux on 2010-10-07
> **xircon said:**
> There is nothing there about isolating PPAs that do not work (or am  I going blind?)

Just untick them in software sources or use ppa-purge.

---

### Post by xircon on 2010-10-07
But how do I know which ones to untick?  Some are working some are not, the error message is so no specific!!

---

### Post by theanswriz42 on 2010-10-07
> **xircon said:**
> But how do I know which ones to untick?  Some are working some are not, the error message is so no specific!!

Post the full output of 'apt-get update' here and maybe we can help you out.

---

### Post by viralmeme on 2010-10-07
> **xircon said:**
> There is nothing there about isolating PPAs that do not work (or am  I going blind?)

"Apt stores a list of repositories or software channels in the file /etc/apt/sources.list", so if you remove all references to [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main, then the error msg will disappear.

---

### Post by xircon on 2010-10-07
```
Ign http://skulltag.net jaunty Release.gpg
Ign http://skulltag.net/download/files/release/deb/ jaunty/multiverse Translation-en
Ign http://skulltag.net/download/files/release/deb/ jaunty/multiverse Translation-en_GB
Ign http://skulltag.net jaunty Release
Get:1 http://dl.google.com stable Release.gpg [191B]
Ign http://skulltag.net jaunty/multiverse amd64 Packages/DiffIndex
Ign http://linux.dropbox.com maverick Release.gpg
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_GB
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_GB
Get:2 http://dl.google.com stable Release.gpg [189B]
Ign http://download.skype.com stable Release.gpg
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_GB
Hit http://apt.spideroak.com release Release.gpg
Ign http://apt.spideroak.com/ubuntu-spideroak-hardy/ release/restricted Translation-en
Ign http://apt.spideroak.com/ubuntu-spideroak-hardy/ release/restricted Translation-en_GB
Ign http://download.skype.com/linux/repos/debian/ stable/non-free Translation-en
Hit http://archive.ubuntu.com maverick Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://download.skype.com/linux/repos/debian/ stable/non-free Translation-en_GB
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Hit http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Hit http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Hit http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://skulltag.net jaunty/multiverse amd64 Packages
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/awn-testing/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/awn-testing/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://download.skype.com stable Release
Ign http://linux.dropbox.com maverick Release
Get:3 http://dl.google.com stable Release [1,311B]
Ign http://apt.boxee.tv maverick Release.gpg
Hit http://apt.spideroak.com release Release
Hit http://extras.ubuntu.com maverick Release
Ign http://apt.boxee.tv/ maverick/main Translation-en
Hit http://archive.ubuntu.com maverick Release
Ign http://skulltag.net jaunty/multiverse amd64 Packages
Ign http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/ maverick/main Translation-en_GB
Ign http://download.skype.com stable/non-free amd64 Packages
Get:4 http://dl.google.com stable Release [1,338B]
Hit http://ppa.launchpad.net maverick Release.gpg
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Hit http://skulltag.net jaunty/multiverse amd64 Packages
Ign http://apt.boxee.tv/ maverick/main Translation-en_GB
Hit http://archive.ubuntu.com maverick/main amd64 Packages
Ign http://apt.spideroak.com release/restricted amd64 Packages
Ign http://linux.dropbox.com maverick/main amd64 Packages
Ign http://apt.boxee.tv maverick Release
Ign http://ppa.launchpad.net/baudm/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/baudm/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/bisigi/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/bisigi/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ maverick/main Translation-en
Ign http://download.skype.com stable/non-free amd64 Packages
Get:5 http://dl.google.com stable/main amd64 Packages [1,001B]
Hit http://archive.ubuntu.com maverick/universe amd64 Packages
Hit http://archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://archive.ubuntu.com maverick/multiverse amd64 Packages
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://apt.spideroak.com release/restricted amd64 Packages
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/compiz/ppa/ubuntu/ maverick/main Translation-en
Ign http://linux.dropbox.com maverick/main amd64 Packages
Err http://download.skype.com stable/non-free amd64 Packages
  404  Not Found [IP: 130.117.72.44 80]
Get:6 http://dl.google.com stable/main amd64 Packages [630B]
Ign http://apt.boxee.tv maverick/main amd64 Packages
Ign http://ppa.launchpad.net/compiz/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://apt.boxee.tv maverick/main amd64 Packages
Err http://linux.dropbox.com maverick/main amd64 Packages
  404  Not Found
Hit http://apt.spideroak.com release/restricted amd64 Packages
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/echidnaman/qapt/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/echidnaman/qapt/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/ maverick/main Translation-en_GB
Err http://apt.boxee.tv maverick/main amd64 Packages
  403  Forbidden
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/geany-dev/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/geany-dev/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/hel-sheep/pastie/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/hel-sheep/pastie/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/kwwii/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/kwwii/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/laurent-parenteau/full-circle-notifier/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/laurent-parenteau/full-circle-notifier/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/loneowais/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/loneowais/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/norsetto/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/norsetto/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/openismus-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/openismus-team/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/psyke83/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/psyke83/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/ricotz/testing/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ricotz/testing/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/silverwave/one-daily-a-month-1/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/silverwave/one-daily-a-month-1/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/webupd8team/rhythmbox/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/webupd8team/rhythmbox/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/webupd8team/unstable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/webupd8team/unstable/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Fetched 4,660B in 9s (517B/s)
```

---

### Post by terry_gardener on 2010-10-07
properly the long winded way but will tell you which are broken and which aren't. 

open the software center and then load the software sources and in the other software tab untick all of them.

then run apt-get update, if you get no errors retick them one by one. and you soon learn what is broken or not.

---

### Post by xircon on 2010-10-07
Cheers Terry, that was my conclusion as well.  Will have a go when bored as it is only an annoyance.

---

### Post by jfernyhough on 2010-10-07
That looks more to me like you have a malformed line in your sources.list or one of the sources.list.d/ files. All of the other PPAs you have are of the form [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/), there are three references to just [http://ppa.launchpad.net/](http://ppa.launchpad.net/) - and this is not a PPA address.

I'd double-check each of the source lines, even just by copying&pasting into a browser and seeing if they load.

---

### Post by Framli on 2010-10-07
This may only work for launchpad ppas, I use it to check if there is already a Maverick version of a ppa.
```
for i in $(cat /etc/apt/sources.list.d/* | grep -o http.* | sed s/\ .*//) ; do echo $i && curl -silent -I $i/dists/maverick | grep -o 404; done;
```

---

### Post by xircon on 2010-10-07
Framli

That is pure genius!!  Will pipe to a file and play with it tomorrow!

---

### Post by nilarimogard on 2010-10-07
> **Framli said:**
> This may only work for launchpad ppas, I use it to check if there is already a Maverick version of a ppa.
```
for i in $(cat /etc/apt/sources.list.d/* | grep -o http.* | sed s/\ .*//) ; do echo $i && curl -silent -I $i/dists/maverick | grep -o 404; done;
```

Thanks! That works with normal repositories too, not just PPAs (like the Dropbox or Opera repositories).

---

### Post by nilarimogard on 2010-10-07
> **xircon said:**
> ```
Ign http://skulltag.net jaunty Release.gpg
Ign http://skulltag.net/download/files/release/deb/ jaunty/multiverse Translation-en
Ign http://skulltag.net/download/files/release/deb/ jaunty/multiverse Translation-en_GB
Ign http://skulltag.net jaunty Release
Get:1 http://dl.google.com stable Release.gpg [191B]
Ign http://skulltag.net jaunty/multiverse amd64 Packages/DiffIndex
Ign http://linux.dropbox.com maverick Release.gpg
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_GB
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_GB
Get:2 http://dl.google.com stable Release.gpg [189B]
Ign http://download.skype.com stable Release.gpg
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_GB
Hit http://apt.spideroak.com release Release.gpg
Ign http://apt.spideroak.com/ubuntu-spideroak-hardy/ release/restricted Translation-en
Ign http://apt.spideroak.com/ubuntu-spideroak-hardy/ release/restricted Translation-en_GB
Ign http://download.skype.com/linux/repos/debian/ stable/non-free Translation-en
Hit http://archive.ubuntu.com maverick Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://download.skype.com/linux/repos/debian/ stable/non-free Translation-en_GB
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Hit http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Hit http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Hit http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://skulltag.net jaunty/multiverse amd64 Packages
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/awn-testing/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/awn-testing/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://download.skype.com stable Release
Ign http://linux.dropbox.com maverick Release
Get:3 http://dl.google.com stable Release [1,311B]
Ign http://apt.boxee.tv maverick Release.gpg
Hit http://apt.spideroak.com release Release
Hit http://extras.ubuntu.com maverick Release
Ign http://apt.boxee.tv/ maverick/main Translation-en
Hit http://archive.ubuntu.com maverick Release
Ign http://skulltag.net jaunty/multiverse amd64 Packages
Ign http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/ maverick/main Translation-en_GB
Ign http://download.skype.com stable/non-free amd64 Packages
Get:4 http://dl.google.com stable Release [1,338B]
Hit http://ppa.launchpad.net maverick Release.gpg
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Hit http://skulltag.net jaunty/multiverse amd64 Packages
Ign http://apt.boxee.tv/ maverick/main Translation-en_GB
Hit http://archive.ubuntu.com maverick/main amd64 Packages
Ign http://apt.spideroak.com release/restricted amd64 Packages
Ign http://linux.dropbox.com maverick/main amd64 Packages
Ign http://apt.boxee.tv maverick Release
Ign http://ppa.launchpad.net/baudm/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/baudm/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/bisigi/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/bisigi/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ maverick/main Translation-en
Ign http://download.skype.com stable/non-free amd64 Packages
Get:5 http://dl.google.com stable/main amd64 Packages [1,001B]
Hit http://archive.ubuntu.com maverick/universe amd64 Packages
Hit http://archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://archive.ubuntu.com maverick/multiverse amd64 Packages
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://apt.spideroak.com release/restricted amd64 Packages
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/compiz/ppa/ubuntu/ maverick/main Translation-en
Ign http://linux.dropbox.com maverick/main amd64 Packages
Err http://download.skype.com stable/non-free amd64 Packages
  404  Not Found [IP: 130.117.72.44 80]
Get:6 http://dl.google.com stable/main amd64 Packages [630B]
Ign http://apt.boxee.tv maverick/main amd64 Packages
Ign http://ppa.launchpad.net/compiz/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://apt.boxee.tv maverick/main amd64 Packages
Err http://linux.dropbox.com maverick/main amd64 Packages
  404  Not Found
Hit http://apt.spideroak.com release/restricted amd64 Packages
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/echidnaman/qapt/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/echidnaman/qapt/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/ maverick/main Translation-en_GB
Err http://apt.boxee.tv maverick/main amd64 Packages
  403  Forbidden
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/geany-dev/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/geany-dev/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/hel-sheep/pastie/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/hel-sheep/pastie/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/kwwii/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/kwwii/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/laurent-parenteau/full-circle-notifier/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/laurent-parenteau/full-circle-notifier/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/loneowais/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/loneowais/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/norsetto/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/norsetto/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/openismus-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/openismus-team/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/psyke83/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/psyke83/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/ricotz/testing/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ricotz/testing/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/silverwave/one-daily-a-month-1/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/silverwave/one-daily-a-month-1/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/webupd8team/rhythmbox/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/webupd8team/rhythmbox/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/webupd8team/unstable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/webupd8team/unstable/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://ppa.launchpad.net maverick/main amd64 Packages
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Fetched 4,660B in 9s (517B/s)
```

That's exactly the non-interesting part of the output. Exactly below it you would have seen the exact PPAs which give the errors. Here's that part for my sources:


```
Ign http://ppa.launchpad.net maverick/main i386 Packages
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Fetched 66B in 2s (31B/s)
W: GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: Failed to fetch http://ppa.launchpad.net/jldupont/jldupont/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/jldupont/jldupont/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

