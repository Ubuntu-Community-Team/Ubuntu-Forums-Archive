---
title: "[SOLVED] rhythmbox database - where do I find it?"
date: 2008-05-01
forum: Multimedia Software
---

### Post by mtbsoft on 2008-05-01
I'm currently testing Hardy on my laptop which has Gutsy installed in a separate partition.

I was editing the Hardy fstab to copy the partition data from my Gutsy fstab and unfortunately included my /home partition - when I next booted Hardy it used the Gutsy /home partition which, amongst other things, fired up rhythmbox.

When I went back to Gutsy I got the message... 

"Could not load the music database

The database was created by a later version of rhythmbox.  
This version of rhythmbox cannot read the database."

While the loss of the database itself is minor (the music is all intact, just a couple of feed to reinstate) I now cannot run rhythmbox and am cautious of doing a full uninstall and reinstall in case I do lose something of value.

Does anyone know how I can reset the database back to a Gutsy version or even just delete it - I presume it would then recreate correctly.

---

### Post by mtbsoft on 2008-05-04
Noone got any idea?  A reinstallation didn't do it.

---

### Post by mtbsoft on 2008-05-05
Eventually found the file at /.gnome2/rhythmbox/rhythmbox.xml

The Gutsy version of the file is named rhythmdb.xml and has a 1.3 version tag inside, whereas the Hardy version has a 1.4 tag.

There are only a couple of extra tags visible per entry on first examination and I found that a simple edit (1.4 -> 1.3) and a rename was all that was required to restore the database, podcasts included.

Hope this helps someone.

---

### Post by aw76 on 2008-11-16
Im getting the same error on my system...im running 8.04, and am a newbie, so didnt understand how you fixed it with that file or whatever.

anyone able to help me solve this problem...

much appreciated...
s

---

### Post by mtbsoft on 2008-11-16
Make a back up copy first (please) then edit the file ~/.gnome2/rhythmbox/rhythmbox.xml - make sure rhythmbox is not running.

The second line should be something like...
```
<rhythmdb version="1.6">
```

You need to change the 1.6 (or whatever) to the correct version number for your version of Rhythmbox.  My educated guesses (NOTE: Guess only) would be 1.4 for Hardy and 1.3 for Gutsy.

You could also try renaming the rhythmbox.xml file to something else, fire up rhythmbox and let it recreate the file then use the info. from the newly created file to repair your existing one and finally put the old one back.  I don't know if this will work though as I haven't tried it myself but I would expect it to.

Hope this helps.

---

### Post by omer.qadir on 2009-01-05
> **mtbsoft said:**
> Make a back up copy first (please) then edit the file ~/.gnome2/rhythmbox/rhythmbox.xml - make sure rhythmbox is not running.

The second line should be something like...
```
<rhythmdb version="1.6">
```

You need to change the 1.6 (or whatever) to the correct version number for your version of Rhythmbox.  My educated guesses (NOTE: Guess only) would be 1.4 for Hardy and 1.3 for Gutsy.

You could also try renaming the rhythmbox.xml file to something else, fire up rhythmbox and let it recreate the file then use the info. from the newly created file to repair your existing one and finally put the old one back.  I don't know if this will work though as I haven't tried it myself but I would expect it to.

Hope this helps.


excellent. Thanks !

---

### Post by jamesisin on 2009-01-05
Any idea what to do if RB stops automatically downloading track/album information?

---

### Post by jamesisin on 2009-01-05
Never mind.  RB has once again started downloading track listing information.  [shakes head]

---

### Post by relic70 on 2009-01-17
> **mtbsoft said:**
> Make a back up copy first (please) then edit the file ~/.gnome2/rhythmbox/rhythmbox.xml - make sure rhythmbox is not running.

The second line should be something like...
```
<rhythmdb version="1.6">
```

You need to change the 1.6 (or whatever) to the correct version number for your version of Rhythmbox.  My educated guesses (NOTE: Guess only) would be 1.4 for Hardy and 1.3 for Gutsy.

You could also try renaming the rhythmbox.xml file to something else, fire up rhythmbox and let it recreate the file then use the info. from the newly created file to repair your existing one and finally put the old one back.  I don't know if this will work though as I haven't tried it myself but I would expect it to.

Hope this helps.

Worked for me as I had an earlier install of Intrepid that I abandoned and found the .xml file for rhythmbox as Version 1.6. Changed to 1.4 for current Hardy install and no longer get the message.

Thanks for the info

---

### Post by volneilo on 2009-02-15
Thanks a lot, **mtbsoft**! I had exactly the same situation here as the one **relic70** mentioned above, but now everything is ok.
Thanks again for sharing your solution!

---

### Post by proycon on 2009-10-29
The file seems to be moved to ~/.local/share/rhythmbox/ on Jaunty and Karmic.

---

### Post by frogotronic on 2011-04-19
1.6 for Lucid

1.7 for Meerkat


- CH

---

