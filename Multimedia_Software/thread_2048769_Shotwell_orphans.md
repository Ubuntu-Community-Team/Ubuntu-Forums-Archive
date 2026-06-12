---
title: "Shotwell orphans"
date: 2012-08-27
forum: Multimedia Software
---

### Post by Anonymousable on 2012-08-27
I've written a little (very quick-n-dirty) script that outputs a list of files found in shotwell's image directory that aren't mentioned in shotwell's database (or are simply inaccessible via shotwell's UI, which is the case for images that have been deleted from shotwell's trash without getting sent to the desktop trash).

[http://paste.ubuntu.com/1169596/](http://paste.ubuntu.com/1169596/)

To use:
1. Follow the link above
2. Select and copy the code
3. Open a text editor
4. Paste the code
5. Save it as shotwell_orphans.py for instance
6. Open a terminal
7. Run find /home/Pictures/20?? > /tmp/files (assuming you have no photos from before 2000 and in shotwell you're using one of the Year/ directory structures)
8. Run my script

It could do with some more work, and I plan to make it a bit neater in future, but I've put it here already in hopes that someone else will find it useful.

---

