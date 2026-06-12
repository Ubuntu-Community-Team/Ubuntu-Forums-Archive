---
title: "THe new Compiz updated totallyed *ucked my compiz settings."
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by mindframe on 2007-11-25
Hello all,


I just installed the new copmiz update yesterday and i must say, it F*CKED my whole compiz configuration up. I hope some people have feedback. I managed to manually restore about 75% of my settings, This time I exported the settings incase the release engineers at Ubuntu decided to ignore things in the future or make changes.
I'll start from the top:

1. First thing I noticed after the upgrade is I have to click HARD on my mouse for it to do anything, say a web page submit button, or even a icon, I can no longer just c lick on it, I have to click and hold the left button for it to do anyting. LIke literally not just do a simple click, but hold down the button. This is annoying on a molecular level. I almost want to reinstall 7.10 because of this right here. It's almost like it ignores the first quick click.

2. The window shadows won't go away and I don't know how to configure them to stop!!! On the right of the window there's a very very thick opaque, mabye 40 pixels wide, dark bar going down the window. 

3. Yes I have reloaded compix with I think compiz --reload. THen proceeded to build my configuration from scratch.


This is extremely annoying for my personal desktop at home. I'm tempted to just say screw it and reinstall 7.10 but these same retarded features are probably already built into that release.


Has anyone else had problems related to 7.10 and the latest copmiz upgrade? It took me by surprise and now I feel like just going back to 7.10 and ignoring any compiz updates because it screwed my desktop envrionment up BIG TIME.


Thanks
Patrick McAndrew
CDI LLC/EMC INC

---

### Post by pjbgravely on 2007-11-25
The recent updates were from backports, which contains some risks. For me I finally have window decorations on my second screen, but the menus on screen 0 are still slow.

The best thing to do is disable backports in Software Sources, then go into Synaptic , search for compiz and reinstall everything relevant. You may have to flush your cache first but I don't think so. 

In the future, use the profile save feature in Advanced Desktop effects settings. If you don't have it get it from Synaptic too.  

Paul

---

### Post by mindframe on 2007-11-25
Also

My Function keybindings DO NOT WORK. ie in firefox, ctl-f4 DOES NOT CLOSE A TAB. and In Compiz Alt-F4 does not close a window.

Thanks
Patrick

---

### Post by mindframe on 2007-11-25
> **pjbgravely said:**
> The recent updates were from backports, which contains some risks. For me I finally have window decorations on my second screen, but the menus on screen 0 are still slow.

The best thing to do is disable backports in Software Sources, then go into Synaptic , search for compiz and reinstall everything relevant. You may have to flush your cache first but I don't think so. 

In the future, use the profile save feature in Advanced Desktop effects settings. If you don't have it get it from Synaptic too.  

Paul

Thanks Paul for your feedback, I'm going out for hte night, I will try this when I get home.

Cheers,

Patrick

---

### Post by ulisesrangel on 2007-11-26
how do you exported your compiz settings?

i was about to do a fresh install, but before i want to save my compiz configuration (i customize it a lot, with many made key bindings, and edges, cube, etc)
i test creating a new user, and trying to export from the old one to import in the new one, but not everything worked, only emerald can be exported/imported almost 100%, compiz not, only some settings.
try changing the flat or gconf in the options, but nothing worked, i ended up (by mistake) erasing the configuration a was trying to export.

also if someone can tell me how to export my panel configuration (i add some customized short cuts, app lanchers, etc)

---

### Post by pjbgravely on 2007-11-26
The export function of CCSM is in preferences. The only problem I see is that you have to add. ".profile" to the file name manually or it won't see the file to import it later.

As an alternative you can manually backup  the .gconf/apps/compiz folder.

For the Panel I would backup .gconf/apps/panel.

Of course daily backups is a should do for anyone experimenting a lot.

Paul

---

### Post by ulisesrangel on 2007-11-27
"As an alternative you can manually backup the .gconf/apps/compiz folder.
For the Panel I would backup .gconf/apps/panel."

i will try this, since the export function of CCSM, dont work for all settings (the animations work, but cube and scale dont, i just can live without scale anymore)

i grow up with the windows, format and reinstall very often, its form of life lol
let me see if i understand, if i copy all the files and directories from home, can i just copy this to a new user (or fresh install) without problems? even if is different name user, group or machine?
can make any conflict with firefox, gnome, etc?
can i bring back to life a bad script, spyware or anything bad if i do this to a fresh install? or are just settings?

thx Paul

============================================
sorry for my english, not my native language.
sorry for basic question, im new in linux,

---

### Post by pjbgravely on 2007-12-15
> **ulisesrangel said:**
> "
let me see if i understand, if i copy all the files and directories from home, can i just copy this to a new user (or fresh install) without problems? even if is different name user, group or machine?
can make any conflict with firefox, gnome, etc?
can i bring back to life a bad script, spyware or anything bad if i do this to a fresh install? or are just settings?


I have transfered the same home directory from many different flavors of Linux. Each time all my settings, Thunderbird mail and Firefox folder continued to be the same. You will probably get errors and won't be able to login. To fix for K/Ubuntu just alt/ctrl/F1 then login and type sudo chown -R yourname.yourname /home/yourname  Just make sure yourname is the same as the name you logged in with. Then  alt/ctrl/F7 and alt/ctrl/backspace ( to restart the login program) and try to login again. 

If you managed to pick up any spyware running Linux then that will be transfered with your homefile. So far I have not heard of any.

Paul

---

