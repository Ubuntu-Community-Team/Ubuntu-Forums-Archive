---
title: "Have I destroyed Mythnews?"
date: 2010-08-29
forum: Mythbuntu
---

### Post by axelsvag on 2010-08-29
I had a very bad order in my rss-feeds in Mythnews. So I tried this advice to make a clean start
 " Purging Feed Data

The feeds you choose during setup are stored in the "newssites" table of the mythconverg database. The article information is stored in the home directory of the user who runs mythfronted in this directory:

    *

      ~/.mythtv/MythNews/

To purge MythNews data and cached articles:

   1.

      Drop the newssites table. From the Backend machine:
          *

            $ mysql -u root -p
            mysql> DROP TABLE mythconverg.newssites;
            mysql> exit

   2.

      Delete cached articles. From the Frontend machine:
          *

            $ cd ~/.mythtv/MythNews
            $ rm *

   3.

      Start the mythfrontend and navigate to Utilities/Setup --> Setup --> Info Center Settings --> News Settings and select the feeds you would like to read. 



But now when I try to choose a new rss site I am unble to choose anything. The boxes are still empty after I hit the enter key. And the same with the remote. is there a fix or do I have to make a fresh install. i got mythbuntu 10.04 with 0.23 autobuild enabled.

---

### Post by axelsvag on 2010-09-11
bump

---

### Post by axelsvag on 2010-09-12
I understand that my problem seems to be unique. Could one solution be to rebuild the database, because the install and uninstall of mythnews did not work.,or should I try to do something through synaptic?

---

### Post by smarttowers on 2010-09-16
Don't know if it could be related but I'm having a problem with the web browser in mythfrontend crashing when I try to go to the news article or try to open a web page. mythbuntu 10.04 clean install.

[http://ubuntuforums.org/showthread.php?t=1522967](http://ubuntuforums.org/showthread.php?t=1522967)

---

### Post by axelsvag on 2010-11-07
It is very annoying not to be able to use the excellent mythnews plugin. Is it possible to do anytjing with the mysql database to get every back and running. The suggested feeds are there in the setting but just greyed out. or can it be a permission problem, but in which file?

---

### Post by ian dobson on 2010-11-07
Hi,

Do you see anything interesting in you frontend log file (/var/log/mythtv/frontend.log)

Regards
Ian Dobson

---

### Post by axelsvag on 2010-11-07
I will look unfortunately I have to wait to next weekend

---

### Post by axelsvag on 2010-11-12
Here is what I found in the logfile that is mythnews related. 

2010-07-29 12:17:29.794 Cannot load language en_us for module mythnews
2010-08-08 14:13:48.306 MythNewsConfig, Error: Could not read content of news-sites.xml
			Error parsing /usr/share/mythtv/mythnews/news-sites.xml
			at line: 1113  column: 49 msg: error occurred while parsing reference
2010-08-29 15:49:41.671 DB Error (MythNews, Error: Could not load sites from DB):
Query was:
SELECT name, url, ico, updated, podcast FROM newssites ORDER BY name
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.newssites' doesn't exist

2010-08-29 16:03:51.160 DB Error (MythNews, Error: Could not load sites from DB):
Query was:
SELECT name, url, ico, updated, podcast FROM newssites ORDER BY name
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.newssites' doesn't exist

it looks like I have to do something with the database but what?

---

### Post by tgm4883 on 2010-11-12
The newssites table doesn't exist (because you deleted it and didn't recreate it). Where did you get those instructions? I assume the instructions should either tell you to recreate the table, or truncate the table rather than drop it.

---

### Post by axelsvag on 2010-11-13
The instructions came from here
[https://help.ubuntu.com/community/MythNews](https://help.ubuntu.com/community/MythNews)
and said this
```
Purging Feed Data

The feeds you choose during setup are stored in the "newssites" table of the mythconverg database. The article information is stored in the home directory of the user who runs mythfronted in this directory:

    *

      ~/.mythtv/MythNews/

To purge MythNews data and cached articles:

   1.

      Drop the newssites table. From the Backend machine:
          *

            $ mysql -u root -p
            mysql> DROP TABLE mythconverg.newssites;
            mysql> exit

   2.

      Delete cached articles. From the Frontend machine:
          *

            $ cd ~/.mythtv/MythNews
            $ rm *

   3.

      Start the mythfrontend and navigate to Utilities/Setup --> Setup --> Info Center Settings --> News Settings and select the feeds you would like to read. 
```

I understand I did something stupid but how do I recreate the database or table?

---

### Post by ian dobson on 2010-11-13
Hi,

I imagine step 3 "Start the mythfrontend and navigate to Utilities/Setup " should recreate the missing table. Try that and have a look in the frontend log file to see if something is going wrong. I imagine it's a permissions problem.

If the worst comes to the worst maybe you can manually recreate the table. Here's a link to the table schema
[http://www.mythtv.org/wiki/Newssites_table](http://www.mythtv.org/wiki/Newssites_table)

Regards
Ian Dobson

---

### Post by axelsvag on 2010-11-14
The step three is the problem I find the rss feeds and see them in the list but it is impossible to put a tick in the box. 

According the last suggestion I am not skilled enough to understand how to do the actual recreation of the mythconverg:mythnews table. All tutorials I find is on too high level for me. I need a more step to step like instruction to be able  recreate the table.

---

### Post by axelsvag on 2010-11-14
It seems scaring just to throw yourself out in mysql wilderness. Ok I tried to put some information together and if someone can confirm that I am on the right track i would be thankful.

1. First go to the terminal and type the following mysql>\u mythconverg;

2. Then type the following putting in enter after each row

CREATE TABLE mythconverg.newssites;
(
emp_id int unsigned not null auto_increment primary key,
f_name varchar(100),
l_name varchar(100),
title varchar(100),
age int,
yos int,
salary int,
perks int,
email varchar(100)
);

I does not completely look like the table in this [http://www.mythtv.org/wiki/Newssites_table](http://www.mythtv.org/wiki/Newssites_table) so there is probably a lot of error in my try.

---

### Post by axelsvag on 2010-11-21
Doe not anybody knows how to recreate the mythnews table?

---

### Post by axelsvag on 2010-12-08
I have now tried my own homemade attempt but it does not seems to work. Does someone know how to make a table the right way?

---

### Post by ian dobson on 2010-12-09
> **axelsvag said:**
> I have now tried my own homemade attempt but it does not seems to work. Does someone know how to make a table the right way?

What do you mean by it doesn't work:-
1) Doesn't create a table
2) Creates a table but the fields are wrong
3) Creates a table but mythtv can't access it
4) Something else
5) All of the above.
.....
42) Answer to the Ultimate Question of Life, the Universe and Everything ([http://en.wikipedia.org/wiki/42_(answer)#Answer_to_the_Ultimate_Question_of_Life.2C_the_Universe_and_Everything_.2842.29](http://en.wikipedia.org/wiki/42_(answer)#Answer_to_the_Ultimate_Question_of_Life.2C_the_Universe_and_Everything_.2842.29))

Id imagine it should look more like this

CREATE TABLE mythconverg.newssites;
(
name varchar(100) not null primary key,
category varchar(256),
url varchar(256),
ico varchar(256),
updated int(10),
podcast boolean
);

Regards
Ian Dobson

---

### Post by axelsvag on 2010-12-11
OK, I will try that and report back

---

### Post by axelsvag on 2011-03-12
Solved at last. Thank you everyone for you help. Here it is what I had to do. But what held me back was mostly my fear for mysql that seems for me a little bit over my skill level. But after reading and thinking I had the courage to try to create a new table in the mythconverg database.


First start a terminal end type the following followed by your root password not the database password.

```
mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 148
Server version: 5.1.41-3ubuntu12.10 (Ubuntu)

```

Then you have to choose the mythconverg database to be able to create a new table inside the database mythconverg. For that you have to do the following.

```
mysql> USE mythconverg
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed

```

I got really scared here since it said it had changed the database but so far nothing bad happened.

Now you are inside the mythconverg databse and the I wanted to look in the newssites table was inside the mythconverg database and for that I used this command and as you see the table was missing.

```
mysql> SHOW TABLES;
+--------------------------------+
| Tables_in_mythconverg          |
+--------------------------------+
| archiveitems                   |
| callsignnetworkmap             |
| capturecard                    |
| cardinput                      |
| channel                        |
| channelgroup                   |
| channelgroupnames              |
| channelscan                    |
| channelscan_channel            |
| channelscan_dtv_multiplex      |
| codecparams                    |
| credits                        |
| customexample                  |
| diseqc_config                  |
| diseqc_tree                    |
| displayprofilegroups           |
| displayprofiles                |
| dtv_multiplex                  |
| dtv_privatetypes               |
| dvdbookmark                    |
| dvdinput                       |
| dvdtranscode                   |
| eit_cache                      |
| filemarkup                     |
| gallerymetadata                |
| gamemetadata                   |
| gameplayers                    |
| housekeeping                   |
| inputgroup                     |
| internetcontent                |
| internetcontentarticles        |
| inuseprograms                  |
| jobqueue                       |
| jumppoints                     |
| keybindings                    |
| keyword                        |
| movies_movies                  |
| movies_showtimes               |
| movies_theaters                |
| music_albumart                 |
| music_albums                   |
| music_artists                  |
| music_directories              |
| music_genres                   |
| music_playlists                |
| music_smartplaylist_categories |
| music_smartplaylist_items      |
| music_smartplaylists           |
| music_songs                    |
| music_stats                    |
| mythlog                        |
| mythweb_sessions               |
| netflix                        |
| netvisionrssitems              |
| netvisionsearchgrabbers        |
| netvisionsites                 |
| netvisiontreegrabbers          |
| netvisiontreeitems             |
| networkiconmap                 |
| oldfind                        |
| oldprogram                     |
| oldrecorded                    |
| people                         |
| phonecallhistory               |
| phonedirectory                 |
| pidcache                       |
| playgroup                      |
| powerpriority                  |
| profilegroups                  |
| program                        |
| programgenres                  |
| programrating                  |
| recgrouppassword               |
| record                         |
| record_tmp                     |
| recorded                       |
| recordedcredits                |
| recordedfile                   |
| recordedmarkup                 |
| recordedprogram                |
| recordedrating                 |
| recordedseek                   |
| recordingprofiles              |
| recordmatch                    |
| romdb                          |
| schemalock                     |
| settings                       |
| storagegroup                   |
| streams                        |
| tvchain                        |
| tvosdmenu                      |
| upnpmedia                      |
| videocast                      |
| videocategory                  |
| videocountry                   |
| videogenre                     |
| videometadata                  |
| videometadatacast              |
| videometadatacountry           |
| videometadatagenre             |
| videosource                    |
| videotypes                     |
| weatherdatalayout              |
| weatherscreens                 |
| weathersourcesettings          |
| websites                       |
+--------------------------------+
106 rows in set (0.00 sec)

``` 

And then I had the courge to create a new table inside the mythconverg database. I used the info from another working mythtv machine so I hope I got most in the right position, so far everything looks OK

```
mysql> CREATE TABLE newssites (name VARCHAR(100), category VARCHAR(255), url VARCHAR(255), ico VARCHAR(255), updated INT(10), podcast TINYINT(1));

```

And then look if the table is created in the mythconverg databse and as you see it is.

```
mysql> SHOW TABLES;
+--------------------------------+
| Tables_in_mythconverg          |
+--------------------------------+
| archiveitems                   |
| callsignnetworkmap             |
| capturecard                    |
| cardinput                      |
| channel                        |
| channelgroup                   |
| channelgroupnames              |
| channelscan                    |
| channelscan_channel            |
| channelscan_dtv_multiplex      |
| codecparams                    |
| credits                        |
| customexample                  |
| diseqc_config                  |
| diseqc_tree                    |
| displayprofilegroups           |
| displayprofiles                |
| dtv_multiplex                  |
| dtv_privatetypes               |
| dvdbookmark                    |
| dvdinput                       |
| dvdtranscode                   |
| eit_cache                      |
| filemarkup                     |
| gallerymetadata                |
| gamemetadata                   |
| gameplayers                    |
| housekeeping                   |
| inputgroup                     |
| internetcontent                |
| internetcontentarticles        |
| inuseprograms                  |
| jobqueue                       |
| jumppoints                     |
| keybindings                    |
| keyword                        |
| movies_movies                  |
| movies_showtimes               |
| movies_theaters                |
| music_albumart                 |
| music_albums                   |
| music_artists                  |
| music_directories              |
| music_genres                   |
| music_playlists                |
| music_smartplaylist_categories |
| music_smartplaylist_items      |
| music_smartplaylists           |
| music_songs                    |
| music_stats                    |
| mythlog                        |
| mythweb_sessions               |
| netflix                        |
| netvisionrssitems              |
| netvisionsearchgrabbers        |
| netvisionsites                 |
| netvisiontreegrabbers          |
| netvisiontreeitems             |
| networkiconmap                 |
| newssites                      |
| oldfind                        |
| oldprogram                     |
| oldrecorded                    |
| people                         |
| phonecallhistory               |
| phonedirectory                 |
| pidcache                       |
| playgroup                      |
| powerpriority                  |
| profilegroups                  |
| program                        |
| programgenres                  |
| programrating                  |
| recgrouppassword               |
| record                         |
| record_tmp                     |
| recorded                       |
| recordedcredits                |
| recordedfile                   |
| recordedmarkup                 |
| recordedprogram                |
| recordedrating                 |
| recordedseek                   |
| recordingprofiles              |
| recordmatch                    |
| romdb                          |
| schemalock                     |
| settings                       |
| storagegroup                   |
| streams                        |
| tvchain                        |
| tvosdmenu                      |
| upnpmedia                      |
| videocast                      |
| videocategory                  |
| videocountry                   |
| videogenre                     |
| videometadata                  |
| videometadatacast              |
| videometadatacountry           |
| videometadatagenre             |
| videosource                    |
| videotypes                     |
| weatherdatalayout              |
| weatherscreens                 |
| weathersourcesettings          |
| websites                       |
+--------------------------------+
107 rows in set (0.00 sec)

```

So for me everything looks solved and hope this could help someone else who use the command in the wiki.

---

