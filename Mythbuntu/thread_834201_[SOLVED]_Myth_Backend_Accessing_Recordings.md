---
title: "[SOLVED] Myth Backend Accessing Recordings"
date: 2008-06-19
forum: Mythbuntu
---

### Post by lantern on 2008-06-19
HI all, 

Long time reader, first post.

I have a funky problem which i hope is due to me not setting up something.

I have a Mybuntu machine which serves as both back and front end. All works fantastically, (BTW i love mythbuntu).
The problem is that when i record a show the show records fine but it is not accessible through the Watch recording menu. It is not accessible at all through Myth on the main unit. I can browse to it via the file system and play it in another player, and heres the Kicker, IT IS AVAILABLE through any another laptop/pc using myth web. I can play it not a problem. But i cannot play it through mythtv on the front/backend server.

Does anyone have an idea, is there a recording group that i should be looking at ( i did create a new one for the weekly recordings).

All Help is appreciated.

Thanks
Lantern 
Ps: the recordings are advert flagged but not transcoded.

---

### Post by klc5555 on 2008-06-19
If you made this new recording directory as root (using "sudo"), then the owners, groups, and permissions are likely not set up properly.

Do a "ls -l" from a terminal for the directory under which your recordings directory is a subdirectory. If it lists the owner and group of the recordings directory as "root", then do a chown and a chgrp of this directory in each case to "mythtv".

The permissions of this directory may also not be right. chmod 755 should set these up OK. (Some people prefer setting them up at 775)

Thereafter, everything ought to be accessible from the front end.

Cheers! :)

---

### Post by freymann on 2008-06-19
> **lantern said:**
> 
The problem is that when i record a show the show records fine but it is not accessible through the Watch recording menu. It is not accessible at all through Myth on the main unit. 


 What happens when you call up the menu (press "M" on your keyboard or the green media button your MCE remote)?

 There are 'filters' in place that let you pick Recorded Shows, LiveTV and then categories.

 You may just have to adjust the filter so you can view the programs you're after..

---

### Post by lantern on 2008-06-19
Thankyou for the quick replies. I am afraid I have use the wrong terminology in my orig post.
I had created my own categories through the myth (8.04) setup menus. I have created a category called weekly which should hold the weekly episodes. It may do but I cannot access through watch recordings.

When I press 'm' I get a menu for adjusting/turn on different functionality.

I will try the replies suggestions when I get home after work. If there are any more ideas I'd love to hear them


Thanks

Lantern

---

### Post by freymann on 2008-06-19
> **lantern said:**
> 
I had created my own categories through the myth (8.04) setup menus. I have created a category called weekly which should hold the weekly episodes. It may do but I cannot access through watch recordings.

 I guess we need to know exactly what screen you're on when you think you can't access the new categories...

 I'm thinking when you're on the Recordings screen... on that screen you can adjust the filters to show you Recorded/LiveTV/Categories. By default it only shows Recorded shows.... to see LiveTV and Recorded shows you have to adjust the filters.... the large green button on the MCE remote usually brings up that window, or I believe the M key on the menu.

 That's what I'm thinking of.. if that doesn't bring up what you're after than what I'm thinking isn't your answer.

---

### Post by lantern on 2008-06-20
A lesson in RTFM.....

You are right - i needed to push M in the recording list to select the category, this is what i was missing.

Much appreciated your quick and accurate replies.

Thanks

All good now.

---

### Post by freymann on 2008-06-20
> **lantern said:**
> 
You are right - i needed to push M in the recording list to select the category, this is what i was missing.


 Excellent. And to be correct (I tried it this morning)...

 You can press "M" on the keyboard

 or the "OK" button on the MCE Remote (not the green media button)

 Glad to help! Enjoy!

---

