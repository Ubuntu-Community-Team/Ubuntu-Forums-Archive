---
title: "Missing MythTV menu items"
date: 2009-03-14
forum: Multimedia Software
---

### Post by RobertSwipe on 2009-03-14
I've managed to mess up my MythTV setup.

It all started when I was trying to create a DVD from two TV recordings, and got an error message telling me about a missing encoder 'mpeg2video'.

Various other posts suggested I needed to download and build my own ffmpeg and x264. I did that, but then got slightly more alarming messages about missing codecs (or similar).

So I removed my new ffmpeg and x264, and I *think* I've now reverted to the originals.

However, half my menus are now missing from MythTV. The "CD/DVD" menu has gone, so I can no longer archive to DVD. The Information Center has lost all the things like "Weather" and now only has "Setup" in it.

How can I recover all my menu options again? I've tried to install things again:
sudo apt-get remove mytharchive-data
sudu apt-get install mytharchive-data

All to no avail.

Any clues?

Thanks!

---

