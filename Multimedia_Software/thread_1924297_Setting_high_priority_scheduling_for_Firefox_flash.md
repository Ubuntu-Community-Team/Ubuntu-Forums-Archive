---
title: "Setting high priority scheduling for Firefox flash plugin-container"
date: 2012-02-12
forum: Multimedia Software
---

### Post by Dusenberg on 2012-02-12
Hi

Kit:
ZOTAC AD02, AMD E350 1.6Ghz dual core, AMD Radeon HD 6310, 4Gb ram, 160Gb 7200rpm 2.5" Seagate HDD, xubuntu 11.10, AMD/ATI Catalyst drivers, Firefox 9, Flash 11.2,r202. 100Mb wired Lan into 10Mb fibre internet connection, audio out to Kenwood hifi.

I need to get the Firefox flash plugin-container automatically run at a -15 scheduling priority so that iPlayer streaming is smooth.  Running at normal priority gives jerky playback and loss of audio sync on many/most streams from most UK iPlayer sources, and makes it unwatchable.  This is a hardware/system issue as my Samsung E55 laptop has no problem playing same streams across a wireless LAN from same internet connection, and its running the same versions of OS etc.

I want to do it automatically as the ZOTAC is set up purely for this iPlayer-type streaming, with autologin, and it doesn't usually have a keyboard attached as everything is workable from the setee via wireless mouse. So having to do it manually each time is a pain.

Coding the following in Terminal with the plugin-container running (ie streaming a flash video through firefox) creates the required results - smooth playback.
```

sudo renice -15 $(pidof -s /usr/lib/firefox-9.0/plugin-container)

```

The plugin-container remains running for as long as Firefox so if I switch from say BBC iPlayer to itv iPlayer, the high priority continues to apply for the whole session which is good.

However I can't find a way to set this high priority automatically.  

I tried replacing /usr/lib/firefox-9.0/plugin-container with a shell script and renaming the plugin-container "_plugin-container" as follows:
```

#!/bin/bash
/usr/lib/firefox-10.0/_plugin-container "$@" &
sudo renice -15 $(pidof -s /usr/lib/firefox-9.0/_plugin-container)

```

but it didn't work. The video streams fine (ie the plugin container is initiated correctly), but the scheduling priority of _plugin-container remains 0, not -15. 

Has anyone any ideas - I'd  really appreciate some help :)

---

