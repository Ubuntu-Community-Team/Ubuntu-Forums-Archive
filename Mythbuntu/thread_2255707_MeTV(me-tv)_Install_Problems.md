---
title: "MeTV(me-tv) Install Problems"
date: 2014-12-06
forum: Mythbuntu
---

### Post by mark bower on 2014-12-06
Using Ubuntu 12.04, what .deb version of me-tv should I be using?  Could you provide the link where to get it?

I realize this section is for MythTV, but thot I would get the best shot at a response here.  I have tried what I believe to be the best version, me-tv_1.4.0~49~precise1_i386.deb, but I could not get it to install and work.  Once I am sure of the right version, I can return for specific help as to the problem.  I can't seem to get the hang of Launchpad and PPA's, at least with respect to MeTV, thus I would like the simplicity of a ".deb".

[edit 14 Dec 14] Please see my following post.  me-tv_1.4.0~49~precise1_i386.deb I now assume is a perfectly o.k. version.  It likely did not install properly due to conflicts.  me-tv when working is very nice and simple for TV viewing and recording.

tx
mark bower

---

### Post by mark bower on 2014-12-12
I now have me-tv working.  I tried a new approach by doing a clean reinstall of 12.04LTS and the following:
Synaptic Pkg Mgr
Gnome Classic
me-tv 1.3.6-1via synaptic
w-scan

I am not sure of this, but seemed like a channels.conf was not created in ~/.me-tv when using the initial acquisition option - but no matter.  I did a w_scan and copied the resultant channels.conf file to the ~/.me-tv folder.  
```
sudo apt-get install w-scan
w_scan -fa -A1 -c US> ~/Desktop/channels.conf
```

I could not determine how to change channels - the 9pg Me-Tv Manual is inadequate and does not provide the below which I found by googling; the manual also does not explain how to use the Channels Editor.  I include the following how-to so that others reading this post might benefit:

"In Me-TV the channel selection area might not be visible.  You can pull it up using the mouse: The cursor will change when you place it at the top of the bottom tool-bar, then you can click left, hold and move up.  You might have to "Change View Mode" first, which will toggle visibility of the channel selection area."

mark

---

