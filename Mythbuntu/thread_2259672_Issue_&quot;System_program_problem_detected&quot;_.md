---
title: "Issue: &quot;System program problem detected&quot; Help needed!"
date: 2015-01-06
forum: Mythbuntu
---

### Post by klaus8 on 2015-01-06
Dear All,
got once a day the dialog "System program problem detected" on  my MythTV backend, and it seems it then let my XBMC/KODI exsits on my frontend computer, and hence need to start XBMC/KODI agian. That **** off Wife :-)

I think what happens is what is written in this wiki --> [http://wiki.robotz.com/index.php/Mythbuntu](http://wiki.robotz.com/index.php/Mythbuntu) area regarding "[COLOR=#000000][FONT=sans-serif]unexplained crashes". Anyone got a solution to this? I have read that this was a commen issue on 0.25-0.26, but I am Mythbuntu 14.04.1 and hence 0.27.4?

Any help very much appriciated!

/Klaus[/FONT][/COLOR]

---

### Post by kpatz on 2015-01-06
Try deleting the files in /var/crash.  When something crashes a log is written there and then you'll get the "system program problem detected" on every boot afterward.

---

### Post by klaus8 on 2015-01-06
ok.....gonna try that-96

logfiles:

[http://pastebin.com/438HLnxP](http://pastebin.com/438HLnxP)

---

### Post by klaus8 on 2015-01-08
Hi agian,
I tried the above, but still I get errors! It seems to me that MythTV backend simply crash once or twice each 24 hours (it have done that for the 3-4 months I have used MythTV; never happend with DVBlogic+WMC), wich generates a myhtbackedn crash report........as I am on xbmc clint frontend on other computer I see this happens as connection is broken and the restroed a few minuts after! VEry frustrating!

---

### Post by khPWXxF on 2015-01-09
Does the name of the file in /var/crash and the time created give a clue?
What is in the back end log at that time?  It is at
/var/log/mythtv/mythbackend.log
Phil

---

### Post by tgm4883 on 2015-01-09
> **klaus8 said:**
> Dear All,
got once a day the dialog "System program problem detected" on  my MythTV backend, and it seems it then let my XBMC/KODI exsits on my frontend computer, and hence need to start XBMC/KODI agian. That **** off Wife :-)

I think what happens is what is written in this wiki --> [http://wiki.robotz.com/index.php/Mythbuntu](http://wiki.robotz.com/index.php/Mythbuntu) area regarding "[COLOR=#000000][FONT=sans-serif]unexplained crashes". Anyone got a solution to this? I have read that this was a commen issue on 0.25-0.26, but I am Mythbuntu 14.04.1 and hence 0.27.4?

Any help very much appriciated!

/Klaus[/FONT][/COLOR]

That is a terrible wiki page riddled with errors.

---

### Post by alien878 on 2015-01-19
I find that backend crashes are often DB related.  There is a script (optimize_mythdb.pl) that can often fix these problems.  I suggest you try running it.  I forget where it is, but if you do a "sudo find / -name optimize_mythdb.pl" you should find it.

Another useful script is find_orphans.py.  The problems it fixes usually don't cause crashes, but it does clean up orphaned files and DB entries.

---

### Post by nainsurvolte on 2015-01-22
Have you done a system upgrade lately? This weekend, I went from 12.04 to 14.04. Following the upgrade I had something similar to that in behavior. Trying to solve issues I had with the array of drives I have or the mythtv database, I had constantly system error detected messages at log on and sometimes out of nowhere and I could hear my client (Kodi) making the sound of loosing connection to mythtv backend.

Since I had so many weird problem, and since my mythtv setup dated from Ubuntu 11.10/ mythtv 0.24? and was upgraded ever since, I simply decided to backup the database and do fresh install... problem solved (and the kids/wife one too, ;).

That may not be the way you wish to take, but at least, I can tell you the issue is not from Mythtv-Kodi relationship. It now works fine.

Good luck,

---

### Post by jgelm on 2015-12-18
I have a fresh install, Dec 4, 2015, of 14.04.2 that is throwing this error very often.  Google searches say to disable apport.  If there is something wrong with apport, it should be fixed in an official update by now as this seems to go back at least 3 years.

I really am having problems like zero length recordings and recordings that show as recording in UPCOMING RECORDINGS that should have been done hours before. E.g, started yesterday at 8PM but still showing the next morning.  

Another thing I notice is that when you do try to use the 'report problem' button things do not go well.  After giving my password, I click 'relaunch' on the next screen.  You would thing that the backend would be restarted but, it is not!  After filing two reports within minutes of each other, I checked system information only to find that the backend had been up for 1 day 11/48min.  Relaunch does not work.  Plus any recordings are FUBARed.  I must either kill the backend or reboot the entire machine.

This situation is really bad because I plan to be away for about 3 months and unable to babysit this mess.

Here is a good ?

Is the problem with myth

or 

buntu?

hmmmmm!

John

---

