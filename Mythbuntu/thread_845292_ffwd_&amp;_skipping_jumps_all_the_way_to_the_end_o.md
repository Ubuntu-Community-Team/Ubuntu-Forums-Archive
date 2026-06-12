---
title: "ffwd &amp; skipping jumps all the way to the end of recordings"
date: 2008-06-30
forum: Mythbuntu
---

### Post by jonno on 2008-06-30
I've had a Mythbuntu 8.04 system running well since it was released (aside from the volume control not working).
I usually install whatever upgrades the system prompts me to without checking them out very carefully so I'm not sure exactly what caused this but...
About 1-2 weeks ago my system started jumping right to the end of recordings whenever I try to fast-forward or skip ahead. Of course this means I can't commercial skip!

Any ideas what might have caused this? I couldn't find anything on the forums with a quick search.

---

### Post by jonno on 2008-06-30
Bit more info:
When jumping forward (or backwards for that matter) the program jumps all the way to the end. Actually I'm not sure if it jumps to the beginning or the end of the show. The timeline bar seems to indicate that has jumped to the end - the bar is full and the time shown is the total time of the recording - but then the program starts over from the beginning again.
When fast-forwarding at 3x it appears to fast-forward just fine but when I try to go back into play mode it does it's thing and jumps to the end.
When fast-forwarding at 5x or greater it simply jumps straight to the end.
Everything works fine in LiveTV mode. This is only a problem with recorded shows.

Weird. And frustrating.

---

### Post by larsolav on 2008-07-01
Hi there,
I have had this happen to me before as well. In fact, after upgrading to 0.21 every recording from 2007 was "unskippable" but the 2008 recordings OK. I never found out why, and just deleted the 2007 shows and let the kid's PBS shows re-record.

And now today my wife called and said she could not skip ahead on any of the recordings...

When I get home I will try to optimize the tables from MCC and see if that doesn't help. Have you tried doing this yet?

---

### Post by jonno on 2008-07-01
> **larsolav said:**
> Hi there,
I have had this happen to me before as well. In fact, after upgrading to 0.21 every recording from 2007 was "unskippable" but the 2008 recordings OK. I never found out why, and just deleted the 2007 shows and let the kid's PBS shows re-record.

And now today my wife called and said she could not skip ahead on any of the recordings...

When I get home I will try to optimize the tables from MCC and see if that doesn't help. Have you tried doing this yet?

I ran the optimize_mythdb.pl script described here, [http://www.mythtv.org/wiki/index.php/Repairing_the_Seektable](http://www.mythtv.org/wiki/index.php/Repairing_the_Seektable) but that didn't help. Not sure if what you're talking about is the same thing but I'll try that tonight. Let me know how you make out.

---

### Post by larsolav on 2008-07-01
Yeah, I think that the optimize option under "advanced" in MCC runs the optimize_mythdb.pl script. Bummer that didn't help.

I don't know if the optimizing feature does the same as running mysqlcheck, so maybe that would help.

Volkswagner wrote this ( [http://ubuntuforums.org/showthread.php?t=691766&highlight=mysqlcheck](http://ubuntuforums.org/showthread.php?t=691766&highlight=mysqlcheck) ) :

> Your situation may be solved otherwise by repairing mysql. Check all mythtv logs.

```
mysqlcheck --auto-repair -A -u mythtv -pmysqlpass
```

Edit "-pmysqlpass" and replace "mysqlpass" with mythtv user password for mysql.

Running the above will automatically repair and tell you what was repaired.

Superm1 wrote this ( [http://ubuntuforums.org/showthread.php?t=590723&highlight=mysqlcheck](http://ubuntuforums.org/showthread.php?t=590723&highlight=mysqlcheck) ) :

> 

```
mysqlcheck -r -u mythtv -pmythtv mythconverg
```

Be sure to substitute in the password being used for the mythtv user in the -p field.

So it will be

```
mysqlcheck -r -u mythtv -pblahblah mythconverg
```

You can get this password from


 ```
/etc/mythtv/mysql.txt
```

I don't know what the difference is between the different options used by Superm1 and Volkswagner, but I am hoping that using one of them will do the trick...

---

### Post by jonno on 2008-07-01
Ok I'll definitely try this out tonight. I've tried some of that before and have always run into difficulties with the mysql password despite resetting it according to others instructions. Your note about how to check the current password may help though.

If you know of any other pointers about mysql permissions etc please point me there.

---

### Post by jonno on 2008-07-01
Ok I tried both of the above mysqlcheck suggestions but everything passed fine.

Someone on the mythtv-users list had suggested this:
```
Stop mysql
run myisamchk *|--silent --force --fast --update-sta|*te
*|/|/path/to/mythconverg/*|/.MYI|*
restart mysql

run mythcommflag --rebuild --all
```
but I'm not sure what to do with the * & |

I also found [a similar suggestion]("http://wiki.linuxmce.org/index.php/Setting_up_MythTV"):
```
 cd /var/lib/mysql/mythconverg
 /etc/init.d/mythtv-backend stop
 /etc/init.d/mysql stop
 myisamchk *.MYI -r
```
but here I run into the problem that I'm denied permission to cd into /var/lib/mysql/mythconverg/
Here are the permissions of that directory:
```
drwx------ 2 mysql mysql    12288 2008-07-01 18:01 mythconverg
```
Should I modify the permissions of it or am I barking up the wrong tree?

---

### Post by jonno on 2008-07-01
My bad. One of the mysqlcheck commands must have done the trick. I'm back to skipping happily!

---

### Post by larsolav on 2008-07-01
Funny thing, for me the mysqlcheck fixed every thing, except for the recordings done on Sunday and Monday! That is a bummer because I recorded a PBS mystery program on sunday and I never can sit through the whole thing in one evening, so not being able to skip in it is a bummer when I want to watch the second half. (bookmarking it doens't work either...)

---

