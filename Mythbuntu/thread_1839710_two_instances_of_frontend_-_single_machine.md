---
title: "two instances of frontend - single machine"
date: 2011-09-06
forum: Mythbuntu
---

### Post by kingmoffa on 2011-09-06
Hi, 

Im looking to run two instances of mythfrontend on a single machine. 

Its got a nvidia motherboard with HDMI , and a seperate nvidia graphics card also with hdmi. I think i've got X setup correctly with two different users. 

Trouble is mythfrontend segfaults when I try and run it twice under different users. 

Anyone have a similar setup? or any suggestions on howto resolve?

---

### Post by thatguruguy on 2011-09-06
I'm trying to understand your set up.  Are you running two monitors?

What's the reason for having two separate users running concurrently on the same front end box?

---

### Post by kingmoffa on 2011-09-12
Hi -  Yep two TVs connected each connected via HDMI. 

I want to use a single machine to save power (and time with booting up).

---

### Post by nickrout on 2011-09-13
Get the first user going then run the second one from the command line and see what error messages are spat out.

How is X configured? Maybe this will help? [http://www.mythtv.org/wiki/Running_MythTV_Dual_Headed](http://www.mythtv.org/wiki/Running_MythTV_Dual_Headed)

---

