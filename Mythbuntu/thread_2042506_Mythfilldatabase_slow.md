---
title: "Mythfilldatabase slow"
date: 2012-08-14
forum: Mythbuntu
---

### Post by lancelot04 on 2012-08-14
I recently upgraded to Kubuntu 12.04 with Mythtv 0. 25. from a Kubuntu 11.04 install.
 

 At first, i was unable to execute Mythfilldatabase, Mythtv refusing to connect to Schedulesdirect.org. I had to enter all then channels manually. It worked and even if Mythtfilldatabase wasn't working properly, I could get EPG informations. Then came the fixes and Mythtv started to connect to Schedulesdirect. 



All problems are not solved though. Mythfilldatabase still gives this error message and takes ages to download from Schdulesdirect :
 

 2012-08-14 09:28:05.936661 C  mythfilldatabase version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)
 2012-08-14 09:28:05.936670 C  Qt version: compile: 4.8.1, runtime: 4.8.1
 2012-08-14 09:28:05.936673 N  Enabled verbose msgs:  general
 2012-08-14 09:28:05.936682 N  Setting Log Level to LOG_INFO
 2012-08-14 09:28:05.936705 I  Added logging to the console
 2012-08-14 09:28:05.936709 I  Added database logging to table logging
 2012-08-14 09:28:05.936755 N  Setting up SIGHUP handler
 2012-08-14 09:28:05.936827 N  Using runtime prefix = /usr
 2012-08-14 09:28:05.936836 N  Using configuration directory = /home/lancelot/.mythtv
 2012-08-14 09:28:05.936895 I  Assumed character encoding: fr_FR.UTF-8
 2012-08-14 09:28:05.937094 N  Empty LocalHostName.
 2012-08-14 09:28:05.937097 I  Using localhost value of Ordi-principal
 2012-08-14 09:28:05.937158 I  Testing network connectivity to '192.168.0.199'
 2012-08-14 09:28:05.937244 I  Starting process manager
 2012-08-14 09:28:05.937271 I  Starting process signal handler
 2012-08-14 09:28:05.937623 I  Starting IO manager (read)
 2012-08-14 09:28:05.937637 I  Starting IO manager (write)
 2012-08-14 09:28:06.053418 N  Setting QT default locale to fr_US
 2012-08-14 09:28:06.053492 I  Current locale fr_US
 2012-08-14 09:28:06.053527 E  No locale defaults file for fr_US, skipping
 2012-08-14 09:28:06.053956 I  Loading fr translation for module mythfrontend
 2012-08-14 09:28:06.055500 I  Current MythTV Schema Version (DBSchemaVer): 1299
 2012-08-14 09:28:06.056150 I  Updating source #1 (numerique) with grabber schedulesdirect1
 2012-08-14 09:28:06.056373 I  Found 21 channels for source 1 which use grabber
 2012-08-14 09:28:06.056420 I  Checking day @ offset 0, date: Tue Aug 14 2012
 2012-08-14 09:28:06.074516 N  Data is already present for Tue Aug 14 2012, skipping
 2012-08-14 09:28:06.074549 I  Checking day @ offset 1, date: Wed Aug 15 2012
 2012-08-14 09:28:06.074553 I  Data Refresh always needed for tomorrow
 2012-08-14 09:28:06.074557 N  Refreshing data for Wed Aug 15 2012
 2012-08-14 09:28:06.074579 I  This DataDirect listings source is shared by 2 MythTV lineups
 2012-08-14 09:28:06.074583 N  We should keep data around after this one
 2012-08-14 09:28:06.074617 I  New static DB connectionDataDirectCon
 2012-08-14 09:28:06.075483 I  Retrieving datadirect data.
 2012-08-14 09:28:06.075511 I  Grabbing data for Tue Aug 14 2012 offset 1
 2012-08-14 09:28:06.075532 I  From Wed Aug 15 04:00:00 2012 to Thu Aug 16 04:00:00 2012 (UTC)
 2012-08-14 09:28:06.075552 I  DataDirect: Grabbing listing data                                                                                                                     
 2012-08-14 09:28:06.075647 I  Downloading DataDirect feed                                                                                                                           
 content-type missing in HTTP POST, defaulting to application/octet-stream                                                                                                           
 content-type missing in HTTP POST, defaulting to application/octet-stream    
 

 I get the same error message if i execute Mythfilldatabase as root.
 

 A lot of my recordings also fail          
 

 I tried all the solutions suggested in the present thread, to no avail.
 

 Thanks to anybody who could help me to solve my problem.

---

### Post by nickrout on 2012-08-14
The mythfilldatabase has been fixed, update to latest 0.25-fixes using mytbuntu repos.

---

### Post by lancelot04 on 2012-08-14
I already applied the 0.25 fix an I still have the same error message. As i wrote earlier, the fix solved the main problem but not the error that is shown in the log i posted.

Thanks anyway.

---

### Post by Ubu_Fester on 2012-09-22
I am reinstalling my mythbuntu system (long story), and at the mythfilldatabase update step after mythtv setup.

The mythfilldatabase is running very slow.  It's been almost 3 hours and is still not finished!  I'm just letting it continue while I do chores....    It's just grabbed Oct 5th data, so it must be finishing soon...

I've have mythtv for a few years now, and have never had to wait this long for mythfilldatabase.

(My profile is old.  I'm on 12.04 and .25 myth using mythbuntu)

---

### Post by Ubu_Fester on 2012-09-22
also:

I am also getting the following message the OP was receiving:
[HTML]
content-type missing in HTTP POST, defaulting to application/octet-stream [/HTML]

---

### Post by nickrout on 2012-09-22
> **Ubu_Fester said:**
> also:

I am also getting the following message the OP was receiving:
[HTML]
content-type missing in HTTP POST, defaulting to application/octet-stream [/HTML]
First step, upgrade to latest 0.25-fixes

---

### Post by Ubu_Fester on 2012-09-23
Thanks.  I'll update and report back...

---

### Post by Ubu_Fester on 2012-09-23
after adding in the 0.25 updates, the mythfilldatabase step is running smoothly....

---

