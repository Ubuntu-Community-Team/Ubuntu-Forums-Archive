---
title: "Python Warning -- Please read"
date: 2010-12-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-12-08
Thanks to philinux for alerting us to upcoming breakage due to a python upgrade.

Tomorrow, Wednesday December 8, we'll change the default Python version in
Natty from 2.6 to 2.7.

This will be followed by a series of no-change uploads to rebuild packages
with Python 2.7. [B]Some parts of the archive will be uninstallable or not
upgradeable for a few days; please wait with upgrades until the rebuilds are
done, and for the next two days, also avoid bug reports about upgrade
problems.[/B]

---

### Post by arpanaut on 2010-12-08
Time for the "Partial Upgrade" sticky again?

There are some pretty good procedures, and advice contained in that one!

---

### Post by cariboo on 2010-12-08
This isn't a partial upgrade issue, doing any updates at all even using aptitude safe-upgrade, will cause breakage.

I'll have to dig up one of 23megs partial upgrade posts and revise it, to suit the testing round.

---

### Post by autocrosser on 2010-12-08
Yes--It's about time---some people will break their systems bad & we'll all hear about it......

---

### Post by kyleabaker on 2010-12-08
> **autocrosser said:**
> Yes--It's about time---some people will break their systems bad & we'll all hear about it......

:lolflag: sadly, thats very true.

---

### Post by dino99 on 2010-12-09
About fresh news:

[http://ubuntuforums.org/showthread.php?t=1640839](http://ubuntuforums.org/showthread.php?t=1640839)

---

### Post by VeeDubb on 2010-12-09
for those of use who didn't see the note before their daily upgrade check, is there a way to revert short of reinstalling?  If not, I'll have to stop testing for a while.  I need a working laptop in the morning.

---

### Post by Quackers on 2010-12-09
Post #16 here worked for me, thanks to cariboo907

[http://ubuntuforums.org/showthread.php?t=1641092&page=2](http://ubuntuforums.org/showthread.php?t=1641092&page=2)

---

### Post by VeeDubb on 2010-12-09
> **Quackers said:**
> Post #16 here worked for me, thanks to cariboo907

[http://ubuntuforums.org/showthread.php?t=1641092&page=2](http://ubuntuforums.org/showthread.php?t=1641092&page=2)

Not looking for a workaround, so much as a way to force the downgrading of all the affected packages until it get's fixed.

---

### Post by Quackers on 2010-12-09
I see. I think I'm going to wait a couple of days until all the updated files have been sorted out, then run update and see what actually runs. Then, hopefully once they're installed, the remaining ones will run - I hope :-)

---

### Post by jaco223 on 2010-12-09
thanks for the heads up ....broke my system twice......as a side note, everything else ii've tried is smooth. not bad for a1 :)

---

### Post by ratcheer on 2010-12-09
I installed a bunch of updates yesterday (Wednesday) and didn't get any breakage. But, I'll wait a few days to install any more.

Will an "all clear" be posted in this thread when things are safer?

Tim

---

### Post by chrismine on 2010-12-09
Oh no - are you guy's trying to relieve me from my apt-get addiction?

I'll just break my system and ask for help on the forums - it works very well...

As you can see from my post count I am not a serial offender...

---

### Post by karmila on 2010-12-09
Lol, i just got this breakage.

Fortunately I back up my natty at least once a week with clonezilla. Now I'm using my "last week Natty" ;)

Is it already safe now to do update?

---

### Post by kyleabaker on 2010-12-09
> **karmila said:**
> Lol, i just got this breakage.

Fortunately I back up my natty at least once a week with clonezilla. Now I'm using my "last week Natty" ;)

Thats a cool idea! I'm gonna look into this, thanks!

> **karmila said:**
> Is it already safe now to do update?

I've not run updates yet since I've been tracking issues like this in the forums, but I was wondering the same thing!?

---

### Post by fibster on 2010-12-09
WOW, this has been known for a long time now on the Arch forums, surprises me that a community this large? can miss the python 2.7 breakage problems.

Hmm maybe time to rethink office applications. Of course I should of said something a long time ago, as i follow these things closely, my bad.

---

### Post by cariboo on 2010-12-09
> **fibster said:**
> WOW, this has been known for a long time now on the Arch forums, surprises me that a community this large? can miss the python 2.7 breakage problems.

Hmm maybe time to rethink office applications. Of course I should of said something a long time ago, as i follow these things closely, my bad.

The conversion here only started on the 8th, with a warning beforehand and the gdm problem was quickly fixed, it took less than 24 hours for a fix to show up.

---

### Post by kyleabaker on 2010-12-09
> **cariboo907 said:**
> The conversion here only started on the 8th, with a warning beforehand and the gdm problem was quickly fixed, it took less than 24 hours for a fix to show up.

Thanks! Thats all I was waiting for to get fixed. I can deal with the other issues. :D

---

### Post by karmila on 2010-12-10
> **kyleabaker said:**
> I've not run updates yet since I've been tracking issues like this in the forums, but I was wondering the same thing!?

I ran update... again, but this time no more problem at login :D

So, i think for now this python upgrade breakage problem already solved.

---

### Post by MacUntu on 2010-12-10
Not over yet here:> The following packages will be REMOVED:
  gm-notify libgirepository1.0-1 openoffice.org-emailmerge python-indicate python-uno ubuntu-desktop unity

---

### Post by trulan on 2010-12-10
...don't let a partial upgrade remove libgirepository - that breaks unity/compiz pretty badly.  Nautilus still works but it makes for a pretty crippled desktop.  ( - note to self:  you knew better than to do that partial upgrade.. :( )
**Edit: Wrong answer!**
Actually libgirepository is supposed to be removed, it is replaced with a renamed packaged to match Debian.  The correct answer would have been:
...don't let a partial upgrade remove python-indicate.

---

### Post by go7Ul1ai on 2010-12-10
> **trulan said:**
> ...don't let a partial upgrade remove libgirepository - that breaks unity/compiz pretty badly.  Nautilus still works but it makes for a pretty crippled desktop.  ( - note to self:  you knew better than to do that partial upgrade.. :( )

Oopsie, yeah I never learn. How can I rectify this, it can't find the package libgirepository now I've let it remove it :(

---

### Post by trulan on 2010-12-10
Well maybe I jumped the gun on blaming the problem on that - synaptic shows something like libgirepository1.0 has been removed but libgirepository-1.0 is installed.  Whatever...

Guess I'll have to keep looking.  Or maybe wait until tonight and see how things mash out then..

Edit:  Looks like the problem was the removal of python-indicate.  I reinstalled that and at least now window decoration works again.  Still no unity...

Edit2: or maybe the correct answer is, all of the above.  The only two packages removed by that partial upgrade were python-indicate (which is installable again) and libgirepository1.0-1 (which currently wants to remove several hundred packages).  libgirepository-1.0-1 is installed but I believe both of them are necessary.

---

### Post by dino99 on 2010-12-10
its a package renaming to match with debian

---

### Post by pressureman on 2010-12-10
I've been putting this off for days, but I can live with the final two packages being removed, neither of which I use: openoffice.org-emailmerge and python-uno. I can reinstall them in a few days when things settle down.

So I'm now running Python 2.7 as the default version. Everything seems to work. Even Django apps are working... yay for Python 2.7, the last in the 2.x series.

The next Python upgrade (to 3.something) will be a lot messier than this :D

---

### Post by trulan on 2010-12-10
> **dino99 said:**
> its a package renaming to match with debian
OK thanks - so libgirepository wasn't the problem at all then - the problem was python-indicate.  Whatever else was wrong got fixed by this evening's updates.  Unity is back in business here!

---

### Post by jaco223 on 2010-12-10
> **trulan said:**
> OK thanks - so libgirepository wasn't the problem at all then - the problem was python-indicate.  Whatever else was wrong got fixed by this evening's updates.  Unity is back in business here!

hi all

is it now safe to update/partial upgrade ....getting itchy here :)

---

### Post by Quackers on 2010-12-10
I have just installed all available updates on both my Natty installs without any further problem. However, coffeecat is not currently fully working (missing most of the top bar headings and applets), so I can't vouch for everyone's system :-(

---

### Post by cariboo on 2010-12-10
It seems to be, I was using:

```
sudo aptitude update && sudo aptitude -y safe-upgrade
```

yesterday, but I've gone back to using synaptic today, as all the dependencies seem to have been met.

---

### Post by MacUntu on 2010-12-10
I've lost just one installation - Unity panel is completely empty (however indicators are running). Doesn't happen on this fully up-to-date machine. :(

---

### Post by jaco223 on 2010-12-10
I did apt-get -f dist-upgrade. it seemed to go off without a hitch wiht the exception of losing the top panel, i.e no date time, no logout etc....any way to repair this?

thanks and sorry for any trouble

jaco

---

### Post by jaco223 on 2010-12-10
> **jaco223 said:**
> I did apt-get -f dist-upgrade. it seemed to go off without a hitch wiht the exception of losing the top panel, i.e no date time, no logout etc....any way to repair this?

thanks and sorry for any trouble

jaco

forgot to add i am using unity

---

### Post by jaco223 on 2010-12-10
> **jaco223 said:**
> forgot to add i am using unity

i was able to get gnome panel back date time etc....however in the upper left of the panel where the ubuntu logo is and application places systems, when i click the ubuntu logo it doesn't open a folder now it shows a drop down list. i would like it to go back to opening a folder .....geez i screwed everything up!

---

### Post by jaco223 on 2010-12-10
> **jaco223 said:**
> i was able to get gnome panel back date time etc....however in the upper left of the panel where the ubuntu logo is and application places systems, when i click the ubuntu logo it doesn't open a folder now it shows a drop down list. i would like it to go back to opening a folder .....geez i screwed everything up!

sorry about this ....i disabled gnome panel ..so just unity is running however i have no date time, logout etc...
any way to get this back?
sorry for the duplicate posts
jaco

---

### Post by Quackers on 2010-12-10
I think coffeecat has the same problem. He didn't find a fix yet.

---

### Post by cariboo on 2010-12-10
I would suggest that if you want answers to your questions, you would be better off checking the other threads here, as there are solutions to your problems there,

I'm going to unstick this thread tomorrow, so it may disappear off the front page fairly quickly

---

### Post by zika on 2010-12-21
Just several days ago I'we got rid of python 2.6.
Today: upgrade recommends python 2.6...
Of course, I said: Thank You...

---

### Post by Harry33 on 2010-12-21
> **zika said:**
> Just several days ago I'we got rid of python 2.6.
Today: upgrade recommends python 2.6...
Of course, I said: Thank You...

What upgraded package did that?
Anyway the transition from python2.6 to python2.7 does not seem to over yet.
The same applies to the transition from gir1.0 to gir1.2 packages.

---

### Post by zika on 2010-12-22
> **Harry33 said:**
> What upgraded package did that?
Anyway the transition from python2.6 to python2.7 does not seem to over yet.
The same applies to the transition from gir1.0 to gir1.2 packages.I do not remember. By habit, I first closed that window and then realized inconsistency...

---

### Post by Harry33 on 2010-12-22
> **zika said:**
> I do not remember. By habit, I first closed that window and then realized inconsistency...

So did you install the python2.6?
If so, try to completely remove it with synaptic.

---

### Post by zika on 2010-12-22
> **Harry33 said:**
> So did you install the python2.6?
If so, try to completely remove it with synaptic.I did that (complete purge) a week or more ago...
As soon as that was possible without any re-install-ments...

---

