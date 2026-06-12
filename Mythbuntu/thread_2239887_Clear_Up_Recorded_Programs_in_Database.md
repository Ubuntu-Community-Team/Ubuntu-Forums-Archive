---
title: "Clear Up Recorded Programs in Database"
date: 2014-08-16
forum: Mythbuntu
---

### Post by johnvic on 2014-08-16
I am not a MySQL expert or even amateur. So my question may be basic. I have a mythbuntu backend and am using an xbmc cmyth frontend. That works fairly well, clunky at times, but works. I have mythbuntu 14.04, release .27. During the period of me trying different antennas and settings I managed to have 4 recorded programs where I deleted the actual recording but the database still thinks they are there. If I try to delete it through the web interface it won't delete, I think because it cannot find the actual files. I currently have no recorded shows, there is nothing to save. 

Is there a way to clear out the recorded programs list? Like I said, I have no programs recorded that I need to keep, just these 4 "empty" listings.

Thanks!

---

### Post by Lester_Burnham on 2014-08-16
Hi,
You need to download find_orphans.py and run it.
Make the file executable and run it in a terminal.
python find_orphans.py
Lester

http://www.mythtv.org/wiki/Find_orphans.py

---

### Post by diyhouse on 2014-08-18
Hi just a little precaution before you start,.. Backup you Database first!!!

find_orphans.py works well and I have used it several times,.. for similar reasons to yourself,.. but I have experienced problems where it has corrupted the database,.. not a big deal with a "young database",.. but a real pain with a mature database with many previous recordings listed in the dup. recordings stuff.  (and NO backup), 

and BTW,.. re-running find_orphans.py on my restored database then worked without issue,.. so just one of those things...

---

### Post by johnvic on 2014-08-19
Thanks to both of you. Yes, I have backed up the database. I made a copy of find_orphans.py. I wasn't sure where to put it so I put it in the /usr/bin directory. I did a chown to root:root and chmod to 755. Was that correct? How do I make it executable?

---

### Post by johnvic on 2014-08-19
I found an ubuntu thread about making a python script executable. So I had already chmod to 755. I left the bang statement as it was, that didn't work. I also tried changing the band to #! /usr/bin/python.

When I try to run it from the /usr/bin directory, I get an error.

 > ./find_orphans.py
bash: ./find_orphans.py: /usr/bin/python^M: bad interpreter: No such file or directory


Any suggestions?

---

### Post by Gillingham on 2014-08-19
Hi a quick google search for "/usr/bin/python^M: bad interpreter: No such file or directory" suggests that the problem may be the ^M, which is a different end of line character. Rather than using "/usr/bin/python" it is looking for "/usr/bin/python" there are a variety of solutions suggested pick the one you like best.

---

### Post by johnvic on 2014-08-19
Thanks. I installed dos2unix and that allowed me to run it. Then I found another syntax problem which I think must have been a copy and paste problem. The good news is I learned a lot, remade the file and it erased the phantom recordings!

---

