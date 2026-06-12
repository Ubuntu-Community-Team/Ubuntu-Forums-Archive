---
title: "BBC iPlayer problem downloading programme"
date: 2011-10-22
forum: Multimedia Software
---

### Post by Grinorcole on 2011-10-22
I am unable to download programmes from the BBC website using BBC iPlayer with a clean install of Oneiric Ocelot. When attempting to download, the GUI gives me the message:

"A Problem Occurred While Downloading This Programme"

Looking in the log file:

```
.appdata/BBCiPlayerDesktop.61DB7A798358575D6A969CCD73DDBBD723A6DA9D.1/Local\ Store/iPlayer.log
```shows some error messages:

```
10/22/2011 08:37:46.556 [INFO] uk.co.bbc.UpdateScheduledDownloadsCommand Updating user schedule to Anytime
10/22/2011 08:37:46.561 [WARN] uk.co.bbc.CrashRecoveryStartupTask Crash detected!
10/22/2011 08:37:46.572 [INFO] uk.co.bbc.RepositoryManager Setting repository /home/mans0954/Videos/BBC iPlayer/repository.
10/22/2011 08:37:46.921 [INFO] uk.co.bbc.NetworkMonitor Online: true
10/22/2011 08:37:47.069 [INFO] uk.co.bbc.IACManager BBC iPlayer Desktop domain is app#BBCiPlayerDesktop.61DB7A798358575D6A969CCD73DDBBD723A6DA9D.1
10/22/2011 08:37:47.225 [INFO] uk.co.bbc.TokenizerUtils Instructions ''
10/22/2011 08:37:47.225 [INFO] uk.co.bbc.TokenizerUtils First token '' (empty string expected during startup)
10/22/2011 08:37:52.543 [INFO] uk.co.bbc.ApplicationUpdaterManager Attempting to load update data from http://www.bbc.co.uk/iplayer/dm/version2/update2.xml 
10/22/2011 08:37:52.617 [INFO] uk.co.bbc.ApplicationUpdaterManager Checking local version 3.2.13 to see if upgrade is required
10/22/2011 08:37:52.618 [INFO] uk.co.bbc.CheckForUpdatesCommand Successfully received update data. Rescheduling for tomorrow.
10/22/2011 08:38:02.500 [INFO] uk.co.bbc.TokenizerUtils Instructions '-d aHR0cDovL3d3dy5iYmMuY28udWsvaXBsYXllci9wbGF5bGlzdC9iMDE2Yno5NS8= b016bz91 null null My4w b016bz95 null'
10/22/2011 08:38:02.501 [INFO] uk.co.bbc.TokenizerUtils First token '-d aHR0cDovL3d3dy5iYmMuY28udWsvaXBsYXllci9wbGF5bGlzdC9iMDE2Yno5NS8= b016bz91 null null My4w b016bz95 null'
10/22/2011 08:38:02.506 [INFO] uk.co.bbc.ContentItemsProxy Resolving content items (playlist, media selector etc) for vpid: b016bz91
10/22/2011 08:38:03.153 [INFO] uk.co.bbc.ContentItemsProxy Playlist file obtained for b016bz91.
10/22/2011 08:38:03.154 [INFO] uk.co.bbc.ValidateProgrammeFolderCommand Validating folder: b016bz91
10/22/2011 08:38:03.159 [INFO] uk.co.bbc.ContentFolderFactory b016bz91 has playlist file. Creating available content folder.
10/22/2011 08:38:03.164 [INFO] uk.co.bbc.CreateContentItemCommand Creating available Content Item vpid b016bz91
10/22/2011 08:38:03.170 [INFO] uk.co.bbc.ContentItem The content item with vpid b016bz91 isPlayable state was false and is now false.
10/22/2011 08:38:03.170 [INFO] uk.co.bbc.ContentFactory The ondemand start time for b016bz91 is set to: Fri Oct 21 21:32:00 GMT+0100 2011 The isPastOnDemandStartDate is set to: true
10/22/2011 08:38:03.188 [INFO] uk.co.bbc.ContentItem The content item with vpid b016bz91 isPlayable state was false and is now false.
10/22/2011 08:38:03.189 [INFO] uk.co.bbc.ContentFactory Available content item b016bz91 created from content folder: Episode 2 isHD: false
10/22/2011 08:38:03.469 [INFO] uk.co.bbc.ContentFactory The availability start date was determined from the media selector response Sat Oct 22 08:38:03 GMT+0100 2011 for epid: b016bz95 vpid: b016bz91.
10/22/2011 08:38:07.174 [INFO] uk.co.bbc.LicenceManager Getting licence for /home/mans0954/Videos/BBC iPlayer/repository/b016bz91/b016bz91_hi_234018534.part
10/22/2011 08:38:07.256 [ERROR] uk.co.bbc.ContentItemsProxy LicenceError:3344
10/22/2011 08:38:07.261 [ERROR] uk.co.bbc.ContentItemsProxy Licence aquisition failed for b016bz91, because: undefinedErrorId: 3344. SuberrorId: 6. 
10/22/2011 08:38:07.265 [INFO] uk.co.bbc.ContentItemsProxy Removing content with vipd b016bz91
10/22/2011 08:38:07.282 [INFO] uk.co.bbc.DeleteFolderCommand Deleting folder=/home/mans0954/Videos/BBC iPlayer/repository/b016bz91, isUserInitiated=false
10/22/2011 08:38:07.340 [ERROR] uk.co.bbc.LicenceManager Licence failed. undefinedErrorId: 3344. SuberrorId: 6. 
10/22/2011 08:38:18.018 [INFO] uk.co.bbc.RevocationManager Attempting to load Revocation data...
10/22/2011 08:38:18.101 [INFO] uk.co.bbc.SubscriptionProxy Loading 0 subscription feeds.

```I've tried installing Gnome Shell in case there's something that iPlayer expects missing from Unity, and I've tried creating a new user in case the problem is caused by something in my profile, but I get the same problem. No additional messages are displayed if I run iPlayer from the command line.

I've sent an e-mail to the BBC, but I'm not sure how much support they're able to provide for Linux users, so I thought I'd ask here for suggestions too. Thanks!

---

### Post by satanselbow on 2011-10-22
Have you tried **get-iplayer** works good for me on 11.10 gnomeshell ;)

---

### Post by Grinorcole on 2011-10-22
Thanks - I thought about that - but I wasn't clear how legal it was :confused:

---

### Post by satanselbow on 2011-10-22
> **Grinorcole said:**
> Thanks - I thought about that - but I wasn't clear how legal it was :confused:

I pay my licence fee and my conscience is clear :biggrin:

It does however allow you to store programme indefinitely / transcode which their own client does not so it could be considered somewhat grey ;)

---

### Post by mellis0 on 2011-10-22
Hi Grinorcole

I've got the same problem as you, ie Download of a programme fails, and I get practically the same as you in the log file.

I'm using 11.10 amd64.

Regards
Mark

---

### Post by Grinorcole on 2011-10-24
I got the following reply from BBC iPlayer Support Team

> I understand you're having problems downloading programmes using the Firefox browser.
 
 We are currently in the process of rolling out a new Embedded Media  Player (EMP) to BBC iPlayer. Enhanced features of this player include a  smoother media playback experience, where you will be given the best  playback experience based on your available bandwidth.
 
 This new EMP player may prompt you to upgrade your Adobe Flash Player to  the latest version (10.3) to allow playback of content. 
 
 If you have an older operating system for which Adobe no longer supports  (Mac PowerPCs for example), then you may still be able use the latest  version of the EMP player by using a version of Adobe's Flash Player  with a version number minimum of 10.1. You can access the latest  supported version of Adobe's Flash Player for your particular operating  system from Adobe's website here: 
 
 [http://kb2.adobe.com/cps/142/tn_14266.html#main_Archived_versions](http://kb2.adobe.com/cps/142/tn_14266.html#main_Archived_versions)
 
 The BBC is not responsible for the content of external internet sites. 
 
 Sadly, if your computer does not meet the minimum requirements for Adobe  10.1, then we regret that we can no longer support any BBC iPlayer  queries on these devices.
 
 If you have upgraded Adobe Flash Player and are using the Opera browser,  we are aware the currently users can not playback TV content. Opera  have identified a bug and have implemented a fix. Please update to the  latest version of the browser when prompted as this should resolve the  recent BBC iPlayer issues you have been experiencing.
 
 Some users have reported Scripting Errors when trying to access  Favourites. This issue has now been resolved, however, please contact us  via the link below if you continue to experience problems.
Completely irrelevant to the problem I described as far as I can see (for the record I have Flash 11.0.1.152).

---

### Post by mellis0 on 2011-10-30
Hi Grinorcole

As you say a totally irrelevant response indicating you should stream the content instead of download.

I think the error reported is related to not being able to use a encrypted store [http://kb2.adobe.com/cps/492/cpsid_49267.html](http://kb2.adobe.com/cps/492/cpsid_49267.html).

Trouble is I've tried this but have not been able to overcome the error when I download a programme.

Regards
Mark

---

### Post by lonetour on 2011-10-30
Hi Guys and Gals

MY problem is that iPlayer won't actually play... I get the message "Loading..." continuously. 

I'm new to Ubuntu, and have Oneiric 11.10.... 

I'm guessing you can play streams live, so why can't I?

Did any of you have problems at first???

Jonathan

---

### Post by mellis0 on 2011-11-05
Hi lonetour

Yes I can stream BBC iPlayer programmes from a webrowser, ie Chrome and I just tested Mozilla Firefox.

I guess the first thing to investigate is version of adobe flash installed. 

I'm not sure if BBC iPlayer is now using HTML5 for steaming.

I guess things affecting your ability to stream maybe:
- soundcard blocking
- settings in your webrowser
- version of adobe flash
- whether you are 32 or 64 bit

So there is a series of steps to go through to eliminate potential blockers to your ability to stream BBC iPlayer in Ubuntu 11.10.

Good luck

Regards
Mark 

Regards
Mark

---

### Post by itsjustarumour on 2011-11-24
I'm getting the same thing as the OP on 11.10 64-bit.

I'm pretty sure I've got the 64-bit Adobe Air installed OK as Tweetdeck is up and running just fine.

I've tried troubleshooting AIR's ELS Storage as per the howto at [http://kb2.adobe.com/cps/492/cpsid_49267.html](http://kb2.adobe.com/cps/492/cpsid_49267.html) which has helped me out with similar things in the past, but alas no dice this time...

---

### Post by itsjustarumour on 2011-11-30
Following on from my previous post, I'm now getting the same problem - and the same error message - in a fresh install of 64-bit Fedora 16.

Once again, Adobe AIR is installed successfully and all other AIR-based apps such as Tweetdeck are working perfectly. Once again, the BBC iPlayer desktop client IS successfully installed, its just when I try and download a programme it starts for about 2 seconds and then shuts down with a "A problem occurred while downloading this programme" message.

Looking in the log files on both Ubuntu and Fedora, I'm seeing the same thing - something along the lines of:

"[ERROR] uk.co.bbc.LicenceManager Licence failed"

So basically what I'm saying is, this doesn't look like a bug with Ubuntu or Adobe AIR, but with the BBC iPlayer desktop client itself, probably failing to register that I'm in the UK when it checks ("DRM"?)

---

### Post by itsjustarumour on 2011-12-01
Just thought I'd post the latest message from iPlayer when trying to download a programme to my *Linux* iPlayer desktop client.  I'm not sure whether to laugh or cry at this point  ;-)

---

### Post by mellis0 on 2011-12-02
Hi itsjustarumour

Doh! and double Doh!
Try and cry and laugh at the same time :confused:

I'll take a look see if things have changed on my Linux client.

Regards
Mark

---

### Post by itsjustarumour on 2012-01-15
Well, still no dice.  Same problem now with Ubuntu 11.04/11.10, Linux Mint 11.10 and Fedora 15 and 16.

I've submitted a "complaint" to the BBC.  Will post up their response if I hear back!

---

### Post by itsjustarumour on 2012-01-17
Received a reply from the BBC today.  No surprises that it was a standard "cut and paste" reply which completely failed to address the issues I had raised, and just refered me to their usual online resources which I've already exhausted and which provide absolutely no answers to the problems myself and others have been experiencing! ](*,)

Heres that letter in full:


Dear Mr ******

Reference ***-*******-*****

Thank you for contacting the BBC iPlayer Support Team.

I am sorry to read that you are experiencing problems with the latest version of BBC iPlayer Desktop on your Linux PC.

Unfortunately we are unable to offer support for Linux setups.

We aim to make information available on the BBC iPlayer Help website wherever possible because we know that information about accessing content through BBC iPlayer is important to all of our audience. We make the most requested information available, and in most cases can advise where it can be found, but in practice it's impossible to provide answers to everything that people ask us about.

The BBC is committed to ensuring that the Licence Fee is used to provide the best value to our audiences, and as such so we cannot always undertake to research individual user issues to their resolution. We receive many unique enquiries each week. I hope that you understand the reasons for this.

We do however capture the details of all enquiries we receive so that we can provide reports to programmes about the nature and type of information people are requesting. This is to encourage better provision of information online on programme websites.

You may wish to know that technical questions are discussed on external messageboards. Details can be found on [http://iplayerhelp.external.bbc.co.uk/help/using_bbc_iplayer/_messageboards](http://iplayerhelp.external.bbc.co.uk/help/using_bbc_iplayer/_messageboards)

Please note that the BBC is not responsible for the content of external internet sites.

Once again thank you for contacting BBC iPlayer.

Kind Regards

Andrew Gilfillan

BBC Audience Services

[www.bbc.co.uk/iplayer](www.bbc.co.uk/iplayer)

NB This is sent from an outgoing account only which is not monitored. You cannot reply to this email address but if necessary please contact us via our webform quoting any case number we provided.

_______________________________________________________________


Needless to say, I'll be getting back to them!  In my original letter, I wasn't asking for "support", I was reporting that their software simply *did* *not* *work* and included the relevant log file demonstrating the main *bug*.

Seems like the Beeb just don't want to know!  :mad:

---

### Post by Knaw on 2012-01-21
Further to the problems described in this topic, when I try to use iPlayer, it plays the video, but at ten times the speed that it should. This problem then spreads to the rest of my system, including YouTube and local videos.

The problem does rectify itself after a few days but in the meantime, it's impossible to watch any videos properly.

I have the most recent version of Flash, Firefox and Ubuntu on a 64-bit computer with six gigs of RAM, so there should not be a problem.

Have you experienced this, and if so, what is the solution?

---

### Post by itsjustarumour on 2012-01-25
> **Knaw said:**
> Further to the problems described in this topic, when I try to use iPlayer, it plays the video, but at ten times the speed that it should. This problem then spreads to the rest of my system, including YouTube and local videos.

The problem does rectify itself after a few days but in the meantime, it's impossible to watch any videos properly.

I have the most recent version of Flash, Firefox and Ubuntu on a 64-bit computer with six gigs of RAM, so there should not be a problem.

Have you experienced this, and if so, what is the solution?

Not seen that problem myself, although other peeps have.  Try checking out this thread to see if its any help:

[http://ubuntuforums.org/showthread.php?t=1445073](http://ubuntuforums.org/showthread.php?t=1445073)

---

### Post by itsjustarumour on 2012-01-25
Just found this new blog posting on the BBC site, in response to someone else's complaint to the BBC (I've also complained to Auntie Beeb myself, but I didn't get anything so informative back...) :

[http://www.bbc.co.uk/blogs/profile.s...serid=14904748](http://www.bbc.co.uk/blogs/profile.s...serid=14904748)

> "Because it might be of wider interest, here is the BBC iPlayer support team's response to complaints about the loss of the iPlayer Desktop on Linux:

"The BBC has chosen Adobe Air to deliver BBC iPlayer to personal computers as this software protects the interests of our rights holders which is essential in order for us to be able to make content available for download.

"Unfortunately, Adobe recently made the decision to no longer support Air for Linux operating systems. Linux users can, however, continue to download programs in the WMV format and they can also stream programmes directly from BBC ilayer as Adobe's Flash Player continues to support Linux.

"We apologise for not giving advance warning on the changes made and for any inconvenience caused." 

This was then followed up with another post from a member of BBC staff:

> After further checks, we need to clarify that our WMV files will not run on Linux. We regret the error. Linux users can continue to stream programmes from the browser version of BBC iPlayer.

The BBC has chosen Adobe Air to deliver the iPlayer Desktop service to personal computers as this software, which can be used across various operating systems, offers us the best combination of features to securely maintain our download windows, which are necessary for editorial, legal, regulatory, financial and rights reasons if we are to make content available for download.

Unfortunately, Adobe recently made the decision to no longer support Air for Linux operating systems. Linux users can, however, continue to stream programmes directly from the browser version of BBC iPlayer as Adobe Flash Player, which is the software required to stream BBC iPlayer content, continues to support Linux.

We apologise for not giving advance warning on the changes made and for any inconvenience caused.

I'd already tried the WMV approach, and found it didn't work.

Well - there we have it then, its official.  ***THE BBC NO LONGER SUPPORTS THE IPLAYER DESKTOP CLIENT FOR LINUX***. :roll::roll::roll:

---

### Post by shantiq on 2012-01-26
sensible suggestion 312 from the sensible suggestion library


get-iplayer is in your synaptic

download what you want to see then delete afterwards [it is way more stable for starters and can view when offline]
if you pay your license no harm no foul

The BBC does not lovingly  cater for Linux   Linux is fringe in their world
It caters for Windows for Mac   for the middle ground

Linux users like ourselves need to think sideways once in a while, why this community is more creative and usually higher IQ'd than the middle ground


anyway this is my humble opinion

---

### Post by itsjustarumour on 2012-01-27
> **shantiq said:**
> sensible suggestion 312 from the sensible suggestion library


get-iplayer is in your synaptic

download what you want to see then delete afterwards [it is way more stable for starters and can view when offline]
if you pay your license no harm no foul

The BBC does not lovingly  cater for Linux   Linux is fringe in their world
It caters for Windows for Mac   for the middle ground

Linux users like ourselves need to think sideways once in a while, why this community is more creative and usually higher IQ'd than the middle ground


anyway this is my humble opinion

Indeed, one can just install get_iplayer :-) And I have, and it works! :-)

HOWEVER.

I support and provide for a whole bunch of people that I've migrated to Linux, including a couple of "senior citizens". For them, the BBC iPlayer desktop is intuitive, feature-rich and easy to use, not to mention "pretty". Getting such non-technical users to use a command-line utility to search and download iPlayer content just isn't going to happen, and I've already had my first call asking me to "put Windows back on my computer so I can use iPlayer again".

What I'm saying is, get_iplayer isn't a solution for a lot of people.

---

### Post by shantiq on 2012-01-28
:KS:KS:KS:KS

ok do they really find iplayer pretty?????

i find it uglier than sin

but on the other stuff absolutely

i thought it was for you....


In any case the beauty of GIP is that you do not have to be online
when viewing AND crucially [ and i have the 50 gig connection ] i have never watched anything on iplayer that did not stop and start whatever the time of day

anyway .....

---

