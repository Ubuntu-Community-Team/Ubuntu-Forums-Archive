---
title: "&quot;Weak Signal&quot; quality even with a strong signal"
date: 2010-02-25
forum: Mythbuntu
---

### Post by boombox1387 on 2010-02-25
I've been using MythTV for less than 24 hours, and considering my lack of expertise in this area, things really aren't going *that* badly.  Unfortunately I've run into a bit of a problem, and I'm out of ideas; thus, I turn to you, Community ;)

The Setup:
I'm in Tampa, FL, so I'm watching US broadcasts.  I'm only attempting to watch over-the-air broadcasts (no cable).  I'm receiving the signal with an RCA digital indoor antenna, which plugs into a single-tuner model of the SiliconDust HDHomeRun.  This plugs into my network, which connects it with my desktop computer (which should have specs more than sufficient for watching TV).  I'm watching live TV with the MythTV Frontend and Backend found in the repositories on my Ubuntu 9.10 installation.

The Problem:
When watching particular channels (but not all channels; just the ones I like), video and audio stutter quite a bit. Video becomes pixelated, and audio has frequent beeps and clicks.  Several channels are bordering unwatchable status.  This has all the signs of being an issue related to poor signal reception, except that NBC (channel 8.1) is unwatchable with 80%+ signal strength (depending on the location of the antenna, up to 95%), while Fox (channel 13.1) comes in perfectly with only 78% signal strength.

Also, possibly related, NBC takes a much longer time to get a Lock (not entirely sure what that is).  The higher the signal strength, it seems the longer it takes to get a lock.  When I move my antenna to a location with 93% signal strength, it times-out while trying to get a lock.  This could just be a coincidence; mostly I'm just curious about what this "lock" is.  NBC takes much longer than FOX and acts like it has a poor signal, so there seems to be some correlation.

The Solution:
This is where you come in.  I have no idea what would cause the symptoms of a poor signal when there isn't actually a poor signal.  I'm also not familiar enough with MythTV to know how to go about debugging.  None of my hardware seems to be running at full capacity: CPU at roughly 85% while watching TV, Memory only half full (and not swapping), and Network bandwidth at only a fraction of its potential.

Really, though, this seems more like a signal issue than a hardware issue.  The "static" looks very much like digital static, and moving the antenna seems to make some difference (though this could just be my imagination).  But the problem happens with more than half of my channels, regardless of their signal strength.  24 hours ago, when I first finished setup and configuration, there wasn't any noticeable problem with any of these channels.

As I said, I'm a complete TV noob, and I'm pretty out of ideas, so if you have any, I would be very grateful.

---

### Post by azmyth on 2010-02-25
You also have S/N and BE to take into account with S/N meaning signal to noise ratio and BE means Bit Error if your signal is good but the S/N and/or BE are high you'll get pixelated, stuttering etc on your TV.

When you first tune into a channel you'll see this info displayed.

---

### Post by boombox1387 on 2010-02-25
Thanks for the response; what are good/bad numbers for S/N and BE? Assuming this is the problem, what can be done to improve it?  Obviously I'd prefer software/free solutions, but failing that, would a higher quality antenna improve things?

---

### Post by azmyth on 2010-02-25
I was just messing around with mine and I went to station that had 79% signal 4.4dB S/N and BE 3000 and I got nothing. On most stations I see 92%+ 4.7dB and BE 0. I think it really varies amongst the three. Seems like the higher the BE the more you see junk on the screen and when the SN is below 4.7dB I don't get anything. Actually, you want the S/N to be high, I misspoke in my other post.

The better your collection efficiency the better your signal will be thus the better picture you receive so a better antenna is what you need.

---

### Post by tgalati4 on 2010-02-25
3 dB of Sigal-to-Noise is roughly:  noise strength is half of the signal level. 6 dB S/N: Noise is 1/4 the Signal level.  4.4 is in between.  For decent broadcast, you want 30 dB of S/N.  10 dB may be acceptable, but error-correction may show drop outs.

Go to anntenna.org and map your signal strength.  If you are 30 miles away from a transmitter, you want at least a 4-bowtie High Def, UHF antenna.  An 8-bowtie antenna (roughly 3' by 3') will give you 3 dB more signal and take you to 35 miles.  Trees, roofing nails, stucco, and moisture will degrade the signal.

Indoor antennas are 1-bowtie and don't really work.

Bit Errors should be 10^-5 to 10^7, in other words 1 in a million, and therefore not visible.

---

### Post by boombox1387 on 2010-02-26
Thanks for all the answers/suggestions.  A few more questions from my end:

-Where exactly to I go to get S/N information?  Frontend? Backend? I'm not seeing it when I tune into a channel.  Is it supposed to appear on the OSD, or somewhere else?  I'm fairly sure now that this is the root of my problem.

-@tgalati4, what exactly was the website you had in mind?  It seems like it might help, but anntenna.org and antenna.org both don't seem relevant.

Also, I've run into major problems now, but they might be better discussed somewhere else.  The address of my HDHomeRun on the network changed from xxx.xxx.x.3 to xxx.xxx.x.2, which just really threw the whole thing off.  I changed the MythTV backend to correctly (I think) handle this change, and it finds all the stations in a scan, but the frontend hasn't loaded any stations since the change.

---

### Post by boombox1387 on 2010-02-26
For the sake of keeping different issues in different threads, I've started [a new thread]("http://ubuntuforums.org/showthread.php?p=8884054") to deal with my current inability to watch any tv with the frontend, which I mentioned in my last post.

[http://ubuntuforums.org/showthread.php?p=8884054](http://ubuntuforums.org/showthread.php?p=8884054)

---

### Post by tgalati4 on 2010-02-26
Sorry, [www.antennaweb.org](www.antennaweb.org)

Real HDTV's have a signal meter buried in the advanced settings.  What TV card are you using?

---

### Post by gordintoronto on 2010-02-26
Here are instructions for building an almost-free antenna:
[http://www.youtube.com/watch?v=EWQhlmJTMzw](http://www.youtube.com/watch?v=EWQhlmJTMzw) 

I use a similar antenna with an actual HD TV, and it works great.

---

### Post by azmyth on 2010-02-26
Right when it tune it shows you the program info  through a popup and it also displays the signal strength etc.

I also use the antenna in the above link it does work well. Just make sure you have a place to hide it :o

---

### Post by boombox1387 on 2010-03-01
> **tgalati4 said:**
> Sorry, [www.antennaweb.org](www.antennaweb.org)

Real HDTV's have a signal meter buried in the advanced settings.  What TV card are you using?

Well, according to antennaweb.org, I shouldn't need anything too powerful to get a lot of channels in this area.

Also, I'm using the HDHomeRun TV tuner, which happens to come with this handy CLI application called hdhomerun_config.  Running that gives me all sorts of useful information about the signal.

```
$ hdhomerun_config FFFFFFFF get /tuner0/status
ch=8vsb:653000000 lock=8vsb ss=81 snq=73 seq=100 bps=19394080 pps=708

```

ss is signal strength, snq is signal quality, and seq is symbol quality.  While it isn't in the exact same form as S/N, it's telling me pretty much the same thing.  This station isn't bad (81% signal strength, 73% signal quality, and 100% correct data from the signal over the last second).  Other signals, like the one I mentioned before, are much, much worse in the snq and seq categories.

Since I'm living in an apartment complex - covered in stucco, of course :p - I don't really know what my options are for outdoor antennas.  I'll probably ask, but I'm also going to try building my own as others suggested.

Thanks for all the tips and suggestions; keep them coming if you have more. :)

---

### Post by tgalati4 on 2010-03-01
Tampa is humid, and moisture can degrade the signal.  Perhaps the weak channel is coming from St Pete.

---

### Post by gordintoronto on 2010-03-01
There is a map showing where the TV stations are near Tampa, at this page:
[http://yourfreedtv.com/TampaBay/](http://yourfreedtv.com/TampaBay/)

It looks like most of them are together.  In an apartment, your neighbour might have something which interferes with or bounces the signal. Is it possible to move the antenna around?

---

