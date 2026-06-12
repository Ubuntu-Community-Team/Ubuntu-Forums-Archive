---
title: "mythtv unable to access mysql in new 16.04LTS / mythtv install"
date: 2017-09-20
forum: Multimedia Software
---

### Post by Mike_Brown on 2017-09-20
My old mythbuntu computer died so I decided to build a new home theater computer using the full verson  Ubuntu 16.04LTS with mythtv, KODI and my HDHomerun tuner.

The LTS installed with no issues, but after installing mythtv and mysql I keep getting the 'unable to find database' error message in myth backend setup. I installed mythtv first using Ubuntu Applications. Since I could not find mysql listed there, I installed it using *sudo apt-get install mysql*.

I set up mysql with mythconverg, mythtv as user, mythtv as password as per the instructions I found here: *[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)*. I have set up the database with a network address (192.168.1.201) instead of 'localhost'.

I have tried the steps over and over, re-booting along the way, to try to get myth backend to find the database, but it never does.

I am able to log into the database through terminal, so I know the database is there & functioning.

This is the error message I got when starting the mythfill database:

[FONT=arial narrow]2017-09-20 17:11:22.419203 E [DBMANAGER0] Unable to connect to database!
2017-09-20 17:11:22.419203 E Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user &#8216;mythtv&#8217;@&#8217;192.168.1.201&#8217; (using password: YES)
 
2017-09-20 17:11:22.419826 E [DBMANAGER0] Unable to connect to database!
2017-09-20 17:11:22.419826 E Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user &#8216;mythtv&#8217;@&#8217;192.168.1.201&#8217; (using password: YES)
 
2017-09-20 17:11:22.420116  I              Testing network connectivity to &#8216;192.168.1.210&#8217;
2017-09-20 17:11:22.420463  I              Starting process manager
2017-09-20 17:11:22.421430  I              Starting process signal handler
2017-09-20 17:11:22.421470  I              Starting IO manager (read)
2017-09-20 17:11:22.421512  I              Starting IO manager (write)
2017-09-20 17:11:22.472244 E              [DBManager1] Unable to connect to database!
2017-09-20 17:11:22.472268 E              Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user &#8216;mythtv&#8217;@&#8217;192.168.1.201&#8217; (using password: YES)[/FONT]

Any assistance will be appreciated.

---

### Post by MoebusNet on 2017-09-30
This is a fairly common issue when using Ubuntu's packages for mythtv because Ubuntu assigns a random password for the mysql database (not mythtv). Check out post #3:

[https://ubuntuforums.org/showthread.php?t=2364872&p=13687510#post13687510](https://ubuntuforums.org/showthread.php?t=2364872&p=13687510#post13687510)

---

### Post by Mike_Brown on 2017-10-09
> **MoebusNet said:**
> This is a fairly common issue when using Ubuntu's packages for mythtv because Ubuntu assigns a random password for the mysql database (not mythtv). Check out post #3:

[https://ubuntuforums.org/showthread.php?t=2364872&p=13687510#post13687510](https://ubuntuforums.org/showthread.php?t=2364872&p=13687510#post13687510)


Tried that many times. I gave up for a while and installed my other apps including TVheadend. TVheadend which worked 1st time with no problems. It records from my antenna with no problems, but I have used Mythtv for years and much prefer it to TVheadend.

I actuall got Mythtv backend to appear to connect to the database and to my HD Homerun. But the frontend does not see the backend to do set up.

When I did my 1st Mythtv set up (Mythbuntu 14.04) I was using linux for the 1st time. I had that set up in 2 days (part time) with no trouble with backend or frontend connecting. I have more Ubuntu experience since then, just can't get Mythtv to work.

Any other ideas?

Thanks for the assistance.

---

### Post by MoebusNet on 2017-10-21
Sorry for your issues; my own dvr went down in flames. I guess Ubuntu is making enough changes with the move away from Unity that the Mythtv devs can't keep up. I tried TVHeadend about 6 months ago and couldn't get it to work; glad it serves for you. All of these, including LinHES and the rest seem to make various tradeoffs of convenience vs customization. I just got VLC working again on my 16.04 boxes (VLC not supporting Nouveau video driver!) so as always this is a work in progress.

I don't have any concrete suggestions other than that this always seems to take constant maintenance. The long-time guys seem, once they achieve a stable Mythtv system, to avoid updates (other than security updates) until such a time as they know they can afford the time to straighten out a broken system. Best of luck!

---

### Post by Mike_Brown on 2017-10-23
> **MoebusNet said:**
> Sorry for your issues; my own dvr went down in flames. I guess Ubuntu is making enough changes with the move away from Unity that the Mythtv devs can't keep up. I tried TVHeadend about 6 months ago and couldn't get it to work; glad it serves for you. All of these, including LinHES and the rest seem to make various tradeoffs of convenience vs customization. I just got VLC working again on my 16.04 boxes (VLC not supporting Nouveau video driver!) so as always this is a work in progress.

I don't have any concrete suggestions other than that this always seems to take constant maintenance. The long-time guys seem, once they achieve a stable Mythtv system, to avoid updates (other than security updates) until such a time as they know they can afford the time to straighten out a broken system. Best of luck!

I haven't had time to work on getting Mythtv to work. I have been using TVHeadend and I think I have it set up and working (using KODI as my frontend). 

I never got my previous Mythtv (Mythbuntu 14.04) to work with any other frontend except for the Myth frontend so it became just a PVR-only appliance. As a result, I had the Mythbuntu computer & a Windows 10 computer for all other HTPC duties. Once the Mythbuntu died I was (am) determined to have only one do-everything HTPC hooked to my receiver & TV.

I really wanted Mythtv to work in that framework. Not getting it to even play nicely with its own frontend has been a deal breaker.

So far, TVHeadend appears to be working nicely with KODI as part of my HTPC system. My main complaint with TVHeadend is setting the directories for the individual TV Series recordings to be saved into. With my previous Mythbuntu, that was easy. The documentation, or lack thereof, in TVHeadend made it difficult to set up the recording end of things in a logical fashion instead of having all recorded shows in one default directory.

You said that you tried TVHeadend about six months ago. You may want to try TVH again. There is a repository for installing online. I believe they have had an update in the past few months. Mine appears to be working pretty good. Good luck.

Thanks again for your assistance.

---

### Post by Doncr on 2017-10-31
Hi - the problem I am having is that my desktop machine is running the bleeding edge version - 17.10 - of Lubuntu, and the server is running the LTS version - 16.04 (?). The latest Lubuntu has Mythtv 0.29, the LTS version is 0.28. So the front and back ends are incompatible.

Oddly enough, Kubuntu 17.10 still has mythtv 0.28.

My dedicated myth boxes - a front end and a back end - generally update without a problem, but I do keep them on LTS versions of Lubuntu (was Mythbuntu - but it is no longer around). It is the front end software on my desktops and laptop that cause the problems - as the versions get updated and the database schemas don't match.

---

### Post by Mike_Brown on 2017-11-01
> **Doncr said:**
> Hi - the problem I am having is that my desktop machine is running the bleeding edge version - 17.10 - of Lubuntu, and the server is running the LTS version - 16.04 (?). The latest Lubuntu has Mythtv 0.29, the LTS version is 0.28. So the front and back ends are incompatible.

Oddly enough, Kubuntu 17.10 still has mythtv 0.28.

My dedicated myth boxes - a front end and a back end - generally update without a problem, but I do keep them on LTS versions of Lubuntu (was Mythbuntu - but it is no longer around). It is the front end software on my desktops and laptop that cause the problems - as the versions get updated and the database schemas don't match.

In my system, both backend & frontend are on the same machine. 

I have put this aside for now since I have TVHeadend working reasonably well with KODI. 

The thing I miss most from my prior Myth setup is the lack of commercial skipping. I have seen that Comskip can be set up to do this with TVHeadend, but haven't gotten around to trying it.

---

