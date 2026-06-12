---
title: "MCE Remote partially working"
date: 2009-02-07
forum: Mythbuntu
---

### Post by twosticks on 2009-02-07
The remote that came with my Dvico tuner didn't work very well so I purchased an Anywhere-branded MCE remote. I set it up in mythtv control center (Mythbuntu 8.10) as a new type MCE remote and at first it seemed to be working fine. I can see the remote presses by cat-ing /dev/lirc0 and looks to be working flawlessly outside of mythtv, however in mythtv I can only execute some limited number of button presses before it stops responding. If I wait I can later execute more button presses but the number that will succeed depends on how long I wait. It's like a queue of some kind is filling up and I have to wait for them to expire or something. I have a wireless keyboard that will continue to work correctly through all this, so it's definitely remote related.

Any ideas?

---

### Post by twosticks on 2009-02-08
I haven't solved this just yet but I've made a little progress. I was able to recreate the weird intermittent behavior outside of mythtv with irw, which makes this a little more straight forward to troubleshoot. I think the problem is with the receiver more than the remote. The receiver that came with the remote is an Anyware HA-IR01SV. I'm hoping I can tweak the settings in lircd.conf but I haven't had a chance to try it out. There's some vaguely relevant info in the troubleshooting section on mce remotes in the mythtv wiki [http://www.mythtv.org/wiki/MCE_Remote#Troubleshooting]("http://www.mythtv.org/wiki/MCE_Remote#Troubleshooting") so I'll see if that gets me anywhere when I can get back to it.

---

