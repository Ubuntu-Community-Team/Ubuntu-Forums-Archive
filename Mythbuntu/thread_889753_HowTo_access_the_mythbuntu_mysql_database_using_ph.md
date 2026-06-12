---
title: "HowTo access the mythbuntu mysql database using phymyadmin"
date: 2008-08-14
forum: Mythbuntu
---

### Post by LarryJ2 on 2008-08-14
I've been tryng to determine why my irblaster channel changing perl script is not called.  Finally I saw a post that suggested the problem was in the database. Consequently, I needed to get into the database.  Here's how I gained access to the database though my firefox browser using phymyadmin

1. First (***Important***) make a copy of your mythbuntu database.
```
myth@mythtv~$ *** REMOVED *** 
```

2. If for some reason, your mucking about in this database destroys your mythbuntu install (easily possible!), then return here and run this line ***to restore your original*** mythconverg mythbuntu mysql database. FYI, mythconverg  is the filename but the database is known to mysql as mythconverg. Also after you have restored your original mythconverg file, a reboot is probably required.
```
myth@mythtv:~$ *** REMOVED ***
```

3. Install php5 and phymyadmin. php5 is a server-side (operates within the html server apache) interpreted HTML scripting language and phpmyadmin is a php5 script program that allows you to browse mysql databases, create copy or rename tables and databases and do table maintenance.
```
sudo apt-get install phpmyadmin php5
```

3.5 Next, you should see a screen text (curses) menu asking what server you want to configure. Move your cursor over to the [ ] by apache2  and hit the space bar.  The selection should look like this: **[*] apache2**  Then tab down to OK and hit Enter.

3.6 If for some reason, you don't see the screen titled "configuring phpmyadmin" with the text menu, try the command below,  then go back to step 3 above.  Be aware that this will affect other possible configurations of phpmyadmin.  That shouldn't be a problem in mythbuntu, as far as I know.
```
sudo apt-get purge phpmyadmin php5
```

4. To access mythtv's mysql database, you need it's name, the mysql username, and the mysql database password.  The password and username you need are found in Mythfrontend setup.So start mythtv frontend  navigate to Utilites/setup->Setup->General then on the page titled  **Database Configuration 1/2** write down the database name, user name, and password.  These should be something like mythconverg, mythtv, and n8zByLc8. That password is typically so obscure you may want to print the page.  8's look like Bs etc.
This information is also contained in the file **/etc/mythtv/mysql.txt**


5. On your mythTV box, in your firefox browser url window, enter
```
http://localhost/phpmyadmin/index.php
```
If that doesn't work, try
```
http://127.0.1.1/phpmyadmin/index.php
```
Similarly this maybe worth a try
```
http://127.0.0.1/phpmyadmin/index.php
```

6. You should see a ***Welcome to phpMyAdmin*** page prompting for a username and password. Enter the username and password you obtained in step 4 above.

7. You should next see phpMyAdmin's splash screen.  The left panel should show something like 
> * information_schema (17)
* mythconverg (82)

Please select a database

8. In the right panel, under the heading **localhost**, click **databases** then click **mythconverg**

9. Now you can begin mucking about.  Just remember if your mythbuntu installation crashes,  open a terminal and enter the command in step 2 above.  But I know you are going to muck about so "Muck On" For example,  under the heading "Table", find the row "channel", move across in this row to the first tool bar icon that prompts "browse".  click on the browse icon.

10. The attachement (chanelTable.png) below shows a portion of my channel table.  Here's where I think I discovered why my irBlaster script was not being called.  All the dishnetwork satellite delivered channels (cspan, cnn etc) are on card 3 (composite in)  not source id 2.

Have fun!

Larry:popcorn:

---

### Post by LarryJ2 on 2008-08-16
Alas and alack!  Nothings apparently wrong in the database.  SourceID 2 is dishNet programs for which I have a separate SchedulesDirect lineup.  Source ID2 is the local OTA ATSC channels, again on a separate schedules direct lineup.   There are three cards in the box,  AirToPC is #1,  KWorld110 ATSC tuner is #2 and the composite in of the KWorld110 is #3.

To illustrate what comes out of phpMyAdmin, I've attached partial screen snaps of four of the  mythbox's database.

---

### Post by wbrokow1 on 2009-12-24
Ok, thanks.

---

### Post by 4romany on 2010-02-28
Just tried this on the latest Mythbuntu with autobuild enabled...worked great...I had this working on a previous myth installation long ago but had not gave the cycles to see about getting it to work.    Couple of comments:

When you are backing up your mythconverg directory I think you need a "cp -a" to do that instead of only "cp"...

For the password to access the DB I had to use the "root" password for mysql...that may have been what you meant...I tried using "mysql" which had read/write privs to mythconverg and it did not work...

Thanks again....

---

### Post by nickrout on 2010-02-28
> **LarryJ2 said:**
> I've been tryng to determine why my irblaster channel changing perl script is not called.  Finally I saw a post that suggested the problem was in the database. Consequently, I needed to get into the database.  Here's how I gained access to the database though my firefox browser using phymyadmin

1. First (***Important***) make a copy of your mythbuntu database.
```
myth@mythtv~$ *** REMOVED *** 
```


Wrong wrong wrong, that is NOT the way to backup your database.

See here: [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

### Post by tgm4883 on 2010-02-28
Yes, that is a very bad way to backup/restore the DB. Please review the page in Nickrout's post.

Also, you shouldn't need to edit the database directly for what you are trying to accomplish. Please use mythtv-setup instead. Sounds like your system was improperly set up.

---

### Post by superm1 on 2010-02-28
Here's some better directions on how to do the backup and restore of a database:

[http://mythbuntu.org/upgrading](http://mythbuntu.org/upgrading)

---

