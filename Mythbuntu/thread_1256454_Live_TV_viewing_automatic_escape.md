---
title: "Live TV viewing automatic escape?"
date: 2009-09-02
forum: Mythbuntu
---

### Post by colinnwn on 2009-09-02
Hi All,

I read the article about how MythTV now deals with [live TV viewing]("http://www.mythtv.org/wiki/LiveTV"), and that is really cool.

However, I occasionally forget to escape out of live TV when I turn my tele off. Letting live TV continue to run when I am not watching increases electricity consumption and decreases hard drive life.

Is there a way to get MythTV to either escape out of live TV viewing on a regular interval (like 120 minutes)? Or better yet would be if I could get it to throw up an on screen dialog at regular intervals that says, "Are you still watching? Press any key." If it did not receive a key press within a few seconds, then it would escape out of live TV.

Thanks.

---

### Post by SiHa on 2009-09-03
There is a database record that can be added to do just this, it will propmt after a set period of Live TV. Have a look at  [[COLOR="Blue"]_this_[/COLOR]](http://ubuntuforums.org/showthread.php?t=825556) thread.

Mind you, it doesn't seem to work for me. I set the hostname to null so it should apply to both frontends, but it doesn't actually do anything. I probably did something daft, but have never bothered to try and fix it, it's not a big deal.

Maybe it'll work for you?

---

### Post by colinnwn on 2009-09-03
Cool, thanks, I'll try it. 

I don't know how much experience you have with SQL. I do a lot of it at work with MS Access (yuck!). I thought for those not familiar with SQL, the obvious mistake would be wrapping 'null' in single quotes, or even thinking null means zero length string '', rather than the real null. So your SQL statement should have been 

> INSERT INTO `mythconverg`.`settings` (`value` ,`data` ,`hostname`)
VALUES ('LiveTVIdleTimeout', '240', null);

If that doesn't work, I have my frontend and backend on the same machine, so for troubleshooting purposes, I'll also try making the host name '127.0.0.1' and see if that works. 

If you need help formatting the update command, lemme know. Though a delete and re-insert might be just as easy, to be sure there is no old data crufting it up. I'm assuming settings.value is a unique key and you shouldn't have to worry about that.

---

### Post by SiHa on 2009-09-03
Thanks for the pointers, I'll have a look. From what I remember though, I think it got inserted into the database correctly, as I can see the field in Mythweb. I'll have a poke while I'm playing with my new freesat card and dish this weekend!

---

### Post by williammanda on 2009-09-06
There is a sleep feature that can be used while watching live tv. Select M while viewing live tv then sleep.
Thanks

---

### Post by colinnwn on 2009-09-06
> **williammanda said:**
> There is a sleep feature that can be used while watching live tv.

Hi williammanda. Thanks for the suggestion, but this wouldn't get what I need. We'd have to press M every time we started watching live TV, and that kills user friendliness. We have a problem falling asleep, or the girlfriend just turning off the TV and not escaping out of live TV. SiHa's suggestion would work perfectly.

MYSQL was refusing to let me sign in and open the mythconverge database as the mythtv user all at once. I got a suggestion on [another question post]("http://ubuntuforums.org/showthread.php?t=1258239") to try signing in first, then opening the mythconverge database, so I can see what portion is failing. 

I'm out of town until early next week, and I tried to set up SSH access to my Myth box so I could play with it while gone. Unfortunately I messed something up. So I will have to wait to try again until I get home.

---

### Post by colinnwn on 2009-09-11
Thanks SiHa. I finally got my mysql signin problem figured out, and got this live TV idle timeout working.

After I did an insert to 1 minute, specified my hostname, and verified it worked, I ran the following update to make it universally applicable. I also verified this update works. Right now I only have a combined front/backend, but some day I hope to add more frontends.

```
mysql> UPDATE `mythconverg`.`settings` SET `settings`.`hostname` = null, `settings`.`data` = '240'  WHERE `settings`.`value` = 'LiveTVIdleTimeout';

Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> SELECT * FROM `mythconverg`.`settings` WHERE `settings`.`value` = 'LiveTVIdleTimeout';

+-------------------+------+----------+
| value             | data | hostname |
+-------------------+------+----------+
| LiveTVIdleTimeout | 240  | NULL     | 
+-------------------+------+----------+
1 row in set (0.00 sec)
```

---

### Post by SiHa on 2009-09-11
Nice. Glad it works for you.

Thanks for posting the command you used, I'll try that.

---

