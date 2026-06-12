---
title: "Stick on Network Manager 0.8"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by aneganov on 2010-02-26
hi all

I added a repo from launchpad to install latest Network Manager and then installed it (version 0.8). Then I decided to rollback to Karmic's version (since 0.8 doesn't work) but failed:

I removed the repo from sources.list
Then apt-get udpate
Then apt-get clean
Then apt-get install network-manager...

But still 0.8 version is downloaded and installed!

How can I restore Karmic's version?

P.S. SOS I have not WiFi anymore :(

---

### Post by chili555 on 2010-02-26
You will probably have to do:```
sudo apt-get remove --purge network-manager
sudo apt-cdrom add
```Drop your installation CD in the tray.```
sudo apt-get update
sudo apt-get install network-manager
```

---

### Post by aneganov on 2010-02-27
> **chili555 said:**
> You will probably have to do:```
sudo apt-get remove --purge network-manager
sudo apt-cdrom add
```Drop your installation CD in the tray.```
sudo apt-get update
sudo apt-get install network-manager
```

I installed Ubuntu from network, so not using cdrom.
My sources.list:
```

deb http://de.archive.ubuntu.com/ubuntu/ karmic main restricted
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

deb http://de.archive.ubuntu.com/ubuntu/ karmic universe
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe

deb http://de.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse

deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main 

```

---

### Post by Arkitekt on 2010-02-27
Try forcing a previous version through synaptic. 

Force version is found under the 'Package'

---

### Post by aneganov on 2010-02-27
> **Arkitekt said:**
> Try forcing a previous version through synaptic. 

Force version is found under the 'Package'

I'd gladly do it, but I don't see any other version of network-manager in repository:
[ATTACH]148370[/ATTACH]
As you can see, there are only 0.8git things.

---

### Post by Arkitekt on 2010-02-27
select the installed network-manager and Ctrl-E, should come up with the Force Version window, just select a previous version.

---

### Post by aneganov on 2010-02-27
> **Arkitekt said:**
> select the installed network-manager and Ctrl-E, should come up with the Force Version window, just select a previous version.

Corresponding menu item (for Ctrl-E) is disabled in menu. Synaptic doesn't know about any other version.

---

### Post by Arkitekt on 2010-02-27
Hmm, perhaps google for a previous version in a ppa? 

or you could uninstall network-manager and install WICD

---

### Post by aneganov on 2010-02-28
LOL, this was all so stupid... 

I don't know how I missed it, but Karmic's version of NM IS 0.8! So I was claiming about how to downgrade from Karmic's official versin to nowhere, thinking it should be 0.7.xxx

I'm sorry. Dunno how this happened and what have made me thinking  that way.

---

