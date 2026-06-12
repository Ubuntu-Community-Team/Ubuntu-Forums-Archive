---
title: "DVD Back up question"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by bennyj on 2007-07-14
Could someone please tell me the difference between using lets say dvdshrink  and lets say ripping the dvd with mencoder then using dvdauthor to make back up copies.The reason i ask is I am a little confused by all the different options available. I have successfully used dvdshirink to make back up copies and now am trying to do it with mencoder and then dvdauthor. Is their any difference in quality between the two? I can make a backup copy with dvdshrink in about an hour. I am currently using mencoder to rip from the DVD and it is going on dang near 4 hours and still ripping.Please tell me I will notice a huge diffence with menu coder due the length of time it has taken.Or is it worth it. Some clarification please.

Also once I am done ripping the dvd with mencoder into and .avi am i going to have to multiplex it then use dvdauthor? What is the sequence of events that needs to take place here...I.e..rip to avi....remux....dvdauthor...burn with growisosfs...watch movie. I have read so many diff how to's that im am totaly confuse as to exactly what is to happen.

Thanks

---

### Post by arcticFire on 2007-07-25
That sounds like a lot of work...

I found the fastest, easiest way to back up my DVDs was doing the following:

Install k9copy
-----------------
Open a terminal and type in: sudo apt-get install k9copy.

Backup DVD
----------------
0 - Put in your DVD that you want backed up / copied
1 - Open k9copy
2 - Click File --> Open
3 - Check the uppermost box on left hand side of the TITLE window so that all boxes on tree are selected.
4 - Checked the lower righthand box 'Keep original menus' 
5- Ensure Output device is the same as your DVDRW Input device 
6 - Click DVD Copy.
7 - Go and make a cup of coffee.
8 - After about 20 mins it pops the DVD out, replace this with blank DVD disk  
9 - When finished - about another 20 mins - eject it and go and play DVD on normal DVD player.....

Hope this helps. Gotta be easier than the above.....

---

