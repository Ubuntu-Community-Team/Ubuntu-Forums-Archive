---
title: "installed ubuntu-restricted-extras and now can't play flash content"
date: 2008-07-04
forum: Multimedia Software
---

### Post by jasonwatkins on 2008-07-04
.. which is annoying ..

it was playing fine before i installed it, but i only installed it because I'd forgotten how to get k3b to burn audio cd's from mp3's, and googled for a solution.

i've removed it completely, but it hasn't reverted back to allowing me to play flash content.

would i need to re-install adobe flash?

or re-install the flash plugin for FF3 ??

---

### Post by ubuntu-freak on 2008-07-04
Check if purging and reinstalling helps:
 
**sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree**
 
You may actually get better performance from Flash v10 beta, see the troubleshooting section of my  [how-to](ubuntuforums.org/showthread.php?t=766683) for details.

---

### Post by jasonwatkins on 2008-07-05
thanks for that but it didn't work - i still just get a grey box where the flash content should be.

don't even get any mplayer pluging controls to play anything either.

*EDIT

fixed it - downloaded and manually installed the flash player tar.gz file and it's working fine now :)

---

### Post by ubuntu-freak on 2008-07-05
Glad I could help.
 
Try my streaming section also, the Gecko Media Player plugin is basically a new and improved MPlayerplug-in.

---

### Post by jasonwatkins on 2008-07-07
it never actually solved it - a day or so later, it just went back to not playing anything.

but i've reformatted now anyway .. drastic solution i know, but hey, i was bored :)

---

