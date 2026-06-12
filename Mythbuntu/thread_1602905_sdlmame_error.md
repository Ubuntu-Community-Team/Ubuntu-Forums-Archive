---
title: "sdlmame error"
date: 2010-10-22
forum: Mythbuntu
---

### Post by miststlkr on 2010-10-22
I am running MythBuntu 10.04 and SDLMAME .139, following the HOW-TO at [http://ubuntuforums.org/showthread.php?t=1340191](http://ubuntuforums.org/showthread.php?t=1340191) to get it working, with a few tweaks [[ie:// the latest install the executable is /usr/games/mame not /usr/games/sdlmame]] and when I try to scan for games I get the following error:

```


 Error preparing query: select distinct ,system,year,genre,gamename from gamemetadata where system in ('SDLMAME') and favorite=1 and  display = 1  order by ;
2010-10-21 22:46:00.704 Driver error was [2/1064]:
QMYSQL3: Unable to prepare statement
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'system,year,genre,gamename from gamemetadata where system in ('SDLMAME') and fav' at line 1


```

Would someone care to throw me a bone please?

---

### Post by ian dobson on 2010-10-22
Hi,

OK, maybe only the scraps of a bone. The SQL query is incorrect it's missing the clause for the order by and the fieldname for the distinct:-

select distinct ,system,year,genre,gamename from gamemetadata where system in ('SDLMAME') and favorite=1 and  display = 1  order by ;

should be
select distinct **something**,system,year,genre,gamename from gamemetadata where system in ('SDLMAME') and favorite=1 and  display = 1  order by **something**;

Why mythtv is doing this, I'm sorry I can't say. What version of mythtv are you running? If it's not 23.1-fixes then update any try again.

Regards
Ian Dobson

---

### Post by miststlkr on 2010-10-23
According to Sytem Status I am on build release-0-23-fixes (24158).   I will look at an update to 23.1 in the morning, thanks. I hadn't realized there was one.

---

### Post by ian dobson on 2010-10-23
Hi,

Just have a look in this thread [http://ubuntuforums.org/showthread.php?t=1032455](http://ubuntuforums.org/showthread.php?t=1032455)

Regards
Ian Dobson

---

### Post by Wes Baker on 2010-11-14
Hi,

I have exactly the same error, also running 10.04 and 0.139, but I am already using the mythbuntu-repos 0.23.1 auto builds in my setup.

Did you find a solution yet?  

Thanks,

Wes

---

### Post by miststlkr on 2010-11-14
No luck so far, I haven't tinkered with it all that much as I have other thiungs I am woring on too, some of which I actually know how to fix so I figured I'd get them out of the way first.  please, if you come up with something before I do, please let me know about it.  I'm thinking this one is beyond my ability to figure out just by poking around blindly.

---

### Post by Wes Baker on 2010-11-14
Thanks for your reply.

Surely will let you know if I find out how to fix it...

---

### Post by IceCap on 2010-12-29
Did you guys ever figure out how to fix this?  I believe I'm having the same problem although I haven't determined the exact error message (how did you do that?).  The scan for games doesn't result in any games found (the scan is really fast).  I posted a question about this yesterday but not getting any bites.  I'm assuming this is something people rarely encounter.

  Thanks

  IC

---

### Post by IceCap on 2011-01-01
I figured it out (in my case).  Turns out that you must put in the game file extension for the roms.  So zip,ZIP in that field and it works.  I believe that is a change from previous versions.

  IC

---

### Post by BugReaper on 2011-08-13
I figured it out.  Run this query on the database (mysql-query-browser):
```
SELECT * FROM settings s 
WHERE s.`value` like '%game%' and not s.`value` = 'GameDBSchemaVer' 

```And check the hostname matches your mythfrontend identifier.
Setting the hostname to null fixed the mythgame SQL error for me. Run this:
```
update settings s 
set s.hostname = null
WHERE s.`value` like '%game%' and not s.`value` = 'GameDBSchemaVer' 
```
If you setup mythgame on one frontend and then used a different frontend the sql error will occur.
Setting hostname to null means all frontends will use the same values.  If you change these settings from mythfrontend->setup->setup->media_settings->game_settings->general_settings then the SQL error may return when you use another frontend.

---

### Post by miststlkr on 2011-08-13
wow, I'd forgotten all about this!  Thanks so much for posting a solution.  I've since given up on it and haven't used mythgame but I'll give it a shot when things slow down a little around here and I get time to try it again.

cheers!!

---

