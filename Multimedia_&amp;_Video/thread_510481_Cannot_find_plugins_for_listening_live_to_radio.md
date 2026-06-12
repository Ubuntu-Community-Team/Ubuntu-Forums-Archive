---
title: "Cannot find plugins for listening live to radio"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by Jored on 2007-07-26
When I try to listen live, the pop-up player from some radio stations indicate a missing plugin. Firefox searches for the plugin and comes back with an unknown plugin message.

The missing plugins, depending from the station are:

application/x-mplayer2
video/x-ms-asf-plugin

I'm running Xubuntu 7.04 with Xfce desktop.

---

### Post by tbroderick on 2007-07-26
Install the mplayerplug-in and the w32codecs.

---

### Post by Jored on 2007-07-27
How, please? I'm very new to Linux.

---

### Post by snoop on 2007-07-27
> **Jored said:**
> How, please? I'm very new to Linux.

You can search for it in synaptic.

---

### Post by tbroderick on 2007-07-27
If you are using Feisty, open a terminal and paste;
```

sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then paste;
```

sudo apt-get update
sudo apt-get install mplayerplug-in w32codecs
```

---

### Post by Jored on 2007-07-27
Thank you, tbroderick. I did as you indicated but I must have screwed up something earlier since clicking on "listen live" on radio stations' websites always opens Totem Movie Player and messages  indicating "requires Windows Media Speech Decoder" or "no decoder" or "no html decoder" come up and streaming doesn't start.

---

### Post by Gremlinzzz on 2007-07-27
> **Jored said:**
> Thank you, tbroderick. I did as you indicated but I must have screwed up something earlier since clicking on "listen live" on radio stations' websites always opens Totem Movie Player and messages  indicating "requires Windows Media Speech Decoder" or "no decoder" or "no html decoder" come up and streaming doesn't start.
go to synaptic package manager  and  click search then type totem when you see totem plugin  uninstall it. then the installed mplayer pulgin will take over.
:guitar:

---

### Post by Jored on 2007-07-27
OK. Got it working accross the board. This is what I did:

Synaptic Package Mgr, click Search, type totem. Uninstall totem-gstreamer plugin (if installed) which also unistalls totem-xine plugin. Search for totem again and install totem-mozilla, which reinstalls totem-xine.

---

### Post by Gremlinzzz on 2007-07-27
> **Jored said:**
> OK. Got it working accross the board. This is what I did:

Synaptic Package Mgr, click Search, type totem. Uninstall totem-gstreamer plugin (if installed) which also unistalls totem-xine plugin. Search for totem again and install totem-mozilla, which reinstalls totem-xine.
you only need to uninstall totem-mozilla
but i don't have any totem either and you can reinstall the rest if you want them
:guitar:

---

### Post by Gremlinzzz on 2007-07-27
You might also want to install smplayer which plays your dvd movies and stuff.
if your using ubuntu and not kubuntu get the one Qt3; without KDE support)
its a deb package download the package and  just right click on it and choose use deb installer
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
:guitar:

---

