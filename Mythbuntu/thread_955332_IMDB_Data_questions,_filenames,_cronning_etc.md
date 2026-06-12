---
title: "IMDB Data questions, filenames, cronning etc"
date: 2008-10-22
forum: Mythbuntu
---

### Post by Lorenzo1985 on 2008-10-22
Some Fairly NOOB questions

- Whats the best way to set up the file name format/structure (or even directory structures) such that the imdb.pl script will find the correct imdb entry. I've run the Bulk updater a few times which works quite well for movies but has completly failed to find any of the series stuff. Is there a file name format you might recommen in order for this stuff to be located properly.


- what commands would you guys use to cron the bulk updater. Would you reccommend running it as a root cron or a user cron? Please can you tell me the command to use in order add my cron line to the crontab.

whats the best way to get the latest imdb.pl file. I tried downloading the one out of the trunk but it didnt seem to work so I had to revert to an older version. (is this file slightly modified for mythbuntu)

---

### Post by toorima on 2008-10-22
For the imdb script to work the file can't contain xvid.group.bla. etc just moviename.avi if it's a 2 cd movie moviename.1.avi and moviename.2.avi works or merge them

the imdb script only works for movies, for tv shows I recommend the metacleanup script, last version found here [http://www.fecitfacta.com/metacleanup-0.4.tar.gz](http://www.fecitfacta.com/metacleanup-0.4.tar.gz) and some info about it can be found here [http://www.mythtvtalk.com/forum/archive/o_t/t_7077](http://www.mythtvtalk.com/forum/archive/o_t/t_7077)

you can no longer just pull the new imdb.pl from svn because its been changed to much but I've posted a modified imdb.pl in this post [http://ubuntuforums.org/showthread.php?t=934511](http://ubuntuforums.org/showthread.php?t=934511) that works

---

