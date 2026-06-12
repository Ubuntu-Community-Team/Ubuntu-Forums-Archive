---
title: "has anyone upgraded from mythbuntu 14.04 to 16.04.1?"
date: 2016-07-30
forum: Mythbuntu
---

### Post by gottabefoss on 2016-07-30
Anyone do an in-place do-release-upgrade to the new mythbuntu LTS?

How did it go?

---

### Post by tgm4883 on 2016-07-30
> **gottabefoss said:**
> Anyone do an in-place do-release-upgrade to the new mythbuntu LTS?

How did it go?

I upgraded from 14.04 to 16.04 and it went fine. It was a backend only machine.

---

### Post by blanik on 2016-07-31
> **gottabefoss said:**
> Anyone do an in-place do-release-upgrade to the new mythbuntu LTS?

How did it go?

Yes - today (1 August 2016) I did an upgrade of mt Mythbuntu 14.04 Frontend/Backend System to 16.04.01.

BIG FAIL.   The upgrade process failed with errors indicating that mysql-server-5.7 was unable to install.  Searches on the Ubuntu Bugs site show that there are numerous bugs and questions indicating that the mysql 5.7 packages have a big problem, but no fixes yet.  My recommendation - DO NOT UPGRADE !

I was unable to recover my system after the upgrade failure - So I did a new clean install (on a freshly partitioned root drive) of Mythbuntu 16.04 - and it ALSO FAILED again with exactly the same error.

Stick with Mythbuntu 14.04 until someone sorts out this mess !

---

### Post by Caysho on 2016-08-01
The bug reports indicate significant breakage with the mysql server upgrade.
The first few times I ran the upgrade, I hit bug [lpbug]1574040[/lpbug] and bug [lpbug]1576767[/lpbug].

On the weekend I ran the upgrade again, after turning off the mythtv mysql tweaks, to 16.04.1 and I had no package breakage.
However, the mythtv backend and front end had been removed.  No clue why though.

The Mythbuntu Control Centre was still present, so I used that to install them again and everything worked as expected.

I am not sure why the mysql-server upgrade was successful this time.

---

### Post by scottn2 on 2016-08-01
If you have the tweaks enabled then you will hit bug [https://bugs.launchpad.net/ubuntu/+source/mythbuntu-common/+bug/1576767](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-common/+bug/1576767) unless you change the line in /etc/mysql/conf.d/mythtv-tweaks.cnf that says
table_cache=
to
table_open_cache=
mysql will fail to start.

---

### Post by jfaberna on 2016-08-01
FYI, I sort of got the upgrade in place done, but had enough issues to just start from scratch with a fresh install of mythbuntu 16.04.1.  Massive issues. going back to 14.04 which worked for years.

---

### Post by gottabefoss on 2016-08-02
well all this is disappointing. 

I did a test upgrade to 16.04 a few months ago and ran into all those mysql and mythweb problems. So I restored my backup image.

All these problems have been documented, so you'd think they'd have been fixed by 16.04.1. A couple of the problems are even noted on mythbuntu's webpage. But they haven't been fixed apparently. I don't know if it's the ubuntu maintainers or the mythbuntu maintainers responsible, but very disappointing. Sad!

Looks like I'll be staying on 14.04 for the foreseeable future.

Thanks!

---

### Post by tgm4883 on 2016-08-03
> **gottabefoss said:**
> well all this is disappointing. 

I did a test upgrade to 16.04 a few months ago and ran into all those mysql and mythweb problems. So I restored my backup image.

All these problems have been documented, so you'd think they'd have been fixed by 16.04.1. A couple of the problems are even noted on mythbuntu's webpage. But they haven't been fixed apparently. I don't know if it's the ubuntu maintainers or the mythbuntu maintainers responsible, but very disappointing. Sad!

Looks like I'll be staying on 14.04 for the foreseeable future.

Thanks!

You could always file a bug with a patch attached. Or a pull request.

---

### Post by darinsson on 2016-08-03
Yes I also hit the 0.28 wall. The same problem if you try to  use 0.28 from  Mythbuntu 14.04 or jump to 16.04. I tried now  for three days and did 22 new installs  and every idea I have is now tested. So I need to go back to 14.04 and avoid 0.28 upgrade also(((

---

### Post by gottabefoss on 2016-08-03
> **tgm4883 said:**
> You could always file a bug with a patch attached. Or a pull request.

These issues were reported during 16.04 and are up on launchpad. 

I was hoping they were fixed by 16.04.1. 

Apparently not.

---

### Post by gottabefoss on 2016-08-03
> **darinsson said:**
> Yes I also hit the 0.28 wall. The same problem if you try to  use 0.28 from  Mythbuntu 14.04 or jump to 16.04. I tried now  for three days and did 22 new installs  and every idea I have is now tested. So I need to go back to 14.04 and avoid 0.28 upgrade also(((

FWIW, I had no problems upgrading to .28 on 14.04 and have been running it successfully with no issues since it came out in February.

---

### Post by tgm4883 on 2016-08-03
> **gottabefoss said:**
> These issues were reported during 16.04 and are up on launchpad. 

I was hoping they were fixed by 16.04.1. 

Apparently not.

Just because there are bug reports filed doesn't mean the devs have time to work on it. Which is why I suggested you could attach a patch or pull request with the fix.

---

### Post by gottabefoss on 2016-08-03
> **tgm4883 said:**
> Just because there are bug reports filed doesn't mean the devs have time to work on it. Which is why I suggested you could attach a patch or pull request with the fix.

whelp, if i knew how to fix 16.04's problems to get it working ... i'd be running 16.04.

---

### Post by darinsson on 2016-08-07
OK, now after almost 100 hours struggling I am almost finished with the upgrade to Mythbuntu 16.04 from 14.04. Of course I made some beginners mistake,  but the transition even if you are experienced , (I have been using it since 2007) is a bumpy ride. I needed to make a completely fresh install of 14.04, get back the old database into the system. Then do not touch anything, anywhere. Make all updates, and then upgrade to 16.04, and cross your fingers. Then when you are inside 16.04 I got all the problems described including the  strange Mythmusic problem. And many many more problems, but I think I found all errors now. Now only my last thing is my tuner card for dvb-c. The card Technotrend 1501c, worked perfect in 14.04 and it is recognized perfect in linux dmesg and   found in mythtv-setup but says it is unknown error. So I will struggle more today. O k, to make a long story short, keep your database very safe, because I used it 100 times these days, and if your not very hard in your mind I recommend  make a new install without old database, or never touch 16.04.

---

### Post by tgm4883 on 2016-08-07
> **gottabefoss said:**
> whelp, if i knew how to fix 16.04's problems to get it working ... i'd be running 16.04.

Can you link to the bug reports?

---

