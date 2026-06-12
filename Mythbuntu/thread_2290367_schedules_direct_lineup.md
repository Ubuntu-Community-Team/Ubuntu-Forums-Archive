---
title: "schedules direct lineup"
date: 2015-08-11
forum: Mythbuntu
---

### Post by baldur2 on 2015-08-11
[COLOR=#000000]i am extremely frustrated right now. i had mythbuntu working well. i ran an update the froze the entire os so i had to hard restart. the corrupted the os so i decided to reformat. i did this and went through the configuration however when i try and pull a [/COLOR][COLOR=#417394]schedules[/COLOR][COLOR=#000000] [/COLOR][COLOR=#417394]direct[/COLOR][COLOR=#000000] [/COLOR][COLOR=#417394]lineup[/COLOR][COLOR=#000000], it gets nothing. i have no idea how to troubleshoot this or what to do next...[/COLOR]

---

### Post by baldur2 on 2015-08-11
[COLOR=#000000]here is some log data...

[/COLOR]Aug 11 20:20:10 Thor mythtv-setup.real: mythtv-setup[4217]: I CoreContext datadirect.cpp:1155 (GrabData) DataDirect: Grabbing channel data
Aug 11 20:20:10 Thor mythtv-setup.real: mythtv-setup[4217]: I CoreContext datadirect.cpp:1017 (DDPost) Downloading DataDirect feed
Aug 11 20:20:41 Thor mythtv-setup.real: mythtv-setup[4217]: E CoreContext datadirect.cpp:1184 (GrabData) DataDirect: Failed to get data: Download error
Aug 11 20:20:41 Thor mythtv-setup.real: mythtv-setup[4217]: E CoreContext videosource.cpp:377 (fillSelections) DDLS: fillSelections did not successfully load selections
Aug 11 20:20:41 Thor mythtv-setup.real: mythtv-setup[4217]: I CoreContext datadirect.cpp:568 (~DataDirectProcessor) DataDirect: Deleting temporary files

---

### Post by Kerby_Armand on 2015-08-13
HI, I'd like to comment and observe.
NOTE: from Mythbuntu:
If you have a paid subscription to Schedules Direct that will continue the way it has worked previously. A simple update to MythTV will be required for users on a supported version of MythTV.
Users that have enabled the MythTV Updates repo and are on a current version of MythTV and a supported version of Ubuntu will receive the fix for this via regular updates. The Mythbuntu team has always recommended enabling the MythTV Updates repo in the Mythbuntu Control Centre and staying up to date on fixes builds. The fix for this issue was added to our packages in the versions in the below table. More information on the Mythbuntu provided MythTV Update repo can be found [here]("http://www.mythbuntu.org/repos").

Users on builds prior to 0.27 (eg. 0.26, 0.25) will need to either upgrade to a supported build version (see [Mythbuntu Repos]("http://www.mythbuntu.org/repos")) or use one of the workarounds (See [MythTV Wiki]("http://www.mythtv.org/wiki/Schedules_Direct_URL_Change"))

[TABLE="width: 1"]
[TR]
[TD]MythTV Version[/TD]
[TD]Fixed in version[/TD]
[/TR]
[TR]
[TD]0.28 (development)[/TD]
[TD]2:0.28.0~master.20141013.4cb10e5-0ubuntu0mythbuntu#[/TD]
[/TR]
[TR]
[TD]0.27.X[/TD]
[TD]2:0.27.4+fixes.20141015.e4f65c8-0ubuntu0mythbuntu#[/TD]
[/TR]
[/TABLE]


WELL: AS I see the issue from that note from Mythbuntu the issue SHOULD be fixed. But I experienced a different response this last week when I found that my schedule simply stopped listing as of Thursday evening at 7pm CST.
I asked Schedules Direct (SD) about this and got a few responses:
1. Can you check
[http://forums.schedulesdirect.org/viewtopic.php?f=6&t=295](http://forums.schedulesdirect.org/viewtopic.php?f=6&t=295)
for instructions and see if they help in solving your issue?
Once you get to the point where you've checked the raw XML using the
xmltv instructions from that post and it's correct, then we know that
it's an application issue and not what you're being sent.
If you're not able to get data using tv_grab_na_dd then that also tells
us something.

2. I went thru that and discovered that it's simply not finding the URL... (hint at DNS issue)
example: WARNING: Storing the password in the config file is not secureIf password is blank, it will be prompted as needed(more secure)
Unsecured password ('x':delete,default:<keep>,): 
Service description '[http://docs.tms.tribune.com/tech/tmsdatadirect/schedulesdirect/tvDataDelivery.wsdl'](http://docs.tms.tribune.com/tech/tmsdatadirect/schedulesdirect/tvDataDelivery.wsdl') can't be loaded: 500 Can't connect to [docs.tms.tribune.com]("http://docs.tms.tribune.com/"):80 (Connection timed out)

3. Reply from SD:
I found when a DNS cleanup was done a few days ago, the DNS link that
Gracenote/Tribune was using was removed.  It was put back.
You should be working now.
You do still have a time-bomb there.. as you are *not* using our DNS
name but Gracenote/Tribune's old one.  That can go away at any time...
and eventually will.
More recent versions of your app *should* contain a fix, but maybe the
devs just use the yum to apply security patches and want you to upgrade
to a new release manually.  I know your XMLTV package is very old.. it's
dated 2011!
Details on workarounds for old applications is in the migration link. 
If you don't upgrade, you should update /etc/hosts to avoid a future
problem.
[http://forums.schedulesdirect.org/viewtopic.php?f=3&t=2652](http://forums.schedulesdirect.org/viewtopic.php?f=3&t=2652)

4. Well, I updated the /etc/hosts file anyways - meaning I will have solved this issue??? I thought... the plot thickened.

5.I replied:
Cool, for the sake of learning -yes, I added the information to /etc/hosts

What about an outdated package? Or Script?
Problem then; when I build one of these boxes in the future - like I just did with this box - I HAVE to remember to add something to the /etc/hosts file each time?
If so, I think that is archaic and is not a solution for the long term.
Out of the &#8216;box&#8217;  - when I install - Mythbuntu it automatically installs all the mythtv, xmltv and other video and codec packages as needed (unlike the old days when I had to build it all) but anyways that is not the point.

What is up with Mythbuntu that they don&#8217;t know to update xmltv-util package to simply just work?
Last fall I did read your warnings to update the mythtv installs or loose connecting to SD&#8230; BUT if you have a newer updated version you&#8217;ll be fine.
I updated, installed the latest and greatest newest baddest mythbuntu - so I declared (to myself at least) we are &#8216;safe&#8217; and fine it will all work.
Until a DNS situation happens and the scripts grabbing the xml won&#8217;t run because it fails on connection.
So, what will be the solution? Me editing this /etc/hosts file ALL the time?
Hmm&#8230; sounds bad.
What are your thoughts?

6. SD Replied:
You have a valid question.. but the question is for the Mythbuntu folks.
We've been very upfront about the changes, they have to implement it
for their users.  Also, distributing an XMLTV from 2011?  I'd love to
hear their excuse for that.
===============================


SO, what I'd like to hear about is what is Mythbuntu's stand on this issue since it seems that the xmltv package (2011) that contains the script is not really updated accord to SD like Mythbuntu has said it is; OR, the package is simply not correct, OR is the URL have to be added manually ALL the time?

Mythbuntu has inferred that if I run the latest greatest we will be fine -and in my experience I am not fine according to SD - and should I really have to edit /etc/hosts ALL the time?

Any thoughts on this? I am not the sharpest tac but I think there are two conflicting 'answers' from two sources here....

Anyone can discuss...

Scan

---

