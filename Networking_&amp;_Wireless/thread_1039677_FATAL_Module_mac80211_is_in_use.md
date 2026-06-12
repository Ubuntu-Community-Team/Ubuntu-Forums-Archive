---
title: "FATAL: Module mac80211 is in use"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by sp0nge on 2009-01-14
](*,):frown: ](*,)

The wireless on this laptop has become the bane of my existence. I've just settled into using the wireless on a regular basis, never mind the fact that I have to load the drivers each time- Im just happy it worked. Anyway, I fire it up when I got home this evening, and as it attempted to connect to my home network (which has happened just this morning and all was well, the info saved), I was advised of the need for the network key, which was already input and correct.

So I unloaded the drivers and tried to load again to get the message you'll see in the title. I unloaded 2 times more and restarted with no changes, same message. I have found no good information on this online, please help me understand.

---

### Post by sp0nge on 2009-01-15
What a weird situation. 

After posting last night, I toyed with the drivers for a little longer before calling it a night. After all, 5:30am comes awfully early! Well after getting up this morning and playing with the dog I sat down to fire the laptop up again to see what the status was.. and wouldn't you know it fired right up and connected without issue!?!?!

Okay, so while this is technically solved, I want to let it linger a little longer in hopes someone more knowledgeable than I can educate me as to why this happened, and perhaps how to prevent this from happening again.

Thanks in advance for the input!

---

### Post by Ayuthia on 2009-01-15
If you get that message, it means that another module needs the mac80211 module for it to function so the system will not let you remove it.  You can see what module is using it by typing (in the Terminal):
```
lsmod|grep mac80211
```and it will show the name of the other module(s).  You will have to remove those modules before you can remove the mac80211.

---

