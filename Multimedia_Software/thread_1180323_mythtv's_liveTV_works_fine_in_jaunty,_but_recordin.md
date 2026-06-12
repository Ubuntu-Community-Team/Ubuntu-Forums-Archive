---
title: "mythtv's liveTV works fine in jaunty, but recording won't"
date: 2009-06-06
forum: Multimedia Software
---

### Post by wilho on 2009-06-06
Hi!

I just recently upgraded ubuntu from intrepid to jaunty. Now there's strange problems with recordings. LiveTV seems to work fine - and recordings which are still recording, but finished recordings won't play properly.

I can't skip ahead, it just skip to end of the show. Usually few minutes after wathcing it just skips to an end. VLC and mplayer are playing those files OK, but there's some problems with Totem too..

Any suggestions? This is a bit frustrating, since mythtv is the only way my family watches TV nowadays, so I'm under pressure so to speak.. :)

---

### Post by Das Hammer on 2009-06-06
Try turning off the option to "automatically skip" commercials and see if that changes anything.  I suspect an issue with the recordings containing some commercial flag data, but maybe not enough.

If doing that changes things, we can work from that point.

These recordings: 
Has commercial flagging run?
Has commercial flagging process completed on this recording?

I don't know what the default settings are in Jaunty, but if you upgraded it should have retained the settings in the database.

---

### Post by wilho on 2009-06-07
Hi, ):P

Thanks for the suggestion, but autoskip commercials is not on. And this happens with recordings I know there's nothing wrong with them, they worked fine before but stopped working after upgrade.

I will look a bit deeper to a commercial flagging if I could disable it entirely because its not useful for me, but I'm quite sure that internal player or its splitter/decoder/whatever is uncapable of following DVB-streams for some reason.

I will definately stick with next LTS, upgrade brakes something every single time :|

---

### Post by wilho on 2009-06-07
Checked the settings, and commercial automatic flagging is job is not enabled at all and haven't been for a long time I suppose. 

I just found out, that if i try to "edit recording", it just says "No seek table" and I cannot edit. This might be important...

---

### Post by wilho on 2009-06-07
I ran mythcomflag --rebuild and noticed that seektable table in database was corrupted. So I ran

mysqlcheck -u root -p -A --auto-repair
and mythcommflag --rebuild again. It still running, but seems that it helps. :)

So you were on the right track hammer, thanks for a tip.

---

