---
title: "amarok collection builder trouble!"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by Titi on 2007-01-31
hi,
when i want to build my music collection in amarok, it always gets stuck around 45%, and after a while it get's stuck at 72% it just won't get any further. so i thought it might have been the m4a files, so converted them all to mp3, but it was still the same. anyone any ideas? all the files (including the m4a's) play in amarok. it doesnt't matter if there are jpg files in the folders i add does it? 
i have absolutely no idea.

---

### Post by Archmage on 2007-01-31
How long did you wait? I need more than one hour to update my collection. So I expect that it will take even longer for build a new collection.

---

### Post by Uncle Spellbinder on 2007-01-31
@ Titi

How many files do you have to build your collection? I have Amarok 1.4.3, and 45,500+ mp3's. It took about 1 hour 40 minutes to initially build the collection for me. It stopped at about 40% for around 10 minutes and 80% for around 10 minutes. Eventually, everything was added fine.

---

### Post by Titi on 2007-01-31
it's about 20 GB. it stopped at 45% for about an hour now...
then when i play a random file, it jumps to 72% and then it's stuck there. 
isn't there a way to add files manually? or to have files i play automatically added? then eventually all files should get there :)
i'm using Listen for now, but i don't like the shuffle function. it shows which is next. i don't want to know that!
amarok seems really interesting, but i need to have all my songs in the collection...

---

### Post by Uncle Spellbinder on 2007-01-31
My collection is about 300 GB.  I found that attempting to play anything while it's loadind/building your collection just screws things up.  Let it finish before you play anything. 

You can assign folders/files as your collection by clicking *settings > configure amarok > collections*.

---

### Post by Titi on 2007-01-31
ok, i tried once more, doing nothing while it was busy, but it still doesn't seem to work. i'm quite desperate. i really like the program. could it help to reinstall? i'll try it anyway..
thanks for the tips though :)

---

### Post by chronic88 on 2007-06-07
I'm having the same problem... except at 5% with myql. I Tried the default SQLite database and it stopped as well at 8%... i've left it running uninterupted for an entire day and got nothing...

I recently installed MySQL Administrator which allows me to monitor connection traffic in specific databases (in this case my amarok database)... when collection building does work for the first 4% a spike in activity is shown (from 2% before it starts to 98% on the graph) but when it hits 5% connection traffic falls back to 2% as it was before amarok was even open indicating to me that amaroks interaction with the MySQL database is just cut off when it hits 5% collection built...

anyone have any ideas on why this would happen?

---

### Post by stfu on 2007-06-15
> **chronic88 said:**
> I'm having the same problem... except at 5% with myql. I Tried the default SQLite database and it stopped as well at 8%... i've left it running uninterupted for an entire day and got nothing...

I recently installed MySQL Administrator which allows me to monitor connection traffic in specific databases (in this case my amarok database)... when collection building does work for the first 4% a spike in activity is shown (from 2% before it starts to 98% on the graph) but when it hits 5% connection traffic falls back to 2% as it was before amarok was even open indicating to me that amaroks interaction with the MySQL database is just cut off when it hits 5% collection built...

anyone have any ideas on why this would happen?

I have similiar problem, SQLite and MySQL both stop after a short while. I'm guessing it might be because of special characters in filenames?

---

### Post by stfu on 2007-06-15
> **stfu said:**
> I have similiar problem, SQLite and MySQL both stop after a short while. I'm guessing it might be because of special characters in filenames?

It seems I forgot the to tag the recursive directory search. Oops :D

---

### Post by IcarusR on 2007-06-17
I have a similar problem. Amarok gets to 80% scanning my collection then stops giving me an error message
'Sorry, the Collection Scan was aborted, since too many problems were encountered.
Advice: A common source for this problem is a broken 'TagLib' package on your computer. Replacing this package may help fixing the issue.
The following files caused problems:'

I have reinstalled TagLib, which makes no difference.


My collection contains 312 albums with 4609 songs & is on a SAMBA  share mounted as cifs. 
Used to work OK but has started doing this in the last couple of weeks.
Always the same tracks that give problems. If I move the guilty tracks then it will stop at other tracks in the same albums. 
The problem albums are not all recent additions, some  have been in my collection since I sarted using Amarok

---

