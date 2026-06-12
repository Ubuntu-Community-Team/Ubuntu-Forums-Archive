---
title: "MCC missing options"
date: 2010-07-22
forum: Mythbuntu
---

### Post by gilson585 on 2010-07-22
In mythbuntu-control-center the only tabs I get are; Log Grabber, and Repositories.
Lemme start from the beginning. I had issues with mysql-server starting. The only way it would start was after a dpkg-reconfigure-mysql-server-5.1 So I backed up my database with the script provided by mythtv. Then I purged mysql-common which also removes mythtv and all related componets. Then I proceeded to install mythtv after which I restored the mysql database. That works fine and all my settings, channels, and recordings are still there but I'm missing the various myth plugins and can't use MCC to install them.

---

### Post by LowSky on 2010-07-22
Install the plugins from synaptic instead.

---

### Post by gilson585 on 2010-07-22
yes I realize that I could do that but the i'd like to retain the functionality and ease of use mcc provides

---

### Post by tgm4883 on 2010-07-22
Looks like you are somehow missing mythbuntu-common

---

### Post by gilson585 on 2010-07-22
thanks a bunch installing mythbuntu-common fixed it

---

