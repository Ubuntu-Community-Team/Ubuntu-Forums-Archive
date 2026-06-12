---
title: "Amarok Last.fm error"
date: 2009-11-02
forum: Multimedia Software
---

### Post by Leiot on 2009-11-02
I'm having an issue with Amarok's last.fm client, despite my being in the USA last.fm complains I must be a paying subscriber to use the service when I try and use it in Amarok. This puzzles me as it worked fine in Linux Mint 7 under Rhythmbox. All I did was a fresh install of Kubuntu 9.10 and it complains I must subscribe yet it worked before.

---

### Post by fraktalek on 2009-11-11
Hi, I've just run into this issue too. It seems like it is intentional and in line with the official last.fm rules:

> 
1) Client streaming is subscriber-only for all users in all countries. This includes the official last.fm player.
2) Web streaming is free in US/UK/DE because on-page ad revenue can cover the licensing costs of playing you that music.

However,

3) This is all based on the new Last.Fm API that was just released this spring. Amarok is using liblastfm, the official c++ library for communicating with last.fm, that uses this new API. This new API comes with the aformentioned restrictions.
4) The current release of the last.fm client uses an old API, and still works.
5) Amarok <2.2 uses an old API version, and still works.
6) The in-development last.fm desktop client is also using liblastfm, and will be subject to the same constraints as amarok 2.2 when it is released.

Last.Fm can turn off the old API whenever they want (when they have released their client clearly). Amarok is not going to consciously try to circumvent the Last.Fm ToS by using an older version of the API that may or may not break at any moment.


Source: [http://izanbardprince.wordpress.com/2009/09/12/kde-starts-enforcing-last-fms-paywall-in-amarok-2-1-80/](http://izanbardprince.wordpress.com/2009/09/12/kde-starts-enforcing-last-fms-paywall-in-amarok-2-1-80/)

---

