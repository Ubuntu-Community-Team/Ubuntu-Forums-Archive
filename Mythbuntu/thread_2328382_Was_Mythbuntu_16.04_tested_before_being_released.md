---
title: "Was Mythbuntu 16.04 tested before being released?"
date: 2016-06-20
forum: Mythbuntu
---

### Post by iry100fan on 2016-06-20
Sorry if this sounds like a rant, but I guess that's what it is...

I wanted to make a note of all of the problems I have encountered with Mythbuntu 16.04.  This release has given me the impression that nothing was tested, at all, before being released to the public.  I guess it's probably working fine for most users out there, but for me it has been a complete disaster from the start.



Below is a list of the problems that affect me the most...

_**BACKEND**_
[LIST]
[*]In Mythbuntu Control Center, under MySQL Configuration, selecting Enable MySQL Performance Tweaks causes the MySQL database to become inaccessible by the software. 
[*]In MythTV Backend Setup, adding Capture Cards takes an unreasonably long time. When you click on New Capture Card, it takes upwards of 5 minutes to progress to the next screen. 
[*]After capture devices were added, the computer must be restarted for them to work at all.  Just restarting the backend application is not good enough. 
[*]Approximately once a week MythTV "forgets" that any tuners are installed.  When I run the Backend Setup, MythTV shows that they are there but refuses to use them.  I have to delete all of the tuners and re-configure them again so that they work for another week.  One interesting note, the S-Video input on those same tuners works all the time even when the over-the-air postion stops.  (Maybe it has someting to do with the TV tuners being setup as DVB  and the S-Video input set as MPEG-2 Encoder. I don't know.) 
[*]If you try to tune in a weak signal, the Backend application locks-up.  (It seems to consume 100% of all processors causing the computer to become extremely sluggish.) 
[*]In the Mythbuntu Control Senter, under Repositories, clicking on Refresh Available Repositories causes a dialog to appear stating "New DB files downloaded finished" but it never disappears and the Mythbuntu Control Center is locked-up. 
[/LIST]

_**FRONTEND**_
[LIST]
[*]When starting the Mythbuntu Control Center, you are instantly greeted with the error "Exception in applyStateToGUI of plugin Pulgins.  Disabling Plugin."  If you go to the Plugins section and  attempt to install or remove any items, when you click on Apply you are greeted with a dialog box asking if you want to Apply Changes but the Apply button is grayed out. 
[*]In the Mythbuntu Control Center, under MySQL Configuration, if you test the connection, I get a green checkmark but the Mythbuntu Control Center locks up. 
[*]In the Mythbuntu Control Center, under Services, if you attempt to enable or reconfigure the VNC Service, you will get that initial startup error message, another Plugins section will appear at the bottom of the list on the right and but VNC will not be configured. 
[*]In the Mythbuntu Control Senter, under Repositories, clicking on Refresh Available Repositories causes a dialog to appear stating "New DB files downloaded finished" but it never disappears and the Mythbuntu Control Center is locked-up. 
[*]Lastly in the Mythubuntu Control Center, under Proprietary Codec Support, when enabling DVD Support, I get the error "DBus Exception:  org.freedesktop.DBus.Python.UnboundLocalError". 
[*]Running the Software Updater locks-up part way through the update process.  (Retrieving and applying the updates vid apt-get on the command line completes fine.) 
[*]When stating up the Frontend application for the first time, it asks you for the which language you wish to use then aborts and restarts again.  The solution is to manually edit the "config.xml" file with the address, username and password of the backend.  Older versions of Mythbuntu (12.04) used to ask you for that information during setup.  Why must the file be edited manually now? 
[*]Under Setup / Theme Chooser, when downloading some themes, the progress bar will reach the end and then the Frontend application will lock up. 
[*]Under the Media Library / Watch Videos, if you Scan for Changes, new videos do appear and you can navigate through them for a few seconds and then the Frontend application will lock-up. 
[/LIST]

_**RECORDING**_
[LIST]
[*]I can watch LiveTV as long as the Signal is above 75%.  If it falls below that, the Backend locks up.  (On 12.04, I get reliable viewing with signals as little as 40%.) 
[*]Scheduled Recordings do not actually record.  They show up in the Watch Recodings list with a size of 0B.  However, if I am watching LiveTV and hit the record button, it records fine. 
[/LIST]

_**MYTHWEB**_
[LIST]
[*]Under Recorded Programs, everything that was viewed on LiveTV shows up as a separate recording. If you "channel surf", you end up with dozens of very shot recorded programs. 
[*]Also under Recorded Programs, when you try and delete a program it gets duplicated in the list and never disappears.  The only way for me to get rid of the recording is to manually delete the actual file from the hard drive. 
[*]Under the Video's section, I cannot edit any of the descriptions.  Clicking on the Edit button does bring up the Editing diaglog box and you can manipulate everying inside with no problems.  The issue occurrs when you try to "Submit" your edits, I get an error stating "Fatal Error:  !!NoTrans: SQL Error: Data truncated" with a large amount of diagnostic info also being displayed. 
[*]Under the Settings / MythWeb / Video Playback section, I cannot select "Enable Video Playback".  There is an error message stating "Fatal error: Uncaught Error: Call to undefined function split()...". 
[/LIST]



Just to clarify a few points about these notes...

This was not an upgrade.  Since I was jumping two releases of software, I thought it was best to backup my data and erase all of the drives so I could start from a clean slate.

Seeing all of these problems, at first I thought I had a bad ISO image that I downloaded via BitTorrent, so I downloaded it again.  When that made no difference, I changed my installation medium from a USB flash drive to DVD-ROM.  (Which was how I installed previous versions of Mythbuntu.)  Since that also didn't make any difference, I downloaded a new ISO direct from the Mythbuntu website.  Still ended up having the same difficulty.  (I finally did check the MD5SUMS's against my ISOs and they all check out.)

Next I thought possibly I have some weird hardware problem.  (Most of my hardware is going on about 5 or 6 years at this point, except for the hard drives which are much newer.)  So I installed Mythbuntu Frontend/Backend system in a couple of virtual machines on my desktop computer and was met with all of the same issues. (Except the tuner issues as I don't have any tuners on my desktop computer.)

Finally, I went back to Mythbuntu 12.04, which is what I had been running prior to this disaster.  Everything seems to be working perfectly (other than some of the repositories seem to be offline now.)



What's next...

Seeing as version 12.04 is losing support, I guess I'll try and build my Mythbuntu system using version 14.04.  Maybe I'll have better luck not making such a large jump.



Thanks to those who made it this far into the post.  I guess this post makes me seem like an ungrateful individual.  I can certainly appreciate the complexity of this project and also the massive amount of time invested by the many people who work on this.  It is just such a disappointment to me that, from my vantage point, the project went from the minimal problems I encountered using 12.04 to the being completely unusable in 16.04.

-Brian

---

### Post by tgm4883 on 2016-06-22
Regarding the MythTV specific issues, are you using the Mythbuntu repos for 0.28? If not, why not?

---

### Post by iry100fan on 2016-06-29
Hi tgm4883,

Thanks for the reply.

Yes, I was using the Mythbuntu 0.28 repos.  I had enabled them through the Mythbuntu Control Center.

Because of all the troubles encountered in Mythbuntu 16.04, I decided to try 14.04.  So far I have not encountered any major issues and I am running the 0.28 repos.  The only issue was *ffmpeg* is no longer part of the official Ubuntu 14.04 repos, however I found a PPA that let me install it.  Other than that, 14.04 has been up and running perfectly since I posted my rant.

---

### Post by manuel_acs on 2016-07-03
hi,

i can confirm some of your troubles and add some other... 
atm - frontend not in use, because i can't scan for channels :/
(clean install Mythbuntu 16.04)


> **iry100fan said:**
> Sorry if this sounds like a rant, but I guess that's what it is...

I wanted to make a note of all of the problems I have encountered with Mythbuntu 16.04.  This release has given me the impression that nothing was tested, at all, before being released to the public.  I guess it's probably working fine for most users out there, but for me it has been a complete disaster from the start.

... this distro seems far away from "out of the box" ready.
- simple graphical texteditor is not installed (eg mousepad)
- no setup for network
- no mixer for alsa or pulseaudio installed
- not even basic dvb-apps like w-scan or dvb5 installed
- software center blocks mouse instantly after opening and hangs
- and some more, i have suppressed


> **iry100fan said:**
> Below is a list of the problems that affect me the most...

_**BACKEND**_

[LIST]
[*]In MythTV Backend Setup, adding Capture Cards takes an unreasonably long time. When you click on New Capture Card, it takes upwards of 5 minutes to progress to the next screen. 
[*]After capture devices were added, the computer must be restarted for them to work at all.  Just restarting the backend application is not good enough. 
[*]In the Mythbuntu Control Senter, under Repositories, clicking on Refresh Available Repositories causes a dialog to appear stating "New DB files downloaded finished" but it never disappears and the Mythbuntu Control Center is locked-up. 
[/LIST]


 _**FRONTEND**_

[LIST]
[*]In the Mythbuntu Control Center, under MySQL Configuration, if you test the connection, I get a green checkmark but the Mythbuntu Control Center locks up. 
[*]In the Mythbuntu Control Senter, under Repositories, clicking on Refresh Available Repositories causes a dialog to appear stating "New DB files downloaded finished" but it never disappears and the Mythbuntu Control Center is locked-up. 
[*]Lastly in the Mythubuntu Control Center, under Proprietary Codec Support, when enabling DVD Support, I get the error "DBus Exception:  org.freedesktop.DBus.Python.UnboundLocalError". 
[*]Running the Software Updater locks-up part way through the update process.  (Retrieving and applying the updates vid apt-get on the command line completes fine.) 
[*]When stating up the Frontend application for the first time, it asks you for the which language you wish to use then aborts and restarts again.  The solution is to manually edit the "config.xml" file with the address, username and password of the backend.  Older versions of Mythbuntu (12.04) used to ask you for that information during setup.  Why must the file be edited manually now? 
[/LIST]


- the long time to the next screen has maybe todo with the access over the network (DNS?)
- the connection test show a green checkmark, but its a lie ()
- the mcc is not usable... most of the tabs are locked after i apply changes (eg log-grabber, prop-codecs, ...)



> **iry100fan said:**
> Thanks to those who made it this far into the post.  I guess this post makes me seem like an ungrateful individual.  I can certainly appreciate the complexity of this project and also the massive amount of time invested by the many people who work on this.  It is just such a disappointment to me that, from my vantage point, the project went from the minimal problems I encountered using 12.04 to the being completely unusable in 16.04.

-Brian

had also 12.04 shortly in use - but dropped it because of the lacked support of "Unicable / Satellite Channel Router / DIN EN 50494" - its now in and try again... its a pain.

linux in common on desktop/htpc have a big problem - sad, several things did not work out of the box. hope this will change

---

### Post by Paulgirardin on 2016-08-19
I am also having many of the same problems.It appears one problem with my HVR2200 tuners is that systemd is starting mythbackend before the tuners have enough time to initialise.
I may end up going to 14.04 if I can't find solutions to these bugs.

---

### Post by gottabefoss on 2016-08-21
The more I read about ongoing problems with 16.04 the more I'm determined to stay on 14.04 until 2019. I tried a fresh install of 16.04 when it was released in a VM (for testing) and ran into most of these problems. Was hoping they'd be fixed in 16.04.1 or upstream from other package devs (mythbuntu? mythtv?) but it seems like most of them are still there. Probably the upgrades to PHP7, mysql to 5.7, mythtv to .28, and switching to systemctl all at once were just way too many large changes to deal with at the same time.

.28 mythtv (+ repos) and the 14.04.5 hardware enablement stack (4.4 kernel, new video drivers) get you most of the current benefits of 16.04 for dedicated htpc/mythbox purposes anyway.

---

### Post by 4partee on 2016-09-24
If you click on release notes at [http://www.mythbuntu.org/download-type]("http://www.mythbuntu.org/download-type") you see NOTHING.
NOTHING?
Was 14.04.2 slapped onto a 16.04 base?

I did get a BE/FE to run with 16.04.1.  

However I also cannot get an FE to work.  At first It kept repeating the country-language screen.

I did modify /etc/mythtv/config.xml by changing localhost to 192.168.0.31 and got the FE menu, however, now I get "cannot connect to backend server".  That is a 10 year old problem!  C'mon Mythbuntu, is it time for an appliance yet?

I Agree with gottabefoss.  Too many changes in the 16.04 base( and that is another BIG topic..., changes for what purpose?).  

Are we looking at the demise of Mythbuntu?  After all, nothing lasts forever.  WMC is gone as well.

I'll use 16.04.1 this weekend for sports shows while I fiddle around with the FE, but next week I will probably be back to 14.04.2.

I use hdhomerun tuners.  Did you know that they(Silicon Dust) is working on their own DVR solution right now?  

John

---

### Post by gottabefoss on 2016-09-24
> **4partee said:**
> C'mon Mythbuntu, is it time for an appliance yet?



LinHES ([http://linhes.org/](http://linhes.org/)) (formerly [COLOR=#001220][FONT=Georgia]KnoppMyth) [/FONT][/COLOR] is a mythtv distribution that is much more appliance-like than mythbuntu, and is based on a highly-customized version of arch linux. I've only tested it in a VM, as apparently migrating a mythtv database from mythbuntu to LinHES is difficult, if not impossible, because of the highly-customized mythtv menus LinHES uses to hide linux complexity underneath -- all system tasks, updates, etc are handled through the mythtv frontend without needing to drop to a command-line. And of course, mythtv puts all its menus in the master database because reasons.

So switching requires basically nuking everything and starting over, which I'm not prepared to do at the moment. 

Earlier versions of LinHES wouldn't boot on my hardware, but the current version is based on linux 4.6 kernel and a more recent Xwindows stack, so if you're willing to start over, LinHES might be worth a try.

---

### Post by 4partee on 2016-09-24
gottabefoss;

Thanks for that link,  I will check that out.

Do we still need to comment out bind-address in my.cnf?

my.cnf is very different now in that it is a series of two links; first to /etc/alternatives and then back to a different file /etc/mysql/mysql.cnf.  It gets funny from there because if you cat my.cnf, you see mysql.cnf which contains two !include commands.

What do you see if you run 'grep -r bind-address /etc/mysql/*' ?

I got two lines and I commented out both lines.

John

---

### Post by vidtek on 2017-02-20
> **iry100fan said:**
> Sorry if this sounds like a rant, but I guess that's what it is...

I wanted to make a note of all of the problems I have encountered with Mythbuntu 16.04.  This release has given me the impression that nothing was tested, at all, before being released to the public.  I guess it's probably working fine for most users out there, but for me it has been a complete disaster from the start.



Below is a list of the problems that affect me the most...

_**BACKEND**_
[LIST]
[*]In Mythbuntu Control Center, under MySQL Configuration, selecting Enable MySQL Performance Tweaks causes the MySQL database to become inaccessible by the software. 
[*]In MythTV Backend Setup, adding Capture Cards takes an unreasonably long time. When you click on New Capture Card, it takes upwards of 5 minutes to progress to the next screen. 
[*]After capture devices were added, the computer must be restarted for them to work at all.  Just restarting the backend application is not good enough. 
[*]Approximately once a week MythTV "forgets" that any tuners are installed.  When I run the Backend Setup, MythTV shows that they are there but refuses to use them.  I have to delete all of the tuners and re-configure them again so that they work for another week.  One interesting note, the S-Video input on those same tuners works all the time even when the over-the-air postion stops.  (Maybe it has someting to do with the TV tuners being setup as DVB  and the S-Video input set as MPEG-2 Encoder. I don't know.) 
[*]If you try to tune in a weak signal, the Backend application locks-up.  (It seems to consume 100% of all processors causing the computer to become extremely sluggish.) 
[*]In the Mythbuntu Control Senter, under Repositories, clicking on Refresh Available Repositories causes a dialog to appear stating "New DB files downloaded finished" but it never disappears and the Mythbuntu Control Center is locked-up. 
[/LIST]

_**FRONTEND**_
[LIST]
[*]When starting the Mythbuntu Control Center, you are instantly greeted with the error "Exception in applyStateToGUI of plugin Pulgins.  Disabling Plugin."  If you go to the Plugins section and  attempt to install or remove any items, when you click on Apply you are greeted with a dialog box asking if you want to Apply Changes but the Apply button is grayed out. 
[*]In the Mythbuntu Control Center, under MySQL Configuration, if you test the connection, I get a green checkmark but the Mythbuntu Control Center locks up. 
[*]In the Mythbuntu Control Center, under Services, if you attempt to enable or reconfigure the VNC Service, you will get that initial startup error message, another Plugins section will appear at the bottom of the list on the right and but VNC will not be configured. 
[*]In the Mythbuntu Control Senter, under Repositories, clicking on Refresh Available Repositories causes a dialog to appear stating "New DB files downloaded finished" but it never disappears and the Mythbuntu Control Center is locked-up. 
[*]Lastly in the Mythubuntu Control Center, under Proprietary Codec Support, when enabling DVD Support, I get the error "DBus Exception:  org.freedesktop.DBus.Python.UnboundLocalError". 
[*]Running the Software Updater locks-up part way through the update process.  (Retrieving and applying the updates vid apt-get on the command line completes fine.) 
[*]When stating up the Frontend application for the first time, it asks you for the which language you wish to use then aborts and restarts again.  The solution is to manually edit the "config.xml" file with the address, username and password of the backend.  Older versions of Mythbuntu (12.04) used to ask you for that information during setup.  Why must the file be edited manually now? 
[*]Under Setup / Theme Chooser, when downloading some themes, the progress bar will reach the end and then the Frontend application will lock up. 
[*]Under the Media Library / Watch Videos, if you Scan for Changes, new videos do appear and you can navigate through them for a few seconds and then the Frontend application will lock-up. 
[/LIST]

_**RECORDING**_
[LIST]
[*]I can watch LiveTV as long as the Signal is above 75%.  If it falls below that, the Backend locks up.  (On 12.04, I get reliable viewing with signals as little as 40%.) 
[*]Scheduled Recordings do not actually record.  They show up in the Watch Recodings list with a size of 0B.  However, if I am watching LiveTV and hit the record button, it records fine. 
[/LIST]

_**MYTHWEB**_
[LIST]
[*]Under Recorded Programs, everything that was viewed on LiveTV shows up as a separate recording. If you "channel surf", you end up with dozens of very shot recorded programs. 
[*]Also under Recorded Programs, when you try and delete a program it gets duplicated in the list and never disappears.  The only way for me to get rid of the recording is to manually delete the actual file from the hard drive. 
[*]Under the Video's section, I cannot edit any of the descriptions.  Clicking on the Edit button does bring up the Editing diaglog box and you can manipulate everying inside with no problems.  The issue occurrs when you try to "Submit" your edits, I get an error stating "Fatal Error:  !!NoTrans: SQL Error: Data truncated" with a large amount of diagnostic info also being displayed. 
[*]Under the Settings / MythWeb / Video Playback section, I cannot select "Enable Video Playback".  There is an error message stating "Fatal error: Uncaught Error: Call to undefined function split()...". 
[/LIST]



Just to clarify a few points about these notes...

This was not an upgrade.  Since I was jumping two releases of software, I thought it was best to backup my data and erase all of the drives so I could start from a clean slate.

Seeing all of these problems, at first I thought I had a bad ISO image that I downloaded via BitTorrent, so I downloaded it again.  When that made no difference, I changed my installation medium from a USB flash drive to DVD-ROM.  (Which was how I installed previous versions of Mythbuntu.)  Since that also didn't make any difference, I downloaded a new ISO direct from the Mythbuntu website.  Still ended up having the same difficulty.  (I finally did check the MD5SUMS's against my ISOs and they all check out.)

Next I thought possibly I have some weird hardware problem.  (Most of my hardware is going on about 5 or 6 years at this point, except for the hard drives which are much newer.)  So I installed Mythbuntu Frontend/Backend system in a couple of virtual machines on my desktop computer and was met with all of the same issues. (Except the tuner issues as I don't have any tuners on my desktop computer.)

Finally, I went back to Mythbuntu 12.04, which is what I had been running prior to this disaster.  Everything seems to be working perfectly (other than some of the repositories seem to be offline now.)



What's next...

Seeing as version 12.04 is losing support, I guess I'll try and build my Mythbuntu system using version 14.04.  Maybe I'll have better luck not making such a large jump.



Thanks to those who made it this far into the post.  I guess this post makes me seem like an ungrateful individual.  I can certainly appreciate the complexity of this project and also the massive amount of time invested by the many people who work on this.  It is just such a disappointment to me that, from my vantage point, the project went from the minimal problems I encountered using 12.04 to the being completely unusable in 16.04.

-Brian

Brian-
I've been using Mythbuntu since about 2002, and have to admit, this one is a doozy.  I like to use my setup as a be/fe combined as I use the machine as a desktop too.  
What I normally do is to install Mythbuntu then install the KDE desktop over the top and it has worked for many years this way, albeit with problems.  I tried in vain to do the same with 16.04, but finally gave up, and installed Mint 18 KDE and stuck Mythtv on top.  This is working reasonably well, a few minor issues, MCC has a problem with the repos not working again, but everything else is going ok.  I downgraded from 0.29 to 0.28 this time.  Mint 18 KDE is smooth as silk, for a linux experience it is the best I've ever had.  

It took less than 20 mins to install (and three weeks to get hardware and software to my liking).  I have some pretty strange stuff, 8 physical tuners, a box that is 20 feet, 2 walls and another storey away from my 55" tv in the front room.  Extension cables for my HDMI, network, speakers and USB's (2 and 3) remote dongles, and a  remote physical switch tapped into the case on/off switch of my box. Connections to my central heating and underfloor heating systems round off the bunch.
At least now I'm back in blighty I no longer have to interface my swimming pool controller (the only way I could run that was in a VM using the windaz app.).

Now that the Mythbuntu is dead, you might want to consider going the Mint route I did, I really think it's the best alternative.

Cheers, Tony.

---

### Post by Rocko262c on 2017-04-26
Dear Tony,

I am extremely sad that Mythbuntu had ended as I have been using Mythbuntu for almost 8 years now.

I am considering trying my hand at "building from the source", but before that i was thinking about your suggestion of installing Mint 18 KDE and then installing Mythtv on top. When you do this, and restart the computer, will it automatically start the frontend of Mythtv as Mythbuntu did?

Cheers,
Rocko262c

---

### Post by tgm4883 on 2017-04-26
> **Rocko262c said:**
> Dear Tony,

I am extremely sad that Mythbuntu had ended as I have been using Mythbuntu for almost 8 years now.

I am considering trying my hand at "building from the source", but before that i was thinking about your suggestion of installing Mint 18 KDE and then installing Mythtv on top. When you do this, and restart the computer, will it automatically start the frontend of Mythtv as Mythbuntu did?

Cheers,
Rocko262c


There isn't a need to build from source, as the Mythbuntu team will continue to build packages for MythTV. There isn't a need to go to Mint either, as you can install Xubuntu and set MythTV to start at boot. This would give you the same functionality as a Mythbuntu system (since Mythbuntu was using Xubuntu parts underneath)

---

### Post by Rocko262c on 2017-04-27
> **tgm4883 said:**
> There isn't a need to build from source, as the Mythbuntu team will continue to build packages for MythTV. There isn't a need to go to Mint either, as you can install Xubuntu and set MythTV to start at boot. This would give you the same functionality as a Mythbuntu system (since Mythbuntu was using Xubuntu parts underneath)

Dear Tony,

Thanks for your kind help. I had no idea that I could set MythTV to start at boot, this is the perfect option for my small children.

Cheers,
Rocko262c

---

