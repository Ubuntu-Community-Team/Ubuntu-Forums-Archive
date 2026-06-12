---
title: "Problems switching from OTA to QAM with HDHomeRun"
date: 2012-12-13
forum: Mythbuntu
---

### Post by granicus on 2012-12-13
NOTE:  My profile on the left is old and incorrect.  I am running MythTV v.25 on Mythbuntu 12.04, clean install as of May 2012.

Hey folks, I have been working on a problem all week, and just when I think I am 99% of the way there BAM things that were working just fine stop completely.  To try to keep it concise (as it is not short), I present the following timeline:

1. Started with working master backend/primary frontend machine (machine 1) and another secondary remote frontend (machine 2), using OTA with an HDHomeRun.
2.  While trying to resolve OTA signal issues on two channels that I had stopped receiving (definitely an issue with signals, not MythTV, so don't get distracted), the motherboard on machine 1 died (it had been in service since I first built the DVR 6 years ago, not a bad run, just stopped rebooting).
3.  Removed hard drive from machine 1 and put it into machine 2, placing original harddrive from machine 2.
4.  Boot machine 2 as the new primary/frontend backend.  

It is at this point that I am "back to nominal".  OTA works exactly as it had on the other machine, with those same two channels having issues.  As I have recently started subscribing to Comcast Digital Cable, I decided to use my HDHR to tune QAM so that I don't have to worry about OTA signal strength anymore.

So, picking up where I left off...

5.  I use Google to try to find a good guide on setting up QAM, but nothing is complete or up to date, exactly.  From what I see, it says to scan the cable frequencies.  One Google search stated that most cable companies transmit their HD streams on "cable-high", so I start there.  After playing with the cable-high (not cable HRC or IRC) scan for a while, I get what I think is my complete channel scan.
6.  I change my SchedulesDirect guide from the broadcast guide to the Comcast cable guide on their website, but when I go into mythtv-setup, go to the input source setup screen, and hit "Retrieve Lineups", the box that used to show my subscribed lineup is now blank. (Problem 1)
7.  After associating the input source to my tuners, I exit and run mythfilldatabase, and it looks like it is populating, but when I go into the frontend and view the channel guide, I see no data and a handful of "garbage" channels, none of which tune. (this problem resolved in point 8)
8.  Skip forward past a lot of time wasted re-scanning channels on cable-high and trying to match with scte65scan results, to where I finally find and then try just "cable" (seriously, why is that near the end of the options list, and not directly between "broadcast" and "cable-high/hrc/irc" options)?  This finds a lot more channels and I now know is the correct scan for my QAM-256.
9.  However, now when I try to run mythfilldatabase, I get errors stating it cannot download the data.  I then go through the process of using the getdata option on the SD website to get an xml file in order to do a manual update with the --ddfile command line option on mythfilldatabase to import (saw it on a Google search).  However, before that I use mythfilldatabase --help to see all options and see a --manual option.  I then run the --manual option and everything runs like a charm, populating the schedule info.  After this point, my subscribed lineup shows correctly in the input sources screen (aha, not so fast.  It goes away again later.)
10.  In the program guide, I now see a ton of duplicate channels with the wrong program info.  However, ignoring the wrong names and guide info I can tune to any and all my HD local channels using the correct channel number.  
11.  At this point I set up some manual channels in the channel editor using the correct channel numbers to record my scheduled shows that night, and re-ran mythfilldatabase to get the correct schedule for those channels (this quick-fix was done since I had to stop here and go to work).
12.  After work, finding that it had properly recorded the only show that was not a re-run, I started working on getting things cleaned up again.
13.  At this point, I went into the channel editor, removing/marking as invisible bad channels or channels I didn't want to watch, and re-naming the good channels to the correct channels and correcting the XMLIDs.
14.  Everything looked good, so I wanted to go ahead and add in a Hauppauge tuner I had (as I had conflicting shows the next night), added the tuner, associated it to the input source, and scanned for channels.  Ran mythfilldatabase, and went back to frontend.  When I went to LiveTV to test the tuner, the stream started on a standard-def channel on the HDHR.  When I tried to switch to the Hauppauge, the machine hung.
15.  I rebooted, and this time tried switching channels on the HDHR tuner, and while it would get the lock on that first standard-def channel it would not tune to any of the HD channels (even the one it recorded correctly just earlier that night).  (Problem 2).
16.  I then decided to remove the Hauppauge tuner and go back to just the HDHR.  No change.
17.  I then set the starting channel for the tuner to one of the channels I want to view.  At this point, going to Live TV doesn't even work anymore.  I get kicked straight out to the menu.  Trying to schedule a recording gets stuck on "tuning" and gives me a bajillion empty recording files under recordings for the HD program I had selected. Strangely, the standard def program I tested with records fine (Problems 3 and 4).
18.  I decide to take a step back, and through mythtv-setup remove all tuners, all input sources, and start from scratch setting them up.  I set up the HDHR tuners and set up the SchedulesDirect input source.  Once again, the problem is back where I cannot see my subscribed lineup when I select to "Retrieve Lineup" (Problem 1 again).
19.  I associate the tuners with the input source and scan for channels.  Once again, the scan seems to find everything.
20.  I exit mythtv-setup and run mythfilldatabase.  Again I have all the mis-mapped channels so after running, I go to the channel editor and correct the names and XMLIDs for just my local HD stations (using the existing channels listed, not adding any new ones) and re-run mythfilldatabase.
21.  Going back into the front-end, again, trying Live TV kicks me immediately back out to the menu.  Trying to schedule a recording gets stuck on "tuning" and gives me a bajillion empty recording files under recordings for the program I had selected.

At this point I am about ready to go HULK SMASH on the thing, but I cannot fathom using the Comcast DVR that seems to be able to hold only 5 hours of HD programming and has a god-awful interface after using my MythTV DVR for the past 6 years.

One big note on this:  During this WHOLE PROCESS, and even now, I can use the HDHomeRun Config GUI utility to successfully tune to ANY CHANNEL.  To me this says it is a MythTV problem, as the HDHR utility is playing the live feed for all these HD channels through VLC.

My next thought is that maybe it is something to do with the channel setup in MythTV, and so my inclination is to clear out the channel information from the MySQL database and try to "start fresh" in that regard.

Can anyone tell me whether or not I am on the right track?  If so, what tables should I make sure to clear?  If not, what should my next steps be?

FYI, I have been a database and software developer for the past 12 years, but in the Microsoft/VB/VB.NET world.  I have a novice knowledge of MySQL, having used it a little bit on some websites, but the totality of my knowledge of Linux comes from working on this DVR and the Google searches related to it.  I can go really technical on any answers given, but please do not assume I know all the usage or command line arguments of any utilities that may referenced.  What I do know I've gotten through trial and error.

Thank you ever so much in advance.

---

### Post by granicus on 2012-12-13
I figured it out.  Actually the fact that my manual channels worked last night gave me the thought of what to try.

In the mythtv-setup, when entering the manual channel you have to put the channel number in the format of xx-yyy.  However, I was using mythweb's channel editor to do the mass editing to make it easier.  When I was cleaning things up, the channel number field still had the format xx-yyy, but did not have the freqid column filled in, so I filled it in.  THAT was the key.

So, in short, in mythweb's channel editor, you can either have the full channel number, xx-yyy, in the channum column and leave the freqid blank, or you can put just the short channel number, yyy, and put the prefix, xx, in the freqid column, but not both.

---

