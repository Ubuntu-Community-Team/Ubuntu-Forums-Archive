---
title: "Program listings and channel problems"
date: 2009-03-13
forum: Mythbuntu
---

### Post by oldtincup on 2009-03-13
Hi.  I am a Comcast customer in Michigan tring to set up Mythbuntu Intrepid.  I have subscribed to Schedules Direct and 
set up Lineups.

I Have an HD5500.  The analog tuner is setup and working, as well as the listings for it, so I will restrict this to my 
digital issues.

I'm going to explain what I have done and the problems I've had along the way, my attempted solutions and where I am at now.

First I scanned for channels.  It found many unencrypted QAM channels ( I also elmminated music channels).

**Problem 1:** Almost all of these came up as unknown. 
 
I manually went through each of these channels and identified them.

**Problem 2:** Not all of these were available on one lineup from Schedules Direct, so I needed 2 digital lineups and created
them.

I then edited the channels - the channel numbers to match my TV set and the call signs, Xmltvid, etc from the lineups. 

I could watch TV and Change Channels, Yeh!

After more searching I came up with this method to combine the lineups / listings.  
I used "tv_grab_combiner" which I set up to use "tv_grab_na_dd" to get each of my listings. This give a xmltv style listing instead of raw, but that shouldn't be a big deal.

I then ran "mythfilldatabase --refresh-all" and after it was complete, I looked at the program listings.

**Problem 3:** All of the channels that I had edited came up as "no data", but I had listings with the channel numbers from 
the lineups.  All the data seemed to be there, but, not with my channel number.

More searching yielded the fact that the xmltv data used a different form for the xmltvid, insead of just using the 5
digit number it used "Ixxxxx.labs.zap2it.com" where xxxxx is the 5 digit xmltvid. 

Oh well, I just edited all the channels 
again using this entire string for the xmltvid.  Using phpmyadmin I also deleted all the channels that had come in with
the listings. I also determined that"--remove-new-channels" should prevent these listing channels from populating the 
database.

So I ran "mythfilldatabase --refresh-all --remove-new-channels".  Guess what. I am still at problem 3, no change.

Why does the "--remove-new-channels" not work?  Why doesn't program data show up for my edited channels?

Where do I go from here?****

---

### Post by klc5555 on 2009-03-13
> **oldtincup said:**
> Hi.  I am a Comcast customer in Michigan tring to set up Mythbuntu Intrepid.  I have subscribed to Schedules Direct and 
set up Lineups.

I Have an HD5500.  The analog tuner is setup and working, as well as the listings for it, so I will restrict this to my 
digital issues.

I'm going to explain what I have done and the problems I've had along the way, my attempted solutions and where I am at now.

First I scanned for channels.  It found many unencrypted QAM channels ( I also elmminated music channels).

**Problem 1:** Almost all of these came up as unknown. 
 
I manually went through each of these channels and identified them.

**Problem 2:** Not all of these were available on one lineup from Schedules Direct, so I needed 2 digital lineups and created
them.

I then edited the channels - the channel numbers to match my TV set and the call signs, Xmltvid, etc from the lineups. 

I could watch TV and Change Channels, Yeh!

After more searching I came up with this method to combine the lineups / listings.  
I used "tv_grab_combiner" which I set up to use "tv_grab_na_dd" to get each of my listings. This give a xmltv style listing instead of raw, but that shouldn't be a big deal.

I then ran "mythfilldatabase --refresh-all" and after it was complete, I looked at the program listings.

**Problem 3:** All of the channels that I had edited came up as "no data", but I had listings with the channel numbers from 
the lineups.  All the data seemed to be there, but, not with my channel number.

More searching yielded the fact that the xmltv data used a different form for the xmltvid, insead of just using the 5
digit number it used "Ixxxxx.labs.zap2it.com" where xxxxx is the 5 digit xmltvid. 

Oh well, I just edited all the channels 
again using this entire string for the xmltvid.  Using phpmyadmin I also deleted all the channels that had come in with
the listings. I also determined that"--remove-new-channels" should prevent these listing channels from populating the 
database.

So I ran "mythfilldatabase --refresh-all --remove-new-channels".  Guess what. I am still at problem 3, no change.

Why does the "--remove-new-channels" not work?  Why doesn't program data show up for my edited channels?

Where do I go from here?****

1) You do have to edit in the xmltvid numbers for most digital channels in Myth. In some cases the analogs too. But why would you want to combine listings using external software? The grabber is by itself perfectly capable of downloading channel information from two or three or more different schedulesdirect lineups, where you have already edited the unnecessary channels out of these lineups by logging in to the schedulesdirect website and using the edit screens. The pertinent bits and pieces of the two lineups you need, consisting of the remaining digital channels you actually can receive, can just be downloaded all together and your program schedule ends up seamless. For a while I had to use two Comcast lineups plus _one channel_ from the local Fios lineup. Once I edited the lineups on the website accurately to eliminate the stations I didn't need, the grabber was fine and the resulting schedule in Myth was seamless.

2) In mythfilldatabase, the "--refresh-all" switch begins refreshing with _tomorrow's_ data. To change _today's_ data, you have to explicitly use the argument "--refresh-today". You may actually already have your altered data on the edited channels, but not starting until after midnight tonight or midnight tomorrow.

Cheers! :)

---

### Post by oldtincup on 2009-03-13
> Originally Posted by **klc5555**
1) You do have to edit in the xmltvid numbers for most digital channels in Myth. In some cases the analogs too. But why would you want to combine listings using external software? The grabber is by itself perfectly capable of downloading channel information from two or three or more different schedulesdirect lineups, where you have already edited the unnecessary channels out of these lineups by logging in to the schedulesdirect website and using the edit screens. The pertinent bits and pieces of the two lineups you need, consisting of the remaining digital channels you actually can receive, can just be downloaded all together and your program schedule ends up seamless. For a while I had to use two Comcast lineups plus _one channel_ from the local Fios lineup. Once I edited the lineups on the website accurately to eliminate the stations I didn't need, the grabber was fine and the resulting schedule in Myth was seamless.

But, If I don't combine listings How do I set 2 Lineups to 1 video source to use for my digital tuner?

---

### Post by oldtincup on 2009-03-13
I looked ahead in my program listings for several days.  No data for my edited channels.

---

### Post by klc5555 on 2009-03-13
> **oldtincup said:**
> But, If I don't combine listings How do I set 2 Lineups to 1 video source to use for my digital tuner?

You don't need to. The grabber keeps grabbing until there is no more schedulesdirect data to download for the various xmltvids you have input for the channels that you have defined with your channel scan in Input Connections and that you may have further edited with your Channel Editor. 

Mythtv doesn't know or care that this data may have come from xmltvids that schedulesdirect  has assigned to different nominal lineups on their website. What your setting up different lineups on schedulesdirect does for you is tell the grabber which directory to look in on the website for the data pertaining to a particular xmltvid. From the grabber's point of view, there's nothing to combine. tv_grab_combiner appears to have been designed for European use with multiple grabbers on earlier iterations of Mythtv. Possibly all tv_grab_combiner has done for you is corrupt your mysql database to the point where you may have to start over with your backend setup. 

Which at this juncture is what I'd recommend doing. Just, when you get to it, omit the entire sequence implementing the tv_grab_combiner. Instead, after setting up your  2 lineups or partial lineups on schedulesdirect and editing in the appropriate xmltvid nos. in Channel Editor, just run mythfilldatabase and call it a day.

---

### Post by oldtincup on 2009-03-14
klc5555

Thanks for the info on how things work.  I'll go ahead and start over. At least it goes faster each time.

---

