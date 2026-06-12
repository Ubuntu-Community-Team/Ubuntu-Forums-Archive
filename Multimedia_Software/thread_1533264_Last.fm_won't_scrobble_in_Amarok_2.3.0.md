---
title: "Last.fm won't scrobble in Amarok 2.3.0"
date: 2010-07-17
forum: Multimedia Software
---

### Post by mdekoning on 2010-07-17
I'm not getting last.fm scrobbling working in Amarok. I'm using KDE 4.4.2 and even though my last.fm profile shows tracks as "now playing" while I'm listening, tracks aren't actually scrobbled and they're gone from my profile once you've moved to the next song. In Gnome everything seems to be working fine, so the problem is most likely somewhere in KDE. I couldn't find any solutions anywhere on the internet, except this one:

it known issue if you disable kwallet. 
edit file ~/.kde/share/config/amarokrc

[Service_LastFm]
fetchSimilar=true
**ignoreWallet=yes**
password=your_pass
scrobble=true
username=your_login

However, this didn't solve anything. Does anybody know another way to solve this?

---

