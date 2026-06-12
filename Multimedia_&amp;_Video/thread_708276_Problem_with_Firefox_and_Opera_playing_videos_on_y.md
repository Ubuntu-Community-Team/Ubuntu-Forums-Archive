---
title: "Problem with Firefox and Opera playing videos on yahoo, cnn, etc."
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by chtaysom on 2008-02-26
Has anybody run into this problem before?

I have installed Gutsy Gibbon 7.10 on my laptop and I have gotten everything to work except I can't ever get any flash based web sites to run.

In addition, I can't get any embedded video players to work.

For example, if I go to yahoo news, or cnn.com or something of that nature, I can't get the  video clips to run.

I'm certain that Adobe flash player is installed on Synaptic.

It is possible that my firewall on my laptop is causing the problem but I know it's not the firewall on the network b/c other computers get videos all the time....it's only on my computer.

Any ideas?





Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.12) Gecko/20080207 Ubuntu/7.10 (gutsy) Firefox/2.0.0.12

This is my version of Firefox

---

### Post by jmagsho on 2008-02-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/mplayerplug-in/+bug/64857](https://bugs.launchpad.net/ubuntu/+source/mplayerplug-in/+bug/64857) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I too just ran across this problem.  I think it may be related to one of the recent software updates.  I'm going to try re-installing the embedded player plugins and will post my results here when complete.  Launchpad URL is for Opera, but there are issues with Firefox as well...

---

### Post by wolfen69 on 2008-02-26
let's try re-installing flash
```
sudo apt-get remove --purge flashplugin-nonfree
```
then, get this [http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb) 
click to install.
then
```
sudo apt-get install mozilla-mplayer
```
if that doesnt work, you may have to remove totem.(it sometimes conflicts with mplayer) let us know what happens.

---

