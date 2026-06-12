---
title: "MythTV &amp; HDHomeRun Prime Request"
date: 2013-05-06
forum: Mythbuntu
---

### Post by Bonte on 2013-05-06
Greetings all,

I've been banging my head for a week now trying to get the HDHomeRun Prime working in MythTV. I've tried various versions of MythTV under various versions of Ubuntu with no go.

First off, I made a valiant attempt at using SchedulesDirect.org for almost a week now until my free trial expired. Something changed at SchedulesDirect.org which made retrieving the initial channel lineup under 0.25 or 0.26 fail. The issue seems to stem from MythTV HTTP code timing out while processing the SOAP request to SchedulesDirect. Appears as though MythTV waits no longer than about 5 seconds for the lineup to be received, but SchedulesDirect is taking about 10 to complete the request (verified this by watching the TCP packets). I never did locate this timeout in the source code, otherwise I might have had a shot at increasing it.

With that said I am trying to configure MythTV /without/ the channel line-up information from SchedulesDirect (this may or may not be the problem) however, something that should work regardless of where the channel line-up comes from. I believe that there are other problems in the configuration of the tuner when SchedulesDirect is NOT used as well as how the channel line-up should be written into the various tables.

Would it be possible for someone with a working configuration of MythTV using HDHomeRun Prime to send me an export a copy of their mythtvconverg database and send it over to me? Once I analyze a working configuration, I'll know what the differences are between one that does not use SchedulesDirect and can isolate the problem. This will save me many MANY hours of going through the code line by line to try to see what values will make everyone happy. I will post my research and let everyone who is not using or cannot use SchedulesDirect.org what they need to do to have a working HDHomeRun Prime under MythTV.

Note: None of the steps below will alter your mythconverg database in any way, the mysqldump command will perform a read-only export of your mythconverg database into a file called mythconverg.sql. Once that file is exported, the additional steps are are to remove your Schedules Direct login and password (if configured). I don't want it, so please remove them from the SQL file before sending them to me.

To export a copy of your mythconverg database, you can use mysqldump:

If running from your master backend:
```
mysqldump -u mythtv -p mythconverg > mythconverg.sql
```

OR

If running from a machine other than your master backend and you've configured mythtv to allow other connections:
```
mysqldump -h <master backend IP or hostname> -u mythtv -p mythconverg > mythconverg.sql
```

You will be prompted for your mythtv password which can be obtained from your config.xml file (/etc/mythtv) or by running mytv-setup and looking at the General settings screen. Note: This password is NOT saved in the mythconverg database.

After exporting the database, please remove your SchedulesDirect login & password from exported file. The password is stored in plain text in the database and can therefor be found in the SQL export (I don't want it!). Easiest way to remove it is by opening it up in an editor such as gedit, or nano.

```
nano mythconverg.sql
```

Press CTRL+W to open the Search box, type or paste in the following and press enter:

```
INSERT INTO `videosource`
```
(Note: Those are backticks, not single quotes.)

You should be able to easily spot your login and password in the INSERT statement. It'll look like this:

```
INSERT INTO `videosource` VALUES (1,'Verizon FiOS','schedulesdirect1','bonte','default',NULL,'MyPassword',0,NULL,-1);
```

Strip your login and password by editing the text between the single quotes. You can delete the login and password altogether or replace it with something like 'login' and 'password' respectively. NOTE: If you have multiple video sources defined, you may find your Schedules Direct login and password on multiple INSERT statements.

When you're done editing the file, press CTRL+X to edit - you will be prompted to save, press Y to save and when it asks you for a file name, just press Enter to overwrite the exported file.

Lastly, zip up the file to compress it before sending:

```
zip mythconverg.zip mythconverg.sql
```

The file should compress about 90% and should easily attach to an email, you can send the copy to bontae `at` ungulate.net.

Thank you so much for helping me! I truly appreciate it. I'm eager to not only get this working for me but also to help others who are unable to get their HDHomeRun Prime working without using Schedules Direct.

Bonte

---

### Post by larsolav on 2013-05-06
I have the HDHomeRun Prime working on my machine. I will try to follow up this eveing after the kids are in bed...
Regarding not being able to get the Schedules direct download to work, have you seen this thread:
[http://ubuntuforums.org/showthread.php?t=2104718](http://ubuntuforums.org/showthread.php?t=2104718) ?
I don't know if it is relevant or not.

Cheers!

---

### Post by drewdin on 2013-05-06
I used these documents to setup my HDHomerun prime, version 11.04 .24fixes, let me know if you cant get it working.

[http://www.mythtv.org/wiki/Configuring_MythTV_for_the_HDHomeRun_Prime](http://www.mythtv.org/wiki/Configuring_MythTV_for_the_HDHomeRun_Prime)

[http://www.mythtv.org/wiki/Talk:Configuring_MythTV_for_the_HDHomeRun_Prime](http://www.mythtv.org/wiki/Talk:Configuring_MythTV_for_the_HDHomeRun_Prime)

---

### Post by billstei on 2013-05-06
I have been trying to get MythTV and an HDHomeRun Prime working on a Ubuntu Raring 13.04 machine without success (also TVHeadEnd with dvb_hdhomerun-utils driver in Ubuntu 12.10, again without success).  I am perfectly willing to go back to Ubuntu 11.x or 12.x if that's what works.  And I too would prefer not to use a schedule service/grabber of any sort.  For the record, the notion that encrypted channels cannot be viewed in Ubuntu (or Linux in general) is wrong.  The Prime does the de-encrypting, and both of these methods work in Ubuntu 12.10 on encrypted channels via the HDHomeRun Prime:

1) Run hdhomerun_config_gui.  Select an HDHomeRun Prime tuner.  Select a channel number (I used 121).  Select a Program from the drop-down list (I used 74, which is listed as "encrypted").  Click View.  VLC is launched viewing network stream rdp://127.0.0.1:5000, and it is playing OK.

2) Same as above, but manually from the command line (use your HDHomeRun ID for XXXXXXXX, and your channel line-up may not have a 121-74):

hdhomerun_config XXXXXXXX set /tuner0/channel 121
hdhomerun_config XXXXXXXX set /tuner0/program 74
hdhomerun_config XXXXXXXX set /tuner0/target 127.0.0.1:5000

To view with VLC using a pipe:

hdhomerun_config XXXXXXXX save /tuner0 - | vlc -

To output to a file and play it in VLC later (use Ctrl-C to end):

hdhomerun_config XXXXXXXX save /tuner0 test_121-74.mpg

Turn off the tuner:

hdhomerun_config XXXXXXXX set /tuner0/channel none

Interesting side note: If you run the following streaminfo command *before* setting the program (as above, 74) encrypted channels are listed as "encrypted", but if you run it *after* setting the program (as above, 74) it is not listed as encrypted.  I can't help but wonder if the problem for apps like MythTV or TVHeadEnd is the assumption that a channel/program listed as "encrypted" is necessarily always that way:

hdhomerun_config XXXXXXXX get /tuner0/streaminfo

@larsolav - when you say it is "working" do you mean working for non-encrypted channels (with or without a cablecard), or do you mean working for encrypted channels with a cablecard?

---

### Post by larsolav on 2013-05-06
Good evening!
I can record encrypted signals having the CCI label "copy freely" using a cable card. Channels or programs labeled "Copy Once" MythTV can not record. I think only Windows Media Center can record those. Don't think Tivo can record them either. I have Optimum cable, and where I am the channels in the "value" package are copy freely (includes Disney HD, CNN etc). all the other channels in the "preferred" "silver" "gold" packages (including Disney XD, BBC America, Own) are copy once and will not record in MythTV. So I have dedicated one of the tuners in my Prime to a Windows Media Center computer to record the copy once channels.

Holy moly! my mythconverg dump is 400 MB...

---

### Post by billstei on 2013-05-06
@larsolav - my CCI says "unrestricted".  Same as "copy freely" ?  What Ubuntu version do you have working, and what MythTV version?

---

### Post by larsolav on 2013-05-06
Mythbuntu 12.04 with 0.26 Mythtv
To set it up I followed the instruction from the Wiki drewdin mentioned

---

### Post by billstei on 2013-05-06
Since 12.04 has 0.25 in the repo, are you using a ppa or compiling from source or ...?

---

### Post by larsolav on 2013-05-07
0.26 is in the repo (it is just not on the 12.04 distro, as the distro came out before 0.26) (see [https://sites.google.com/a/mythbuntu.org/website/repos](https://sites.google.com/a/mythbuntu.org/website/repos)). I just selected 0.26 in the Mythbuntu Control Centre and ran all the resulting updates. Cheers!

---

### Post by tgm4883 on 2013-05-07
> **larsolav said:**
> 0.26 is in the repo (it is just not on the 12.04 distro, as the distro came out before 0.26) (see [https://sites.google.com/a/mythbuntu.org/website/repos](https://sites.google.com/a/mythbuntu.org/website/repos)). I just selected 0.26 in the Mythbuntu Control Centre and ran all the resulting updates. Cheers!

Also, [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)  I really wish there was a way to fix that other URL (common Google) :/

---

### Post by billstei on 2013-05-07
Just to document my experience with testing these ideas:

Using mythbuntu-control-centre to make the change on my Ubuntu 12.10 machine to MythTV 0.26 resulted in the following repo being added to Software Sources -> Other Software:

deb [http://ppa.launchpad.net/mythbuntu/0.26/ubuntu](http://ppa.launchpad.net/mythbuntu/0.26/ubuntu) quantal main

The details for this repository can be found here: [Mythbuntu 0.26 PPA]("https://launchpad.net/~mythbuntu/+archive/0.26")

It was not entirely clear when using Mythbuntu Control Centre -> Repositories that clicking the Refresh button did not add the repo, and it immediately went gray... the correct sequence (I think) was check the Activate MythTV Updates repository checkbox, select 0.26 in the drop-down list, do NOT click Refresh (either one of the two), and click Apply at the bottom of the window, and a list of Apply tasks pops up -- if the repo change is not listed (it took me three varied attempts) try something different, I was and still am confused.

Using mythbuntu-control-centre to make the change on my Ubuntu 13.04 machine resulted in a crash:

bill@AVS2:~$ mythbuntu-control-centre
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 40, in <module>
    from aptdaemon.gtkwidgets import (AptErrorDialog,
ImportError: cannot import name AptMessageDialog

This bug is being tracked here: [Bug #1158117]("https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/1158117")

But obviously the task of adding the repo to Raring can also be done with Software Sources -> Other Software as above:

deb [http://ppa.launchpad.net/mythbuntu/0.26/ubuntu](http://ppa.launchpad.net/mythbuntu/0.26/ubuntu) raring main

I have not tested whether Ubuntu 13.04 Raring with MthTV 0.26 can successfully view/record HDHomeRun Prime encrypted channels, but that is the goal...

---

### Post by billstei on 2013-05-07
My tests on Ubuntu 13.04 Raring with MythTV 0.26 repo were a complete failure, can't Scan, can't View (after manual SQL channel import), can't Record.  Also the launcher for mythtv-setup (i.e. MythTV-Backend Setup) hangs, so for those who want to wrestle with 13.04 use mythtv-setup.real on the command line to launch, but note that calling it this way does not start/stop the mythtv-backend service, or run mythfilldatabase afterwards.  I also ran the frontend this way: mythfrontend.real

It is unclear to me whether having a grabber like Schedules Direct will help (I am using no grabber), but as per Comment #1 above, I doubt it.

Will try Ubuntu 12.04 as per larsolav's success with it, but in order to do so I have to get past the newer Atheros ethernet controller on that machine's MB which is not supported out-of-the box in 12.04, so maybe-maybe-not...

Edit: For anyone who stumbled on my thread-unrelated Atheros comment, my plan is to use one of these packages that I will move over to the machine manually (USB flash drive):
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_amd64.deb)
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_i386.deb)

EditEdit: Ethernet working via method in Edit above (initially with 12.04.02 not-upgraded 3.5.0-23 kernel, and still working in 3.5.0-28), using terminal in directory with one of the deb files above:
dpkg -i [whichever_deb_listed_above_you_used]
sudo modprobe alx

---

### Post by billstei on 2013-05-07
Initial test results using Ubuntu 12.04.02 and MythTV 0.26 ppa repo:

Scan channels runs and appears to find all the relevant channels.  Setting startup channel to non-encrypted 89-2 results in a failure by the Frontend to Watch TV, with the backend and frontend logs: [Failed Tune/WatchTV Backend/Frontend Logs]("http://pastebin.ca/2375949")

This test was not using Virtual Channel tuning (for example 89-2 is tuned as "7" here), and larsolav might be doing that, so as per Comment #1, I too would like to see his mythconverg (channels table?), but 400 MB is too scary big.

The failed "unknown" tuner_type of 0x2000 is kTunerTypeOCUR (as defined in dtvconfparserhelpers.cpp (circa lines 47, 61, 82) in mythtv source code libs/libmythtv), and the question (I think) is whether using kTunerTypeATSC will work for the Prime since it effectively acts the same as the HDHomeRun Dual (because the de-encryption is done in the Prime, transparently), and where that is stored in mythconverg (or ?).  Or to put it a different way (and making an assumption): Why does larsolav not get the Unknown tuner_type 0x2000 error?

---

### Post by billstei on 2013-05-07
@larsolav - what firmware version is in your HDHomeRun Prime?  Please don't update it...

And it has a CableCard installed, correct?

---

### Post by tgm4883 on 2013-05-07
I'd just like to add MythTV 0.26+fixes and 12.04. My HDHomerun Prime works with Comcast and a cablecard.

Model: HDHR3-CC 
Device ID: 131378F3 
Firmware: 20120405

---

### Post by larsolav on 2013-05-08
> **billstei said:**
> @larsolav - what firmware version is in your HDHomeRun Prime?  Please don't update it...

And it has a CableCard installed, correct?

Yup, I have a cable card. I will have to check which firmware it is running tonight (I think I updated it when I installed the Prime last December). 
I also private messaged you a link to my mythconverg (only 61 mb zipped....). 
I also believe the OP will post a solution to his problem, which hopefully also helps you.

Cheers!

---

### Post by Bonte on 2013-05-08
Just a quick reply, with Lars's help, I got it figured out!

It's definitely a bug in the channel scan code which is incorrectly writing dtv_multiplex value and providing the mplexid against the channel. Technically speaking, the HDHomeRun Prime tunes by vchannel (your provider's channel #) and does NOT use "transponder" information (all those frequencies you see).

One cannot simply delete the transponders, as this causes a trigger delete causing the channels to be deleted as well. But with some simple SQL, it's easily resolved.

Before I provide a work-around in the form of a write up or code, I'd be glad to walk you through this over the phone or over an IM conversation. I was successful in getting TWO separate machines, one running 0.25 and the other running 0.26 working just fine last night!

Now, I did write a small program - but it's a hackjob at best, to copy the channel data from the HDHomeRun Prime so that I didn't have to wait for the channel scan to complete, however if you already have a completed channel scan and your channel table is populated, we can use that as well.

I will DM you my contact info.

TLDR; Success!

PS: How can I credit Mr. larsolav for helping to find a solution?

Thanks!
Bonte

---

### Post by Bonte on 2013-05-08
> **billstei said:**
> The failed "unknown" tuner_type of 0x2000 is kTunerTypeOCUR (as defined in dtvconfparserhelpers.cpp (circa lines 47, 61, 82) in mythtv source code libs/libmythtv), and the question (I think) is whether using kTunerTypeATSC will work for the Prime since it effectively acts the same as the HDHomeRun Dual (because the de-encryption is done in the Prime, transparently), and where that is stored in mythconverg (or ?).  Or to put it a different way (and making an assumption): Why does larsolav not get the Unknown tuner_type 0x2000 error?

Send you a PM - this is exactly the same error that I started with an was able to correct. Let's get your setup working and then post our findings and hopefully help many others that reached a dead end here!

Bonte

---

### Post by larsolav on 2013-05-08
> PS: How can I credit Mr. larsolav for helping to find a solution?
Aww. I'm blushing... all I did was following your instructions and sending you a file...

But for my understanding, am I correct that your and billstei's problem stems from not fetching channels from the listings source (Schedules Direct), but instead doing the channel scan?

Glad you got it fixed!

---

### Post by Bonte on 2013-05-08
> **larsolav said:**
> Aww. I'm blushing... all I did was following your instructions and sending you a file...

But for my understanding, am I correct that your and billstei's problem stems from not fetching channels from the listings source (Schedules Direct), but instead doing the channel scan?

Glad you got it fixed!

Hi Lars,

You are correct. There is unfortunately a dreadfully simple to fix bug in MythTV packages in Ubuntu (0.25 and 0.26, all variants) that causes the SchedulesDirect lineup fetch to fail because MythTV expects that it comes back in under 5 seconds, but large listings such as 400+ channel digital FiOS/Cable take at least twice as long than that. This prevents SchedulesDirect from being used with Ubuntu's packages, sadly. I'll probably start using SchedulesDirect once I find the timeout value in the code and change it or use a different PPA, but until then I wanted to at least use MythTV with the HDHR Prime and that is not possible due to the problem with the channel scan.

The channel scan isn't a terrible thing, but it's dreadfully slow and seems that it's doing FAR more than necessary - why it doesn't just fetch the vchannel vstatus values from the HDHR Prime is beyond me. I simply wrote a 20 line bash script that requests channels 1-2000 from the HDHR Prime by using hdhomerun_config. hdhomerun_config returns good exit levels which can be used to parse a good or bad vchannel, and then the vstatus (I believe that's the value) will report the channel name (like "Comedy Central" etc.) and if the channel is authorized or not. Once I had that, I just needed to insert them into the database, so I built the INSERT statement with the necessary default values and voila.

The alternative is to convert the channels found in the channel scan to non-dtv_multiplex channels, this will force MythTV to tune the HDHR Prime correctly vs. trying to send it to the wrong tuning handler. I might try that with billstei as otherwise he'll have to do the hack job that I did and pull down his channels from the HDHR Prime - or else, he'll have a lot of manual typing to do :p

Thanks again, you're awesome!
Bonte

---

### Post by billstei on 2013-05-08
@larsolav - got your mythconverg but I hope I don't have to actually open a 400 M file with a text editor and dig through it -- lol

@Bonte - I don't mind doing some typing/converting and in fact I already generated a custom SQL channel import file, but using it does not help.  I am of course interested to know what steps you took to get the Prime working.

@everybody_else - if you are running firmware 20120405 I would be very cautious about changing it, because I get the feeling that the success stories are dependent on it, and the failure stories are for those of us running 20130328.  Ironically I suspect 20120405 has a bug that "helps"...

Regarding the "Unknown tuner type = 0x2000" error, the routine DTVMultiplex_::_ParseTuningParams(), circa line #289-330 in the file [dtvmultiplex.cpp]("http://code.mythtv.org/trac/browser/mythtv/mythtv/libs/libmythtv/dtvmultiplex.cpp") simply does not have an "if" test for tuner type "kTunerTypeOCUR", and MythTV identifies (at least for firmware 20130328 it does) the HDHR Prime as kTunerTypeOCUR, hence the "error".  The question is whether changing line #322 from this:

if (DTVTunerType::kTunerTypeATSC == type)

to this:

if ((DTVTunerType::kTunerTypeATSC == type) || (DTVTunerType::kTunerTypeOCUR == type))

would "fix" the problem with tuning, or does OCUR need to be parsed differently?  If using virtual channels, the answer might be "differently", but if using "89-2" as the default scan does, the answer might be "yes, fixed" -- I am not informed enough to know...

---

### Post by Bonte on 2013-05-08
> **billstei said:**
> @larsolav - got your mythconverg but I hope I don't have to actually open a 400 M file with a text editor and dig through it -- lol

@Bonte - I don't mind doing some typing/converting and in fact I already generated a custom SQL channel import file, but using it does not help.  I am of course interested to know what steps you took to get the Prime working.

@everybody_else - if you are running firmware 20120405 I would be very cautious about changing it, because I get the feeling that the success stories are dependent on it, and the failure stories are for those of us running 20130328.  Ironically I suspect 20120405 has a bug that "helps"...


I'm running the absolute latest firmware (the one with the approved DLNA protocol from March) and it's 100% successful!

> **billstei said:**
> 
Regarding the "Unknown tuner type = 0x2000" error, the routine DTVMultiplex_::_ParseTuningParams(), circa line #289-330 in the file [dtvmultiplex.cpp]("http://code.mythtv.org/trac/browser/mythtv/mythtv/libs/libmythtv/dtvmultiplex.cpp") simply does not have an "if" test for tuner type "kTunerTypeOCUR", and MythTV identifies (at least for firmware 20130328 it does) the HDHR Prime as kTunerTypeOCUR, hence the "error".  The question is whether changing line #322 from this:

if (DTVTunerType::kTunerTypeATSC == type)

to this:

if ((DTVTunerType::kTunerTypeATSC == type) || (DTVTunerType::kTunerTypeOCUR == type))

would "fix" the problem with tuning, or does OCUR need to be parsed differently?  If using virtual channels, the answer might be "differently", but if using "89-2" as the default scan does, the answer might be "yes, fixed" -- I am not informed enough to know...

See, I thought the same thing and I went down the path in the code just as you did -but here's what gets me. This is -not- a DTV tuner and the only reason that this part of the code is being called is because the channel has a reference to an mplexid. When changing a channel on the HDHR Prime, you simply tell the HDHR Prime which cable channel (not frequency) and select a program by ID or filter OR select by the virtual channel (the channel lineup from the provider) and it will tune. I discovered by trial and error that MythTV simply uses the vchannel and does not care worth a damn about the TRUE cable frequency/program/video id/audio id/filters etc, it lets the HDHR Prime do all the work (as it should!).

In Lars's configuration, the mplexid value for every channel on his source 3 (the video source for the HDHR Prime) was set to 32767. This was the key. This means that the dtv_multiplex table is unnecessary. In fact, if you look at it, you'll only see his ATSC channels as the terrestrial tuner he's using IS a DTV tuner and that's where it comes in handy.

I doubt at this point that it's making it down that path in the code, because the tuner type (8192/0x2000) is actually coming from the OCUR tuner type as you discovered and it's written into the dtv_multiplex table as an integer. One thing that could be easily tested is dropping a log output in the code and executing it in a working configuration, if I were a betting man, I'd bet that this function is never called in a working HDHR Prime set up.

Let's chat directly, I think our combined research and instructions will surely help many other folks facing the same problem.

Bonte

---

### Post by billstei on 2013-05-08
I can probably get on IRC tomorrow (today is busy), I assume either #mythtv-users or #mythtv ?

In the meantime, in order to pursue my own pet theory that the 20120405 firmware has bug that makes their MythTV users happy, if @tgm4883 were to gather the responses from the following two commands (replacing XXXXXXXX with your Device ID), both of which should be benign "get"s that do not "set" anything:

hdhomerun_config XXXXXXXX get /sys/model
hdhomerun_config XXXXXXXX get /oob/status

or anyone who meets the following criteria:

1) The device is an HDHomeRun Prime (not the Dual).
2) The device has a "working" CableCard *inserted*.
3) The device has firmware 20120405 (or at least not 20130328).

---

### Post by billstei on 2013-05-08
More test results: Changing dtvmultiplex.cpp line #322 as per Comment #21 above allows me to use MythTV Frontend to Watch TV on non-encrypted channels, but not encrypted channels (versus not being able to Watch TV anything previously).  Note that this is using the default QAM-256 channel scan that MythTV performed.  I have not tried importing my own virtual channel SQL file (yet).

---

### Post by billstei on 2013-05-08
@Bonte - How does this: [SQL Channel Import]("http://pastebin.ca/2376670") compare to the tables you are generating?

---

### Post by tgm4883 on 2013-05-08
Talking with upstream, the timeout for that use to be 10 seconds and should be 60 seconds now (Was bumped up around the beginning of the year). Since you are on 0.26, assuming you are running 0.26+fixes, the problem is likely on your end rather than a MythTV issue.

:EDIT:

Here is the bug report that ended up getting the timeout bumped up
[http://code.mythtv.org/trac/ticket/11287](http://code.mythtv.org/trac/ticket/11287)

And here is the commit to 0.26+fixes
[http://code.mythtv.org/trac/changeset/bcc459fa2893f65c1debe9a7f976d3c23e865531/mythtv](http://code.mythtv.org/trac/changeset/bcc459fa2893f65c1debe9a7f976d3c23e865531/mythtv)

---

### Post by billstei on 2013-05-09
More test results: Same test as Comment #24 above but using the SQL import from Comment #25, I can tune/Watch-TV non-encrypted channels only.  It is however the first time I have successfully used virtual channel tuning.

---

### Post by billstei on 2013-05-11
I finally have it working, and I am not using any mythtv source code changes (I think -- I need to complete purge this thing and start over to be sure...).  I can do a scan, but the resulting table data does not work (duh), and afterwards there are no less than two values that need to be changed in this table to make it work:

table "channel"
freqid = I set this to the value that my Set-top Box would use, the virtual channel, so 120-70 is "70" on my Set-top Box.  The scan had "120", and I changed that to "70".
mplexid = 32767 (as per Bonte's comment above)

Entries in the dtv_multiplex table can be deleted if they have a sourceid pointing back to any HDHomeRun Prime sources, and if that is the only source(s) then the entire table can be empty and it still works (again as Bonte commented above).

I do not think there is a way to change the freqid and mplexid values in the channel table with myth-setup, so I used Webmin running on the backend machine to get into the mythconverg database, and the "channel" table.  It could be that using the Channel editor in myth-setup would overwrite the freqid and mplexid values and break it (again)...

---

### Post by billstei on 2013-05-14
Now that I have the HDHR Prime working I attached a zip file of the two SQL files that I manually created to import into mythconverg, one for the HDHomeRun Prime (with CableCard) with sourceid=1, and one for the HDHomeRun Dual (non-CableCard, Clear-QAM only) with sourceid=2.  Note that these channel lineups are unique to my cable company and area, and the easiest way (I think) to discover what the channels/programs are for your setup is to use the hdhomerun_config_gui program and tune to each Channel and then check the Program drop-down list.

Import into mythconverg database with:

mysql --user=root --password=xxxx mythconverg < name_of_SQL_file

[ATTACH]242588[/ATTACH]

---

