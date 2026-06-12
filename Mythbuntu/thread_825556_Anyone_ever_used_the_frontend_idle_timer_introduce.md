---
title: "Anyone ever used the frontend idle timer introduced by  mythtv 0.21?"
date: 2008-06-11
forum: Mythbuntu
---

### Post by Verzweifler on 2008-06-11
In the release notes of mythtv 0.21 you'll find a statement 
> Added an optional idle timer to LiveTV. If we haven't received any remote/keyboard input for X minutes then we show a dialogue asking if the user is still watching. After 45 seconds without any response, we exit LiveTV. If the user responds, then the timer is reset. 

However, I did not find any details on that so far nor was I able to actually find a setting allowing for enabling/configuring that feature.

Anyone of you ever stumbled across this timer?

---

### Post by Verzweifler on 2008-06-11
I googled the following post from Ronald Frazier at pipermail: 
> Looking at the code, there is no place to set this in the GUI. You
will need to insert it into the database directly (in the settings
table). The setting name is LiveTVIdleTimeout, and the value is the
number of minutes after which to timeout.You can do that using the
following SQL command (replace <X> with the number of minutes you want
to set the timeout to, and replace <Y> with the hostname of your
frontend).

INSERT INTO `mythconverg`.`settings` (`value` ,`data` ,`hostname`)
VALUES ('LiveTVIdleTimeout', '<X>', '<Y>');


-- 
Ron


Thanks Ron

I'll give it a try tonight as soon as my wife finished watching TV (do not want to spoil the WAF  :lol: )

---

### Post by SiHa on 2008-10-28
I just stumbled across this feature in Launchpad .I'd like to try it out - just a bit of a newb-type question. 'Hostname' would be the login name of the backend?

eg - my backend is mythbox@192.168.1.152, so I assume I'd need something like:```
INSERT INTO `mythconverg`.`settings` (`value` ,`data` ,`hostname`)
VALUES ('LiveTVIdleTimeout', '240', 'mythbox');

```
How do I do this? I've never touched SQL, and am a little scared of screwing it all up...

TIA,

Simon

---

### Post by tgm4883 on 2008-10-28
I've used it.  If you make the hostname null then the setting will apply to all of your frontends, otherwise you can make different settings for each frontend.

---

### Post by SiHa on 2008-10-28
OK,thanks!

Thing is, how do I run this SQL command? Do I just enter the above on a singe line at a terminal prompt?

Sorry for the stupid question, but I just have no experience of SQL - must read a book - and really don't want to screw um my database.

---

### Post by volkswagner on 2008-10-28
> **SiHa said:**
> OK,thanks!

Thing is, how do I run this SQL command? Do I just enter the above on a singe line at a terminal prompt?

Sorry for the stupid question, but I just have no experience of SQL - must read a book - and really don't want to screw um my database.

To run the above you will do it within mysql.  To get the mysql command prompt run the following in a terminal.

```
mysql -u mythtv -p mythconverg
```

The above assumes you have set a password.

---

### Post by SiHa on 2008-10-28
Great, that did it, thanks. I've checked in Mythweb, and it's there. All I've got to do now is see if it works.
Next I'll have to swot up on mysql stuff - it scares me because I don't understand it.
Hey - I mastered visudo last week, this should be a breeze.

---

