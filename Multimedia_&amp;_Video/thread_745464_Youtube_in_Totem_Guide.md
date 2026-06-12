---
title: "Youtube in Totem Guide?"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by Tyler H on 2008-04-04
Can someone post a quick guide on the Totem Youtube plugin?

I've searched around and have yet to come up with anything, or even find the plugin itself.

---

### Post by FleetAdmiral74 on 2008-04-04
Have you followed instructions found at the [top google result]("http://tecnocode.co.uk/2007/10/12/totem-youtube-plugin/") for "Totem Youtube plugin"?

---

### Post by Tyler H on 2008-04-04
Well to some extent. Is SVN Totem some special release that I need to download?

---

### Post by Tyler H on 2008-04-04
Ok well I've converted the totem-youtube.rpm plugin for fedora to a deb and installed it, however I'm not able to enable the plugin. It installed with no fusses.

---

### Post by DrBob on 2008-04-17
> **Tyler H said:**
> Ok well I've converted the totem-youtube.rpm plugin for fedora to a deb and installed it, however I'm not able to enable the plugin. It installed with no fusses.

You probably don't have the right Python packages installed. You need the python-gdata package, for example.

It would've been better if you'd used the Totem 2.22.1.1 package from Hardy, or waited until Hardy's released, but you should be able to get it working without.

---

