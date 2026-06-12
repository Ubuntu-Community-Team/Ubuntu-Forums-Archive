---
title: "How to record in &quot;Stereo Mix&quot; (Record what comes out of your speakers)"
date: 2010-05-28
forum: Multimedia Software
---

### Post by DodgeV83 on 2010-05-28
I found many threads on this, none with quite the answer I was looking for.  Everything was too long and complicated, I knew there had to be an easier way...and there was!

To get your recording software to record in "Stereo Mix" mode, to directly record what comes out of your speakers, follow the steps below.

1.  Click Applications -> Sound & Video -> PulseAudio Volume Control -> Recording tab.  It should now be blank, because no software is attempting to record anything.

2.  Start your recording software, I'm using RecordMyDesktop.

3.  The Recording tab should now be populated with your Recording software.

4.  Change the "Record From" to "Monitor of..."

It will now be recording from your speaker output.

[IMG]http://img44.imageshack.us/img44/8708/combinedp.png[/IMG]

Note: You may need to install the PulseAudio Volume Control, not sure if it comes default.

```
sudo apt-get install pavucontrol
```

Note 2:  I didn't have to change the recordmydesktop settings settings at all, I kept it at "DEFAULT".

[IMG]http://img412.imageshack.us/img412/8859/screenshotrecordmydeskt.png[/IMG]

Good luck!

---

