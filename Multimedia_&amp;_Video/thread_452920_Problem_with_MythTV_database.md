---
title: "Problem with MythTV database"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by whein on 2007-05-23
While looking through various log files, I noticed several entries along the lines of > May 23 20:22:39 MythTvBox2 mysqld[5312]: 070523 20:22:39 [ERROR] /usr/sbin/mysqld: Table './mythconverg/recordedseek' is marked as crashed and should be repaired
After a litle searching on the web, I found a [page ]("http://www.mythtv.org/wiki/index.php/Frequently_Asked_Questions#Q:_I_get_a_database_145_error.__What_is_it.3F")that indicated I could fix this using
```
mysqlcheck -u mythtv -p<password> --repair mythconverg

```
Great, I ran the above and got:
```
mythconverg.archiveitems                           OK
mythconverg.callsignnetworkmap                     OK
mythconverg.capturecard                            OK
mythconverg.cardinput                              OK
mythconverg.channel                                OK
mythconverg.codecparams                            OK
mythconverg.credits                                OK
mythconverg.customexample                          OK
mythconverg.diseqc_config                          OK
mythconverg.diseqc_tree                            OK
mythconverg.dtv_multiplex                          OK
mythconverg.dtv_privatetypes                       OK
mythconverg.dvdinput                               OK
mythconverg.dvdtranscode                           OK
mythconverg.eit_cache                              OK
mythconverg.favorites                              OK
mythconverg.filemarkup                             OK
mythconverg.gamemetadata                           OK
mythconverg.gameplayers                            OK
mythconverg.housekeeping                           OK
mythconverg.inuseprograms                          OK
mythconverg.jobqueue                               OK
mythconverg.jumppoints                             OK
mythconverg.keybindings                            OK
mythconverg.keyword                                OK
mythconverg.music_albums                           OK
mythconverg.music_artists                          OK
mythconverg.music_genres                           OK
mythconverg.music_playlists                        OK
mythconverg.music_smartplaylist_categories         OK
mythconverg.music_smartplaylist_items              OK
mythconverg.music_smartplaylists                   OK
mythconverg.music_songs                            OK
mythconverg.music_stats                            OK
mythconverg.musicmetadata                          OK
mythconverg.musicplaylist                          OK
mythconverg.mythlog                                OK
mythconverg.networkiconmap                         OK
mythconverg.oldfind                                OK
mythconverg.oldprogram                             OK
mythconverg.oldrecorded                            OK
mythconverg.people                                 OK
mythconverg.pidcache                               OK
mythconverg.playgroup                              OK
mythconverg.profilegroups                          OK
mythconverg.program                                OK
mythconverg.programgenres                          OK
mythconverg.programrating                          OK
mythconverg.recgrouppassword                       OK
mythconverg.record                                 OK
mythconverg.record_tmp                             OK
mythconverg.recorded                               OK
mythconverg.recordedcredits                        OK
mythconverg.recordedmarkup                         OK
mythconverg.recordedprogram                        OK
mythconverg.recordedrating                         OK
mythconverg.recordingprofiles                      OK
mythconverg.recordmatch                            OK
mythconverg.romdb                                  OK
mythconverg.schemalock                             OK
mythconverg.settings                               OK
mythconverg.tvchain                                OK
mythconverg.videocategory                          OK
mythconverg.videocountry                           OK
mythconverg.videogenre                             OK
mythconverg.videometadata                          OK
mythconverg.videometadatacountry                   OK
mythconverg.videometadatagenre                     OK
mythconverg.videosource                            OK
mythconverg.videotypes                             OK

```
But mythconverge.recordedseek is not in the list!  Oi!
This is also keeping me from being able to backup my database
```
whein@MythTvBox2:~$ mysqldump -u mythtv -p<password> mythconverg -c > mythtv_backup.sql
mysqldump: Got error: 145: Table './mythconverg/recordedseek' is marked as crashed and should be repaired when using LOCK TABLES

```
???
How do I fix this, and then how do I backup the database should things go south later?
-Will

---

### Post by fenian on 2007-05-23
Install phpmyadmin...
> 
sudo apt-get install apache2
sudo apt-get install phpmyadmin

this allows you to maintain mythconverg through a web browser.Type localhost in the browsers address bar,click the phpmyadmin link,the default username is root and the password is blank,in the pulldown database menu select mythconverg,in the window that opens go to the bottom of the list cliak the check all option and choose repair table in the pulldow menu after it completes chek all the items again and choose optimize table from the pulldown menu.Logout  of phpmyadmin.

---

### Post by whein on 2007-05-24
Ok, Synaptic shows both those installed but if I type in either 127.0.0.1 or localhost into the address bar Firefox gives me an error saying it can't establish a connection.  grrr...  ideas?
-Will

---

### Post by whein on 2007-05-29
Ok,I think I made some headway.  I uninstalled mysql-admin and now I can see the phpmyadmin when I go to 127.0.0.1 in Firefox.  However, even with scripting allowed for 127.0.0.1 and cookies enabled I can't get past the login screen.  I know I have the right username and password, but when I press submit it just reloads the same login page.  oi.  the pain.

So after more hunting on the web, I found that I can access the specific table in the mythconverg database by appending it to the end like so:
```
mysqlcheck -u mythtv -p<password> --repair mythconverg recordedseek
mysqlcheck -u mythtv -p<password> --repair mythconverg settings
```I had been trying to figure out the syntax for a week now, trying all manner of forward and backwards slashes, periods, comma, colons, etc.  So hopefully this little nugget of info can save someone else the effort I spent.  :)
Cheers!
-Will

---

### Post by teet on 2007-12-18
Thanks!  I got the same error message when I was trying to backup my database.  

```
mysqlcheck -u mythtv -p<password> --repair mythconverg recordedseek
```

This fixed it!  Thanks for posting the solution :)

-teet

---

### Post by kansei on 2008-02-12
hmm wonder why everyone's recordedseek table gets corrupted?

I think it's time I get ubuntu off my house server..  too many problems sadly

---

### Post by Greg Shallard on 2008-02-14
> **kansei said:**
> hmm wonder why everyone's recordedseek table gets corrupted?

I think it's time I get ubuntu off my house server..  too many problems sadly

I think it might have had to do with a recent batch of updates. I think there was a mysql update in there!

---

### Post by kansei on 2008-02-15
> **Greg Shallard said:**
> I think it might have had to do with a recent batch of updates. I think there was a mysql update in there!

:) too late, server already has debian etch on it :P

---

