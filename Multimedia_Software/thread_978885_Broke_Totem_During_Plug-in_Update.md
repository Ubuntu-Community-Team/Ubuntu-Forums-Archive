---
title: "Broke Totem During Plug-in Update"
date: 2008-11-11
forum: Multimedia Software
---

### Post by Rulls on 2008-11-11
On first-time insertion of a commercial DVD movie, Totem presents the dialogue offering to search for plug-ins to play the media.  Two entries were located.  I checked both and clicked update.  The process appeared to run to completion, then the entire Totem window shaded gray, and never returned to normal.  Totem was not responding, and I force closed.

After reboot and multiple attempts to restart Totem and play DVD media, Totem behavior has alternated between gray-shaded "not responding" and a message that indicates unauthorized DVD access.  Totem still functions for playback of certain other video media.

How can I back out the latest changes and restore Totem to its state prior to the plug-in download process?  It does not appear that install of the plug-ins was completed (the only two plug-ins indicated as active on the plug-in configuration panel are BBC and YouTube), but something was definitely downloaded and Totem behavior is definitely changed from time of initial DVD movie insert.  I haven't been able to determine the change history (not yet fully familiar with the admin. tools).

Thank you in advance for your assistance.

(Running fresh install of Intrepid, x86-64).

---

### Post by Rulls on 2008-11-11
Perhaps a more important question:
Has anyone been able to play standard commercial DVD movies using Totem?

---

### Post by gandaran on 2008-11-11
> **Rulls said:**
> Perhaps a more important question:
Has anyone been able to play standard commercial DVD movies using Totem?
yes, install the ubuntu-restricted-extras package, and add the medibuntu repository to synaptic [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
then install **libdvdcss2**, this is needed for drm protected dvd play

---

