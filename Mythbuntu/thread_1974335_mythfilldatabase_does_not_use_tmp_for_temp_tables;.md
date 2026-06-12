---
title: "mythfilldatabase does not use /tmp for temp tables; config hack"
date: 2012-05-05
forum: Mythbuntu
---

### Post by nopdotcom on 2012-05-05
Disclaimer: somebody may have noticed this already. I couldn't find it in some web searching, and I thought I should write it down.

When using schedulesdirect, mythfilldatabase creates temporary tables in the database to temporarily hold the data it parsed out of from XML. The SQL looks like:
```
"CREATE TEMPORARY TABLE IF NOT EXISTS " + ptablename
"TRUNCATE TABLE " + ptablename
``` in DataDirectProcessor::CreateTempTables() in mythtv/libs/libmythtv/datadirect.cpp , so it's pretty clear these tables can live on volatile storage like tmpfs. OK; I added a /tmp to fstab.

However, snooping the queries during the hours-long mfdb run and seeing 100% busy on the /var/lib/mysql drive in /usr/bin/atop during inserts to dd_* temps made me think the temporary tables were **not** going in /tmp like they should.

The default mysql configuration does set tmpdir to /tmp. My guess was that the temporaries were going in the unified InnoDB table space, which is on /var/lib/mysql, and requires write barriers. I added
```
default_storage_engine=MyISAM
``` to the /etc/mysql/conf.d/mythtv-tweaks.cnf. My reasoning was that the critical mythconverg tables had already been created as InnoDB and would not be affected; the setting only applies to newly created tables.

So anyway, this made my mythfilldatabase runs measurable in minutes rather than hours.   I don't know the full consequences; I'm no mysql expert. The right thing sounds like it should be turning on innodb_file_per_table but that still seems to peg /var/lib/mysql. If InnoDB forces disk touches for these temporary tables a better hack is to patch datadirect.cpp to explicitly request MyISAM tables. 

My new backend motherboard needed new RAM, so I put 8G in it; this tempts me to suggest using the MEMORY engine. That's not going to work for everybody. For general use, something in /tmp is better because people with memory to spare can make it tmpfs, and those without can safely mount a /tmp with all of the data consistency options forced off; why flush hard to disk if after power failure you might as well be running mkfs on it?

---

### Post by mwahal on 2012-08-06
I just want to say thank you very much. You pointed to the right issue, I was so frustrated since I accidentally upgraded to mysql-5.5. I was trying to hack my way into install mysql-5.1 but it was giving me so many issues with other packages.

And the DD will not finish downloading as it was excruciatingly slow to update the tables. With this change, I was able to download all 14 days and update the mythtv database in less than 10mins !!

I ended up modifying the ./libs/libmythtv/datadirect.cpp function DataDirectProcessor::CreateTempTables and added "Engine = MyISAM" after all 9 dd_* tables. Because I dont want to change the default engine.

Once again, thank you very much!!!

---

### Post by anonymousdog on 2012-08-06
Almost certain the fix for this is already in 0.25-fixes.  Are you not running current MB repo builds?

---

### Post by tgm4883 on 2012-08-06
> **anonymousdog said:**
> Almost certain the fix for this is already in 0.25-fixes.  Are you not running current MB repo builds?

It's been fixed for months.

---

### Post by mwahal on 2012-08-07
Forgot to mention that I am still at 0.24.1 since I use XBMC+MythBox ([http://code.google.com/p/mythbox/](http://code.google.com/p/mythbox/)) as my frontend. MythBox plugin doesn't have support for 0.25 as of now, so I am still using 0.24.1. This fix really helped me and if anyone is still using 0.24.1, it can help them too.

---

### Post by tgm4883 on 2012-08-07
> **mwahal said:**
> Forgot to mention that I am still at 0.24.1 since I use XBMC+MythBox ([http://code.google.com/p/mythbox/](http://code.google.com/p/mythbox/)) as my frontend. MythBox plugin doesn't have support for 0.25 as of now, so I am still using 0.24.1. This fix really helped me and if anyone is still using 0.24.1, it can help them too.

They should probably get on that. 0.26 should be released in the next couple months. (although that shouldn't really matter, since starting with 0.25 their support shouldn't be version specific)

---

