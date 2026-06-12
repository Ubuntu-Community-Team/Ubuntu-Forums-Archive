---
title: "apt-get says I have latest Flash, sites complain I need to upgrade"
date: 2013-12-22
forum: Multimedia Software
---

### Post by dheianevans on 2013-12-22
Went to look at a video site to get the news on the Toronto ice storm and was told I needed to grab the latest Flash, version **11.2.202.332**.

Did a sudo apt-get update and upgrade...no new flash. Tried sudo apt-get install flashplugin-installer and was told I had latest version. [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) says I have the latest version too...BUT the firefox plugin checker says 11.2 r202

Not quite sure why the Flash page would say it's fine, but the Mozilla plugin page would say it's old.

Thanks.

---

### Post by monkeybrain20122 on 2013-12-22
Which site is that? You are probably unlucky enough to stumple on a stupid site which really expects the latest flash. 11.2 is not the latest(11.9 is the latest), and you are not going to get the latest in Linux because adobe has dropped flash for Linux after 11.2 except for security updates, that's why apt-get install will always tell you it is the latest, cos there is no more.

The only way to get the latest flash in Linux would be to use Chrome because it bundles with its own flash . I have chrome installed just in case I need the latest flash but I almost never use it as I haven't come across any website for which 11.2 doesn't work, but it seems that you are really unlucky/lucky today.

---

### Post by mc4man on 2013-12-22
Possibly you're trying to watch CTV News? If so it appears they're requiring a newer flash version than you can get in linux (other than google-chrome, pepper flash

if so then maybe watch vids on some other more reasonable station or install google-chrome where it works fine (don't know about chromium..

---

### Post by monkeybrain20122 on 2013-12-22
Yeah, flash 11.2 doesn't work on CTV, but works on CBC, CityTV, TVO and GlobalTV, in other words, every other major Canadian/Toronto TV site. So either use Chrome or watch other stations.

P.S. You may need to disable adblock for some of these.

P.s. Chrome probably wouldn't work either because the problem appears to be DRM rather than flash version [http://gedakc.users.sourceforge.net/display-doc.php?name=streaming-ctv-shows](http://gedakc.users.sourceforge.net/display-doc.php?name=streaming-ctv-shows) I tried Chrome, I could see some videos but most require subscriptions. If DRM is the issue there is an easier way than to set up full blown browser with wine, just use pipelight to install Windows flash would work (google it if you must) but I wouldn't bother.

---

### Post by dheianevans on 2013-12-22
Yeah trying to watch CP24.com. Will try chrome. It wasn't working with Chromium. Thanks.

---

### Post by monkeybrain20122 on 2013-12-23
I found out that Chrome's pepper flash doesn't work with cp24's live stream either even though it is up to date,  presumably because of DRM. So if you really want to watch it, an obvious option is Pipelight (it works very smoothly, I have just tested) [http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

I would still keep the native Naapi flash (11.2) around and switch when needed because it works for 99%  of the time and there are things that the wine solution won't work. Examples: Speech doesn't work in google translate with pipelight flash;  Pipelight flash doesn't detect my webcam but the native flash does, there may be other scenarios where you need to change flash's settings. 

Another way may be to install hal and use native flash (FF's or Chrome's) . hal is no longer available in 13.10, but there is a ppa.[https://launchpad.net/~mjblenner/+archive/ppa-hal](https://launchpad.net/~mjblenner/+archive/ppa-hal)
I haven't tried this though.

P.S. Chromium uses the same system flash as Firefox, if FF doesn't work it won't either. Don't even need to try.

---

### Post by monkeybrain20122 on 2013-12-23
Strange. Chrome (pepper flash) does work today.

---

