---
title: "EIT/EPG from DVB-S fails  (mythtv 0.24)"
date: 2011-10-12
forum: Mythbuntu
---

### Post by MartinusEx on 2011-10-12
Hi Folks,

I just replaced my old mythbuntu by 11.04/0.24
The installation worked quite fine.
Besides the channel scan did not work so I had to switch to the channels.conf-method.

Now I experience the following:

In mythbackend setup (ahm german verknüpfungen, can't remember the correct english term)
where the video source and the tuner are combined, i set the grabber part 
to EIT/EPG only (from DVB-S) which worked fine with the old installation.

Now I do not see any EPG data.
From  frontend -> information-> systeminformation -> EPG-Data
I get that EPG data was successfully downloaded but no data is available.
Further two questions whether mythfilldatabase is running respectively if I have set it up to 
run frequently.


In the end I set the grabber source to a xmltv source from switzer land (no german availabe which
is not commercial- who might be THAT dumb ](*,) -)
But I'd like to continue to use EIT/EPG from DVB-S

Any ideas from the community?

THX a lot

Martin

---

### Post by shad0w_walker on 2011-10-12
When I setup my DVB-S the first time, it took a while to populate the data (It seems to come in slowly on each channel)
Have you tried leaving it set to EIT/EPG overnight and seeing it that gives you any result? Also, it might be worth checking if the tuner is to 'Open on demand'
That would only open the tuner card when it is being used for TV tuning and might stop it getting EIT/EPG data properly. If it's enabled, try turning it off and seeing if that helps.

---

### Post by iamlindoro on 2011-10-12
Using EIT with MythTV requires using the channel scanner.  EIT will not function when importing a channels.conf.

---

### Post by MartinusEx on 2011-10-17
@iamlindoro:
THX

not a solution but now I'm know what I feared..
I'll see how to get aorund this issue


Martin

---

### Post by alien878 on 2011-10-17
I believe you can correct this in mythweb.  Go to settings->channels.  There is a button for each channel to use EIT.  This has to be selected.

---

### Post by MartinusEx on 2011-10-17
@alien878
THX for your input

I checked the settings in mythweb, the checkbox for EPG is checked for every channel.
-> nothing happend
information -> system -> epg-Data shows 
any time of today
data OK but no data in mythconverg
does mythfilldatabase run?

So for my understanding:
when EPG is downloaded from a SAT channel, how is it transferred to mythconverg?

For instance:
Is the downloaded data stored to a certain file and grabbed by mythfilldatabase?
Any other way of working

THX

Martin

---

### Post by alien878 on 2011-10-18
The backend will crawl the tuners when it is idle (not recording anything) for EIT information.  As someone else mentioned, this can take some time.  For me, it takes several hours, but it probably depends on the number of channels and how often guide info is sent.

If waiting longer doesn't work, I suggest you check /var/log/mythtv/mythbackend log.  EIT scanning is logged there, so you should see something.

---

### Post by iamlindoro on 2011-10-18
Once again, no matter what you do to it, EIT *will not function* when you use channels.conf import.

You *must* use the MythTV channel scanner for EIT to function.  You cannot "correct" it in mythweb or anywhere else.

Robert
MythTV

---

### Post by MartinusEx on 2011-10-19
To iamlindoro and aline 878,

first of thank you for your comments and support

> **iamlindoro said:**
> Once again, no matter what you do to it, EIT *will not function* when you use channels.conf import.

You *must* use the MythTV channel scanner for EIT to function.  You cannot "correct" it in mythweb or anywhere else.

Robert
MythTV

Robert,

I went to mythbackend setup and did the following:

I deleted all channels set by channels.conf within "channel settings" (translated from German "Sender Einstellungen") where one can manage channels for existence, visibility and channel number and so forth.
Then I ran a scan again on "All transponders".
Interestingly this time it worked, I could see receiving levels of the sat antenna and the count of channels found.
The now found channels where stored to the database.

So I assume that mythtv now is in a state where it had used the channel scanner and knows to find its channels.
Is this sufficient to get rid of this "channels.conf" limitation with respect to EIT/EPG?

Looking into Information -> system -> EPG data it says:
Frontend version : ....
Last update of EPG/EIT
Begin 2011-10-19 11:03
End 2011-10-19 11:03
Result: Successful

Still there is the question if I have mythfilldatabase active

In  /var/log/mythtv.mythbackend.log I found :

```

2011-10-19 11:03:30.741 Running mythfilldatabase
2011-10-19 11:03:31.334 MainServer::ANN Monitor
2011-10-19 11:03:31.406 adding: mythbuntu as a client (events: 0)
2011-10-19 11:03:31.449 MainServer::ANN Monitor
2011-10-19 11:03:31.489 adding: mythbuntu as a client (events: 1)
2011-10-19 11:03:31.585 Reschedule requested for id -1.
2011-10-19 11:03:31.814 Scheduled 15 items in 0.2 = 0.09 match + 0.13 place
2011-10-19 11:10:26.858 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-10-19 11:17:01.912 MainServer::ANN Monitor
2011-10-19 11:17:01.991 adding: mythbuntu as a client (events: 2)
2011-10-19 11:25:26.947 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-10-19 11:40:27.031 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-10-19 11:55:27.115 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

```

I do not see what is wrong here.


Open question:

If I started off with "channels.conf", is it sufficient to get back to normal behavior (re EIT/EPG) when I do as I did (see above)

Again: With mythtv 0.21 the Hauppauge DVB-S card worked fine, so I do not understand, why with 0.24 scanning channels seems not to work anymore, so that I was forced to use channels.conf first hand.
Might this be a bug?

Any other suggestions?

THX

Martin

---

### Post by iamlindoro on 2011-10-21
No, the channels are just program numbers on multiplexes-- it's the multiplexes you imported with channels.conf which are broken.  You need to start with a band new video source, with no channels or multiplexes defined, and scan from scratch, to get working EIT.  Any attempt to remove only the channels will leave the broken configuration.

Robert

---

### Post by MartinusEx on 2011-11-05
Robert,

I set up a new video source and ended up as in the beginning.
Mythtv is not able to tune my Hauppauge DVB-S.
Some errors are stated, which do not help to solve the issue

I close this thread although not solved and refer to one thread I opened up earlier referring to the tuning problem..

THX for all your input Folks

rgds

Martin

---

