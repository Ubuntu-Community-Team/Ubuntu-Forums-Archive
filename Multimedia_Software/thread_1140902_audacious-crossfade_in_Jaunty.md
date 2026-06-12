---
title: "audacious-crossfade in Jaunty"
date: 2009-04-28
forum: Multimedia Software
---

### Post by Jose Catre-Vandis on 2009-04-28
This still works in Jaunty, but you may have to use OSS?

[http://ubuntuforums.org/showpost.php?p=4402878&postcount=14](http://ubuntuforums.org/showpost.php?p=4402878&postcount=14)

Also found a link to a rebuild that runs ALSA

[https://bugs.launchpad.net/ubuntu/+source/xmms-crossfade/+bug/208666/comments/32](https://bugs.launchpad.net/ubuntu/+source/xmms-crossfade/+bug/208666/comments/32)

---

### Post by lunatico on 2009-07-31
So I'm using Audacious because I have a bluetooth headset and with Audacious it is so easy to configure and it works perfect.
I would like to get crossfade to work.
I don't see crossfade anywhere in the plugins, I use ALSA because that's the way to get it working as you can see [here]("http://wiki.bluez.org/wiki/HOWTO/AudioDevices").
Any ideas?

---

### Post by Jose Catre-Vandis on 2009-08-01
Not sure I can help with this one, as I have no experience with bluetooth headsets. However, the crossfade plugin appears to be quite specific about its needs!

Does crossfade work for you through normal speakers / headphones?

If so, its a bluetooth quirk that stops it running through your headset.

If not, I suggest you getting working through normal sound routes then move on to your headset issue.

---

### Post by Jose Catre-Vandis on 2009-09-05
UPDATE:

Just checked the audacious website, they are on version 2.1 !! So I downloaded the tarballs and compiled from source. As I watched the compile I noticed "crossfade". And yes, they have now included it in the main plugin set, so no more conflicts. We'll see how this one gets on with pulse audio trying to run everything :)

EDIT:
However, on testing, it doesn't seem to work properly

---

