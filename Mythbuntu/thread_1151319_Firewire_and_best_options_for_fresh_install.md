---
title: "Firewire and best options for fresh install"
date: 2009-05-06
forum: Mythbuntu
---

### Post by Saxomophone on 2009-05-06
I had previously tinkered with mythbuntu, I had previously gotten my stb to prime via firewire, but never took it any further. Summer is coming, and since I'm a teacher, I'll have time to tinker. I'm planning on doing a fresh install with the newest mythbuntu version. I read in the release notes that it's easier to set up multiple partitions, as I do have a 500 gig hdd i'd like to use exclusively for storing recorded video.

My questions: For those more experienced, any tips I should keep in mind when doing a fresh install? STB is a  scientific atlanta 4250 HD, video card is geforce 8800 gts

Also, what is the current state of stb firewire user friendliness? As I said, I had gotten it to prime in terminal, but never got around to getting it working within the program itself.

---

### Post by Saxomophone on 2009-05-11
Bump.

---

### Post by 4dognight on 2009-05-11
I assume you have 2 hard drives.
Put / and swap on one,  and /var/lib/mythtv/recordings on the 500gb. Use XFS for the recordings.

Your video card should be capable of VDPAU, I have heard it cam help for playback to reduce cpu load. 

I use firewire for my stb, but they are a different model than yours. It works without problems for me.

---

