---
title: "Clean old 'previously recorded' from DB?"
date: 2009-02-28
forum: Mythbuntu
---

### Post by SiHa on 2009-02-28
I'm sure I've read it somewhere, but can't seem to find it.

I'm running the **optimize_mythdb.pl** weekly, but I'd like to remove or at least reduce the list of previous recordings from the database. Is there a script somewhere to do this? (as my mySQL expertise is nil!)

TIA,

Simon

---

### Post by SiHa on 2009-03-10
What, really? I thought it would be a fairly common requirement. 
Oh well, guess I'm going to have to learn to play with SQL.](*,)

---

### Post by toorima on 2009-03-10
Why do you want to clean out previously recorded? it is only used for scheduling to make sure not to rerecord a rerun, but if you want to clean it out you can use phpmyadmin and the database is mythconverg and table is oldrecorded

---

### Post by SiHa on 2009-03-11
Good question.
My backend has recently started to drop out for no good reason. I've sucessfully added a 'Myth-Watch' script at startup (Thanks Ian Dobson) to restart it whewn it falls over, but I'd like to understand why it's stopping, or at least stop it happening.
As there is a large amount of data in 'oldrecorded' that has to be searched every time a new recording is scheduled, it occurred to me that it may be this that occasionally causes these dropouts. I think I read this theory on this forum somewhere once as well.
Anyway, thanks for the advice, I'll have a look if I manage to get half an hour at the weekend.

---

### Post by toorima on 2009-03-11
You might not have to use mysql for this, if I remember correctly you can delete previously recorded shows from manage recordings in the front end.

---

### Post by SiHa on 2009-03-11
Yes you can, but only one at a time, I've got 9 months worth of recordings. At about three button presses for each one with the usual slight delay in remote response, I reckon it'd take about a week and I'd have RSI of the thumb by the time I'd finished!
Unless I'm missing some magic 'Delete All' option???
Cheers anyway.

---

