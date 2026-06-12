---
title: "Trouble enabling/installing MythGame plugin"
date: 2010-07-13
forum: Mythbuntu
---

### Post by prometh on 2010-07-13
[LIST=1]
[*]When I tried enabling MythGame from the plugins section of the Mytbuntu Control Centre, I get the error message:
> Package mythgame isn't available

[*]Since subversion wouldn't install correctly for me, I tried downloading the plugin file from the MythTV site and followed the [_installation instructions_]("http://www.mythtv.org/wiki/Configuring_MythGame"), which resulted in this error message:
> qmake for Qt4 not found. Please specify the correct qmake with --qmake=


[*]I am also experiencing [_this issue_]("http://ubuntuforums.org/showthread.php?p=9143437").
[/LIST]

As a side note, I really don't know much about bash and most of what I *do* know was learned on Mac OSX and DOS.

[B]Idea:
Plugin options should be available during installation.[/B]

---

### Post by tgm4883 on 2010-07-13
Open up Synaptic and see if mythgame is listed in there.

---

### Post by prometh on 2010-07-13
It isn't, and in fact, it's not even listed.

---

### Post by tgm4883 on 2010-07-13
post your /etc/apt/sources.list

---

### Post by prometh on 2010-07-13
I wasn't able to upload *.list, nor *.tgz

So, in case you run into issues, I renamed it from *.tgz to *.gz

**Download:** [attach]163341[/attach]

---

### Post by tgm4883 on 2010-07-14
Looks fine. Open up synaptic, hit reload, then tell me if it is listed there

---

### Post by prometh on 2010-07-14
Heh, that fixed it.

Thank you :)

---

