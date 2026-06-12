---
title: "patching and recompile mythtv ?"
date: 2007-12-26
forum: Mythbuntu
---

### Post by erland on 2007-12-26
I would like to apply some patches to the mythbackend, is there some easy way to recompile the mythtv package distributed with mythbuntu ?

I know I can probably recompile from svn source the standard way and run "make install" to install it, but I thought it would be better to patch and recompile the mythtv package distributed with mythbuntu to avoid conflicts with other parts of the mythbuntu software.

Will I get an exact copy of the standard mythtv package if I run the following ?
1. apt-get source mythtv
2. apt-get build-dep mythtv
3. dpkg-buildpackage

Or do I have to do something special to make sure mythtv is compiled in the same way with the same flags as the standard Mythbuntu mythtv package ?

---

### Post by superm1 on 2007-12-26
> **erland said:**
> I would like to apply some patches to the mythbackend, is there some easy way to recompile the mythtv package distributed with mythbuntu ?

I know I can probably recompile from svn source the standard way and run "make install" to install it, but I thought it would be better to patch and recompile the mythtv package distributed with mythbuntu to avoid conflicts with other parts of the mythbuntu software.

Will I get an exact copy of the standard mythtv package if I run the following ?
1. apt-get source mythtv
2. apt-get build-dep mythtv
3. dpkg-buildpackage

Or do I have to do something special to make sure mythtv is compiled in the same way with the same flags as the standard Mythbuntu mythtv package ?
That should work for you (other than the fact that you will have a lot of build dependencies on the box).
If these patches aren't "urgent", but would be beneficial to have in the official packages: we can add them to the weekly mythtv package builds.

If they are only applicable to yourself and a few others (and damaging to have in the builds for other people), then do it that way.

---

### Post by erland on 2007-12-26
> **superm1 said:**
> 
If these patches aren't "urgent", but would be beneficial to have in the official packages: we can add them to the weekly mythtv package builds.

If they are only applicable to yourself and a few others (and damaging to have in the builds for other people), then do it that way.
I'm intrerested in the patches required to get MythTV with a Nexus CA DVB-C card to work together with sasc-ng.

The patches can be found here:
[http://opensvn.csie.org/myth_dvb_ng/20-FIXES/3_NEXUS/](http://opensvn.csie.org/myth_dvb_ng/20-FIXES/3_NEXUS/)

Some more information in this readme:
[http://opensvn.csie.org/myth_dvb_ng/README](http://opensvn.csie.org/myth_dvb_ng/README)
And on this wiki page:
[https://opensvn.csie.org/traccgi/sascng/wiki/Ubuntubuild](https://opensvn.csie.org/traccgi/sascng/wiki/Ubuntubuild)

If appling these nexus patches to the standard distribution, you should probably also consider applying the rest of the patches in the myth_dvb_ng package:
[http://opensvn.csie.org/myth_dvb_ng](http://opensvn.csie.org/myth_dvb_ng)

If it was possible to apply this to the standard distribution, it would be great, however I also realize that the MythTV community has tried not to integrate sasc patches previously so I guess the same reasoning might apply to sasc-ng patches. As I understand it sasc-ng normally doesn't need MythTV to be patched for most DVB cards.

---

### Post by superm1 on 2007-12-26
> **erland said:**
> I'm intrerested in the patches required to get MythTV with a Nexus CA DVB-C card to work together with sasc-ng.

The patches can be found here:
[http://opensvn.csie.org/myth_dvb_ng/20-FIXES/3_NEXUS/](http://opensvn.csie.org/myth_dvb_ng/20-FIXES/3_NEXUS/)

Some more information in this readme:
[http://opensvn.csie.org/myth_dvb_ng/README](http://opensvn.csie.org/myth_dvb_ng/README)
And on this wiki page:
[https://opensvn.csie.org/traccgi/sascng/wiki/Ubuntubuild](https://opensvn.csie.org/traccgi/sascng/wiki/Ubuntubuild)

If appling these nexus patches to the standard distribution, you should probably also consider applying the rest of the patches in the myth_dvb_ng package:
[http://opensvn.csie.org/myth_dvb_ng](http://opensvn.csie.org/myth_dvb_ng)

If it was possible to apply this to the standard distribution, it would be great, however I also realize that the MythTV community has tried not to integrate sasc patches previously so I guess the same reasoning might apply to sasc-ng patches. As I understand it sasc-ng normally doesn't need MythTV to be patched for most DVB cards.
I suspected sasc-ng.  Unfortunately this is one of those taboo topics.  Unless upstream (mythtv upstream) is willing to integrate it, we're avoiding it as well.

---

