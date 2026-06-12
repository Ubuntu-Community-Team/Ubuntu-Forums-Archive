---
title: "mythtv backend closes after been left running"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by Dubstar_04 on 2007-04-24
Mythtv has started closing the backend of its own accord. 

Where do i look for log files?
is there any power saving options that would cause myth / mysql to close?

I have the autowake / shutdown options disabled and the problem doesn't seem to folow any rules, or patterns. sometimes it can be running 30+ hours and then close and some times it does it straight after boot!!

not the same problem but is it possible to stop the check that starts after being booted 30 times? as i won't be upgrading this pc once all the niggles are solved??

Dubstar_04

---

### Post by josesanders on 2007-04-24
Do you have multiple TV cards or video devices?  The backend can crash if it tries to access an incorrectly configured device.  This might account for the seemingly randomness of the crashing, because it won't always necessarily be accessing that device.

To see why it is crashing, I recommend running mythbackend in a terminal.  That way, you should be able to see any error messages.

---

### Post by Dubstar_04 on 2007-04-24
I have two cards configured. how do i run ythtv backend in terminal 

```
 mythbackend && ? 
```

if this is the problem would it still crash after 30+ hours first 10 being in use and the other 20 being idle?

its a weird problem!!

---

### Post by josesanders on 2007-04-24
To run mythbackend in the terminal:

$ sudo mythbackend

If you have two cards, maybe the second card is not configured correctly, but it doesn't cause a problem until MythTV tries to access it, i.e. when it needs to record two programs at the same time.  As long as it is only recording one thing, it may only access the first card every time.

---

### Post by Dubstar_04 on 2007-04-25
I can watch one channel and record one fine, i'm 99% sure that the cards are confgured properly. Its only started doing it over the last few days before that it was left on over 3 days at a time with no problem. It crashes when its idle too!! 

I might just reinstall the whole mythtv suite for peace of mind. 

What do you think?

---

### Post by superm1 on 2007-04-25
> **josesanders said:**
> To run mythbackend in the terminal:

$ sudo mythbackend

If you have two cards, maybe the second card is not configured correctly, but it doesn't cause a problem until MythTV tries to access it, i.e. when it needs to record two programs at the same time.  As long as it is only recording one thing, it may only access the first card every time.
Be careful launching it this way.  You will get recordings owned by root created that you won't be able to touch.

Your best bet is to look at all logs in /var/log/mythtv, and see if there is any indication of what is said when the backend crashes.  If nothing is narrowed down via this, then you can add more options to /etc/default/mythtv-backend and restart via the init script.  Then the extra options will take effect and cause more logging to /var/log/mythtv/*

---

### Post by Dubstar_04 on 2007-04-25
I have had a look at the logs. This is the time that it crashed. It crashed at exactly 9 pm just as two program were about to start. Please could you   
cast your eye over it see if you notice anything?

```
 2007-04-24 21:00:04.226 AFD: Opened codec 0xa9e886c0, id(MPEG2VIDEO) type(Video)
2007-04-24 21:00:04.249 AFD: Opened codec 0xa9e3e990, id(MP3) type(Audio)
2007-04-24 21:00:04.251 AFD: Opened codec 0xa9e26cf0, id(MP3) type(Audio)
2007-04-24 21:00:04.252 AFD: Opened codec 0xa9e27040, id(DVB_SUBTITLE) type(Subtitle)
[mpeg2video @ 0xb722a2e8]ac-tex damaged at 7 33
2007-04-24 21:00:04.874 Finished recording Britain's Drowned World: channel 1004
2007-04-24 21:00:05.740 Finished recording Britain's Drowned World: channel 1004
2007-04-24 21:00:06.436 TVRec(1): RingBufferChanged()
2007-04-24 21:00:06.496 Finished recording Britain's Drowned World: channel 1004
2007-04-24 21:00:08.709 Preview Error: Previewer file '/media/sdb1/Recorded TV/1004_20070424210003.mpg' is not valid.
2007-04-24 21:00:08.710 Reschedule requested for id -1.
2007-04-24 21:00:09.173 Scheduled 5 items in 0.5 = 0.25 match + 0.21 place
2007-04-24 21:02:11.516 Using runtime prefix = /usr
2007-04-24 21:02:11.940 New DB connection, total: 1
2007-04-24 21:02:12.025 Connected to database 'mythconverg' at host: localhost
2007-04-24 21:02:12.044 Current Schema Version: 1160
Starting up as the master server.
2007-04-24 21:02:12.558 New DB connection, total: 2
2007-04-24 21:02:12.644 Connected to database 'mythconverg' at host: localhost
2007-04-24 21:02:12.748 EITHelper: localtime offset 1:00:00 
2007-04-24 21:02:12.840 New DB connection, total: 3
2007-04-24 21:02:12.847 Connected to database 'mythconverg' at host: localhost
2007-04-24 21:02:12.969 EITHelper: localtime offset 1:00:00 
2007-04-24 21:02:12.981 DVBChan(1) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2007-04-24 21:05:00.253 Using runtime prefix = /usr
2007-04-24 21:05:00.738 New DB connection, total: 1
2007-04-24 21:05:00.768 Connected to database 'mythconverg' at host: localhost
2007-04-24 21:05:00.879 Current Schema Version: 1160
Starting up as the master server.
2007-04-24 21:05:01.290 New DB connection, total: 2
2007-04-24 21:05:01.513 Connected to database 'mythconverg' at host: localhost
2007-04-24 21:05:01.681 EITHelper: localtime offset 1:00:00 
2007-04-24 21:05:01.778 New DB connection, total: 3
2007-04-24 21:05:01.804 Connected to database 'mythconverg' at host: localhost
2007-04-24 21:05:01.926 EITHelper: localtime offset 1:00:00 
2007-04-24 21:05:03.267 New DB scheduler connection
2007-04-24 21:05:03.574 Connected to database 'mythconverg' at host: localhost
2007-04-24 21:05:03.894 Main::Starting HttpServer
2007-04-24 21:05:04.239 Main::Registering HttpStatus Extension
2007-04-24 21:05:04.831 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-04-24 21:05:04.836 Enabled verbose msgs:  important general
2007-04-24 21:05:04.954 AutoExpire: Found 2 recorders w/max rate of 277 MiB/min
2007-04-24 21:05:05.091 AutoExpire: Required Free Space: 4.2 GB w/freq: 5 min
2007-04-24 21:05:06.064 Reschedule requested for id -1.
2007-04-24 21:05:09.056 Scheduled 5 items in 3.0 = 2.42 match + 0.57 place
2007-04-24 21:05:09.136 Recording starts soon, AUTO-Startup assumed
2007-04-24 21:05:10.553 TVRec(1): Changing from None to RecordingOnly
2007-04-24 21:05:10.566 TVRec(1): HW Tuner: 1->1
2007-04-24 21:05:10.686 Started recording: CSI - Crime Scene Investigation: channel 1005 on cardid 1, sourceid 1
2007-04-24 21:05:11.576 MainServer::HandleAnnounce Monitor
```

---

### Post by josesanders on 2007-04-25
I see this:

> 2007-04-24 21:02:12.981 DVBChan(1) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)

But maybe that isn't the problem.  Since as you said, it crashed at exactly the time when two programs were about to be recorded, it would seem to be a problem with your second card.  What types of cards do you have?  If you take the primary card out, can you record or watch live TV from MythTV using only the secondary card?

---

### Post by Dubstar_04 on 2007-04-25
I have two cards.
1. Hauppauge 1300 HVR
2.compro T300

I can use the cards as expected. when one car is in use i can open up live tv and watch it and change channels with the second card, it also says the correct card in the osd when live tv is started.

now you mention there maybe a problem i have noticed this. when i'm watching tv and a recording is about to begin a dialog box pops up saying that mythtv is scheduled to record and wants to change channels then give a list of options and a 5 minute timer. I expected it to just use a free card instead of notifying the user. is this correct or is one of my cards faulty? 

I do have other cards to try, maybe that is an option. I have another hauppauge hvr 1300 card, maybe i should use both of them and get rid of the compro one??

it does work fine most of the time just every so often it goes mad!!

I do need a reliable system as this pc will be going to my parents when it is all sorted.

---

### Post by josesanders on 2007-04-26
I'm not sure what the problem is, but the compro card uses an saa7134 chipset.  Cards like that have always been a problem, but if you are sure you can watch live TV from within MythTV using that card, then the card should be working.

If you have the option, I would try putting in the second Hauppauge and letting it run for about a week to see if you get the same problem.  At least then you can narrow down what the problem is.

---

### Post by Dubstar_04 on 2007-04-26
The problem has now gone again!! 

The box has been on for over 24 hours with no problems. Its so frustrating!!

---

### Post by josesanders on 2007-04-26
Just a thought, and I'm not sure if it applies to your situation, but when I used two TV cards, when I started up the machine, the order they were loaded in seemed to be totally random.  Sometimes my PVR150 would be device 0 and my saa7134 would be device 1.  And sometimes it was the other way around.  The MythTV setup expects the same card to always be the same device number, so sometimes when I booted up, the backend would crash because it was trying to access the saa7134 as a PVR150.

It's just an idea.  I still would recommend that you put in the second hauppauge card.

---

### Post by Wiiilmaa on 2007-04-27
Hello,

I have got a similar problem running mythtv on Ubuntu with three identical cards all running simultaneously.
I noticed that the log file often is empty when MythTV crashes so the problem could be bound to logrotation.

I will do some further investigation...

---

### Post by Dubstar_04 on 2007-04-27
damn box has been on 3 days ans is still fine!! 

I shouldn't be complaining but its so annoying because i know it will crash next week half way through a good film!!

---

### Post by Dubstar_04 on 2007-05-01
I tried installing both hauppauge cards and I couldn't get the sound device to loads at 0 so I can't use both cards together under feisty. The problem was simple to resolve in edgy, simply adjust the alsa-base file to the require settings and voila the vards loaded in the required order.

I have also spent the last few days altering the text sizes in the xml files so everything looks good in an openbox session. I'm now really pleased with how it all looks.

---

### Post by Dubstar_04 on 2007-05-01
Check out these tv logos They really modernize the look of mythtv. I might post them as a new thread.

---

### Post by superm1 on 2007-05-01
> **Dubstar_04 said:**
> Check out these tv logos They really modernize the look of mythtv. I might post them as a new thread.
Ooh I do like these.  Start another thread about them explaining how to use and such.

---

### Post by Dubstar_04 on 2007-05-08
after trying for days on end to get my two hauppauge 1300 hvr cards to work together, I have given up and ordered two hauppauge nova-t pci cards. I just couldn't get the hvr cards to work because ubuntu always loads one as a sound card and i can't get any sound because of it!!

I am desperately hoping that I have not made a massive mistake and that this will solve the problem, because if it doesn't i will be stuck with 6 tv tuners and only be able to use 1!!

Has anyone had any luck using multiple Nova t cards??

---

### Post by Dubstar_04 on 2007-05-09
Hey hey hey, I got my Nova t cards today and what a difference!!! I have them both installed and they don't show up as sound devices, so thats the sound problem solved!! 

Now only time will tell if the backend closing issue is still alive!!

Anyone want to buy a 2 hauppauge hvr 1300 cards? Ha ha!!

---

