---
title: "Not finding all ClearQAM channels"
date: 2009-02-07
forum: Mythbuntu
---

### Post by The Odometer on 2009-02-07
I have a Pinnacle 800i Hybrid Tuner. I set it up successfully in Myth and scanned for channels, specifically looking for ClearQAM channels. I found about 10 ClearQAM channels. They all worked perfectly, but I should have found around 95. The issue is that my cable provider only broadcasts 20 or so analog channels. The other basic channels are broadcast via QAM--so I have to get it working to use Myth. It seemed that it would find one or two more each time I scanned, really weird.

I wanted to make sure the channels were there, so I installed Windows 7 and got it working and scanned--I found all of the expected channels, so I know they are there, and my hardware can find them.

Anyone have any ideas on how to find the ClearQAM channels in Myth? I'm not going to use Windows--unless I'm totally forced (and then, I still might now...) I tried the guide here: [http://www.mythtv.org/wiki/Adding_QAM_Channels_For_HDTV_Tuner_Cards](http://www.mythtv.org/wiki/Adding_QAM_Channels_For_HDTV_Tuner_Cards) and was able to generate a channels.conf--but got lost shortly thereafter. I couldn't fix it using the DVB search option--

Please help, because I want to use Mythbuntu as I love many of the other features that it give me! (and the wife is dying for it to get going again!)

Thanks!

---

### Post by toddk111 on 2009-02-08
Have you tried scanning all forms of QAM?  

When I set up my machine, I scanned for QAM64...then scanned again for QAM128 with mininimal updates...and finally scanned again with QAM256 and minimal updates.  My cable provider has some channels in QAM64 and some in QAM256 so I did end up getting more channels after all of those scans.  

Hope this helps.
-Todd

---

### Post by The Odometer on 2009-02-08
Thanks for the advice--I had tried that--and it helped..but I am still missing a bunch of channels. Seems as if (based on the Windows scan) that my cable provider actually gives me two types of each channel (maybe one QAM-64, one QAM 256?). However, I'm not finding any of them (especially ESPN!)

---

### Post by toddk111 on 2009-02-08
Hmm...strange.  On my FusionHDTV5 USB tuner, the Windows application will tell me the type of QAM for each channel and if the channel is unencrypted.  Does the Windows application that comes with your Pinnacle 800i Hybrid tuner give any details about the channels it found?  

I wouldn't think its a tuner issue, I've done scans in Myth using both my HDHomeRun and my FusionHDTV5 USB tuners and received the same channels.  This is also the same channel list as my scans performed in Windows.

One other thought...your tuner is a Hybrid.  Are you sure that the Windows application is only finding QAM and not also finding analog channels?

---

### Post by The Odometer on 2009-02-08
Turns out my tuner was finding both the analog and the digital channels. My cable company broadcasts the first 20 channels in both digital and analog, then the rest in only digital. They were labeled as such on the windows app--plus--I had three entries (two digital, one analog) for some channels. 

I've heard that people have had issues with Myth's included scanner--but I can't find an easy to use guide on using the command line utilities. This wouldn't be an issue if my cable provider had not decided to change everything up in November...

(My PVR 150 was working beautifully!)

---

### Post by newlinux on 2009-02-09
Just to be sure, those channels that windows is finding and myth isn't are unencrypted QAM, correct - so you verified you can view them in Windows? My cable provider did the same thing and for now they are all unencrypted QAM, but they say they are going to encrypt them. But for now I'm loving having all those stations unencrypted QAM because most of my tuners are digital. I n addition to the QAM 64 and 256 scans, try some of the HRC and IRC scans as well (I think those are available).

I will note, that tuning sensitivity can vary, and some apps have different thresholds than others. And the strength of signal can vary too. There are two channels that when I scan in one place in my house I always get, but other places never get them. Using the same model card.

As for commandline, I can help you with that. I did this a while ago, and I may miss some steps, but you want to do something like:

```

sudo apt-get install dvb-utils
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-Standard-center-frequencies-QAM256 > ~/.mplayer/channels.conf

```
(you may want to scan other QAM frequencies as well and append those to the channels.conf. You can find the other QAM frequencies in /usr/share/doc/dvb-utils/examples/scan/atsc/) 

These scans will take a while and will show errors where things aren't tuned. Just let them complete - this is normal.

Then you can use mplayer to step through the channels

```

mplayer dvb://channelName

```
Channelname is whatever is before the first : in each line of the channels.conf file. You can step forward and backwards through channels in mplayer using the h and k keys, if memory serves me correctly. Otherwise you could just keep calling mplayer with a different channel name.

hope that helps and hope I didn't forget something in those steps.

---

### Post by The Odometer on 2009-02-10
Thanks for the help so far. Here's what I got:

When I ran dvb utils--I was able to generate a channels.conf. However, I'm having issues tuning mplayer to a channel using it. Here's a splice of my channels.conf...

```
[0002]:219000000:QAM_256:33:36:2
[0003]:219000000:QAM_256:49:52:3
[0004]:219000000:QAM_256:65:68:4
[0005]:219000000:QAM_256:81:84:5
[0006]:219000000:QAM_256:97:100:6
[0007]:219000000:QAM_256:113:116:7
[0008]:219000000:QAM_256:129:132:8
[0009]:225000000:QAM_256:145:148:9
[000a]:225000000:QAM_256:161:164:10
[000b]:225000000:QAM_256:177:180:11
[000c]:225000000:QAM_256:193:196:12
[000d]:225000000:QAM_256:209:212:13
[000e]:225000000:QAM_256:225:228:14
[000f]:225000000:QAM_256:241:244:15
[0010]:225000000:QAM_256:257:260:16
```

When I try to tune a channel, mplayer says that no channel exists.

I also tried w_scan to little success either. 

And yes, I have verified the channels I saw on windows were both QAM and not encrypted. The cable company has made that well known around here as well. I was able to tune the channels with little to no issues. I'm still able to scan in Myth and get a few channels here and there (today I got TLC and Animal Planet--along with a few channels with no data).

In the past I've picked up TNT, WGN, CMT, BET, a couple of local channels, and ironically enough, the cable systems QAM test channel.

Thanks for the help so far and I look forward to figuring this out.

---

### Post by newlinux on 2009-02-11
Sorry to if this is too elementary, but you have your channels.conf file in ~/.mplayer, correct?

What does mplayer output when you do:

```

mplayer dvb://

```

From there you can also move up and down the channels with h and k keys. Maybe it doesn't like the brackets in the channel name... in my channels.conf I have replaced all those with real channel names...

I'm just curious if you are getting more channels with the scan utility than you are with myth's

---

### Post by The Odometer on 2009-02-11
Ok--now some progress. When I typed in mplayer dvb:// at the command line--I began to be able to go through channels. Obviously--it did not like my channel configuration. However, I was going through and it stopped and said end of file at channel 12. I should have quite a bit more, judging by the size of the file (366 services came up). Is this because I got to a channel that was found that did not exist?

Either way, scan found significantly more channels than did myth. Since it was dvb://, I'm assuming that it was actually digital (b/c those channels are also broadcast as analog--through channel 20).

Edit: Just found more channels in my Myth Scan. It also, for the first time, identified the channels by their name. It seemed as if the tuning by mplayer affected myth. Is that possible?

---

### Post by The Odometer on 2009-02-12
I was able to find all of my QAM channels using mplayer tonight. I edited my channels.conf so that it now reflects what I should be finding. 

So now--the question--how to import it into myth?

I've tried to go to the channel scanner and import channels.conf--and it "scans" and says it cannot find the channels.


Any ideas?

---

### Post by newlinux on 2009-02-13
Clearly there is a problem with myth's scanner, if the scan utility can pick up all the channels - but at least we know it isn't a Linux specific problem.

I did a little research on this, and all I could fine is that for many people importing the channels.conf worked well in .20 but not in .21 - when I get a chance I'll look into it more and see if I can find out how to get this to work. You can manually enter all the transports and multiplexes into the database - but that seems painstaking and error prone...

---

### Post by The Odometer on 2009-02-13
First of all--thanks for the help. I kinda found the same thing looking around last night (that this seems to be a problem with 0.21, etc). I tried to manually enter the transports into myth..but it still did not find the channels. Clearly, the bunch of channels that it found the other day were on the same frequency (from looking at my channels.conf). 

I'm going to try to scan elsewhere tonight or tomorrow. This cable line that it is connected to is split before it comes out of the wall. Others in the house aren't split--so maybe that will give me a different result.

---

### Post by The Odometer on 2009-02-14
It appears that I have solved this issue, at least. The key was extending the scan timing. I checked the box for "Ignore signal timeout" and extended the time for the scan of each channel. I also scanned each transport--which picked up all of the channels, most of them correctly named.

I have a few issues, but I can at least--begin to watch TV and record. Thanks for all the help!

---

