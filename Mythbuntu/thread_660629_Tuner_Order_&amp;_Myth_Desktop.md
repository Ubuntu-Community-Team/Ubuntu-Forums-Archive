---
title: "Tuner Order &amp; Myth Desktop"
date: 2008-01-07
forum: Mythbuntu
---

### Post by hey_ygbsm on 2008-01-07
Happy New Year!  After a brief test drive of Hardy (My Firefox & OpenOffice apps would not launch from the icons) I decided to regress & reinstall the more stable Gutsy with Mythbuntu.  A couple of questions:

1 - I have an HDHomerun which works splendidly.  I also have a KWorld ATSC 115 installed.  Myth automatically starts with the analog Kworld tuner.  Is there a quick way I can change the default startup tuner source to the HDHomerun? I'd prefer to have HD first & analog as the lowest/last priority.

2 - Love the Mythbuntu capability, but, I'm not in love with the Mythbuntu desktop.  I'd like to keep my standard Ubuntu gnome desktop and have myth running in the background so I can switch quickly between web surfing and a football game, for example. Any ideas on how to accomplish this?

Thanks in advance for your assistance.

---

### Post by aaltieri on 2008-01-07
Greetings!

for issue 1:  Look at this page:

[http://www.mythtvtalk.com/forum/viewtopic.php?t=1604&highlight=tuner+order]("http://www.mythtvtalk.com/forum/viewtopic.php?t=1604&highlight=tuner+order")

I used phpmyadmin to do it, but the same thing.  I think that's a tad easier than trying to install them in a certain order.  Also, as has been noted, the record priority and the playback priority are not the same, so this shows you how to set that as well.


As to the second issue, two thoughts:

1 - I also run Mythfront end on my mac, and I have it set such that it only uses the top right corner of the screen, about a quarter of it.  Then I brows the web, or do whatever I need in the rest of the screen.

2 - I also had Ubuntu on a workstation for a short time for testing.  I ran Myth in one workspace, and then just hit the key sequence to move to my work in another workspace.  Just one bit of warning to you though.  The key sequence to switch windows was something like Lft-Ctr, Lft-Alt, lft/rt-arrow."  This key combination is also used in a few game emulators!  Made for some interesting MatMania pins, let me tell ya! ;-)


Have fun!

Anthony

---

### Post by hey_ygbsm on 2008-01-07
Many thanks aaltieri!  Exactly what I needed for the tuner priority for TV viewing.  I'll do this when I get home tonight and report back.

---

### Post by hey_ygbsm on 2008-01-07
Anthony,
   I loaded Hardy to attempt to have Ubuntu automatically recognize my KWorld 115, which it did.  However, as I said, I lost launch capability for for Firefox & all the OpenOffice apps. Unfortunately, it's taking me some time to regain my previous software load in Gutsy.  I really liked my desktop setup.  I had Myth video cropped to fit neatly into my Gutsy gnome desktop leaving the top & bottom taskbar panels exposed for easy access to all my often used launch icons.  It was pretty sweet. I could jump into my web browser during a football timeout or commercial...and ALT-Tab instantly back to the game when I heard the audio return to game action.  Your solution sounds very similar.

Pete

---

### Post by newlinux on 2008-01-07
If you have multiple backends and frontends the following link is important to know when setting up cardids, since how you do it could differ depending on whether or not you have the "Avoid Scheduling conflicts..." option set.

[http://www.mythtv.org/wiki/index.php/Frequently_Asked_Questions#Need_to_prioritise_cards.2Finputs_for_live_TV](http://www.mythtv.org/wiki/index.php/Frequently_Asked_Questions#Need_to_prioritise_cards.2Finputs_for_live_TV)

---

### Post by hey_ygbsm on 2008-01-08
I just have one front/backend.  I did the mythconverge database edit using mysql admin and it worked like a champ!  The link provided by aaltieri was most helpful. I now have my HDHomerun tuners setup as cardid 1&2, the KWorld digital as #3 and the Kworld analog tuner as #4. Very bueno. Thanks!! Now to onto restoring my old desktop settings....

---

### Post by hey_ygbsm on 2008-01-08
Life is good.  I logged out of Mythbuntu...changed session to Gnome desktop upon login and I'm back in business.  I have my spiffy Gnome desktop and all my tuners recognized and sorted correctly.  You guys rock! And so does the Ubuntu forums.  Appreciate the help.

PS - We might want to consider adding the tuner re-order procedure to the Myth tutorial...or make it a sticky perhaps.

---

