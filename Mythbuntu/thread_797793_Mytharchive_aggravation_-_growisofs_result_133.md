---
title: "Mytharchive aggravation - growisofs result 133"
date: 2008-05-17
forum: Mythbuntu
---

### Post by agamotto on 2008-05-17
:confused:  I have been searching the forums for my situation, and can't find anything that seems to be it.  I upgraded to Mythbuntu 8.04, and everything was fine until late last week, when I tried to put some programs onto a disc for a friend.  When running Mytharchive, I keep getting a growisofs message/error 133 at the very end of the process.  I have tried four search engines, these forums, and can't find anything in syntax I understand as to what message/error 133 is about.  I have found things about .py scripts, missing /tmp directories and such, but nothing that clearly states a problem/connection with message/error 133. 

Any clues?  I really don't want to lose three weeks of stuff to go back to 7.10 to 'fix' it.

---

### Post by drick55 on 2008-05-19
Hi agamotto, have you had any luck sorting this out, I am having the same problem, and this thread you posted is the only reference I can find on this problem.

---

### Post by agamotto on 2008-05-19
Not so far, but I figure I will give it until Sunday, copy my recordings over to another hd, wipe, install 7.10, and not update anything to .21 until I hear about what causes this.

I have confirmed that it is trying to write to the correct drive, and that the files are not corrupted, but I have no clue where to go from here...

---

### Post by agamotto on 2008-05-23
Hmmm, nothing.  Oh well, back to 7.10  I don't think I am going to bother with anything .21 again... I don't mind things occasionally screwing up due to my monkeying around, but when I upgrade and lose features, not my cup of tea. 

Thanks to everyone who tried to help me with this!

---

### Post by agamotto on 2008-05-27
Well, over the long weekend I went back to 7.10.  I can now burn my DVDs, and oddly enough, some of the streams in Mythstream now work when they didn't under 8.04, all with the same hardware.  Go figure

---

### Post by adz_c on 2008-06-01
Having a similar issue since upgrading to 8.04 

I think my problem is related to missing quotes from the growisofs command which are required when the title name has spaces or funny characters:
[FONT="Courier New"]
[COLOR="Blue"]ERROR: Failed while running growisofs.
Result 133, Command was: growisofs -dvd-compat  -use-the-force-luke -Z /dev/scd0 -dvd-video -V **Property Ladder** /media/storage/mythtv/mytharchive/work/dvd[/COLOR][/FONT]

Command should read:

[FONT="Courier New"][COLOR="Blue"]growisofs -dvd-compat  -use-the-force-luke -Z /dev/scd0 -dvd-video -V **"Property Ladder"** /media/storage/mythtv/mytharchive/work/dvd[/COLOR][/FONT]

But I can't figure out how to alter the command??

Any ideas?

---

### Post by agamotto on 2008-06-03
Hmmm, that gives at least a clue as to what the problem is/could be.  Any python experts out there who know how to check the script for sytax errors?

---

### Post by adz_c on 2008-06-06
This is so frustrating because I have every other part running perfectly !!!

I would love to be able to just archive stuff I've recorded also sometimes your friends miss something and you can just burn them an episode...

Well I won't be looking into this for a while as I have a new flat which needs a lot of work on it (including networking for mythbuntu network ;)

Do let me know if you come up with a fix!

---

