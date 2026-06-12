---
title: "Getting remote frontend to remember the password?"
date: 2010-07-10
forum: Mythbuntu
---

### Post by GuiGuy on 2010-07-10
I have a frontend running on a client PC (Lucid). Everytime I start it up I need to type in the mysql password. ie the displayed dbpassword is incorrect. Oddly the IP address and all other details are correct and persistent. 

The password entered in /home/<user>/.mythtv/config.xml is correct.
The password entered in /etc/mythtv/config.xml is correct.
The password entered in /etc/mythtv/mysql.txt is correct.

What else needs to be checked/ configured?


T.I.A.

Cheers

---

### Post by ian dobson on 2010-07-10
Hi,

Just check that all copies of mysql.txt and config.xml have the same/correct information. 

To find where copies of the files are hiding use "updatedb" to rebuild the file list then "locate <FILENAME>" to list them.


Regards
Ian Dobson

---

### Post by GuiGuy on 2010-07-10
> **ian dobson said:**
> 
To find where copies of the files are hiding use "updatedb" to rebuild the file list then "locate <FILENAME>" to list them.


Thanks Ian, but I had no luck with that. I'm now running a grep search for the incorrect password that's being thrown up. It may take a while... <sigh>

---

### Post by GuiGuy on 2010-07-10
Found the problem.

It was between the back of my chair and the keyboard. :redface:

(Had entered two different passwords in the mysql.txt file :(

---

