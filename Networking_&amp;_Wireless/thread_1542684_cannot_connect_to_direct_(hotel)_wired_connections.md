---
title: "cannot connect to direct (hotel) wired connections since running ppoeconf"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by bjaz on 2010-07-30
hello all

i'm currently travelling in across Japan and facing difficulties connecting to hotel's ethernet connections under ubuntu 10.0.4- when plugging in the ethernet cable nothing happens- rebooting doesn't change anything either.

 this wasn't a problem before, and i can connect to hotel's ethernet under windows 7 which i'm currently using to post this, but something doesn't work under ubuntu, which is now my main os.
 
staying at my inlaw's house for a while, i ran pppoeconf to use their optical fibre connection, which worked, but also seems to be the root of the problems i'm now facing to go online via ethernet elsewhere. it seems like pppoeconf disabled something

can anyone help ? there's virtually no free wireless in japan, and i would really like to fix this but have no idea how

thanks in advance

b

---

### Post by iponeverything on 2010-07-31
Its ugly but I would remove and purge pppoeconf using dpkg and then just reinstall pppoeconf when needed. The pppoeconf deb for reinstall should be /var/cache/apt/archives

```
sudo dpkg -P pppoeconf
```

Also right click on Network Manager and go to Edit Connections to check to see if it disabled the Ethernet connection.

---

### Post by dineshs on 2010-07-31
10.04 uses Network manager(NM).
Instead of using pppoeconf you may try configuring the connection via the DSL tab in NM.If you run pppoeconf the file /etc/network/interfaces wiil be edited and NM will no longer manage the connections.Kindly try this
First backup your /etc/network/interfaces
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```then follow
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

---

### Post by bjaz on 2010-07-31
that worked, thanks a lot ! back online on the hotel's ethernet.

should use the above to un-edit the lines when i move back to my inlaw's house to get their ( pppoe) optical fibre connection working or is there another way to use netork manager to do this ?

thanks again, life just got a lot easier

ben

---

### Post by dineshs on 2010-07-31
> **bjaz said:**
> that worked, thanks a lot ! back online on the hotel's ethernet.

should use the above to un-edit the lines when i move back to my inlaw's house to get their ( pppoe) optical fibre connection working or is there another way to use netork manager to do this ?

thanks again, life just got a lot easier

ben
You can use the DSL tab in NM to configure pppoe
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)

---

