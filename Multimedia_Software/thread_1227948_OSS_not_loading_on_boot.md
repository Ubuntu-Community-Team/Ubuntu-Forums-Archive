---
title: "OSS not loading on boot?"
date: 2009-07-31
forum: Multimedia Software
---

### Post by litlfrog on 2009-07-31
About one time out of three, I get absolutely no sound when Ubuntu starts. No sound files or CD will play, none of the test sounds will play when I go to Sound Preferences. I've been using OSS because it gives me much better sound quality than the default sound app. If I reboot, things usually come back fine. Is there a way to get the sound to work without rebooting the computer?

---

### Post by martinbaselier on 2009-07-31
Are the drivers loaded?

**lsmod | grep oss**

**sudo service oss restart**
will restart just oss.

---

