---
title: "Please help me setup Mythbuntu 10.04 and my HDHomerun Tuner"
date: 2010-07-27
forum: Mythbuntu
---

### Post by Turtleggjp on 2010-07-27
I've been using MythTV since about last September (2009).  I was using Mythbuntu 9.04 and the VDPAU patched version of MythTV 0.21 (from Avanard's repo), since the machine I was running it on was an Ion system.  The system ran ok for the most part except for a couple of nagging things.  The most annoying was that about every 3 days, the backend would lose connection with my HDHomerun tuner, and could no longer record shows, though I could still watch recordings.  Simply entering Mythbackend setup and exiting again would bring back the tuner for another 3 days.  Needless to say, I could never count on MythTV 100% to record my shows when they came on, and was eager to upgrade it.  When 9.10 came out, I tried installing it (fresh install), but found it to be an even bigger mess than what I had.  With my TV Shows in full swing, I decided to tough it out with what I knew worked, so I stuck with 9.04.  Now that my shows have all ended for the summer, I'm trying to get 10.04 working.  I must not be setting up my HDHomerun tuner correctly because I'm having two problems.

1. MythTV seems to think it only has one of the two tuners.  If I start watching a live TV channel, tell MythTV to record it (pressing 'R'), stop watching the show live, the start watching live TV again, I can only tune to the sub channels that are on the same carrier channel as the one being recorded.  I know it is using the same tuner since I have them labeled "HD Homerun Tuner0" and "HD Homerun Tuner1" in the backend setup.  I set up the two tuners pretty much the same way I did in 9.04, where I did not have this problem.  Is there some new procedure for setting up a dual tuner HD Homerun in 0.23?  I seem to remember this being one of the issues I had while trying out Mythbuntu 9.10 and MythTV 0.22.  I've also tried this on two machines, one with the HDHomerun connected directly to a dedicated ethernet port on the system (USB DLink Ethernet device), and the other where I connected the HDHomerun to the rest of my LAN.  

2. Something must also be wrong with how the channels are setup, because when the backend begins the EIT scan, it starts duping all sorts of data to the mythbackend.log file.  Here is an example:

```
2010-07-26 06:28:40.366 Could not find channel 2_1 in CVCT
2010-07-26 06:28:40.918 
VCT Cable: channels(3) tsid(0x46b) seclength(142)
Channel #0 name(KTLA Di) 5-1 mod(SCTE mode 2) cTSID(0x46b)
 pnum(421) ETM_loc(0) access_ctrl(0) hidden(0)
path_select(0) out_of_band(0) hide_guide(0) service_type(ATSC TV) source_id(13)
 descriptors length(33) count(1)
  ExtendedChannelNameDescriptor: 'KTLA Digital Television'

Channel #1 name(KTTV-DT) 11-1 mod(SCTE mode 2) cTSID(0x46b)
 pnum(422) ETM_loc(0) access_ctrl(0) hidden(0)
path_select(0) out_of_band(0) hide_guide(0) service_type(ATSC TV) source_id(17)

Channel #2 name(This TV) 5-2 mod(SCTE mode 2) cTSID(0x46b)
 pnum(423) ETM_loc(0) access_ctrl(0) hidden(0)
path_select(0) out_of_band(0) hide_guide(0) service_type(ATSC TV) source_id(18)


2010-07-26 06:28:40.933 Could not find channel 2_1 in CVCT
2010-07-26 06:28:40.937 
VCT Cable: channels(3) tsid(0x46b) seclength(142)
Channel #0 name(KTLA Di) 5-1 mod(SCTE mode 2) cTSID(0x46b)
 pnum(421) ETM_loc(0) access_ctrl(0) hidden(0)
path_select(0) out_of_band(0) hide_guide(0) service_type(ATSC TV) source_id(13)
 descriptors length(33) count(1)
  ExtendedChannelNameDescriptor: 'KTLA Digital Television'

Channel #1 name(KTTV-DT) 11-1 mod(SCTE mode 2) cTSID(0x46b)
 pnum(422) ETM_loc(0) access_ctrl(0) hidden(0)
path_select(0) out_of_band(0) hide_guide(0) service_type(ATSC TV) source_id(17)

Channel #2 name(This TV) 5-2 mod(SCTE mode 2) cTSID(0x46b)
 pnum(423) ETM_loc(0) access_ctrl(0) hidden(0)
path_select(0) out_of_band(0) hide_guide(0) service_type(ATSC TV) source_id(18)
```You can see from the timestamps in the log that it is generating this message about 2 times per second.  I also notice that the channels it says it is finding have dashes in their names (5-1, 5-2, 11-1), while during the initial channel scan, it sets up all the channel names with underscores (5_1, 5_2, 11_1).  As you can see from above, it says it could not find channel 2_1, but it shouldn't anyway since it is on a different carrier channel.  I don't know why it is complaining about 2_1 and not the rest of the channels that are also not on this carrier channel.  

Anyway, if you could help me figure this out, I'd really appreciate it.  I've looked all over for guides on how to setup MythTV for my HDHomerun, but they all seem to be for older versions, and obviously something has changed between 0.21 and 0.23 when it comes to setting up a HDHomerun.  Thanks!

Matt

---

### Post by ian dobson on 2010-07-27
Hi,

I'm not totally sure, but it looks as if something is screwed up in the DTV (multiplex) table.

Have you tried deleting all the channels/tuners and recreating them. I know it's a pain but it looks as if the upgrade didn't upgrade all the tables correctly.

Regards
Ian Dobson

---

### Post by Turtleggjp on 2010-07-27
Thanks Ian,

This is from a brand new install of Mythbuntu, there was no upgrade.  Deleting the channels and tuners wouldn't be that hard, but considering it is a fresh install I doubt that would do any good.  I happen to know the 4 sequential QAM channels that hold all the local channels that I care about, so re-scanning takes less than a minute.

When I got through the backend setup steps, I add both my HDHomerun tuners (0 and 1 from the same device) in step 2, add a single EIT source in step 3, then connect both tuners to the EIT source in step 4, running the limited scan for each one.  Does something seem wrong with that process?

Matt

---

### Post by ian dobson on 2010-07-27
Hi,

That looks about right. Are you using the fixes branch of 0.23 or just the plain 0.23.

Maybe try going over to the fixes branch, from what I remember/read in the dev mail list there where afew updates for the HDHomerun tuners.


Regards
Ian Dobson

---

### Post by Turtleggjp on 2010-07-27
I am using whatever comes with Mythbuntu 10.04.  I thought this was a release candidate actually.  How do I go about switching?

---

### Post by LowSky on 2010-07-27
the how to for enabling autobuilds (fixes branch as Ian put it)

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by Turtleggjp on 2010-07-27
Thanks.  I am updating now, and will report back later on tonight when I get home and connect the system back up to my tuner.  

I noticed that link during the Mythbuntu install.  I think it would be better if the choice of how to keep MythTV updated were an additional step in the Mythbuntu setup, rather than a link that goes by quickly during the install.  Especially when the version that comes with the distro is not even the final version, which I thought was the case with Mythbuntu 10.04 (and even 9.10 if I remember correctly).

Matt

---

### Post by Turtleggjp on 2010-07-27
Just tried it with the updated version of MythTV.  No change. :(  I even tried updating the firmware on my HDHomerun, but still no change.  Any other ideas?

Matt

---

### Post by static_g on 2011-10-01
For anyone else that finds this in a Google search...

To get MythTV .24 to use both HDHomeRun tuners, I had to:
1. Add each tuner, deviceid : 0,  and deviceid : 1.
2. Add a single input connection (not eit, see below), scan it on tuner 0, and also assign it to tuner 1. No need to rescan on tuner 1.
3. Make sure to set the recording group to Generic for both tuners. (When you go back in there, they will each be set to something else -- that's fine.) If you set both tuners to the same custom group, they can't/won't work at the same time.
4. In the frontend, General settings, "Avoid conflict between Live TV and scheduled shows".

On a separate note, EIT does not work for me with HDHR and .24. Your /var/log/mythtv/x.log will get filled up tons, and my HDHR was randomly changing channels on me. Disabling EIT fixes both problems.
[FONT=monospace][/FONT]

---

### Post by nickrout on 2011-10-01
> **static_g said:**
> For anyone else that finds this in a Google search...

To get MythTV .24 to use both HDHomeRun tuners, I had to:
1. Add each tuner, deviceid : 0,  and deviceid : 1.
2. Add a single input connection (not eit, see below), scan it on tuner 0, and also assign it to tuner 1. No need to rescan on tuner 1.
3. Make sure to set the recording group to Generic for both tuners. (When you go back in there, they will each be set to something else -- that's fine.) If you set both tuners to the same custom group, they can't/won't work at the same time.
4. In the frontend, General settings, "Avoid conflict between Live TV and scheduled shows".

On a separate note, EIT does not work for me with HDHR and .24. Your /var/log/mythtv/x.log will get filled up tons, and my HDHR was randomly changing channels on me. Disabling EIT fixes both problems.
[FONT=monospace][/FONT]

Most EIT source is crap anyway and should be avoided. This is particularly true in the USA, but there you are lucky enough to have Schedules Direct.

---

