---
title: "gnomebaker DVD+rw help"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by carverj on 2007-02-01
Hi all,
         Am trying to burn over some data. Firstly, I try to format the DVD using Gnomebaker.
it says complete after a few seconds, but it hasn't actually wiped any data.
Secondly, when trying to burn over the existing data I get the following error:-

```
WARNING: /dev/hdb already carries isofs!
About to execute 'mkisofs -gui -V GnomeBaker data disk -A GnomeBaker -p Jeremy Carver -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-jeremy/gnomebaker-P92INT | builtin_dd of=/dev/hdb obs=32k seek=0'
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
Using Assignment2000.doc;1 for  /Assignment2.doc (Assignment2.doc)
Using Assignment2001.doc;1 for  /Assignment2.doc (Assignment2.doc)
Using Tasksheet1sess7000.doc;1 for  /Tasksheet1sess7.doc (Tasksheet1sess7.doc)
Using Network_Security_Risk_As000.doc;1 for  /Network Security Risk Assessment.doc (Network Security Risk Assessment.doc)
Using Network_Security_Risk_An000.ppt;1 for  /Network_Security_Risk_Analysis.ppt (Network_Security_Risk_Analysis.ppt)
Using Activity_1000.ppt;1 for  /Activity 1.ppt (Activity 1.ppt)
Using Activity1_session3000.doc;1 for  /Activity1 session3.doc (Activity1 session3.doc)
Using ITB007_Assignment1_Minutes000.d;1 for  /ITB007_Assignment1_Minutes09.08.06.doc (ITB007_Assignment1_Minutes07.08.2006.doc)
Using ITB007_Assignment1_Minutes001.d;1 for  /ITB007_Assignment1_Minutes07.08.2006.doc (ITB007_Assignment1_Minutes04.08.2006.doc)
Using ROOM_FOR_RENT000.doc;1 for  /ROOM FOR RENT.doc (ROOM FOR RENT.doc)
Using droppenguins1000.jpg;1 for  /droppenguins1.jpg (droppenguins1.jpg)
mkisofs: Error: '/home/jeremy/hdb1_bak/qut 06/sda1/oop/Sudoku/FInal/Assignment2.doc' and '/home/jeremy/hdb1_bak/qut 06/sda1/oop/Sudoku/Assignment2/Assignment2.doc' have the same Rock Ridge name 'Assignment2.doc'.
mkisofs: Error: '/home/jeremy/hdb1_bak/qut 06/sda1/oop/Assignment2.doc' and '/home/jeremy/hdb1_bak/qut 06/sda1/oop/Sudoku/FInal/Assignment2.doc' have the same Rock Ridge name 'Assignment2.doc'.
mkisofs: Error: '/home/jeremy/hb6_bak/tafebackup/tafesem2/Security cluster/Network_Security_Risk_Analysis.ppt' and '/home/jeremy/hb6_bak/tafebackup/tafesem2/Security cluster/Network_Security_Risk_Analysis.ppt' have the same Rock Ridge name 'Network_Security_Risk_Analysis.ppt'.
mkisofs: Error: '/home/jeremy/hb6_bak/tafebackup/tafesem2/Security cluster/Network Security Risk Assessment.doc' and '/home/jeremy/hb6_bak/tafebackup/tafesem2/Security cluster/Network Security Risk Assessment.doc' have the same Rock Ridge name 'Network Security Risk Assessment.doc'.
mkisofs: Error: '/home/jeremy/hb6_bak/tafebackup/tafesem2/Security cluster/Tasksheet1sess7.doc' and '/home/jeremy/hb6_bak/tafebackup/tafesem2/Security cluster/Tasksheet1sess7.doc' have the same Rock Ridge name 'Tasksheet1sess7.doc'.
mkisofs: Error: '/home/jeremy/hb6_bak/tafebackup/tafesem2/Security cluster/Activity1 session3.doc' and '/home/jeremy/hb6_bak/tafebackup/tafesem2/Security cluster/Activity1 session3.doc' have the same Rock Ridge name 'Activity1 session3.doc'.
mkisofs: Error: '/home/jeremy/hb6_bak/tafebackup/tafesem2/Security cluster/Activity 1.ppt' and '/home/jeremy/hb6_bak/tafebackup/tafesem2/Security cluster/Activity 1.ppt' have the same Rock Ridge name 'Activity 1.ppt'.
mkisofs: Error: '/home/jeremy/hb6_bak/QUT/ROOM FOR RENT.doc' and '/home/jeremy/hb6_bak/ROOM FOR RENT.doc' have the same Rock Ridge name 'ROOM FOR RENT.doc'.
mkisofs: Error: '/home/jeremy/hb6_bak/tafebackup/droppenguins1.jpg' and '/home/jeremy/hb6_bak/droppenguins1.jpg' have the same Rock Ridge name 'droppenguins1.jpg'.
mkisofs: Unable to sort directory 
:-( write failed: Input/output error

```

Have tried to erase files on already on DVD with terminal to no avail.
Also looked into growisofs command, but have already condensed all the data I want saved into a gnomebaker file!
Can anyone offer any assistance? Would greatly appreciate it!

---

### Post by carverj on 2007-02-01
Tried to burn to completely blank dvd to same effect! Any clues?

---

