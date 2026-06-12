---
title: "Rhythmbox / DAAP"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by onedotseven on 2007-01-31
Hello,

I'm having some troubles with Rhythmbox.

I have on my Ubuntu system Firefly (mt-daapd), Rhythmbox and Banshee. I have iTunes on a Windows PC on the same network. In iTunes, I see Firefly, Banshee and Rhythmbox shares fine. In Banshee, I see Firefly, Rhythmbox and iTunes shares. But in Rhythmbox, I see only the iTunes share. It looks like Rhythmbox cannot see local daap servers. This is happening with Rhythmbox 0.9.6 (default Ubuntu install) and a freshly installed 0.9.7 (with daap enabled).

Anyone has an idea what's going on? :( 


Thank you.

---

### Post by onedotseven on 2007-01-31
Just found the information. It's a known, confirmed bug. Local DAAP shares are not listed if their user owner is the same than the one running Rhythmbox:

[https://launchpad.net/ubuntu/+source/rhythmbox/+bug/55045](https://launchpad.net/ubuntu/+source/rhythmbox/+bug/55045)
[http://bugzilla.gnome.org/show_bug.cgi?id=342655](http://bugzilla.gnome.org/show_bug.cgi?id=342655)

If anyone is interested...

---

