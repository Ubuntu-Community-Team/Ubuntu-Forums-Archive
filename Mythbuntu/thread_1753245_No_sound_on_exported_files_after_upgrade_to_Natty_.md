---
title: "No sound on exported files after upgrade to Natty (mythexport)"
date: 2011-05-08
forum: Mythbuntu
---

### Post by lingenfr on 2011-05-08
I upgraded my backend to Natty. Since then, my exported recordings (using Mythexport) have no sound.

My mythexport log has the following error:

Unknown encoder 'libfaac'

I assume that is the source of the problem. I reenabled medibuntu and did an update/upgrade. I got a few new libs but no 'aac'. What do I need to do to get my sound back. My recorded files have sound, just not the exported ones. Thanks.

SOLUTION: For me the problem seems to have been that my upgrade to natty did not complete. After reading another post, I tried:

sudo apt-get dist-upgrade -s

to simulate a distribution upgrade. That showed that one file had failed to upgrade (a codecs file) and that seemed to be the problem. I did a:

sudo apt-get dist-upgrade

and now everything seems to be working properly.

---

### Post by rhpot1991 on 2011-05-09
Make sure you have medibuntu enabled, and then upgrade after that, to make sure you have all the ffmpeg bits from medibuntu.  I have verified that aac (-acodec libfaac) works fine from there with natty.

---

### Post by lingenfr on 2011-05-24
See the first post for my solution.

---

