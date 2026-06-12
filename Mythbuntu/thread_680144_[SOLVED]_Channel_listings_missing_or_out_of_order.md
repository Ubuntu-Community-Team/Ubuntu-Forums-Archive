---
title: "[SOLVED] Channel listings missing or out of order"
date: 2008-01-27
forum: Mythbuntu
---

### Post by lingenfr on 2008-01-27
I spent a few hours sorting out a problem with my EPG today. I expect it is not uncommon, so I thought that I would go ahead and post the solution.

Symptom: Program listings are off by two (or some number) of channels and a few (either at the beginning or end) are missing.

Solution: 

1) **THIS STEP WILL DELETE ALL YOUR CHANNELS. ONCE THEY ARE GONE YOU CAN'T TUNE TO THEM UNTIL YOU RELOAD THEM.** Use mythweb and go to settings (wrench and key icon at top) > mythtv channel info and check all the delete boxes and hit save to delete all your channels.

2) Then log in to one of your backends (I used my slave, but should be any unless you have set up multiple listing sources) and run mythtv-setup. Go to Inputs. Select your TV input and you will notice that you no longer have channels. Click the button to fetch listings from your source (don't scan for them unless you really like typing). Make sure it is starting on the appropriate channel and that it is set to bcast/cable etc as appropriate for your method, then finish and get out of mythtv-setup.

3) Run mythfilldatabase --refresh-all

You should be good to go. I put the warning up so that you make sure that others using your frontends know that when the channels are deleted, they are not available until you reload them in step 2. I ran mythtv-setup on my slave backend and my family watched tv (same channel) throughout the whole operation without disruption.

---

### Post by mjezell on 2008-01-30
Nice solution, I need to look at mythweb more closely,  I've ran into the same problem but solved it in a little different fashion.  For those folks familiar with phpmyadmin you can empty the channel table and reload from mythtv-setup as you described. :)

---

