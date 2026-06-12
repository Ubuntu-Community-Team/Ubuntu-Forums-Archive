---
title: "Anyone using Mythbuntu 12.04 w/ MythTV .26 w/ PVR-* cards?"
date: 2012-12-04
forum: Mythbuntu
---

### Post by dannyboy79 on 2012-12-04
I have a current system with 1 PVR-350 and 1 PVR-500 which is running mythbuntu 10.04.4 and 0.23.1+fixes. All is running perfectly. I have been considering moving to 12.04.1 and MythTV 0.26 but I want to be certain that it's not plagued with the zero byte recordings bug that I was reading about. Can anyone confirm all is well using the PVR-* analog cards with MythTV .26 and Mythbuntu 12.04.1? I saw that Mythbuntu 12.04.1 is based with MythTV .25.2, is there an option to get .26 using mythbuntu repos?

I would run a "test" with a live cd if I could but the system is an old Dell Dimension 8200 and only has 256 of RAM so it wouldn't pan out to well! I just noticed that Mythbuntu 12.04.1 requires 512 mb of ram and 2gb is suggested. What if the system is just going to be a headless server? No gui needed? Can I somehow use an Xubuntu alternate install disc, then add the mythbuntu repos and get my box equivalent to running Mythbuntu 12.04.1 with MythTV .26? I will just admin it over ssh or a tty session as I do now.

---

### Post by klc5555 on 2012-12-04
> **dannyboy79 said:**
> I just noticed that Mythbuntu 12.04.1 requires 512 mb of ram and 2gb is suggested. What if the system is just going to be a headless server? No gui needed? 

I don't think there's any supported configuration for any flavor of Ubuntu to run without X and a gui going. That's why I only use Ubuntu on frontend machines nowadays --I couldn't see having X a gui and the graphical-shell Network Manager running on backend-only machines that never have a monitor hooked to them.

---

### Post by dannyboy79 on 2012-12-04
ubuntu minimal cd. :)

---

### Post by klc5555 on 2012-12-04
I stand corrected. :)

Also I suppose the server edition would give you this capability. You could probably still do a pure backend in 256M RAM. Out of curiosity, would you use wicd or a network startup script for your X-less networking?

---

### Post by GaryP2 on 2012-12-04
Presumably the [ivtv (PVR-*) bug]("http://code.mythtv.org/trac/ticket/10732#") has been patched. Someone [commented]("http://code.mythtv.org/trac/ticket/10732#comment:43") that the patch fixed the latest release of .25. 
 
I haven’t yet upgraded my system but hoping to sometime soon.

---

### Post by dannyboy79 on 2012-12-06
> **klc5555 said:**
> I stand corrected. :)

Also I suppose the server edition would give you this capability. You could probably still do a pure backend in 256M RAM. Out of curiosity, would you use wicd or a network startup script for your X-less networking?not sure what you mean, my Dell Dimension 8200 which this will be installed on doesn't have a wireless card, only ethernet and there are already is a startup script for networking. I just edit the /etc/network/interfaces file and I am all set.

---

### Post by klc5555 on 2012-12-06
> **dannyboy79 said:**
> not sure what you mean, my Dell Dimension 8200 which this will be installed on doesn't have a wireless card, only ethernet and there are already is a startup script for networking. I just edit the /etc/network/interfaces file and I am all set.

Ah. Much like Network Mangler itself, wicd is both a wired _and_ a wireless manager; it just does its job without X (though various gui interfaces are available if you wish to configure/use it in X) Just configuring /etc/network/interfaces is at least as good for an ethernet connection, of course, since it shouldn't require wicd's auto-reconnect capabilities like wireless usually does. 

I was just a bit curious about which of the two or three easiest non-X methods for configuring the network your mini-CD-based installation used.

---

### Post by nickrout on 2012-12-06
> **GaryP2 said:**
> Presumably the [ivtv (PVR-*) bug]("http://code.mythtv.org/trac/ticket/10732#") has been patched. Someone [commented]("http://code.mythtv.org/trac/ticket/10732#comment:43") that the patch fixed the latest release of .25. 
 
I haven&#8217;t yet upgraded my system but hoping to sometime soon.Yes you can see quite clearly here [https://github.com/MythTV/mythtv/commits/fixes/0.25](https://github.com/MythTV/mythtv/commits/fixes/0.25) that the patch was applied on 29 November by stuartm. Commit number starts 11ef56

---

### Post by azmyth on 2012-12-08
When 0.26 came out I tried it using a pvr-150 on 10.04. Unfortunately, when the channel had a transition I ended up with video buffer issue and then it dumped me back to the FE. I never had this issue with 0.25 so I ended up downgrading. 

This is the same bug as this

[http://code.mythtv.org/trac/ticket/11175](http://code.mythtv.org/trac/ticket/11175)

I don't know if it a bug or if it is my system.

---

### Post by mookie60 on 2013-01-22
Until early last December, I had no issues with a pvr150 and hvr1600(analog side) running 10.04/.25.   

For an early xmas present, I assembled a new machine and installed 12.04 with .25.   Turned on the .25 repos and have done all updates.  

Could no longer scan either tuner, but using the old channel data the tuners still recorded.   Live tv on either of the tuners also worked, but took about 15 seconds for a channel change.  Since I didn't use live tv, it didn't matter.   Commercial markings also failed to work since the switch to 12.04 (the process occurs, but nothing is marked).

I was still content with it till a few days ago when the 150 recordings became distorted, some weird mix of multiple images and snow.   The 1600 recordings were still ok.

Removed the 150 today and deleted its capture card into in the backend.   Upon reboot, the 1600 was no longer detected by Mythtv, it is found with lspci.  Remove/reinstall in different slots - nothing.  The 150 is still detected, but all the recordings are unwatchable (distorted multiple images).   It's doubtful that both cards have failed at the same time.

I'm giving up.   Getting ready to put 10.04 on a usb stick; I'll boot from that and see if the cards are detected/working.

Hope your upgrade goes better than mine.

update:  Before doing anything with 10.04, I tried 12.04/.26 - as .26 was dannyboy's original question.  The pvr150 is tuning much quicker with "live tv" and seems to record correctly again.   The analog side of the 1600 is still not found by Myth.  The analog 1600 is found with lspci, and functional with 10.04.

---

### Post by nightwar on 2013-02-08
I have been using mythtv/mythbuntu since version 7.10, version 7-11 worked great!  I have a pvr-150 and a pvr-350 in the backend. 

Earlier, near the beginning of November 2012 I tried to upgrade mythtv(Like I normally do, I wait 6 months or so for issues to be fixed).....

I upgrade frontend and the backend, rebooted and Live TV stopped working...

I ended up spending a good full day reinstalling everything from the CD to finally get everything working right again...

Later I seen there was a fix released around Nov. 29, 2012 which may have fixed the problem, so I tried again to upgrade in the middle of January, the fix did not work for live tv, so I again tried to upgrade to 0.26 and live tv did not work.... spent another day reinstalling.

Please don't take this thread as a "complaint" for having to reinstall, its just frustrating. I want to be on the latest version of mythtv, however live tv will not work for me on the pvr series of cards.


So, searching around today I was reading the code fixes:

[http://code.mythtv.org/trac/ticket/11229]("http://code.mythtv.org/trac/ticket/11229")


so my question: the last comment in the link says a fix was pushed to 0.26 that may have fixed the problem..

"v0.26.0-93-ga1b9b1f" is the version that contains the fix.  I was wondering if anyone with a pvr-150 is running that version, and has functional live tv?


Beyond that, im open to suggestions for tv tuner cards that do work with live tv. 

I have time warner cable and have the coax plugged into the pvr-150(I get channels 2-99) no digital, no tv antenna, just ntsc cable.

My last option at this point is to go back version 10 of mythbuntu where I had stability with live tv.

---

### Post by GaryP2 on 2013-02-09
It looks like it might be fixed. I don&#8217;t use Live TV very often, and when I do I watch an HD channel from an HDHR. So I don&#8217;t have lot of experience with it. But after seeing your question I tried Live TV against channels coming from a PVR-150 tuner and the frontend would successful tune the first analog channel but fail with a buffer error whenever I tried to switch to a second analog channel. I tried that same scenarios a few times after the update I did this morning and it didn&#8217;t fail for me. 

It looks promising, but again I don&#8217;t use Live TV much so I won&#8217;t be testing it very extensively. Here is my old and new version info.

It failed under (last updated Dec 8 2012):
```
myth@mythbe0:~$ mythfrontend --version
xprop:  unable to open display ''
Please attach all output as a file in bug reports.
MythTV Version : v0.26.0-55-g09ac5b2
MythTV Branch : fixes/0.26
Network Protocol : 75
Library API : 0.26.20120822-1
QT Version : 4.8.1

Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-34-generic x86_64)
```

It worked for me under (updated this morning Feb 9 2013):
```
myth@mythbe0:~$ mythfrontend --version
xprop:  unable to open display ''
Please attach all output as a file in bug reports.
MythTV Version : v0.26.0-93-ga1b9b1f
MythTV Branch : fixes/0.26
Network Protocol : 75
Library API : 0.26.20130112-1
QT Version : 4.8.1

Ubuntu 12.04.2 LTS (GNU/Linux 3.2.0-37-generic x86_64)
```

---

### Post by mad73 on 2013-07-18
Hello 

I recently installed mythbuntu, version 12.04.2 and can't get my Hauppauge PVR-150 (Nova-S-Plus) get working. I have configured it as described in [https://help.ubuntu.com/community/MythTV_DVB-S](https://help.ubuntu.com/community/MythTV_DVB-S) 
it is possible to configure the tuner card, there is a text showing that a Conexant chip was found. When I return to the card-config-menu there is an error-message saying that access to the card is not possible. I don't know if access to the card is using ivtv driver (that now should be integrated in the kernel) as this was the case in former editions. But I can't record any tv show with ivtv-tune and cat /dev/... > movie.mpg.

Any help is greatly apreciated. Also some hints where I could find the reason of this behaviour.

Thank you.

---

### Post by nickrout on 2013-07-19
You are seriously confused. The PVR-150 is not a DVB-S card.

---

