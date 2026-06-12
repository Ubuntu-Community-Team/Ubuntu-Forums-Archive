---
title: "Analog TV dies"
date: 2009-12-28
forum: Mythbuntu
---

### Post by Johnius on 2009-12-28
I live on the border of the US and Canada.  This gives me the opportunity to watch TV in Digital (US) and Analog (CA).  Whenever I tune my Analog receiver on my Pinnacle 800i, I can watch for 10-60 seconds before the screen goes to static.  If I exit, I can retune and watch for another 10-60 seconds before it happens again.  Any ideas?  Where can I grab logs / data to help you help me?

Thanks.

---

### Post by Johnius on 2010-01-06
Bump.  I have Mythbuntu 9.10 with MythTV .22  I tried upgrading to .23, and it seemed to make things worse, so I went back to .22.  I'd really like to watch hockey and The Red Green Show.  Thanks!

---

### Post by Caps18 on 2010-01-07
Aren't the Canadian stations broadcasting in digital?

---

### Post by Johnius on 2010-01-08
Nope.  They are analog until later this year, I think.  But they are definitely still analog for a while.

---

### Post by ian dobson on 2010-01-09
Hi,

Do you see anything intersting in your backend log (/var/log/myhtv/mythbackend.log) or your syslog (/var/log/syslog) when you loose your analog channel?

Regards
Ian Dobson

---

### Post by Johnius on 2010-01-09
This is my backend log, which I think tells me my problems, but I don't know how to fix:

2010-01-09 09:39:58.235 TVRec(1): Changing from None to Watching WatchingLiveTV
2010-01-09 09:39:58.387 TVRec(1): HW Tuner: 1->1
2010-01-09 09:39:58.784 New DB connection, total: 4
2010-01-09 09:39:58.865 Connected to database 'mythconverg' at host: localhost
[COLOR="Red"]2010-01-09 09:39:58.943 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2010-01-09 09:39:58.979 NVR(/dev/video0) Error: Unknown audio codec[/COLOR]
2010-01-09 09:39:59.041 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-01-09 09:39:59.391 RecBase(1:/dev/video0): GetKeyframePositions(0,9223372036854775807,#1) out of 1

And this is my syslog:

Jan  9 09:39:01 dvr-desktop CRON[2135]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  9 09:39:59 dvr-desktop kernel: [  255.193227] cx88[0]: Calling XC5000 callback

I'm going to go poke around and see what happens.  I'd appreciate any further ideas.

Thanks for your help.
John

---

### Post by Johnius on 2010-01-09
I changed the settings like it said and got this:

2010-01-09 10:06:14.569 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
2010-01-09 10:06:14.700 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
strange error flushing buffer ... 
strange error flushing buffer ... 
strange error flushing buffer ... 
strange error flushing buffer ... 
strange error flushing buffer ... 
strange error flushing buffer ... 
strange error flushing buffer ... 
strange error flushing buffer ... 
2010-01-09 10:06:15.545 RecBase(1:/dev/video0): GetKeyframePositions(0,9223372036854775807,#1) out of 1

---

### Post by Johnius on 2010-12-09
My analog is still dying.  Any other suggestions?  I think (shot in the dark) that my digital tuner isn't shutting itself off because my EIT is set to scan when the card is inactive and it isn't populating the TV schedule if left on over night.  Any suggestions to check if the DVB card is being left on?

---

### Post by Johnius on 2010-12-10
The DVB is set to actively scan for EIT data by default.  If you open MythTVBackend -> Capture Cards -> DVB card -> Record options and then untick the "Actively Scan for EIT Data" box, it worked.  

I messed around with a LOT of settings today and managed to get rid of the "strange error flushing buffer" message (I think by trying MPEG, MPEG-2 settings [which naturally don't work, but I think it fixed my buffer]).

---

