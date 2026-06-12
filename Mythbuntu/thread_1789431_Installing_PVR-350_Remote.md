---
title: "Installing PVR-350 Remote"
date: 2011-06-23
forum: Mythbuntu
---

### Post by windom on 2011-06-23
I have used MythTV for several years using KnoppMyth and LinHes. Circumstances have led me to change to another distro so I installed Mythbuntu 11.04. My question is straightforward. How to I get my Hauppauge PVR350's remote to work? I have worked through the guts of Myth quite a bit over the years and thought I was quite familiar with lirc but this has kicked my butt. From what I can tell there have been kernel/modules/lirc changes that have made lirc a brand new game and the more I google the more confused I get. I have yet to find a definitive authority on what's going on in 11.04. Help is needed. I have tried various combinations of modules to no avail.

windom

---

### Post by windom on 2011-06-25
Well I have most of this figured out finally. Not having a job let me put in the many hours I've spent chasing this down. This problem is due to another "let's change everything about this part of linux" situation. I understand why it was done, and it will be good for the future, but in the meantime the MythTV part of my life has been a living hell. Because so much changed, what I knew about lirc and remotes mostly no longer applies. This situation reminds me the more recent grub 1 to 2 version change, or, going back several years, the Red Hat libc fiasco. Hmmm... that was around RH5 in the late 90s (I'm guessing). I lived to tell about those problems so I know I will eventually make my way through this.

Anyways, if one has this problem, the first read should be this to get the background on the situation: [http://wilsonet.com/?page_id=95]("http://wilsonet.com/?page_id=95")

Next, follow the guide here [http://www.mythtv.org/wiki/LIRC]("http://www.mythtv.org/wiki/LIRC") and/or here [http://parker1.co.uk/mythtv_ubuntu2.php]("http://parker1.co.uk/mythtv_ubuntu2.php")

This thread is also good for more background: [http://www.gossamer-threads.com/lists/mythtv/users/470918?do=post_view_threaded#470918]("http://www.gossamer-threads.com/lists/mythtv/users/470918?do=post_view_threaded#470918")

Also an install of ir-keytable will be needed (covered in the above links). Use the google to get some background on the utility. Because there evidently has been a problem since 10.04 there is a lot of noise out there about fixing this problem so just follow the 11.04 guides and don't get sidetracked by the old info like I did for days. For more help, try Jarod (the guy from wilson.net above and main dialog person in the gossamer-threads topic). He appears to be very approachable on the subject even though he has written the howto on the mythtv wiki.

My remote is working now. However, it still needs some fine-tuning since the signals are going out too fast and a cursor move only hits every other menu item. 

My hope is that this thread will save people the time I wasted figuring this out. Also, I should mention that this is for the A415-HPG remote aka as grey or silver or new.

Now on to getting my blaster working.

WINdom

---

