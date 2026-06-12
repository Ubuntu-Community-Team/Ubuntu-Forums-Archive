---
title: "How to upgrade from 8.04 to 9.04 ?"
date: 2009-05-01
forum: Mythbuntu
---

### Post by Verzweifler on 2009-05-01
I am considering to upgrade my system from 8.04 to 9.04, but I realized that the usual 8.04 -> 8.10 -> 9.04 way is not an option because there are no 8.10 Mythbuntu images around any more (and alternate disks are no longer available as well).
I do NOT want to perform a fresh install from a 9.04 Mythbuntu CD, so how can I upgrade smoothly?

My system is a backend-only server running with neither Ubuntu/Kubuntu/Xubuntu desktop and serving out diskless images to my frontends. Will an upgrade using the Alternate UBUNTU disks (8.10 and 9.04) as suggested in the Ubuntu upgrade notes work on MYTHBUNTU as well, or do I risk to hose my system (or to even activate a fancy desktop I do not need)? or to ask it another way round: will a cdromupgrade performed from the alternate disk only upgrade existing packages or will it install whatever it considers necessary (like e.g. OpenOffice or the like)?

If this turns out to be a tricky issue, I guess I'll better wait for 0.22 and then perform a cool reconstruction of my system (i.e. fresh install).

Thanks


Mike

---

### Post by madu on 2009-05-12
I also want to know this. Anybody?

---

### Post by klc5555 on 2009-05-13
> **madu said:**
> I also want to know this. Anybody?

Eventually 8.10 should end up at [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

But it's not there yet (beyond the alpha-3)

Until then, it's still available lots of places on the web for the cost of a google search. Not least of all here:

[http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)

Cheers! :)

---

### Post by the_crowbar on 2009-05-13
I am currently updating from 8.10 to 9.04. All I do is make a backup of my sources.list and then edit all the intrepid lines to jaunty.

Something like:
```

sudo cp /etc/apt/source.list /etc/apt/sources.list.intrepid
sudo sed -e 's/intrepid/jaunty/' /etc/apt/sources.list.intrepid >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade

```
Basically that is the steps I do when I upgrade remotely in a console. You could try going straight 8.04->9.04 or you could try 8.04->8.10->9.04.

---

### Post by tgm4883 on 2009-05-13
> **the_crowbar said:**
> I am currently updating from 8.10 to 9.04. All I do is make a backup of my sources.list and then edit all the intrepid lines to jaunty.

Something like:
```

sudo cp /etc/apt/source.list /etc/apt/sources.list.intrepid
sudo sed -e 's/intrepid/jaunty/' /etc/apt/sources.list.intrepid >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade

```
Basically that is the steps I do when I upgrade remotely in a console. You could try going straight 8.04->9.04 or you could try 8.04->8.10->9.04.

This is not a recommended upgrade path by anyone.  I'd recommend grabbing the torrent of 8.10 as it is still around.  It can be found at linuxtracker.org

These links should get you there

```
http://linuxtracker.org/index.php?page=torrent-details&id=ec67ccfd4ee57ef82c7b203d628ab93ea59e2465
http://linuxtracker.org/index.php?page=torrent-details&id=04dc07217ae0e3395a5e5b8181952a04f259a728
```

---

### Post by the_crowbar on 2009-05-13
Care to share what the recommended remote (ssh) console upgrade path is? When I first looked I did not fine one. My way works for Debian and appears to work for Mythbuntu as well.

---

### Post by tgm4883 on 2009-05-13
> **the_crowbar said:**
> Care to share what the recommended remote (ssh) console upgrade path is? When I first looked I did not fine one. My way works for Debian and appears to work for Mythbuntu as well.

I believe the official command line way of doing it is

```
sudo do-release-upgrade
```

---

### Post by the_crowbar on 2009-05-13
do-release-upgrade failed to find a new release for Mythbuntu. I have used it on Ubuntu server, but it did not see Mythbuntu 9.04.

---

### Post by tgm4883 on 2009-05-13
I'll have to check when I get home.  It might default to LTS only, have you checked switches?

IIRC, there is a -d or something that you need to do.

:EDIT:

Actually, -d would make more sense for a dev release, so i'm not sure

---

### Post by Ama Zing on 2009-11-17
Hi a **newbee** here :D. I am just upgrading naively by using **the update manager** in X-windows installed on **Hardy 8.04 LTS**.
You know what is my upgrade option? **Upgrade to version 10.10** when we would expect 8.10 (or 9.04 LTS)!
Just fired it up and you know whats next? **it is actually upgrading to 9.10**! **Ama-Zing** isn't it? The fully automated updater really amazes since it jumps to the latest version available!
From here on we continue to **Don't care**!
During upgrade it is only asking something about a PAM setting for Dovecot, just continue with Forward.
 
Saw some funny messages again in between like these:
"**Xlib: Generic event extension missing on Display :0.0**"
let the beat go on!
**Unable to delete old directory ... FireFox**.. 
Don't care... for a fox more or less - there are so many Foxes nowadays ;)
Looks like **new kernel**(headers) going to be somethin like **2.6.31-14**
That Cool "Generic event extension missing on Display :0.0" was passing by many times again.
:popcorn:takin more than an hour had some time to watch movie and have my popcorn.
Meanwhile Xedit replace popped up and later on another 2 poppers or so - Ok replace the old stuff man!
Saw some other msg that some directory cud not be deleted - what the hack.
Cool now manual pages dbs being rebuild in man.db!
Oops saw at least **2 red Fail messages** in between :o
What the hack we also have **Bicyclerepair**man installed:lolflag:!
Spotted **"Warning! root - failed to setup dbus (ignored)** another Don't care!
 
**FYI**: This silicon stuff is in a **DELL Optiplex GX260 Desktop** with P4 and 1Gigmem serving as a test machine for small VMware guests, Wine glasses, Imap clients and internet gateway for Wifi test clients so not much to worry if somethin wud break.
 
**1 hour and a half have passed..**
After the restart of the system you know what is next?
It will start graphics automatically in contrary to the previous LTS Ubuntu so I **don't need to StartX** anymore! Amazing! But **LTS is gone** too **from the startup menu**.
Obviously 9.10 is not LTS ok ..**but everything is working!**
Firing up the wireless router connected to eth1 enables me to call Skype pals by IPhone again :guitar:IN ONE WORD **AMAZING**!
 
**2011 is still far just wait for Lucid Lynx and we are back in Long Term Support!**
 
**cheers and don't care!**
 
[I]Edit on Friday 20 November 2009 10:01AM JST:
[/I]/etc/resolv.conf appeared without the previously setup nameserver 127.0.0.1 so nslookups wouldn't resolve well.
Strange though that after the upgrade it did lookups correctly. Next day it did not function well anymore which cud be narrowed down to named and finally resolv.conf.
The Hardy 8.04LTS from which was upgraded in 1 step to 9.10 was completely up2date with the November 2009 bugfixes maybe this is why it went kind a flawless?

__________________
:idea: To Bug or not Debug that is the Q

---

