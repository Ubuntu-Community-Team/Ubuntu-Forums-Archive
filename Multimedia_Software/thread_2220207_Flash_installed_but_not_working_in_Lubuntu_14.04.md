---
title: "Flash installed but not working in Lubuntu 14.04"
date: 2014-04-27
forum: Multimedia Software
---

### Post by fugazi32 on 2014-04-27
Hi there,

Just upgraded :)

Chromium is saying Flash isn't installed, but it is according to the software centre.

I've also done this: [https://wiki.ubuntu.com/Chromium/Getting-Flash]("https://wiki.ubuntu.com/Chromium/Getting-Flash")

But the command line says *sudo update-pepperflashplugin-nonfree --install* isn't a valid command.

Any ideas? Flash has always worked out of the box when I've upgraded, but now it's broken :(

Nathan

---

### Post by monkeybrain20122 on 2014-04-27
The command is 
```
sudo apt-get install pepperflashplugin-nonfree
```
System flash no longer works in Chromium because google has dropped support for all NPAPI plugins (i.e mozilla plugins). So other multimedia plugins won't work on Chromium either (e.g no more quicktime or window media plugins, so you won't be able to watch Apple trailers on Chromium, for example)

---

### Post by fugazi32 on 2014-04-27
Thanks for the reply, did a bit of searching and found this: [http://itsfoss.com/fix-flash-player-issue-chromium-in-ubuntu-14-04/]("http://itsfoss.com/fix-flash-player-issue-chromium-in-ubuntu-14-04/")

Might give Chrome or Firefox a go.

Many thanks,
Nathan

---

