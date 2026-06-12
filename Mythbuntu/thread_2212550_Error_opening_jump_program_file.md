---
title: "Error opening jump program file"
date: 2014-03-21
forum: Mythbuntu
---

### Post by loggerhead on 2014-03-21
I've recently installed mythtv and I've run into this error when switching from SD stations to an HD station.  I've searched and searched online, unable to find a solution that works for me (mythtv won't let me assign a starting station that is HD instead of SD, for some reason).  [Here is a thread]("http://ubuntuforums.org/showthread.php?t=1309997&highlight=Error+opening+jump+program+file") that outlines multiple people with this same issue.  It has been closed and I don't seem to see too many new threads with this issue, which is making me wonder if I'm missing something simple.  I originally had installed 0.24, but I upgraded to 0.27 last night and the problem persists.  I'm wondering if I had issues with the upgrade, even though when I check this

```
[COLOR=#000000][FONT=Ubuntu Mono]apt-cache policy mythtv[/FONT][/COLOR]
```

It shows 0.27 as installed and candidate, though nothing seems different from 0.24 to 0.27

Any thoughts would be greatly appreciated since I've been pulling my hair out over this one.

Thanks!

---

### Post by blm-ubunet on 2014-03-21
logfiles??
BE logs when you try to tune the HD channel..

DVB-T(@2 or S2 or C ???

Can you record this HD channel?
Can you play this recording in mythtv?

---

### Post by loggerhead on 2014-03-21
I'll be able to post my log files when I'm at my computer later tonight. Like the thread above, I can record these hd stations and watch them, even a second after they start recording. I just can't jump to them on live TV. All watching is done on a front-end that is the same computer as the backend in mythtv. 

Pardon my ignorance, but I'm not certain what you mean by DVB-T. I have an hdhomerun dual tuner that is getting unencrypted ASTC broadcast stations locally, nothing more.

---

### Post by blm-ubunet on 2014-03-22
ASTC is the US version of the international std DVB-T.

Are you using the 0/27+fixes ppa from mythbuntu repos?

Probably need to start the FE with extra logging..maybe:
```
mythfrontend -v all --loglevel=debug > BE-logfile.txt

```

---

### Post by loggerhead on 2014-03-22
So I deleted some channels that mythtv found that aren't really there and it seems to have solved my problem. I was able to choose and HD channel as default and it worked. Thanks for the help!

---

### Post by purza on 2014-04-09
I had a similar problem when I set the channel to a Comcast Music Channel 400 and something.  After doing a couple of google searches came across this link [http://www.mythtv.org/pipermail/mythtv-users/2012-January/325684.html](http://www.mythtv.org/pipermail/mythtv-users/2012-January/325684.html) and was able to clear the error and watch live TV again.

Can anyone tell me why a Comcast Music Channel would cause this?  I am running a clean install of Mythbuntu Precise 12.04 Mythtv 25 using a Ceton InfiniTV PCIe 4 Channel card.  Does comcast use a different encoding scheme etc for their music channels not recognized by Myth or the Ceton card.  I haven't checked if they were clear... CC01,2 or 3 (restricted)

---

