---
title: "MLB.tv &quot;Unable to verify location&quot; ?"
date: 2012-06-24
forum: Multimedia Software
---

### Post by arliss99 on 2012-06-24
On my laptop I have a dual boot Win 7 and Ubuntu 12.04. I can watch MLB.tv on win7 with no issues.  When I want to watch on Ubuntu I get a message "Unable to verify your location" and something about blackout rules.  If there is a free game that works fine on Ubuntu.  Anyone have this issue before?  I sent an email to MLB.tv but I thought I would also ask here.

Thanks.

---

### Post by SeijiSensei on 2012-06-25
> **arliss99 said:**
> On my laptop I have a dual boot Win 7 and Ubuntu 12.04. I can watch MLB.tv on win7 with no issues.  When I want to watch on Ubuntu I get a message "Unable to verify your location" and something about blackout rules.  If there is a free game that works fine on Ubuntu.  Anyone have this issue before?  I sent an email to MLB.tv but I thought I would also ask here.

Thanks.

You might try installing the Firefox add-on [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/) and see if you can send mlb.tv a Windows User-Agent string.

It seems odd that it claims to be unable to verify your location when it presumably just looks at your IP address to do so.  It obviously shouldn't matter what OS and browser you use.  

If you're talking about watching home games where blackout rules apply, MLB may be using the built-in DRM controls that come with Windows to limit its stream to authorized viewers.  If that is the case, it would explain why it doesn't work on Ubuntu where the required DRM software isn't available.

Depending on how often you use Windows, you might want to consider installing [VirtualBox]("http://www.virtualbox.org/") and running Windows in a VM.  It's more convenient than dual-booting if your Windows needs are limited.

---

