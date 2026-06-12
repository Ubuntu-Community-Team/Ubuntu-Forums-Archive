---
title: "[SOLVED] Automatically sleep after X amount of house"
date: 2008-09-21
forum: Mythbuntu
---

### Post by bmathis on 2008-09-21
I did some searching but couldnt find anything specific to my question, so here it goes.

I have a single master backend/frontened that I use to not only record but watch live tv on, often times falling asleep while its on. 8 hours of sleep = 8 hours of recorded live tv that takes a day to disappear!

My question is this; is there a way to have my myth box go into "sleep" mode after a certain amount of hours and then automatically turn on when a scheduled recording starts or I press a key on the remote. Dish Network has a similar feature and was nice when I had dish.

---

### Post by volkswagner on 2008-09-21
I don't think you will want your pc to go to sleep while watching live tv.

---

### Post by tgm4883 on 2008-09-21
> **volkswagner said:**
> I don't think you will want your pc to go to sleep while watching live tv.

You can set a live tv timeout, that would stop your live tv if you don't press a key for X number of minutes.  There currently is not a frontend to do this, you have to add the necessary row in the database.  Details here  [http://www.mythtv.org/pipermail/mythtv-commits/2007-June/029400.html](http://www.mythtv.org/pipermail/mythtv-commits/2007-June/029400.html)


You could then combine that with this in order to get your mythbox to shutdown [http://www.mythtv.org/docs/mythtv-HOWTO-11.html#ss11.5](http://www.mythtv.org/docs/mythtv-HOWTO-11.html#ss11.5)

---

### Post by volkswagner on 2008-09-21
That's good to know.  After reading your link provided, I see how easily false shutdowns won't occur.  

There will be an OSD warning.  I gather if nobody argues, live tv will halt.

Pretty cool.

---

### Post by bmathis on 2008-09-21
Thanks tgm, that live tv timeout is exactly what I wanted.

For anyone else who needs it, here is the SQL command ```
INSERT INTO `mythconverg`.`settings` (`value` ,`data` ,`hostname`)
VALUES ('LiveTVIdleTimeout', '<X>', '<Y>');

```

Replace X with the number of minutes before it times out and Y with the name of your frontend. 

[SIZE="1"]Source: [http://www.mythtv.org/pipermail/mythtv-users/2008-March/215077.html]("http://www.mythtv.org/pipermail/mythtv-users/2008-March/215077.html")[/SIZE]

---

### Post by tgm4883 on 2008-09-21
> **bmathis said:**
> Thanks tgm, that live tv timeout is exactly what I wanted.

For anyone else who needs it, here is the SQL command ```
INSERT INTO `mythconverg`.`settings` (`value` ,`data` ,`hostname`)
VALUES ('LiveTVIdleTimeout', '<X>', '<Y>');

```

Replace X with the number of minutes before it times out and Y with the name of your frontend. 

[SIZE="1"]Source: [http://www.mythtv.org/pipermail/mythtv-users/2008-March/215077.html]("http://www.mythtv.org/pipermail/mythtv-users/2008-March/215077.html")[/SIZE]

It's probably also good to note that if you set the hostname as null, then that will be the timeout for all frontends.

---

