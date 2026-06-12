---
title: "Raise volume level up in each boot"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by Nighto on 2007-03-21
Hi,
i have an Acer TravelMate 2480-2551 running Ubuntu Feisty Fawn Herd 5 with 2.6.20.12-generic linux kernel, and i got some problems with my soundcard, which is the following:

```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

when I boot it, my volume levels come like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=27981&stc=1&d=1174511631[/IMG]

and i have to manually let it like this if i want to hear something:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=27982&stc=1&d=1174511732[/IMG]

the alterations in the sound level are not persistent to reboot. what can i do?

---

### Post by yabbadabbadont on 2007-03-21
Adjust the volumes to your preferred settings.  Open a terminal window.  Run "sudo alsactl store".  That should do the trick.

---

### Post by Nighto on 2007-03-21
> **yabbadabbadont said:**
> Adjust the volumes to your preferred settings.  Open a terminal window.  Run "sudo alsactl store".  That should do the trick.

It didn't works :(

anything else i can try? i'm wondering if this is related to the driver...

---

