---
title: "DVD Ripping Issue (rar-2.80)"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by whoopn on 2007-08-09
Ok so I am using (or trying to) DVDrip and here is what I get when I do a check:

```
 
Default DVD device: /dev/scd0 exists : Ok
Default data base directory: /media/disk writable : Ok
Default directory for .rip project files: /media/disk/dvdrip-data writable : Ok
Preferred language: not tested : Ok
------------------------------------------------------------------------------------------------------------------------
DVD player command: /usr/bin/mplayer executable : Ok
File player command: /usr/bin/mplayer executable : Ok
STDIN player command: /usr/bin/xine executable : Ok
rar command (for vobsub compression): rar-2.80 not found : NOT Ok
------------------------------------------------------------------------------------------------------------------------
Start cluster control daemon locally: not tested : Ok
Hostname of server with daemon: not tested : Ok
TCP port number of daemon: 28646 is numeric : Ok
------------------------------------------------------------------------------------------------------------------------
Default video codec: not tested : Ok
Default container format: not tested : Ok
OGG file extension: not tested : Ok
Default BPP value: not tested : Ok
Grab subtitles while ripping: not tested : Ok
Workaround transcode NPTL bugs: not tested : Ok
Set LD_ASSUME_KERNEL to: not tested : Ok

```

So the rar command (is that like winrar? or something else?) "rar-2.80" can't be found...

How do I fix this?

Thanks!

---

### Post by nickmcg on 2007-08-20
Hi,

Edit->Preferences and change the command line from rar-2.80 to rar

This gets rid of that error, but I still can't rip a DVD

Nick

---

### Post by Amazona aestiva on 2007-08-22
Here is it, and change back rar to rar-2.80.
And should see my signature!

---

### Post by nickmcg on 2007-08-22
> **Amazona aestiva said:**
> Here is it, and change back rar to rar-2.80.
And should see my signature!

Great tip/howto - thanks

Nick

---

### Post by ricardisimo on 2007-09-20
Amazona, the uploaded file (rar-2.80) appears to have been replaced with a generic attachment marker (attachment.php). Could someone re-attach the file. Thanks.

---

### Post by ricardisimo on 2007-09-20
Never mind... I just renamed it "rar-2.80_2.80-2_i386.deb" and that did the trick. Thanks.

---

### Post by Jungliztik on 2007-12-17
I've managed to get DVD::rip working fine for both my 32-bit boxes but the 64-bit system won't install **rar-2.80** and all the references I can see for it are all i386.deb's.

Anyone know where I can find the 64-bit version?  I want to get my server up and running with Myth before Christmas, so I need DVD::rip to get all my films on there to keep the family quiet!

TIA.
Dave.

---

