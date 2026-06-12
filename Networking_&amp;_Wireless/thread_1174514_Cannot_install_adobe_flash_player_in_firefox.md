---
title: "Cannot install adobe flash player in firefox"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by amishera on 2009-05-31
Hi,

I have ubuntu 8.04 installed in my pc. Whenever I try to access sites with flash videos in them, the firefox shows flash player plugin missing. Then I go to the adobe's website to download the flash player for linux. But then whatever choice I select(tar.gz, .deb etc) as soon as the browser tries to download the file, the "page not found" page pops up. I tried to download the file from windows but it tries to install the player corresponding to windows. What is the cure for such a problem?

Thanks.

---

### Post by pastalavista on 2009-05-31
You need to search Synaptic Package Manager for 'adobe-flashplugin' or run in terminal```
sudo apt-get install adobe-flashplugin
``` To do that, third-party and restricted software sources have to be enabled in Synaptic settings.

---

