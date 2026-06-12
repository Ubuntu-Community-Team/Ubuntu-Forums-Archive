---
title: "mythtv is filling my /var/lib/mythtv with crap, help needed"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by mja on 2007-02-06
Hi,
I really like Mythtv now that I've got it up and running. However, there's one annoying thing that makes me ](*,) 

Whenever I start watching something, it gets recorded in /var/lib/mythtv. Even if I stop the frontend, the recording still continues I think. How do I stop this? I only want Mythtv to record the shows that I schedule for recording. I'm going abroad soon and my girlfriend does not want to manually delete all the mpgs that mythtv records and the recordings fill the hard drive quite quickly..

Any help appreciated.

Yours,
Miika

---

### Post by techstop on 2007-02-06
> **mja said:**
> Hi,
I really like Mythtv now that I've got it up and running. However, there's one annoying thing that makes me ](*,) 

Whenever I start watching something, it gets recorded in /var/lib/mythtv. Even if I stop the frontend, the recording still continues I think. How do I stop this? I only want Mythtv to record the shows that I schedule for recording. I'm going abroad soon and my girlfriend does not want to manually delete all the mpgs that mythtv records and the recordings fill the hard drive quite quickly..

Any help appreciated.

Yours,
Miika

AFAIK, this is just how it works. It records live tv continuously so that you can watch it at any time. The programs that get recorded automatically will also get automatically deleted if there are any manually scheduled programs and not enough disk space. If you go into Information Center->System Status->AutoExpire List you can see all of the programs that will automatically get deleted. You need to set up AutoExpire in the Setup menu as well (Setup->TV Settings->General->AutoExpire). You can reduce the number of days that LiveTV recordings are kept here as well.

---

### Post by mja on 2007-02-06
> **techstop said:**
> AFAIK, this is just how it works. It records live tv continuously so that you can watch it at any time. The programs that get recorded automatically will also get automatically deleted if there are any manually scheduled programs and not enough disk space. If you go into Information Center->System Status->AutoExpire List you can see all of the programs that will automatically get deleted. You need to set up AutoExpire in the Setup menu as well (Setup->TV Settings->General->AutoExpire). You can reduce the number of days that LiveTV recordings are kept here as well.
Thanks for the answers! I'll try these out. I did try going through the menus before btw. but there's just so many different options..

---

### Post by mja on 2007-02-06
I guess the problem I'm having is that I don't keep the computer on all the time. Apparently the old LiveTV-recordings do not get deleted automatically when starting up the computer/mythtv. Any suggestions? I checked that the autoexpire is set to 1 day.

---

### Post by fenian on 2007-02-06
You can change the directory that holds the recordings to one that has full read/write permissions and empty the directory manually when your done with mythtv.On my mythtv box I have a seperate partition (XFS format) strictly for holding recordings.

---

### Post by Roebi on 2007-02-07
> **fenian said:**
> You can change the directory that holds the recordings to one that has full read/write permissions and empty the directory manually when your done with mythtv.On my mythtv box I have a seperate partition (XFS format) strictly for holding recordings.

I think that it is not a good idea to empty the recordings directory manually. Information about the recordings (even LiveTV) are stored in the mythtv database. So even if you have removed a recodring from your disk the database would still have a trace of it, which will end messing up your complete database in the long run.
My best advice would be to try to understand how the auto expire works, configure it to have it remove your recordings quickly, and then you are set.
I know that getting grips on all aspects and settings of mythtv is not done over one night, but in the long run, it will pay off.


Roebi

---

### Post by majoridiot on 2007-02-07
autoexpire will automatically expire the programs for you after 24 hours if you have autoexpire
set to 1.  your best bet is to enable LiveTV in the filters Setup-->TV Settings-->Playback
4th page "view recordings (recording groups)" and make sure the "Show LiveTV recording
when using "All Programs" filter" is checked.  then you can go into manage recordings and
manually delete all of the livetv that hasn't autoexpired.  once this is done, it should be able
to keep up on its own, assuming you have a decent sized HD.

---

### Post by punx45 on 2007-02-07
interesting... my /var/lib/mythtv is empty.
but i don't watch live tv often.

i will check the back/front end settings when i get home (if i remember)

i do remember seeing live tv recordings somewhere when browsing around, maybe my system keeps them in another place.

I have a MythDora system, it may have been set up differently.

__________
Post-Script

Looks like my system puts everything in /video/recordings whether its live or scheduled.

---

