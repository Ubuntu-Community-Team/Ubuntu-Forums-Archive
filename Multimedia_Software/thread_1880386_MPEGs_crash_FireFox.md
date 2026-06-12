---
title: "MPEGs crash FireFox"
date: 2011-11-13
forum: Multimedia Software
---

### Post by windfix on 2011-11-13
I am using Oneiric 32 bit and FF 7.0.1.  Videos are crashing my browser.  I am using an mpeg file to test, but FF is not playing other videos either.  Help?

Plugins installed: DivX Browser, DivX Web Player, gecko-mediaplayer, realplayer 9, shockwave flash, vlc multimedia, vlc mm (totem 3.0.1 compatible), windows media, windows media (totem), quicktime 7.6.6.

Help?

I get the following crash output:

Add-ons: [email]unplug@compunach:2.050,en-US@dictionaries.addons.mozilla.org:5.0.1,{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}:1.3.10,firefox@openattribute.com:0.9.8,langpack-en-GB@firefox.mozilla.org:7.0.1,langpack-en-ZA@firefox.mozilla.org:7.0.1,globalmenu@ubuntu.com:2.0.1,zotero@chnm.gmu.edu:2.1.10,ubufox@ubuntu.com:1.0,zoteroOpenOfficeIntegration@zotero.org:3.5b2,{972ce4c6-7e08-4474-a285-3208198ce6fd}:7.0.1,unityfox@mozilla.org[/email]:0.1.5
BuildID: 20111008085056
CrashTime: 1321210405
EMCheckCompatibility: true
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1318616659
ProductName: Firefox
SecondsSinceLastCrash: 1074
StartupTime: 1321209572
Theme: classic/1.0
Throttleable: 1
URL: file:///home/paul/Desktop/ETEC%20697/Website697/video/Intro,%20small.mpeg
Vendor: Mozilla
Version: 7.0.1

This report also contains technical information about the state of the application when it crashed.

---

### Post by windfix on 2011-11-14
I found that the mozilla-plugin-vlc package was the culprit.  Complete removal via Synaptic package manager, and voila FireFox works with MPEGs again.

---

