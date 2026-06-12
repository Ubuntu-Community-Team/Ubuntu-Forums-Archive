---
title: "optimize_mythdb script doesn't work?"
date: 2014-05-19
forum: Mythbuntu
---

### Post by neutron68 on 2014-05-19
In the Mythbuntu Control Centre, when you check the box for enabling daily database scan-and-fix scripts, it puts scripts into your /etc/cron.daily folder.
One of these is optimize_mythdb.
I just tried to run the optimize_mythdb script in the cron.daily folder and I got errors!

I think this means that the auto cleaner has not been working since I checked the box in the Mythbuntu Control Centre??

Here's the output I got when I tried to run that script:

```
user@Mythbuntu:/etc/cron.daily$ sudo sh optimize_mythdb
optimize_mythdb: 14: optimize_mythdb: use: not found
optimize_mythdb: 15: optimize_mythdb: use: not found
optimize_mythdb: 18: optimize_mythdb: Syntax error: "(" unexpected
```

Has this been reported before?
Eric

---

### Post by khPWXxF on 2014-05-19
I will not comment on the cron bit but a few things about running it manually:

1.  Check that both /home/mythtv/.mythtv/mysql.txt and ~/.mythtv/mysql.txt exist and are the same.  
        On my 12.04 system they are both links to /etc/mythtv/mysql.txt.
 
2.  Do not sudo the script – that will run it under root which you don’t want, though I suppose it might work if you had a /home/root/.mythtv/mysql.txt.

3.  You are trying to run it as a shell script – it is a perl script.  Do this instead:

Locate it with: 
```
locate optimize_mythdb.pl
```
In my case it’s in /usr/share/doc/mythtv-backend/contrib/maintenance/optimize_mythdb.pl

Issue that as a command (cut and paste it), complete with the .pl a the end.
```
/usr/share/doc/mythtv-backend/contrib/maintenance/optimize_mythdb.pl
```

Should work.  HTH
Phil

---

### Post by neutron68 on 2014-05-19
Hi Phil,

Yes, agreed.  The optimize_mythdb.pl scirpt is in the same location on my machine.
Yesterday afternoon, I was able to successfully make my own script that calls that .pl script (same as you just suggested), and it does work.

What I'm pointing out is that the Mythbuntu Control Centre puts a script called "optimize_mythdb" (not "optimize_mythdb.pl") into the /etc/cron.daily folder, and it does not work.

Bottom line:  Anyone relying on this script to automatically fix their database, is not protected!  

This should probably get fixed?  Yes?

---

### Post by khPWXxF on 2014-05-19
Hi Eric,
   Sorry - I missed the point you made.  Agreed it's a bug though the important thing is the backup.  Optimising (just can't get used to those Z's) is only icing on the cake.
Did you hit the Control Centre bug which prevents you changing anything?

Phil

---

### Post by blm-ubunet on 2014-05-19
Note that mysql.txt file was deprecated some release(s) ago.
The file(s) in question are config.xml

2c worth..
You can easily (manually) run the dB scripts from mythweb.
Unless your machine is crashing repeatedly I would think running the maintenance script(s) once per week is adequate.
Don't forget about dB backups.

---

### Post by khPWXxF on 2014-05-20
A good point, but I was going by the OPs profile and his search tags of 12.04.
Phil

---

### Post by blm-ubunet on 2014-05-20
As you say..the OP could be using old unsupported 0.25.

12.04 can use 0.27+fixes via mythbuntu repos.

The use of mysql.txt file was deprecated from 0.26.
[http://www.mythtv.org/wiki/Release_Notes_-_0.26#Special_Notices_.26_Instructions](http://www.mythtv.org/wiki/Release_Notes_-_0.26#Special_Notices_.26_Instructions)

---

### Post by neutron68 on 2014-05-23
Hi khPWXxF,

No, I've never seen the Control Centre bug that keeps you from changing anything.  Sounds frustraiting!

Here are the specifics of the system where the automatically-installed script wasn't working:

Mythbuntu Version: 12.04
MythTV Version : v0.25.3-49-gb5adf03
MythTV Branch : fixes/0.25
Network Protocol : 72
Library API : 0.25.20130225-1
QT Version : 4.8.1

I am helping a friend keep his system running in good order.  
I have a system with the same versions on it.
He has been having random lockups and that appears to be corrupting records in the mythconverg database.

Back in January, I advised my friend to activate the automatic database scanning/fixing scripts from the Mythbuntu Control Centre.
I just expected them to work.
When he continued to have database problems, I looked into his /etc/cron.daily directory to see what the Control Centre put in there.
That's when I discovered that the script bombs out and doesn't do anything.

What are the highest known-working versions being used now?
I've been hesitant to upgrade from 12.04, Myth 0.25.3 and fixes/0.25.
I've learned that every time you switch versions, new bugs appear and you have to spend a weekend or 2 chasing them down.

I've not found an easy to use, complete backup system for Mythbuntu.
As far as I can see, the only way to have an easily restorable complete Mythbuntu backup is to make a bit-for bit clone of your hard drive to another hard drive.

Eric

---

### Post by blm-ubunet on 2014-05-23
You don't need to tie the ubuntu version to the mythtv upgrade.
Mythbuntu team provide 0.27+fixes for 12.04 LTS.
You don't need to update mythbuntu distro to upgrade mythtv package.

There has been one meaningful commit to 0.25+fixes in the last year..Everything else is 2 years or older.

[http://smolt.mythtv.org/static/stats/stats.html](http://smolt.mythtv.org/static/stats/stats.html)
More users (that have submitted stats) are using 0.27 (& later) than 0.25.

Master (git) runs very well on 10.04-LTS (& no crashes).
After the last couple of commits it works >= than it ever worked.
These commits will get into 0.27+fixes after wider testing/reporting.

The release notes for each version document the possible gotchas.
[http://www.mythtv.org/wiki/Category:Release_Notes](http://www.mythtv.org/wiki/Category:Release_Notes)

---

