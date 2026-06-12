---
title: "Newbie upgrades to .24, fails"
date: 2010-12-15
forum: Mythbuntu
---

### Post by Psyael on 2010-12-15
I attempted to add the upgrade PPA and do an Upgrade Manager update today. I saw in a previous thread someone saw what I saw, that it suggested a Partial Upgrade, and after they did it everything worked fine.

Well, I did it and everything didn't work fine. I'm getting a message about the FE not seeing the BE. I know there's threads on this, can't understand all of it. I've tried marking upgrade packages in Synaptic after reading an earlier thread and nothing happened. In another post, a '*sudo aptitude safe-upgrade*' command was suggested but I'm told by the Terminal that aptitude is an invalid command.

Please help. I know this is not the first thread on this issue but I've literally begun using Linux about three weeks ago. I'm a quick learner (I had Myth almost working twice so far : ), but the discussions so far are a little above my experience level.

---

### Post by thatguruguy on 2010-12-15
> **Psyael said:**
> I attempted to add the upgrade PPA and do an Upgrade Manager update today. I saw in a previous thread someone saw what I saw, that it suggested a Partial Upgrade, and after they did it everything worked fine.

Please look again at whichever thread you're talking about.  I would be stunned that someone did a partial upgrade and everything worked fine.  My guess is, that person wanted to know how to get the complete upgrade.  

Are you using a tv tuner card?  If so, which one?

If you go to synaptic and do a search on "Myth", it will list all packages associated with mythtv.  If you then click the "Mark all upgrades" button, it will tell you which packages are causing conflicts, and which packages can't be upgraded.  Do that and come back to this thread, and we'll go through the next steps.

---

### Post by Psyael on 2010-12-16
Thank you for replying.

I have an HD Homerun (two tuners) via antenna and analog cable using a Hauppage HVR-1800 (still haven't figured out how to get it to work right yet, though.)

I decided to go ahead and reformat and do the updates through Synaptic. If it bombs tomorrow then I will come back.

---

### Post by kratz13 on 2010-12-16
I just solved a similar problem with my setup.   On mine, I haven't gotten a tuner card yet. I upgraded from .23 to .24 and was getting the error that front-end could not connect to the back-end. From my web searching, it was because of the new requirement for a tuner card. I had to create a test card (using a mpeg file), but I was still stumped.   What I had to do was set up my channel (video) source, I used "no grabber", and then go to input connections to tie the card to video source... mine had not been set before, once that was done, it worked.  So check all you backend setup, items 2, 3, and 4 on the menu.  Hope that helps..

---

### Post by Psyael on 2010-12-17
I have to say I'm having a few problems:

1) I've put some TV shows in var/mythtv/video so that MythVideo will recognize and play them, but nothing I seem to do gets artwork and metadata for these files. Did the .24 upgrade break Jamu?

2) I installed the frontend on my Ubuntu box to connect, but it's .23, and once I tried to connect I got an incorrect database version error. So I uninstalled, then installed the myth-updates repos from Mythbuntu on my box and it installed mythtv-frontend and updated mythlib. Upon starting the .24 mythtv-frontend on Ubuntu the pea green background appears and before it can ask me my language it turns to grey and crashes.

Help, Mr. Wizard! :) A lot of interface bugs in mythtv-setup are graciously fixed in .24 but between all the problems I'm having and their wrapping the OSD into themes, I'm almost thinking of wiping everything *again* and just sticking with .23's bugs until Mythbuntu releases a new distro, perhaps alongside Natty or something. But I'd like to work things out if at all possible.

---

