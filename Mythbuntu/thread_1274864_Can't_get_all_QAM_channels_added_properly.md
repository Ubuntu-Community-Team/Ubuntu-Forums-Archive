---
title: "Can't get all QAM channels added properly"
date: 2009-09-25
forum: Mythbuntu
---

### Post by yzfr1 on 2009-09-25
New to mythbuntu and trying to get everything running.

Hauppauge 1250

uname
2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

I am having trouble getting all of my channels to show up.

I have digital cable through time warner.

First I tried scanning through the myth frontend but that didn't seem to work at all.  I ended up with channels with no names and I didn't get very many channels at all.

So I did research and I found this [link]("http://www.mythtv.org/wiki/Adding_QAM_Channels_For_HDTV_Tuner_Cards") for adding dvb channels for QAM.

I did that and ran the scan.  I ended up with around 229 channels in my list.

I had some problems with mplayer playing streams to verify these channels (mplayer was not enable with db option at configure).  I fixed that.  That is another story as it took me a while to find that out.

Ok so I have a file with 229 channels found with scan.  However, when I ran the script from this [page]("http://www.mythtv.org/wiki/DVB_search"), which shows me how to write a script and use mencoder to output the video and verify the channel, I ended up with only a small amount of channels.

I know these channels can't be all of my channels.  I understand some channels are encrypted and some are not.  I can get a lot of channels on a tv that is only connected through regular coax.

If I can get all of these channels without going through time warner's hdtv cable box then why can't I view them through my tuner card?

What do I need to do to view these channels?  How do I find the channels I am missing and add them?

I have looked over many different sites so any help would be much appreciated.

Thanks.

---

### Post by mitchell2345 on 2009-09-25
First your TV has a QAM and Analog tuner.  So analog channels are going to show up as 15, 64, 18, etc.  Digital channels as: 56-1 or 56.4.

Your digital QAM tuner can only pick up the channels that are digital.

Now, a good ref to see what channels you *should* get is Silicons HDHomerun lineup server.

[http://www.silicondust.com/hdhomerun/channels_us](http://www.silicondust.com/hdhomerun/channels_us)

Is that matching what your TV gets?

Also, I assume you are using .21-fixes and not trunk?

Mitchell

---

### Post by yzfr1 on 2009-09-25
> **mitchell2345 said:**
> First your TV has a QAM and Analog tuner.  So analog channels are going to show up as 15, 64, 18, etc.  Digital channels as: 56-1 or 56.4.

Your digital QAM tuner can only pick up the channels that are digital.

Now, a good ref to see what channels you *should* get is Silicons HDHomerun lineup server.

[http://www.silicondust.com/hdhomerun/channels_us](http://www.silicondust.com/hdhomerun/channels_us)

Is that matching what your TV gets?

Also, I assume you are using .21-fixes and not trunk?

Mitchell

Thanks for the reply Mitchell.

I am only looking for digital channels at this point.  I used the QAM-256 file for scanning (tried standard, HRC, and IRC)

I have to be honest, I don't know if I am using .21-fixes.  How do I tell?  I just installed everything about 2 weeks ago..  re-installed many times in the first few days due to graphics card issues.

I do not find most of those channels listed on that website.  That is my problem.  I followed the directions to scan and view the channels but I don't seem to come up with them.  I would say I might get just a few of them.  

Like I said, my scan with dvb-apps produced 229 channels.  However, I can't view most of them on mplayer.  I tried testing them with dvb-apps/test_dvr while tuning a channel with azap and I didn't get anything with many of the channels I couldn't view in mplayer. 

So, what do I need to do to find these channels and tune them in?  

I know they exist and are not encrypted as I can view them on a tv that uses just the normal coax cable.

---

### Post by mitchell2345 on 2009-09-25
who is your providor? and what zip.

If you havent changed anything out of mythbuntu your running .21-fixes.

What ATSC card are you using?

Mitchell

---

### Post by yzfr1 on 2009-09-25
> **mitchell2345 said:**
> who is your providor? and what zip.

If you havent changed anything out of mythbuntu your running .21-fixes.

What ATSC card are you using?

Mitchell

I haven't changed anything out of mythbuntu other than the updates that come through automatically.  Which I haven't even downloaded them in a few days as I don't want to mess up any work that I have already done.

I have Time Warner Cable
I am using Hauppauge 1250 tuner.
Zip code 75254 
Dallas, TX

I found this [link ]("http://www.mythtv.org/wiki/Allen%2C_TX_75013")which says they are getting all of these channels..  and that is what I should be getting as Allen, the city they are in, is serviced by the same area as I am.  They are about 10 miles away and inside the North Dallas/DFW area.

---

### Post by mitchell2345 on 2009-09-25
when you configure the capture card what settings are you doing?

---

### Post by yzfr1 on 2009-09-25
> **mitchell2345 said:**
> when you configure the capture card what settings are you doing?


Sorry a little new to all this.

Can you be more specific?  Configuring it where?  The MythTV Backend?

---

### Post by mitchell2345 on 2009-09-25
in mythtv-setup, first option captures cards.

---

### Post by yzfr1 on 2009-09-25
> **mitchell2345 said:**
> in mythtv-setup, first option captures cards.


Capture Card

Card Type : DVB DTV capture card (v3.x)

DVB Device Number: 0

Frontend ID : LGT3305 Subtype: ATSC

Signal Timeout: 3000

Tuning Timeout: 5500

---

### Post by mitchell2345 on 2009-09-25
looks like you have it configured right.  

how many channels you get with mythtv setup?

when you scan you wont get channel names.  you will need to manually enter channel names and xmltvid's from schedules direct then run a mythfilldatabase.

I can show you later this afternoon if you like.

Mitchell

---

### Post by yzfr1 on 2009-09-25
> **mitchell2345 said:**
> looks like you have it configured right.  

how many channels you get with mythtv setup?

when you scan you wont get channel names.  you will need to manually enter channel names and xmltvid's from schedules direct then run a mythfilldatabase.

I can show you later this afternoon if you like.

Mitchell


If I run channel scan with mythtv I get about 30 channels.

Some of them they don't seem to play or crash my frontend.

I had looked through them and didn't see some of the channels I know I should get.

I have seen many people saying that mythtv scan doesn't get all of the channels.  has this been fixed?

If you could show me the best way of doing it that would be great!  Many thanks!

---

### Post by yzfr1 on 2009-09-25
> **mitchell2345 said:**
> looks like you have it configured right.  

how many channels you get with mythtv setup?

when you scan you wont get channel names.  you will need to manually enter channel names and xmltvid's from schedules direct then run a mythfilldatabase.

I can show you later this afternoon if you like.

Mitchell


Mitchell, I appreciate all of you help.  Will you be able to help me get this set up correctly?

---

