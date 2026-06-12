---
title: "[SOLVED] No Sound in Ubuntu! (Did have when first installed OSS)"
date: 2008-11-06
forum: Multimedia Software
---

### Post by Trifid on 2008-11-06
I installed OSS following this guide: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Which worked perfectly until I restarted where I ended up not having sound any more. If I enter Sound in preferences I get this error:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

I tried to follow the guide through again and ended up with another error on volume control:

> No volume control GStreamer plugins and/or devices found.

This error resolved its self after a restart but I still have the same problem as above. And am now stuck.

Can anyone share some pointers here?

Many thanks.

---

### Post by alikas on 2008-11-06
Try 
 **sudo dpkg-reconfigure linux-sound-base**
:)

---

### Post by Trifid on 2008-11-06
Is this keeping the OSS sound drivers? ALsa doesn't appear too happy with my M-audio 2496.

---

### Post by Trifid on 2008-11-06
> **alikas said:**
> Try 
 **sudo dpkg-reconfigure linux-sound-base**
:)

That didn't fix it. It was part of the linked to guide, which I went through again when I realised there was a problem. 

Any other ideas?

Fixed it by reinstalling PulseAudio. (scratches head why it fixed it...)

---

