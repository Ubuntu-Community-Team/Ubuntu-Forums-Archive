---
title: "Network Directory auto-mount and sync"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by erikdstock on 2011-03-28
Hi everybody- I'm wondering if any of the following is possible:

a)automatically mounting my shared home directory from my mac when it is accessible. I feel like i did this in the past, but then ditched my laptop and had no more ubuntu. (accessible could mean when I am on my home network, when it is there, whatever)

b)automatically syncing this directory with my ubuntu home directory when i am at home, perhaps using Unison? This would obviously be preferable.

For the record I am on 10.10.

---

### Post by Bufke on 2011-03-28
a) Look up pam_mount.
b) God I wish this were easy to do. Unison would do it but isn't automatic, it could be scripted. ifolder does this more automatically, but is a burden to set up. I assume you want something more like Dropbox but locally run? Sparkle share would do this but isn't done yet. 
If you don't mind using a hosted solution Dropbox or Ubuntu One is the way to go. Ubuntu One can sync any folder, but is buggy. Dropbox IMO is far better, but you have to fight with sym links to get it syncing your entire home folder (I would recommend not the entire home, just pick what's important).

---

### Post by erikdstock on 2011-03-28
Thanks for the reply. I use dropbox (chose it over ubuntuone for lack of mac support, but i might switch in the future).

The issue is that I'm not looking to back up all my music for a subscription fee right now. 

It would be nice if a cloud like UbuntuOne would recognize your home network and trigger some kind of sync between comps without using the cloud for things like your music library... In the mean time, I guess I will look in to that pam_mount.

---

