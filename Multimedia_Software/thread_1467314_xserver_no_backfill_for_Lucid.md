---
title: "xserver no backfill for Lucid?"
date: 2010-04-30
forum: Multimedia Software
---

### Post by KrGAce on 2010-04-30
Hello All,

Have to say I am loving the new Ubuntu (Lucid), however I have the same problem I do every time I upgrade and that is the maximize/minimize delay in Firefox or any open window for that matter.  In the past I have installed a deb file called xserver-nobackfill and it fixes the problem, but I cannot find one for Lucid.  I try an older version and it tells me a newer version is already installed.  I know Lucid just came out yesterday, but I wondered if someone knew where to look, or something to try.

Many thanks in advance,

AceMan

---

### Post by jrichter on 2010-04-30
I am having the same problem, and the previous fixes worked for me as well.  

Dell Studio 1537 ATI Mobility Radeon 3450

---

### Post by jrichter on 2010-04-30
I found a thread that had a fix for the minimize/maximize problem.

[http://ubuntuforums.org/showthread.php?p=9207063#post9207063](http://ubuntuforums.org/showthread.php?p=9207063#post9207063)

You just need to enable Direct2D

sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE

---

### Post by Yellow Pasque on 2010-04-30
[http://www.phoronix.com/forums/showthread.php?t=21846](http://www.phoronix.com/forums/showthread.php?t=21846)

---

### Post by KrGAce on 2010-04-30
Thanks to all for the responses.  The new ppa for the no backfill worked for me after a reboot.


Thanks again,


AceMan

---

### Post by obiwankamote on 2010-05-03
> **jrichter said:**
> I found a thread that had a fix for the minimize/maximize problem.

[http://ubuntuforums.org/showthread.php?p=9207063#post9207063](http://ubuntuforums.org/showthread.php?p=9207063#post9207063)

You just need to enable Direct2D

sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE

This worked for me :) Thanks!!

---

### Post by sirlatrom on 2010-05-21
Yessssssssss, finally!!

```
sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE
```

worked for me too :)

---

### Post by stevenmansour on 2010-05-26
+1 Worked for me on Lenovo T500 with Radeon 3650 - thanks!

---

### Post by hojjat on 2011-04-18
When I try
```
sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE
``` on Lucid, I get the following error message:

```
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
aticonfig: parsing the command-line failed.

```

Running sudo aticonfig --initall gives me this:
```

Found fglrx primary device section
 Unable to find any supported Screen sections

```

What can I do?

---

### Post by Yellow Pasque on 2011-04-18
Back up your old xorg.conf and create a new one.
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo aticonfig --initial -f
```
Log out and back in to restart with new xorg.conf

---

### Post by hojjat on 2011-04-18
Awesome! Thank you.

---

### Post by hojjat on 2011-04-19
Ever since I did this change, some Wine-based applications (such as Microsoft Word) are looking weird. Can you please tell me how to undo this modification?

---

### Post by alphacrucis2 on 2011-04-19
The backfill/backclear patches shouldn't be needed with recent Catalyst versions. Maybe the Catalyst version in the Lucid repos is too old. I would install the latest Cat 11.3 from AMD which is what I use on MM. (Actually Cat 11.4 should be out fairly soon)

---

### Post by hojjat on 2011-04-20
POST UPDATED:

Excellent point. I downloaded ATI Catalyst 11.3 from [AMD](http://support.amd.com/us/gpudownload/Pages/index.aspx) and then followed the instructions on [this HowTo](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), and now I don't have any of the problems I previously had.

Thank you very much.

---

