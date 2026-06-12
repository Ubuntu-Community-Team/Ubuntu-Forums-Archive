---
title: "New MythBuntu Install - Audio CD, Rip, Remote, DB errors all fail from fresh install"
date: 2012-10-07
forum: Mythbuntu
---

### Post by fscottf1 on 2012-10-07
As the title says-- I DL'd a fresh copy of Mthybuntu to load on a Dell OptiPlex 755 PC.

I'm doing my best to embrace and become a Linux and Ubuntu advocate!  But it's beyond-frustrating when I can't play a simple audio CD!  I went and put the audio CD's in my cheap $50 10 year old DVD player and they play FINE.  But nope, not on Mythbuntu--the system designed for playing media!

Any fixes for all these problems out of the box??  It should not be this hard!! This is why Windows wins, which sucks.

Install went fine.  I did a Front end w/ Back End install.

I have these failures out of box:

1. Can not mount or play audio dics's either from desktop nor from Myth front end.  (Fixed the problem of unable to mount from desktop w/ fix found from another post.)

2. Can not play ripped audio disc from Myth front end after successful rip.  (Library shows empty.  Later encounters an error saying I don't have write permissions after I attempted to re-rip.)

3. After reboots of PC, get an error on Myth front end saying "Can not connect to backed database -- Are you sure it's running?"  (Well I should hope it is running- it was installed!!)

4. Remote app for Android - i have it fully configured but get connection refused error when trying to connect.  Other have reported this.

---

### Post by klc5555 on 2012-10-07
> After reboots of PC, get an error on Myth front end saying "Can not connect to backed database -- Are you sure it's running?" (Well I should hope it is running- it was installed!!)

Mythtv is a difficult place for those just getting involved in Linux to begin using it.

From the sounds of the errors, it appears you may have installed the backend and frontend, but haven't completely configured the backend yet. Until completely configured,** including tuner cards, video sources, input connections, storage groups, etc**.the backend won't start at boot, won't run, the frontend accordingly won't be able to connect to it, and mythtv won't be usable, including what might at first glance appear to be simple front-end functions like mythvideo or myth music. In the absence of a running mythtv installation, I imagine your audio CDs are still playable from Mythbuntu's Xubuntu desktop itself (rather than the Mythfrontend menus) by using one of the other standalone audio/video players that a default mythbuntu installation provides. 

You may wish to consult ch.3 of mythtv's manual for backend configuration info: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend)

If you believe the backend has been completely configured and is in fact running, the place to begin looking for debugging and error info for mythtv problems are the mythtv logs, normally to be found under /var/log/mythtv The error outputs from the mythbackend and mythfrontend logs (and/or from other debugging tools that may at a later time turn out to be appropriate) are more likely to help the folks at this forum diagnose and correct the issues that you may continue to be experiencing before and after the configuration process is complete.

---

### Post by fscottf1 on 2012-10-20
Tried to read the technical doc you provided by clicking on the link and get an error: There is currently no text in this page. You can search for this page title in other pages, or search the related logs.

Checked the URL and it looks like it cut the "d" out of "detailed" so I added that for the right url, and surprise surprise still no content.

I completely realize MythTV is complex -- but i'm confused about something -- I thought the whole concept behind Mythbuntu was to automate and create an ease-of-installation experience?  

So after I install Mythbuntu, if I am reading your post correctly -- I have to manually configure all those details MANUALLY even though I used Mythbuntu installer that is suppose to make installing idiot-proof?  

OK, well, I guess I'll go read the Wiki on how to manually configure all that junk, OOOH nevermind, no content on the Wiki you provided.

What a joke...

---

### Post by nickrout on 2012-10-21
> **fscottf1 said:**
> Tried to read the technical doc you provided by clicking on the link and get an error: There is currently no text in this page. You can search for this page title in other pages, or search the related logs.

Checked the URL and it looks like it cut the "d" out of "detailed" so I added that for the right url, and surprise surprise still no content.

I completely realize MythTV is complex -- but i'm confused about something -- I thought the whole concept behind Mythbuntu was to automate and create an ease-of-installation experience?  

So after I install Mythbuntu, if I am reading your post correctly -- I have to manually configure all those details MANUALLY even though I used Mythbuntu installer that is suppose to make installing idiot-proof?  

OK, well, I guess I'll go read the Wiki on how to manually configure all that junk, OOOH nevermind, no content on the Wiki you provided.

What a joke...
Clearly you are the class of idiot that even mythbuntu cannot fix. Please try not to be rude. 

The url above seems to have been mangled by the forum interpreting part of it as a smiley. However if you search the wiki I am sure you will find the page he intended.  

Mythbuntu cannot guess all your settings, tv provider, listings provider etc. There ate just too many tv cards, tv providers, tv delivery systems etc.you therefore need to follow instructions and do some setup.

---

### Post by klc5555 on 2012-10-21
> OK, well, I guess I'll go read the Wiki on how to manually configure all that junk, OOOH nevermind, no content on the Wiki you provided.


The URL for the section of the manual was corrupted in my original post. It is [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index)  Of course, even where you landed, you might perhaps have noticed the "User Manual" link at the lower left of the page.

Mythbuntu is intended to "create an ease of installation experience" ...for those who already reasonably familiar with Linux, but who may not want to compile all their own mythtv binaries from source or configure their own MYSQL installation for the database. For those who those who know absolutely nothing, cinch up, 'cause it's going to be a challenge. 

The mythbuntu "idiot-proof" installer installed the software correctly, but it's still up to the idiot himself to configure it.

---

