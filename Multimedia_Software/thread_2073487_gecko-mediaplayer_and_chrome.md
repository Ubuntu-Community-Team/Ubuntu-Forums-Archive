---
title: "gecko-mediaplayer and chrome"
date: 2012-10-19
forum: Multimedia Software
---

### Post by monkeybrain2012 on 2012-10-19
In Ubuntu 12.10 gecko-mediaplayer doesn't load in chrome. In Ubuntu 12.04 gecko-media player loads but crashes immediately (in Chrome) This happens with both video and audio links.

The crash in Ubuntu 12.04 seems to happen only with Nvidia cards (with both nouveau and the proprietary drivers). Tested on a few computers with Nvidia graphic cards and gecko-media player failed in all cases, but it works fine with a few other machines with AMD cards.

The problem happens only in Chrome, in Firefox everything works.

Any insight or hint to where the problem might be will be greatly appreciated. Thanks.

---

### Post by monkeybrain2012 on 2012-10-20
Bump!

---

### Post by monkeybrain2012 on 2012-10-20
Actually it doesn't even work in Firefox, I use ViewTube to replace flash for Youtube [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)  I could  see gecko-mediaplayer started  and then it got stuck at 1.8%. forever, whereas totem's plugin  works.

---

### Post by monkeybrain2012 on 2012-10-22
Hello?? Anyone?

---

### Post by monkeybrain2012 on 2012-10-23
So no one else is experiencing this problem??

---

### Post by monkeybrain2012 on 2012-10-29
Someone has filed a bug report against gecko-mediplayer for not loading in Chrome 
[https://bugs.launchpad.net/ubuntu/+source/gecko-mediaplayer/+bug/1069635](https://bugs.launchpad.net/ubuntu/+source/gecko-mediaplayer/+bug/1069635)

However. as I said above it is not working in FF either for Ubuntu 12.10. I am suspecting that it may have something to do with the Nvidia driver. Does anyone experience any loading problem in Firefox with or without a Nvidia card? 

Please provide some feedback.

---

### Post by monkeybrain2012 on 2012-11-13
Anyone?? Again it doesn't work in Firefox either.

---

### Post by marcellotescari on 2012-11-27
Hello, i'm new here. 
I am using kubuntu 12.10. That problem occurs to me with chrome (23) but not with firefox. Intel HD video card. Hope this can help. I haven't found a solution yet. 
Works fine with both browser on 12.04 (as long as chrome 20 was used, didn't try afterwards)

---

### Post by monkeybrain2012 on 2012-12-26
upgrade gnome-mplayer and gecko-mediaplayer to ver 1.8a using this ppa and all problems solved. Now gecko-mediaplayer works in both chrome and Firefox

[https://launchpad.net/~brandonsnider/+archive/gnome-mplayer-dev?field.series_filter=quantal](https://launchpad.net/~brandonsnider/+archive/gnome-mplayer-dev?field.series_filter=quantal)

When you add the ppa and upgrade, synaptic asks to remove gnome-mplayer and gecko-mediaplayer and upgrade some other stuffs, instead, check the boxes to upgrade gnome-mplayer and gecko-mediaplayer and those other dependencies will be removed. click apply and everything will work.

---

