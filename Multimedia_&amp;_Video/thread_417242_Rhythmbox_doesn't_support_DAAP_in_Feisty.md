---
title: "Rhythmbox doesn't support DAAP in Feisty"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by beerfan on 2007-04-21
I have a brand new Feisty Fawn install. I've confirmed that avahi-daemon is installed and running. I've confirmed that my remote mt-daapd server is visible with service discovery. I've confirmed that the mt-daapd is still accessible with Rhythmbox on my Edgy machine. I've trolled the Rhythmbox bugs in Launchpad and at gnome.org but can't find anyone else who is having this problem. So, why can't my Rhythmbox 0.10 in Feisty Fawn find my remote music?!?

Any suggestions?

---

### Post by beerfan on 2007-04-22
I finally discovered why Rythmbox isn't seeing my daap share. I looked in GConf at the following property and it's disabled by default.

/apps/rhythmbox/plugins/daap/active

Enabling it allows RB to see my remote mt-daapd share but it won't play songs from the share. I never had some many problem with Rythmbox 0.98 in Edgy. I guess I'll have to use banshee until someone can fix RB daap. :-(

---

