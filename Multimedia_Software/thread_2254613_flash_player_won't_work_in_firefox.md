---
title: "flash player won't work in firefox"
date: 2014-11-28
forum: Multimedia Software
---

### Post by john294 on 2014-11-28
Hi,
I use Ubuntu 14.04 with an Xfce4-Desktop. Somehow I can't get flashplayer to work under firefox.
I tried following the suggestion posted here: "http://askubuntu.com/questions/521234/my-flashplugin-doesnt-work-on-firefox", but Flashplayer still won't work.
Whenever I trie to load anything that needs Flash in Firefox I get the following message:[INDENT]```
Failed to load "libpepflashplayer.so"
```[/INDENT]
I don't have this problem on my other systems (One system running Ubuntu 14.04 with the Unity Desktop and another running Xubuntu)
Any suggestions?

---

### Post by Impavidus on 2014-11-28
The pepper flash player doesn't work on firefox. To get flash in Firefox, you need **flashplugin-installer** (available from the software centre or any other interface to the Ubuntu repositories). This flash player is stuck at version 11.2, although security updates are still provided. The pepper flash player is more recent, but only runs on chrome or chromium. See the last comment on that askubuntu page.

---

