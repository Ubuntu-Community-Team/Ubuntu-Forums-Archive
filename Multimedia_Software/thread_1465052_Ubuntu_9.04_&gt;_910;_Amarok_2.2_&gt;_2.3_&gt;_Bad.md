---
title: "Ubuntu 9.04 &gt; 910; Amarok 2.2 &gt; 2.3 &gt; Bad Video"
date: 2010-04-29
forum: Multimedia Software
---

### Post by davexnet on 2010-04-29
Hello,
upgraded my dist from Ubuntu 9.04 to 9.10.  Just did it today.
When the system was up an running I tested a few apps I had installed,
there wasn't that many.  "Movie Player" was playing OK, but Amarok had
no audio.  I couldn't get Amarok to work, so I upgraded it from
2.2 > 2.3 via the PPA.  Amarok is working now.

Now Movie Player is showing the color all distorted in xvid avi and
mpeg-1 files.  Here's a screen print.  ANy idea's about this?
Thanks for any info.

[[IMG]http://img269.imageshack.us/img269/9684/screenshotdrwhobbcbreak.png[/IMG]](http://img269.imageshack.us/i/screenshotdrwhobbcbreak.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by davexnet on 2010-04-29
It has something to do with the Nvidia driver.
I opened System/Administration/Hardware Drivers.

Driver version 185 was recommended and installed.  There was an
alternative, version 173.  I dropped back to this older version,
rebooted and problem is resolved.

I wonder if it's something that went screwy during the
distribution update?  Anyway, I'm going to put back the 
recommended driver and see if it's fixed now.

---

### Post by davexnet on 2010-04-29
Switching back to the more recent driver and the problem returned.

Any idea how to troubleshoot ?
TIA for any info.

---

### Post by davexnet on 2010-04-29
This was resolved by resetting the movie players display 
in the preferences.

---

