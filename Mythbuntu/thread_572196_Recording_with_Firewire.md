---
title: "Recording with Firewire"
date: 2007-10-10
forum: Mythbuntu
---

### Post by dmfrey on 2007-10-10
I am experiencing some bizarre behavior when trying to record with firewire.  I am getting intermittent recordings.  If a show records, there is no issue, however, if I see in the logs that no signal was received within 15 seconds, the recording proceeds to record nothing for the duration and when complete, myth-backend dies.

My setup:
AMD 64 3200+
Asus nvidia 6200 turbo
250 GB hd
PVR 150 - Tuner 1
Firewire from DCT-6200 - Tuner 2

I can record from the pvr 150 without issue.

I did a fresh install of the latest beta, mythbuntu-7,10-071002-amd64.iso, and obtained all the latest updates from the repo.  This only appears to be since the update from the repo occurred.

I understand that there are issues with recording with firewire, i.e. the port seems to want to change from 2 to 1 whenever it feels like it.  I tried getting around this issue by plugctl at regular intervals to reset the firewire subsystem so that it is reading the information accurately.  However, after doing this, I see that the plugreport showed the correct information and myth-backend still died.

Thanks for any help.  Please let me know if there is anymore information I can provide.

---

### Post by tgm4883 on 2007-10-10
Unfortunatly that is a problem with firewire.  It sounds like a poorly broadcast signal from the cable company.  Is the backend log showing any errors?

---

### Post by dmfrey on 2007-10-10
Unfortunately, the mythbackend.log doesn't show anything because the backend server has died.  The only message is that a recording has finished.

I was attempting to do a cronjob at 28 and 58 minutes past each hour to reset firewire with plugctl so that it is always up to date.  Not sure if that helped or hurt anything.  Maybe I should try this in the mythty-backend init script instead of every half hour.

I was thinking of looking at IEEE1349 Commander project on Sourceforge to see if that utility can perform the reset.

---

### Post by tgm4883 on 2007-10-10
Yes, and the backend log should tell you why it crashed.  If nothing is in there you should look into the depth of logging that is being done.

---

### Post by dannyboy79 on 2007-10-10
the latest firewire_tester can reset the firewire bus just fine. You have to make sure that your firewire input is associated to a source that only has the channels that are "in the clear". I used test-mpeg2 to find out all of mine. I get 8 of them.

---

### Post by dmfrey on 2007-10-10
Here is the output from my logs

```
2007-10-09 20:38:58.056 AFD: Opened codec 0x830e60, id(MPEG2VIDEO) type(Video)
2007-10-09 20:38:58.057 AFD: Opened codec 0x917330, id(AC3) type(Audio)
2007-10-09 21:00:02.422 TVRec(2): Changing from None to RecordingOnly
2007-10-09 21:00:02.442 TVRec(2): HW Tuner: 2->2
2007-10-09 21:00:04.037 FireRec: Buffered packets 2000 (8000 KB)
2007-10-09 21:00:04.037 Started recording: The Unit "Always Kiss Them Goodbye": channel 2181 on cardid 2, sourceid 2
2007-10-09 21:00:04.074 scheduler: Started recording: The Unit "Always Kiss Them Goodbye": channel 2181 on cardid 2, sourceid 2
2007-10-09 21:00:19.058 FireRec: No Input in 15 seconds [P:0 N:2] (select)
2007-10-09 22:00:00.252 TVRec(2): Changing from RecordingOnly to None
2007-10-09 22:00:00.261 Finished recording The Unit "Always Kiss Them Goodbye": channel 2181
2007-10-09 22:00:00.264 scheduler: Finished recording: The Unit "Always Kiss Them Goodbye": channel 2181
2007-10-09 22:34:54     firewire ownership acquired
2007-10-09 22:34:58.268 Using runtime prefix = /usr
2007-10-09 22:34:58.438 New DB connection, total: 1
2007-10-09 22:34:58.482 Connected to database 'mythconverg' at host: localhost
2007-10-09 22:34:58.486 Current Schema Version: 1160
Starting up as the master server.
2007-10-09 22:34:58.511 mythbackend: MythBackend started as master server
2007-10-09 22:34:58.532 New DB connection, total: 2
2007-10-09 22:34:58.537 Connected to database 'mythconverg' at host: localhost
2007-10-09 22:34:58.539 EITHelper: localtime offset -4:00:00 
2007-10-09 22:34:58.543 New DB connection, total: 3
2007-10-09 22:34:58.544 Connected to database 'mythconverg' at host: localhost
2007-10-09 22:34:58.689 EITHelper: localtime offset -4:00:00 
2007-10-09 22:35:00.252 New DB scheduler connection
2007-10-09 22:35:00.253 Connected to database 'mythconverg' at host: localhost
2007-10-09 22:35:01.656 Main::Registering HttpStatus Extension
2007-10-09 22:35:01.656 mythbackend version: 0.20.20070821-1 www.mythtv.org
2007-10-09 22:35:01.657 Enabled verbose msgs:  important general
2007-10-09 22:35:01.669 AutoExpire: Found 2 recorders w/max rate of 210 MiB/min
2007-10-09 22:35:01.671 AutoExpire: Required Free Space: 2.6 GB w/freq: 5 min
2007-10-09 22:35:02.271 Reschedule requested for id -1.
2007-10-09 22:35:03.491 Scheduled 468 items in 1.2 = 0.85 match + 0.37 place
2007-10-09 22:35:03.497 scheduler: Scheduled items: Scheduled 468 items in 1.2 = 0.85 match + 0.37 place
2007-10-09 22:35:03.500 Seem to be woken up by USER
2007-10-09 22:35:08.521 mythbackend: Running housekeeping thread
2007-10-09 22:36:29.823 MainServer::HandleAnnounce Monitor
2007-10-09 22:36:29.827 adding: mythcenter as a client (events: 0)
2007-10-09 22:36:29.828 MainServer::HandleAnnounce Monitor
2007-10-09 22:36:29.830 adding: mythcenter as a client (events: 1)
2007-10-09 22:37:10.301 JobQueue: Commercial Flagging Starting for The Unit "Always Kiss Them Goodbye" recorded from channel 2181 at Tue Oct 9 21:00:00 2007
2007-10-09 22:37:10.307 commflag: Commercial Flagging Starting: The Unit "Always Kiss Them Goodbye" recorded from channel 2181 at Tue Oct 9 21:00:00 2007
2007-10-09 22:37:10.429 Using runtime prefix = /usr
2007-10-09 22:37:10.444 New DB connection, total: 1

```

You will notice at 21:00 the program starts to record.

At 21:00:19, the message FireRec: No Input in 15 seconds [P:0 N:2] (select) is displayed in the logs.

At 22:00, This message is displayed: Finished recording The Unit "Always Kiss Them Goodbye": channel 2181.  The resulting recording is nothing but a black screen.  This is where the backend shutdown.

I restarted it at 22:34:54 when my mythtv user obtains ownership of /dev/raw1394.  As you can see, there was no message as to why mythbackend died.

I have been noticing these messages when reviewing dmesg, however, I cannot tie them to outage in the mythbackend.log.
```
[80995.801581] mythbackend[5137] general protection rip:2afb074cb6ab rsp:428077d0 error:0
```

Thanks again for any help.

---

### Post by tgm4883 on 2007-10-10
just to be sure.  Have you checked to see if there is copy protection enabled on that channel?

---

### Post by dmfrey on 2007-10-10
It was the HD CBS offered by RCN in Allentown, PA.  This channel has not been encrypted in the past.  None of their broadcast channels are encrypted.  I guess I could test that this same behavior occurs by setting it to record something off of, say, HBO, which I know to be encrypted.

---

### Post by tgm4883 on 2007-10-11
Or you could just check the channel.  Wouldn't that be an easier test to see if it is encrypted.  I believe the button combo is like power then quickly press exit (or something like that, check the guide) then check for the two different encryption/drm settings.

---

### Post by dannyboy79 on 2007-10-11
or you could just do what I suggested and check the channels with test-mpeg2. then if it doesn't record a stream (fole size is 0) that means it's encrypted whether you thought it was or not. That's just the way it goes. You'll then have to tune to a KNOWN CLEAR CHANNEL, and use the firewire_tester with the -R switch to reset the firewire bus.

---

### Post by dmfrey on 2007-10-11
I am going to try with test-mpeg2 tonight when I get home.  For some reason, I cannot watch live tv on the firewire input, only the pvr150; I could do this before moving to mythbuntu.  The key editor says that 'C' is the key to switch between inputs, but it only stays on the pvr 150.

Thanks for everyone's help.

---

### Post by dannyboy79 on 2007-10-11
Y is the button to switch inputs. [http://www.mythtv.org/docs/mythtv-HOWTO-11.html](http://www.mythtv.org/docs/mythtv-HOWTO-11.html)

---

### Post by tgm4883 on 2007-10-11
> **dannyboy79 said:**
> or you could just do what I suggested and check the channels with test-mpeg2. then if it doesn't record a stream (fole size is 0) that means it's encrypted whether you thought it was or not. That's just the way it goes. You'll then have to tune to a KNOWN CLEAR CHANNEL, and use the firewire_tester with the -R switch to reset the firewire bus.

Wouldn't that also be the case if it wasn't setup correctly?

---

### Post by dannyboy79 on 2007-10-11
wouldn't "what" be the case if "what" wasn't setup correctly?

---

### Post by newlinux on 2007-10-11
You should check the box.
[http://en.wikibooks.org/wiki/How_to_use_a_Motorola_DVR/Configuration#How_To_Check_If_5C_DTCP_is_Enabled](http://en.wikibooks.org/wiki/How_to_use_a_Motorola_DVR/Configuration#How_To_Check_If_5C_DTCP_is_Enabled)

Please note that it can turned on program by program (they do this in my area) not just channel by channel. For example in my area CCI was set to 0x02 for the football games on CBS a couple of weeks ago. But not for other programs that I checked. So you might want to also check the settings on the programs you want to watch.

BTW, I think running that cronjob twice an hour every hour might mess up your recordings when the job runs... Not sure about this though.

---

### Post by newlinux on 2007-10-11
Oh, and 'C' switches inputs on the same card (such as if a card can tune analog and digital, like the Kworld ATSC110s or Dvico Fusion 5s or between the composite in and the tuner on a PVR-150). 'Y' switches  tuner cards.

---

### Post by tgm4883 on 2007-10-11
> **dannyboy79 said:**
> wouldn't "what" be the case if "what" wasn't setup correctly?

If the firewire wasn't setup correctly, wouldn't the foil size still be 0?  Therefore making it impossible to tell if it was an encrypted channel or an incorrect configuration of firewire?

---

### Post by dannyboy79 on 2007-10-11
you're correct, I assumed that he defined the node  and port correctly within mythtv-setup. you just use plugreport to find out your node and port, then use firewire_tester to check whether to use p2p or broadcast. I use p2p with a sa 3250hd. then you check your channels with test-mpeg2 to find out channels in the clear, if they record and you can playback file with mplayer, than that means they are in teh clear (for now anyway-damn cable companies!!!)

newlinux=I thought I read that he has a sa 3250hd stb. I wish the documentation was as good for the sa 3250hd as the Moto 6200

---

### Post by newlinux on 2007-10-11
> **dannyboy79 said:**
> 
newlinux=I thought I read that he has a sa 3250hd stb. I wish the documentation was as good for the sa 3250hd as the Moto 6200

First post says DCT-6200... I only skimmed the thread, so maybe that was corrected.

And you are right about "damn cable companies." I used to get all my stations (including HD premium stations) DTCP clear. Gets less and less all the time. But it is still useful for ESPN/ESPN2 HD, TNT HD, and other stations I don't get via QAM or analog.

---

### Post by dmfrey on 2007-10-11
I was able to stop home at lunch and verify that test-mpeg2 can successfully record channel 181.  The channel was in the clear.

The firewire config in mythtv-seup was setup correctly, however, I have resorted remoting in and manually updating the firewire_port on the capturecard table from 2 to 1 when it decides to change ports.  I disabled the cron job the other night when I found out it didn't resolve this issue.

It is configured to use broadcast, not p2p.  P2P is less stable than broadcast on my box.

---

### Post by dannyboy79 on 2007-10-11
if it's broadcast, then you have to use some kind of primer I think. I don't use broadcast, I can't help much more. good luck

---

### Post by dmfrey on 2007-10-11
I don't use a primer.  It usually seems to work just fine without it (except for recently).

I did, however, make the script changes to mythtv-backend to allow the mythtv user to take ownership of the firewire port for the duration of the mythtv-backend session.

---

### Post by newlinux on 2007-10-11
I just run firewire_tester with the -B option to stabilize the broadcast connection that I use. I have a cron job that runs that once a day and that's it. The community documentation here has a more sophisticated way of doing it, half of which (taking ownership) you have already implemented. If I had problems with recordings, I'd probably implement this the whole way through:


[https://help.ubuntu.com/community/MythTV_Firewire#head-9fe3de73cf5d2687360be13ec3941b1b39fa43d7](https://help.ubuntu.com/community/MythTV_Firewire#head-9fe3de73cf5d2687360be13ec3941b1b39fa43d7)

---

### Post by dmfrey on 2007-10-14
I was able to get a stable P2P connection the other night.  I am going to let that run for a few days to see if it performs any better than the broadcast connection.  Also, I bought a new firewire cable, just in case my problem could be related to the physical connection between the two.

---

### Post by dmfrey on 2007-10-19
I believe this issue was related to the firewire cable itself.  I replaced the cable and have not had an issue with it in a week.  The Firewire port has not switched one time and every recording has been recorded successfully on both tuners.

---

