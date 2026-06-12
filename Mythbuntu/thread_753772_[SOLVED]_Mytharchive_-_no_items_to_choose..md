---
title: "[SOLVED] Mytharchive - no items to choose."
date: 2008-04-13
forum: Mythbuntu
---

### Post by chaumurky on 2008-04-13
After following the menus I get as far as the "Select Archive Items" page but there are no items there to select!

The first field has "Show Items |X|" but nothing beside or below it.
The second field is empty.
Then the usual suspects at the bottom - "Cancel", "Previous" and "Next".

I know I have plenty of items - I can see them in Mythweb, Recordings Manager etc.

Any ideas?

---

### Post by agamotto on 2008-04-21
As stupid as this is going to sound, try going into the setup portion for MythArchive and make sure you have a working dir for the temporary files.  When I upgraded to 0.21, I had to go in and add '/tmp' to this before I could even get into the selection dialogue.   

I hope this helps.

---

### Post by chaumurky on 2008-04-23
In the setup I have:

"Myth Archive Temp Directory:" /media/data/.temp/
(this is set to 0777 and contains folders "config", "logs" and "work" created by MythArchive it seems.

"Myth Archive Share Directory:" /usr/share/mythtv/mytharchive/

I'm using mythconverg from Gutsy imported into Hardy - I wonder if that has anything to do with it. I found this post:
[http://mysettopbox.tv/phpBB2/viewtopic.php?t=15163&](http://mysettopbox.tv/phpBB2/viewtopic.php?t=15163&)

I might look into deleting and resetting the tables mentioned there.

*get's out mysql handbook*

---

### Post by Ubeast on 2008-04-23
OMG I think I know what the answer to this problem is. Hope I'm right because that would be the first time I've ever helped someone else on here hehe.

You don't mention what version of Mythtv you are running, but I had this problem with 0.21 (Hardy beta) and solved it. For me it was theme related. The theme you are using may not be correctly written to display the new layout in mytharchive. On the Select Archive Items screen you should have 6 buttons:
Add Recording, Add Video, Add File, Cancel, Previous, Next. If you are missing the 'Add' buttons, try using a new theme. In 0.21 neon-wide works fine (first one I tried and the buttons appeared).

FYI I had been using this theme: [http://miffteevee.co.uk/themes/metallurgy.html](http://miffteevee.co.uk/themes/metallurgy.html) which is really awesome but obviously missing a couple of things. No updates since Jan.

---

### Post by chaumurky on 2008-04-23
OK, Lemme check - I'm using the Glass theme...




brb...



:D

---

### Post by chaumurky on 2008-04-23
Well how about that! You nailed it! I never would have thought of that you know - a stoopid skinning issue! I now have "Add Recording" Add Video" and "Add File" options and I can go forward and clear my harddrive. Thank you so very much for that. You've made my day.

:guitar:

---

### Post by entourage on 2008-06-12
Thanks for the fix!  This also worked for me.  I had been using the Glass-Wide theme and for the life of me couldn't figure out why I wasn't seeing any of my recordings!

---

