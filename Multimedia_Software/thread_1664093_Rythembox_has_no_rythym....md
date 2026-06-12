---
title: "Rythembox has no rythym..."
date: 2011-01-10
forum: Multimedia Software
---

### Post by MAFoElffen on 2011-01-10
I've been using Ubunti since 9.04 through 10.10... Through every Aplha and Beta release..  Through all this, Rhythembox has given me consistant, successful use... until now.

Thsi only thing I can figure out as a posible change or cause is upgrades and updates.  I figured, maybe I should reinstall it // made no change.  I completely uninstalled and then installed//no change.

The origianl problem was that all of a sudeen, I couldn't start up Rythembox at all.  It would start to load, then just falt crash. (With no residual process left/completely gone). 

Someone on the forums said to try disabling the Ubuntu one connection, that there was an ongoing problem with that piece-- it started and I was happy unitl... There is no FM-Raio, It just crashes if you try.  If you insert an audio CD and try to play-- again crashes.

What is going on?  Is "this" a problem that others are having?  Os it just my PC?  How do I get things working right and they should be and were in the past (functionally)?

---

### Post by MAFoElffen on 2011-01-10
Update-- Since last night, there were only 2 updates on xorg changes.  After playing a CD last night that I created from a playlist in Rythembox --> Brasero... then unsuccessfully being able to play in Rythembox (just would crash)... so I play it in Movieplayer...

Now I'm back to my original Problem = Rythembox starts to load then just crashes hard and goes away.  This is getting real frustrating!

Edit- Not exactly the origianl problem--> When I put an audio CD in my CD/DVD drive, Rthyembox crashes.  This is just getting wierd!

So what did I do... I added to the problem of course. I upgraded to Gnom's Rythythembox v0.12.2... then same problems plus, lost some of the connection/tie in's with Ubuntu's Sound applet.  Where the applet is, it had the Rhythembox as a menu item, but lost the abilty to start it from there... and when a song was playing, it showed it, but lost the pause/play, forward, back button in that applet...

So then I went to help in Rythembox, which had a "report Problem" item... which then said that this version was not an Ubuntu version.  Not wanting to lose my settings, I forced a downgrade to the Ubuntu with upgrades version... More troubles.  All the connections to the applet still showed as last song played with the l"ast version" of rythembox.(no the current installed version).  When I closed the player. it continued to play the songs and go through the playlist, with the player gone from the desktop.  I had to restart the OS to get it to stop.

I think it's time to get rid of the new app that I had to spec for v0.13.2, uninstall again.. then reinstall fresh again.  Hpoing to get back to somewhere half-ways usable!!!!!

---

### Post by MAFoElffen on 2011-01-10
Okay- Did complete removal.  Doing fresh install (again). Lets see where this gets me. 

Got me where it was at least updated in the top bar applet and I could try to start it with it crashing again... Now going to remove the Ubuntu One Music Store Pluggin.

That got me back to being able to start Rhythembox and having it all connected to the Gnome sound applet with all it's controls. When I shut down the player, it sops and unloads correctly--

Now just the crashing problems when an Audio CD is inserted, when you try to go to an interner radio (such as Last-fm) and  no Ubuntu One Music Store (which is a known problem?)

---

### Post by BicyclerBoy on 2011-01-10
Try running rhythmbox from a terminal...

rhythmbox -d

This should stdout lots of error messages.

---

### Post by MAFoElffen on 2011-01-11
> **BicyclerBoy said:**
> Try running rhythmbox from a terminal...

rhythmbox -d

This should stdout lots of error messages.
Is there any way of directing the stdout of error messages to a file?  Terminal only seems to keep about 150 lines of it in it's buffer, so most of it is not there to review...

---

### Post by dewdrop_world on 2011-01-11
> **MAFoElffen said:**
> Is there any way of directing the stdout of error messages to a file?  Terminal only seems to keep about 150 lines of it in it's buffer, so most of it is not there to review...

```
rhythmbox -d >~/my_rbox_errors.log
```

is the usual way.

---

### Post by MAFoElffen on 2011-01-12
This was what was directed to the error log:
```
(rhythmbox:5753): Rhythmbox-DEBUG: Received SaveYourself(SmSaveLocal, !Shutdown, SmInteractStyleNone, !Fast) in state idle
(rhythmbox:5753): Rhythmbox-DEBUG: Setting initial properties
(rhythmbox:5753): Rhythmbox-DEBUG: Sending SaveYourselfDone(True) for initial SaveYourself
(rhythmbox:5753): Rhythmbox-DEBUG: Received SaveComplete message in state save-yourself-done
(rhythmbox:5753): Rhythmbox-DEBUG: ayatana-plugin.vala:17: Rhythmbox - Goodbye Ayatana world

found device path /dev/sdc2 for mount /media/DATA
device /dev/sdc2 has no ID_MEDIA_PLAYER tag in udev
/media/DATA is already a mount point
override file /media/DATA/.is_audio_player not found on mount /media/DATA
```

What was actually sent to the screen was much different... and could not include in this same post so -->

---

### Post by MAFoElffen on 2011-01-12
(Part 1)
This was what was left on the screen:
[HTML]21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Sarah%20Brightman/04%20Sarah%20Brightman%20-%20Anytime,%20Anywhere.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Sarah Brightman/04 Sarah Brightman - Anytime, Anywhere.mp3:  Error stating file '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Sarah Brightman/04 Sarah Brightman - Anytime, Anywhere.mp3':  No such file or directory
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Def%20Leppard/love%20bites.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Mandy%20Moore/03%20-%20MANDY%20MOORE-%20CRY.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Mandy Moore/03 - MANDY MOORE- CRY.mp3: Error stating file  '/media/DATA/Notebook_Backup/D_Data/Downloaded Music/DL_M/Mandy Moore/03  - MANDY MOORE- CRY.mp3': No such file or directory
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/The%20Lonley%20Island/****%20in%20a%20box.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Jet/Are%20You%20Gonna%20Be%20My%20Girl.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Traveling%20Wilburys/Last%20Night.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/The%20Strokes.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/My%20chemical%20Romance/Teenagers.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Bruce%20Springsteen/Born%20in%20the%20usa.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Katy%20Perry/One%20of%20the%20Boys/Takes%20One%20to%20Know%20One.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Three%20Days%20Grace/Pain.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Apocalypica/I%20Dont%20Care.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Disturbed/Disturbed_/Disturbed_-_Decadence.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/coheed%20and%20cambria/welcome%20home.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/coheed and cambria/welcome home.mp3: Error stating file  '/media/DATA/Notebook_Backup/D_Data/Downloaded Music/coheed and  cambria/welcome home.mp3': No such file or directory
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/aerosmith/jaded.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/aerosmith/Pink.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/red%20hot%20chili%20peppers/all%20around%20the%20world.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Evanescence/Call%20Me%20When%20You're%20Sober%20-%20Evanescence.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Foo%20Fighters/Best%20Of%20You.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Yngwie%20Malmstein/Yngwie%20Malmstein%20-%20Overture%201622.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Evanescence/Evanescence%20-%20Lies.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/pearl%20jam/jeremy.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/heart/barracuda.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Disturbed_/Disturbed-The_Game.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Disturbed_/Disturbed-The_Game.mp3: Error stating file  '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Disturbed_/Disturbed-The_Game.mp3': No such file or directory
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Disturbed_/Disturbed%20-%20Never%20Again.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Disturbed_/Disturbed - Never Again.mp3: Error stating file  '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Disturbed_/Disturbed - Never Again.mp3': No such file or  directory
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/The%20Who/Who%20are%20you.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Coheed%20and%20Cambria/welcome%20home.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Three%20Days%20Grace/Three%20Days%20Grace%20-%2003%20-%20World%20So%20Cold.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Three Days Grace/Three Days Grace - 03 - World So Cold.mp3:  Error stating file '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Three Days Grace/Three Days Grace - 03 - World So Cold.mp3':  No such file or directory
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Coheed%20And%20Cambria/Coheed%20And%20Cambria%20-%20Always%20&%20Never.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Coheed And Cambria/Coheed And Cambria - Always &  Never.mp3: Error stating file  '/media/DATA/Notebook_Backup/D_Data/Downloaded Music/DL_M/Coheed And  Cambria/Coheed And Cambria - Always & Never.mp3': No such file or  directory
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Traveling%20Wilburys/Heading%20for%20the%20Light.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Three%20Days%20Grace/Three%20Days%20Grace%20-%20Time%20Of%20Dying.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/three%20days%20grace/Three%20Days%20Grace%20-%2002%20-%20Break.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/three days grace/Three Days Grace - 02 - Break.mp3: Error stating  file '/media/DATA/Notebook_Backup/D_Data/Downloaded Music/three days  grace/Three Days Grace - 02 - Break.mp3': No such file or directory
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Norman%20GreenBaum/Spirit%20in%20the%20Sky.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/The%20Who/My%20Generation.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/iron%20maiden/Run%20To%20The%20Hills.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Sean%20Kingston/Beautiful%20Girls.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Sweet/Ballroom%20Blitz.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/aerosmith/Rag%20Doll.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Temple%20of%20the%20Dog/Hunger%20Strike.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing file:///(null)/3%20days%20grace.mp3: Couldn't access  file:///(null)/3 days grace.mp3: Error stating file '/(null)/3 days  grace.mp3': No such file or directory
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/papa%20roach/last%20resort.mp3
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Rage%20Against%20The%20Machine/Killing%20In%20The%20Name%20Of.mp3
[/HTML]

---

### Post by MAFoElffen on 2011-01-12
(Part 2)
[HTML]
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Three%20Days%20Grace/Three%20Days%20Grace%20-%20Time%20Of%20Dying.mp3:   Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Three Days Grace/Three Days Grace - Time Of Dying.mp3: Error  stating file '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Three Days Grace/Three Days Grace - Time Of Dying.mp3': No  such file or directory
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Kiss/detroit%20rock%20city.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Brain%20Adams/Summer%20Of%2069.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Rage%20Against%20The%20Machine/Testify.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Akon/Lonely.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/system%20of%20a%20down/Aerials.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/audioslave/Be%20Yourself.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Motorhead/Ace%20of%20Spades.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Evanescence/Evanescence%20WHISPER%20.MP3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/3OH!3/dont%20trust%20me.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Evanescence/Evanescence%20-%20You.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Disturbed/Disturbed_/Disturbed%20-%20Believe.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Metallica/Enter%20Sandman.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/linkin%20park/Linkin_Park_vs_Evanescence_-_Crawling_vs_Missing.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/linkin park/Linkin_Park_vs_Evanescence_-_Crawling_vs_Missing.mp3:  Error stating file '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/linkin park/Linkin_Park_vs_Evanescence_-_Crawling_vs_Missing.mp3':  No such file or directory
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Sarah%20Brightman/04%20Sarah%20Brightman%20-%20Anytime,%20Anywhere.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Linkin%20Park/Linkin_Park_-_Numb.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Katy%20Perry/One%20of%20the%20Boys/Diamonds.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Linkin%20Park/Linkin_Park_-_In_The_End.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Evanescence/Evanescence%20-%20October.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Disturbed_/03-disturbed-awaken-pr.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Disturbed_/03-disturbed-awaken-pr.mp3: Error stating file  '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Disturbed_/03-disturbed-awaken-pr.mp3': No such file or  directory
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Yngwie%20Malmstein/04.%20yngwie%20-%20seventh%20sign%20-%20forever%20one.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/The%20Bravery/Above%20and%20Below.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Three%20Days%20Grace/3%20days%20grace.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/The%20Lonley%20Island/Gary%20Jules/DeVotchKa/How%20it%20ends.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Sarah%20McLacchlan/Sarah%20McLachlan%20-%20Possession.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Kayne%20West/Heartless.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/All%20Along%20The%20Watchtower.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/genitourers/I%20Touch%20Myself.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Rolling%20stones/paint%20it%20black.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Alice%20in%20Chains/man%20in%20the%20box.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/OK%20go/Here%20It%20Goes%20Again.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/The%20Lonley%20Island/Im%20On%20A%20Boat.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Disturbed_/Disturbed_-_Decadence.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Disturbed_/Disturbed_-_Decadence.mp3: Error stating file  '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Disturbed_/Disturbed_-_Decadence.mp3': No such file or  directory
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Evanescence/Evanescence%20-%20Anything%20For%20You.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/pearl%20jam/evenflow.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Nine%20inch%20Nails/Little%20Sister.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Boston/Long%20Time.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Linkin%20Park/Linkin_Park_vs_Evanescence_-_Crawling_vs_Missing.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/oasis/live%20forever.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Janis%20Joplin/Take%20another%20Little%20Piece%20of%20my%20heart.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Three%20Days%20Grace/Three%20Days%20Grace%20-%2002%20-%20Break.mp3:   Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Three Days Grace/Three Days Grace - 02 - Break.mp3: Error  stating file '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Three Days Grace/Three Days Grace - 02 - Break.mp3': No such  file or directory
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Easton/Tractors%20sexy.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Adam%20Sandler/secret.mp3
 (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
 (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Alice%20in%20Chains/them%20bones.mp3
 [/HTML]

---

### Post by MAFoElffen on 2011-01-12
(Part 3)
[HTML]
(21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/other/Cascada/Rocky%20Balbia/Queen/Prince/Rage%20against%20the%20machine/Nickelback/RockStar.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Run-D.M.C/Walk%20This%20Way.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Bon%20Jovi/Ugly.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/red%20hot%20chili%20peppers/snow%20(Hey%20Oh).mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/STYX/Come%20Sail%20Away.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/coheed%20and%20cambria/Coheed%20And%20Cambria%20-%20Always%20&%20Never.mp3:    Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/coheed and cambria/Coheed And Cambria - Always & Never.mp3:  Error stating file '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/coheed and cambria/Coheed And Cambria - Always & Never.mp3':  No such file or directory
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Alison_Kraus/alison%20krauss%20-%20allison%20kraus%20-%20you%20say%20it%20best%20when%20you%20say%20nothing%20at%20all.mp3:    Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Alison_Kraus/alison krauss - allison kraus - you say it best  when you say nothing at all.mp3: Error stating file  '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Alison_Kraus/alison krauss - allison kraus - you say it best  when you say nothing at all.mp3': No such file or directory
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Def%20Leppard/rock%20of%20ages.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Journey/small%20town%20girl.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Disturbed/Disturbed_/07%20Disturbed%20-%20Hell.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Three%20Days%20Grace/On%20my%20own%20three%20days%20grace.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Disturbed/Disturbed_/Disturbed-The_Game.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/linkin%20park/Linkin_Park_-_Numb.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/linkin park/Linkin_Park_-_Numb.mp3: Error stating file  '/media/DATA/Notebook_Backup/D_Data/Downloaded Music/linkin  park/Linkin_Park_-_Numb.mp3': No such file or directory
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Katy%20Perry/One%20of%20the%20Boys/Hook%20Up.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/ZZ%20Top/Sharp%20Dressed%20Man.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Kid%20Cudi/Day%20&%20Night.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Rush/Tom%20Sawyer.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Ozzy%20Osbourne/I%20Just%20Want%20You.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Yngwie%20Malmstein/Yngwie%20Malmstein%20-%20Overture%201622.mp3:    Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Yngwie Malmstein/Yngwie Malmstein - Overture 1622.mp3: Error  stating file '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Yngwie Malmstein/Yngwie Malmstein - Overture 1622.mp3': No  such file or directory
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Evanescence/Evanescence%20-%20My%20Last%20Breath.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Disturbed_/Disturbed%20-%20Voices%20.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Disturbed_/Disturbed - Voices .mp3: Error stating file  '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Disturbed_/Disturbed - Voices .mp3': No such file or  directory
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Unknown%20Artist/make%20it%20rain.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Black%20Eyed%20Peas/Boom%20boom%20pow.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Nirvana/Plateau.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/three%20days%20grace/Three%20Days%20Grace%20-%20Time%20Of%20Dying.mp3:    Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/three days grace/Three Days Grace - Time Of Dying.mp3: Error  stating file '/media/DATA/Notebook_Backup/D_Data/Downloaded Music/three  days grace/Three Days Grace - Time Of Dying.mp3': No such file or  directory
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Yngwie%20Malmstein/Yngwie%20Malmsteen%20-%20Fire%20And%20Ice.mp3:    Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Yngwie Malmstein/Yngwie Malmsteen - Fire And Ice.mp3: Error  stating file '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Yngwie Malmstein/Yngwie Malmsteen - Fire And Ice.mp3': No  such file or directory
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Evanescence/Evanescence%20-%20Weight%20of%20the%20World.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/aerosmith/Dream_On.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/aerosmith/Crazy.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Bruce%20Springsteen/born%20to%20run.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Sixx%20A.M/Life%20Is%20Beautiful.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Traveling%20Wilburys/Wilbury%20Twist.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Bon%20Jovi/nsg.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Saving%20Abel/07-saving_abel-addicted_3_.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/stone%20temple%20pilots/Big%20Empty.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Coheed%20and%20Cambria/Coheed%20And%20Cambria%20-%20Always%20&%20Never.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Traveling%20Wilburys/Handle%20Me%20With%20Care.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/CCR/Have%20you%20ever%20seen%20the%20rain.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/The%20Who/Wont%20Get%20Fooled%20Again.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Van%20Halen/Jump.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/three%20days%20grace/Three%20Days%20Grace%20-%2003%20-%20World%20So%20Cold.mp3:    Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/three days grace/Three Days Grace - 03 - World So Cold.mp3: Error  stating file '/media/DATA/Notebook_Backup/D_Data/Downloaded Music/three  days grace/Three Days Grace - 03 - World So Cold.mp3': No such file or  directory
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Tenacious%20d/The%20metal.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/red%20hot%20chili%20peppers/scar%20tissue.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Eric%20Clapton/Tears%20In%20Heaven.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Foo%20Fighters/Let%20It%20Die.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Dead%20Kennedys/Holiday%20in%20Cambodia.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Whitesnake/Still%20Of%20The%20Night.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/red%20hot%20chili%20peppers/higher%20ground.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/three%20days%20grace/Pain.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/three days grace/Pain.mp3: Error stating file  '/media/DATA/Notebook_Backup/D_Data/Downloaded Music/three days  grace/Pain.mp3': No such file or directory
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Evanescence/Evanescence%20-%20Broken.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Cheap%20Trick/Surrender.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Three%20Days%20Grace/Three%20Days%20Grace%20-%2003%20-%20World%20So%20Cold.mp3
  (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
  [/HTML]

---

### Post by MAFoElffen on 2011-01-12
(Part 4)
[HTML]
(21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Mandy%20Moore/03%20-%20MANDY%20MOORE-%20CRY.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Foo%20Fighters/Monkey%20Wrench.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/The%20Who/The%20Seeker.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/the%20Police/Roxanne.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Linkin_Park/Linkin_Park_-_Numb.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Linkin_Park/Linkin_Park_-_Numb.mp3: Error stating file  '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Linkin_Park/Linkin_Park_-_Numb.mp3': No such file or  directory
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Katy%20Perry/One%20of%20the%20Boys/03%20Wish%20you%20the%20worst.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Disturbed/Disturbed_/Disturbed%20-%20Never%20Again.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/red%20hot%20chili%20peppers/Californication.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Easton/buy%20you%20a%20drink.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Easton/Good%20Life.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Evanescence/Evanescence%20-%20Anything%20For%20You(2).mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/audioslave/Like%20a%20Stone.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Alice%20in%20Chains/Rooster.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Assorted/Puddle%20Of%20Mud%20-%20Blurry.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/3OH!3/starstrukk.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/other/Cascada/Rocky%20Balbia/Queen/Prince/Erotic%20city.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Linkin_Park/Linkin_Park_vs_Evanescence_-_Crawling_vs_Missing.mp3:     Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Linkin_Park/Linkin_Park_vs_Evanescence_-_Crawling_vs_Missing.mp3:     Error stating file '/media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Linkin_Park/Linkin_Park_vs_Evanescence_-_Crawling_vs_Missing.mp3':     No such file or directory
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Yngwie%20Malmstein/dedomito%20-%20trilogy%20yngwie.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/aerosmith/Bohemian%20Rhapsody.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2112:  error accessing  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/DL_M/Yngwie%20Malmstein/dedomito%20-%20trilogy%20yngwie.mp3:  Couldn't access file:///media/DATA/Notebook_Backup/D_Data/Downloaded  Music/DL_M/Yngwie Malmstein/dedomito - trilogy yngwie.mp3: Error stating  file '/media/DATA/Notebook_Backup/D_Data/Downloaded Music/DL_M/Yngwie  Malmstein/dedomito - trilogy yngwie.mp3': No such file or directory
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Billy%20Squier/The%20Stroke.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Alice%20cooper/Schools%20Out.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/red%20hot%20chili%20peppers/Dani%20California.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/foriegner/Jukebox%20Hero.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Eminem/we%20made%20you.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Rehab/Sittin%20At%20A%20Bar.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Beastie%20Boys/fight%20for%20your%20right.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2505: processing RHYTHMDB_EVENT_STAT
   (21:00:13) [0x20fff60] [rhythmdb_process_stat_event] rhythmdb.c:2146:  not modified:  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music/Boston/more%20than%20a%20feeling.mp3
   (21:00:13) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2531: processing RHYTHMDB_EVENT_THREAD_EXITED
   (21:00:13) [0x20fff60] [rb_statusbar_sync_status] rb-statusbar.c:472:  updating status with: '534 songs, 2 days, 16 hours and 16 minutes, 2.3  GB', '', 999.000000
   (21:00:15) [0x20fff60] [actually_hide_controls] rb-visualizer-plugin.c:801: hiding controls
   (21:00:15) [0x20fff60] [paned_size_allocate_cb] rb-shell.c:2949: paned position 160
   (21:00:15) [0x20fff60] [paned_size_allocate_cb] rb-shell.c:2950: right_paned position 400
   (21:00:20) [0x20fff60] [rhythmdb_sync_library_location] rhythmdb.c:4697: starting library monitoring
   (21:00:20) [0x20fff60] [monitor_library_directory]  rhythmdb-monitor.c:207: beginning monitor of the library directory  file:///media/DATA/Notebook_Backup/D_Data/Downloaded%20Music
   (21:00:20) [0x20fff60] [monitor_library_directory]  rhythmdb-monitor.c:207: beginning monitor of the library directory  file:///home/mafoelffen/.local/share/ubuntuone/Purchased%20from%20Ubuntu%20One
   (21:00:20) [0x7f1344154b80] [_uri_handle_recurse] rb-file-helpers.c:768:  error enumerating  file:///home/mafoelffen/.local/share/ubuntuone/Purchased%20from%20Ubuntu%20One:  No such file or directory
   (21:00:25) [0x20fff60] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:743: No username set
   ^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B(21:00:40) [0x20fff60]  [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:743: No  username set
   (21:00:55) [0x20fff60] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:743: No username set
   (21:01:10) [0x20fff60] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:743: No username set
   (21:01:12) [0x20fff60] [rhythmdb_read_enter] rhythmdb.c:1239: counter: 1
   (21:01:12) [0x7f1344196200] [query_thread_main] rhythmdb.c:4020: entering query thread
   (21:01:12) [0x7f1344196200] [rhythmdb_query_internal] rhythmdb.c:3997: doing query
   (21:01:12) [0x7f1344196200] [do_query_recurse] rhythmdb-tree.c:2301: doing recursive query, 1 conjunctions
   (21:01:12) [0x20fff60] [rhythmdb_read_enter] rhythmdb.c:1239: counter: 2
   (21:01:12) [0x7f13441551c0] [query_thread_main] rhythmdb.c:4020: entering query thread
   (21:01:12) [0x7f13441551c0] [rhythmdb_query_internal] rhythmdb.c:3997: doing query
   (21:01:12) [0x7f13441551c0] [do_query_recurse] rhythmdb-tree.c:2301: doing recursive query, 1 conjunctions
   (21:01:12) [0x7f1344196200] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2248: adding 201 entries
   (21:01:12) [0x20fff60] [idle_process_update] rhythmdb-query-model.c:1187: inserting 201 rows
   (21:01:12) [0x7f1344196200] [rhythmdb_query_internal] rhythmdb.c:4003: completed
   (21:01:12) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2538: processing RHYTHMDB_EVENT_QUERY_COMPLETE
   (21:01:12) [0x20fff60] [rhythmdb_read_leave] rhythmdb.c:1253: counter: 1
   (21:01:12) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2531: processing RHYTHMDB_EVENT_THREAD_EXITED
   (21:01:12) [0x7f13441551c0] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2248: adding 66 entries
   (21:01:12) [0x7f13441551c0] [rhythmdb_query_internal] rhythmdb.c:4003: completed
   (21:01:12) [0x20fff60] [idle_process_update] rhythmdb-query-model.c:1187: inserting 66 rows
   (21:01:12) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2538: processing RHYTHMDB_EVENT_QUERY_COMPLETE
   (21:01:12) [0x20fff60] [rhythmdb_read_leave] rhythmdb.c:1253: counter: 0
   (21:01:12) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2531: processing RHYTHMDB_EVENT_THREAD_EXITED
  (21:01:25) [0x20fff60] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:743: No username set
    (21:01:40) [0x20fff60] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:743: No username set
    (21:01:55) [0x20fff60] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:743: No username set
    ^[[B(21:02:10) [0x20fff60] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:743: No username set
    ^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B(21:02:12) [0x20fff60] [rhythmdb_read_enter] rhythmdb.c:1239: counter: 1
    (21:02:12) [0x7f1344196200] [query_thread_main] rhythmdb.c:4020: entering query thread
    (21:02:12) [0x7f1344196200] [rhythmdb_query_internal] rhythmdb.c:3997: doing query
    (21:02:12) [0x7f1344196200] [do_query_recurse] rhythmdb-tree.c:2301: doing recursive query, 1 conjunctions
    (21:02:12) [0x20fff60] [rhythmdb_read_enter] rhythmdb.c:1239: counter: 2
    (21:02:12) [0x2c15000] [query_thread_main] rhythmdb.c:4020: entering query thread
    (21:02:12) [0x2c15000] [rhythmdb_query_internal] rhythmdb.c:3997: doing query
    (21:02:12) [0x2c15000] [do_query_recurse] rhythmdb-tree.c:2301: doing recursive query, 1 conjunctions
    (21:02:12) [0x7f1344196200] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2248: adding 201 entries
    (21:02:12) [0x20fff60] [idle_process_update] rhythmdb-query-model.c:1187: inserting 201 rows
    (21:02:12) [0x7f1344196200] [rhythmdb_query_internal] rhythmdb.c:4003: completed
    (21:02:12) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2538: processing RHYTHMDB_EVENT_QUERY_COMPLETE
    (21:02:12) [0x20fff60] [rhythmdb_read_leave] rhythmdb.c:1253: counter: 1
    (21:02:12) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2531: processing RHYTHMDB_EVENT_THREAD_EXITED
    (21:02:12) [0x2c15000] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2248: adding 66 entries
    (21:02:12) [0x2c15000] [rhythmdb_query_internal] rhythmdb.c:4003: completed
    (21:02:12) [0x20fff60] [idle_process_update] rhythmdb-query-model.c:1187: inserting 66 rows
    (21:02:12) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2538: processing RHYTHMDB_EVENT_QUERY_COMPLETE
    (21:02:12) [0x20fff60] [rhythmdb_read_leave] rhythmdb.c:1253: counter: 0
    (21:02:12) [0x20fff60] [rhythmdb_process_one_event] rhythmdb.c:2531: processing RHYTHMDB_EVENT_THREAD_EXITED
    (21:02:25) [0x20fff60] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:743: No username set
    (21:02:40) [0x20fff60] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:743: No username set
    (21:02:48) [0x20fff60] [window_focus_cb] rb-mmkeys-plugin.c:153: window got focus, re-grabbing media keys
    (21:02:52) [0x20fff60] [rb_shell_quit] rb-shell.c:2644: Quitting
    (21:02:52) [0x20fff60] [rb_shell_player_stop] rb-shell-player.c:3174: stopping
    (21:02:52) [0x20fff60] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3110: setting playing source to (nil)
    (21:02:52) [0x20fff60] [prev_action_sensitive_cb] rb-mpris-plugin.c:988: emitting CanGoPrevious change
    (21:02:52) [0x20fff60] [next_action_sensitive_cb] rb-mpris-plugin.c:979: emitting CanGoNext change
    (21:02:52) [0x20fff60] [rb_shell_player_sync_with_source] rb-shell-player.c:2934: playing source: (nil), active entry: (nil)
    (21:02:52) [0x20fff60] [rb_shell_set_window_title] rb-shell.c:2253: clearing title
    (21:02:52) [0x20fff60] [show_controls] rb-visualizer-plugin.c:852: showing controls
    (21:02:52) [0x20fff60] [rb_shell_player_get_playing_song_duration]  rb-shell-player.c:3382: Did not get playing entry : return -1 as length
    (21:02:52) [0x20fff60] [rb_shell_player_sync_buttons] rb-shell-player.c:3029: syncing with source 0x2318200
    (21:02:52) [0x20fff60] [rb_shell_playing_source_changed_cb] rb-shell.c:2130: playing source changed
    (21:02:52) [0x20fff60] [playing_source_changed_cb] rb-mpris-plugin.c:971: emitting CanPause change
    (21:02:52) [0x20fff60] [rb_shell_player_sync_with_source] rb-shell-player.c:2934: playing source: (nil), active entry: (nil)
    (21:02:52) [0x20fff60] [rb_shell_set_window_title] rb-shell.c:2253: clearing title
    (21:02:52) [0x20fff60] [show_controls] rb-visualizer-plugin.c:852: showing controls
    (21:02:52) [0x20fff60] [rb_shell_player_get_playing_song_duration]  rb-shell-player.c:3382: Did not get playing entry : return -1 as length
    (21:02:52) [0x20fff60] [rb_audioscrobbler_song_changed_cb] rb-audioscrobbler.c:1146: called with no playing entry
    (21:02:52) [0x20fff60] [playing_entry_changed_cb] rb-mpris-plugin.c:908: emitting Metadata and CanSeek changed
    (21:02:52) [0x20fff60] [rb_shell_player_get_playing_song_duration]  rb-shell-player.c:3382: Did not get playing entry : return -1 as length
    (21:02:52) [0x20fff60] [playing_changed_cb] rb-mpris-plugin.c:888: emitting PlaybackStatus change
    (21:02:52) [0x20fff60] [show_controls] rb-visualizer-plugin.c:852: showing controls
    (21:02:52) [0x20fff60] [rb_shell_player_sync_buttons] rb-shell-player.c:3029: syncing with source 0x2318200
    (21:02:52) [0x20fff60] [rb_shell_source_deleted_cb] rb-shell.c:2095: source deleted
    (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x338c020: 'Last.fm'
    (21:02:52) [0x20fff60] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x337e3e0
    (21:02:52) [0x20fff60] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x337e3e0
    (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x338c020: 'Last.fm'
    (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x337e4a0 count: 1
    (21:02:52) [0x20fff60] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x337e4a0
    (21:02:52) [0x20fff60] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x337e4a0
    (21:02:52) [0x20fff60] [rb_audioscrobbler_dispose] rb-audioscrobbler.c:302: disposing audioscrobbler
    (21:02:52) [0x20fff60] [rb_audioscrobbler_finalize] rb-audioscrobbler.c:349: Finalizing Audioscrobbler
    (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Last.fm
    (21:02:52) [0x20fff60] [rb_audioscrobbler_plugin_finalize] rb-audioscrobbler-plugin.c:108: RBAudioscrobblerPlugin finalising
    (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Media Player Keys
    (21:02:52) [0x20fff60] [impl_deactivate] rb-disc-recorder-plugin.c:754: RBDiscRecorderPlugin deactivating
    (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Audio CD Recorder
    (21:02:52) [0x20fff60] [rb_disc_recorder_plugin_finalize] rb-disc-recorder-plugin.c:150: RBDiscRecorderPlugin finalized
    [/HTML]

---

### Post by MAFoElffen on 2011-01-12
(Part 5)
[HTML]
(21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Portable Players - iPod
     (21:02:52) [0x20fff60] [rb_ipod_plugin_finalize] rb-ipod-plugin.c:148: RBIpodPlugin finalising
     (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin MPRIS D-Bus interface
     (21:02:52) [0x20fff60] [rb_shell_source_deleted_cb] rb-shell.c:2095: source deleted
     (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Magnatune Store
     (21:02:52) [0x20fff60] [rb_python_object_finalize] rb-python-plugin.c:220: Finalizing python plugin instance
     (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Portable Players - MTP
     (21:02:52) [0x20fff60] [rb_mtp_plugin_finalize] rb-mtp-plugin.c:159: RBMtpPlugin finalising
     (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Status Icon
     (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Cover art
     (21:02:52) [0x20fff60] [rb_python_object_finalize] rb-python-plugin.c:220: Finalizing python plugin instance
     (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Ayatana
     (21:02:52) [0x20fff60] [rb_shell_source_deleted_cb] rb-shell.c:2095: source deleted
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x25491c0: 'Radio'
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x3373a70
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x3373a70
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x25491c0: 'Radio'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x3095610 count: 1
     (21:02:52) [0x20fff60] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x3095610
     (21:02:52) [0x20fff60] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x3095610
     (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Internet Radio
     (21:02:52) [0x20fff60] [rb_iradio_plugin_finalize] rb-iradio-plugin.c:90: RBIRadioPlugin finalising
     (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Audio CD Player
     (21:02:52) [0x20fff60] [rb_audiocd_plugin_finalize] rb-audiocd-plugin.c:115: RBAudioCdPlugin finalising
     (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Power Manager
     (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Portable Players
     (21:02:52) [0x20fff60] [rb_generic_player_plugin_finalize] rb-generic-player-plugin.c:135: RBGenericPlayerPlugin finalising
     (21:02:52) [0x20fff60] [rb_shell_source_deleted_cb] rb-shell.c:2095: source deleted
     (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Jamendo
     (21:02:52) [0x20fff60] [rb_python_object_finalize] rb-python-plugin.c:220: Finalizing python plugin instance
     (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin Visualization
     (21:02:52) [0x20fff60] [rb_visualizer_plugin_dispose] rb-visualizer-plugin.c:273: RBVisualizerPlugin disposing
     (21:02:52) [0x20fff60] [rb_visualizer_plugin_finalize] rb-visualizer-plugin.c:330: RBVisualizerPlugin finalising
     (21:02:52) [0x20fff60] [rb_plugin_info_free] rb-plugins-engine.c:399: Unref plugin IM Status
     (21:02:52) [0x20fff60] [rb_python_object_finalize] rb-python-plugin.c:220: Finalizing python plugin instance
     (21:02:52) [0x20fff60] [rb_podcast_source_shutdown] rb-podcast-source.c:1796: podcast source shutdown
     (21:02:52) [0x20fff60] [rb_shell_sync_state] rb-shell.c:1042: saving playlists
     (21:02:52) [0x20fff60] [rb_shell_sync_state] rb-shell.c:1046: saving db
     (21:02:52) [0x20fff60] [rhythmdb_save] rhythmdb.c:3186: saving the rhythmdb and blocking
     (21:02:52) [0x20fff60] [rhythmdb_save_async] rhythmdb.c:3168: saving the rhythmdb in the background
     (21:02:52) [0x20fff60] [rhythmdb_read_enter] rhythmdb.c:1239: counter: 1
     (21:02:52) [0x33785b0] [rhythmdb_save_thread_main] rhythmdb.c:3116: entering save thread
     (21:02:52) [0x33785b0] [rhythmdb_save_thread_main] rhythmdb.c:3134: saving rhythmdb
     (21:02:52) [0x33785b0] [save_entry_type] rhythmdb-tree.c:1184: saving entries of type ignore
     (21:02:52) [0x33785b0] [save_entry_type] rhythmdb-tree.c:1184: saving entries of type song
     (21:02:52) [0x33785b0] [save_entry_type] rhythmdb-tree.c:1184: saving entries of type podcast-feed
     (21:02:52) [0x33785b0] [save_entry_type] rhythmdb-tree.c:1184: saving entries of type iradio
     (21:02:52) [0x33785b0] [save_entry_type] rhythmdb-tree.c:1184: saving entries of type lastfm-station
     (21:02:52) [0x33785b0] [save_entry_type] rhythmdb-tree.c:1184: saving entries of type podcast-post
     (21:02:52) [0x20fff60] [rhythmdb_save] rhythmdb.c:3203: done
     (21:02:52) [0x20fff60] [main_shell_weak_ref_cb] main.c:418: caught shell finalization
     (21:02:52) [0x20fff60] [rb_shell_finalize] rb-shell.c:1092: Finalizing shell
     (21:02:52) [0x20fff60] [rb_shell_player_stop] rb-shell-player.c:3174: stopping
     (21:02:52) [0x20fff60] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3110: setting playing source to (nil)
     (21:02:52) [0x20fff60] [rb_shell_player_sync_with_source] rb-shell-player.c:2934: playing source: (nil), active entry: (nil)
     (21:02:52) [0x20fff60] [rb_shell_player_sync_buttons] rb-shell-player.c:3029: syncing with source 0x2318200
     (21:02:52) [0x20fff60] [rb_shell_player_sync_with_source] rb-shell-player.c:2934: playing source: (nil), active entry: (nil)
     (21:02:52) [0x20fff60] [rb_shell_player_sync_buttons] rb-shell-player.c:3029: syncing with source 0x2318200
     (21:02:52) [0x20fff60] [rb_shell_finalize] rb-shell.c:1118: shutting down playlist manager
     (21:02:52) [0x20fff60] [rb_shell_finalize] rb-shell.c:1121: unreffing playlist manager
     (21:02:52) [0x20fff60] [rb_playlist_manager_dispose] rb-playlist-manager.c:354: Disposing playlist manager
     (21:02:52) [0x20fff60] [rb_playlist_manager_finalize] rb-playlist-manager.c:391: Finalizing playlist manager
     (21:02:52) [0x20fff60] [rb_shell_finalize] rb-shell.c:1124: unreffing removable media manager
     (21:02:52) [0x20fff60] [rb_shell_finalize] rb-shell.c:1128: unreffing clipboard shell
     (21:02:52) [0x20fff60] [rb_shell_finalize] rb-shell.c:1131: destroying prefs
     (21:02:52) [0x20fff60] [rb_shell_finalize] rb-shell.c:1139: destroying window
     (21:02:52) [0x20fff60] [rb_static_playlist_source_dispose]  rb-static-playlist-source.c:233: Disposing static playlist source  0x2549000
     (21:02:52) [0x20fff60] [rb_playlist_source_dispose] rb-playlist-source.c:399: Disposing playlist source 0x2549000
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x2549000: 'Play Queue'
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2555510
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2555510
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2555580
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2555580
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x25555f0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x25555f0
     (21:02:52) [0x20fff60] [rb_static_playlist_source_dispose]  rb-static-playlist-source.c:227: Dispose has already run for static  playlist source 0x2549000
     (21:02:52) [0x20fff60] [rb_static_playlist_source_finalize]  rb-static-playlist-source.c:263: Finalizing static playlist source  0x2549000
     (21:02:52) [0x20fff60] [rb_playlist_source_finalize] rb-playlist-source.c:425: Finalizing playlist source 0x2549000
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x2549000: 'Play Queue'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x2579b40 count: 3
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x2318200: 'Music'
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2555740
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2555740
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2559040
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2559040
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x25590b0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x25590b0
     (21:02:52) [0x20fff60] [rb_podcast_source_dispose] rb-podcast-source.c:442: dispose podcast_source
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x2584210: 'Podcasts'
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2559190
     (21:02:52) [0x20fff60] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x25c3580
     (21:02:52) [0x20fff60] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x25c3580
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2559190
     (21:02:52) [0x20fff60] [rb_podcast_source_dispose] rb-podcast-source.c:442: dispose podcast_source
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x2584210: 'Podcasts'
     (21:02:52) [0x20fff60] [rb_podcast_source_finalize] rb-podcast-source.c:490: finalizing podcast source
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x2584210: 'Podcasts'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x25b7980 count: 2
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x25bb060: 'Missing Files'
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x25bb060: 'Missing Files'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x25bb060: 'Missing Files'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x25b7a40 count: 2
     (21:02:52) [0x20fff60] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x25c0320
     (21:02:52) [0x20fff60] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x25c0320
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x22fb850: 'Import Errors'
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x22fb850: 'Import Errors'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x22fb850: 'Import Errors'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x25c8d40 count: 2
     (21:02:52) [0x20fff60] [rb_vis_widget_dispose] rb-vis-widget.c:229: vis widget 0x311b970 disposed
     (21:02:52) [0x20fff60] [rb_vis_widget_dispose] rb-vis-widget.c:229: vis widget 0x311b970 disposed
     (21:02:52) [0x20fff60] [rb_playlist_source_dispose] rb-playlist-source.c:399: Disposing playlist source 0x3040080
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x3040080: 'Downloaded Music'
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2fefe60
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2fefe60
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2fefdf0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2fefdf0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x311bed0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x311bed0
     (21:02:52) [0x20fff60] [rb_playlist_source_dispose]  rb-playlist-source.c:393: Dispose has already run for playlist source  0x3040080
     (21:02:52) [0x20fff60] [rb_playlist_source_finalize] rb-playlist-source.c:425: Finalizing playlist source 0x3040080
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x3040080: 'Downloaded Music'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x2fd6010 count: 2
     (21:02:52) [0x20fff60] [rb_playlist_source_dispose] rb-playlist-source.c:399: Disposing playlist source 0x3040230
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x3040230: 'Purchased from Ubuntu One'
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2dcb190
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2dcb190
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x3164080
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x3164080
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2dcb0b0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2dcb0b0
     (21:02:52) [0x20fff60] [rb_playlist_source_dispose]  rb-playlist-source.c:393: Dispose has already run for playlist source  0x3040230
     (21:02:52) [0x20fff60] [rb_playlist_source_finalize] rb-playlist-source.c:425: Finalizing playlist source 0x3040230
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x3040230: 'Purchased from Ubuntu One'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x2fc30c0 count: 2
     (21:02:52) [0x20fff60] [rb_playlist_source_dispose] rb-playlist-source.c:399: Disposing playlist source 0x30403e0
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x30403e0: 'My Top Rated'
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x3039ab0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x3039ab0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x3039810
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x3039810
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x3164320
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x3164320
     (21:02:52) [0x20fff60] [rb_playlist_source_dispose]  rb-playlist-source.c:393: Dispose has already run for playlist source  0x30403e0
     (21:02:52) [0x20fff60] [rb_playlist_source_finalize] rb-playlist-source.c:425: Finalizing playlist source 0x30403e0
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x30403e0: 'My Top Rated'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x2fdb3d0 count: 2
     (21:02:52) [0x20fff60] [rb_playlist_source_dispose] rb-playlist-source.c:399: Disposing playlist source 0x3040590
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x3040590: 'Recently Added'
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2dcb4e0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2dcb4e0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2dcb550
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2dcb550
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2dcb5c0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2dcb5c0
     (21:02:52) [0x20fff60] [rb_playlist_source_dispose]  rb-playlist-source.c:393: Dispose has already run for playlist source  0x3040590
     (21:02:52) [0x20fff60] [rb_playlist_source_finalize] rb-playlist-source.c:425: Finalizing playlist source 0x3040590
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x3040590: 'Recently Added'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x300e490 count: 2
     (21:02:52) [0x20fff60] [rb_playlist_source_dispose] rb-playlist-source.c:399: Disposing playlist source 0x3040740
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x3040740: 'Recently Played'
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2f79090
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2f79090
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2f79100
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2f79100
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2f79170
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2f79170
     (21:02:52) [0x20fff60] [rb_playlist_source_dispose]  rb-playlist-source.c:393: Dispose has already run for playlist source  0x3040740
     (21:02:52) [0x20fff60] [rb_playlist_source_finalize] rb-playlist-source.c:425: Finalizing playlist source 0x3040740
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x3040740: 'Recently Played'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x2f84d50 count: 2
     (21:02:52) [0x20fff60] [rb_static_playlist_source_dispose]  rb-static-playlist-source.c:233: Disposing static playlist source  0x2f2b0c0
     (21:02:52) [0x20fff60] [rb_playlist_source_dispose] rb-playlist-source.c:399: Disposing playlist source 0x2f2b0c0
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x2f2b0c0: 'Life_With_PTSD'
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2f98c40
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2f98c40
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2f98cb0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2f98cb0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x2f98d20
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x2f98d20
     (21:02:52) [0x20fff60] [rb_static_playlist_source_dispose]  rb-static-playlist-source.c:227: Dispose has already run for static  playlist source 0x2f2b0c0
     (21:02:52) [0x20fff60] [rb_static_playlist_source_finalize]  rb-static-playlist-source.c:263: Finalizing static playlist source  0x2f2b0c0
     (21:02:52) [0x20fff60] [rb_playlist_source_finalize] rb-playlist-source.c:425: Finalizing playlist source 0x2f2b0c0
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x2f2b0c0: 'Life'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x2face40 count: 2
     (21:02:52) [0x20fff60] [rb_static_playlist_source_dispose]  rb-static-playlist-source.c:233: Disposing static playlist source  0x2f2b260
     (21:02:52) [0x20fff60] [rb_playlist_source_dispose] rb-playlist-source.c:399: Disposing playlist source 0x2f2b260
     (21:02:52) [0x20fff60] [rb_source_dispose] rb-source.c:445: Disposing source 0x2f2b260: 'Mike01'
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x31afb40
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x31afb40
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x31afc40
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x31afc40
     (21:02:52) [0x20fff60] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:518: disposing property model 0x31afcb0
     (21:02:52) [0x20fff60] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:545: finalizing property model 0x31afcb0
     (21:02:52) [0x20fff60] [rb_static_playlist_source_dispose]  rb-static-playlist-source.c:227: Dispose has already run for static  playlist source 0x2f2b260
     (21:02:52) [0x20fff60] [rb_static_playlist_source_finalize]  rb-static-playlist-source.c:263: Finalizing static playlist source  0x2f2b260
     (21:02:52) [0x20fff60] [rb_playlist_source_finalize] rb-playlist-source.c:425: Finalizing playlist source 0x2f2b260
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x2f2b260: 'Mike01'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x31c6010 count: 2
     (21:02:52) [0x20fff60] [rb_library_source_finalize] rb-library-source.c:294: finalizing library source
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:472: Finalizing source 0x2318200: 'Music'
     (21:02:52) [0x20fff60] [rb_source_finalize] rb-source.c:475: Unreffing model 0x25a6560 count: 2
     (21:02:52) [0x20fff60] [rb_shell_finalize] rb-shell.c:1147: shutting down DB
     (21:02:52) [0x20fff60] [rhythmdb_shutdown] rhythmdb.c:1045: 2 outstanding threads
     (21:02:52) [0x2df5850] [action_thread_main] rhythmdb.c:2924: exiting action thread
     (21:02:52) [0x20fff60] [rb_shell_finalize] rb-shell.c:1150: unreffing DB
     (21:02:52) [0x20fff60] [rb_shell_finalize] rb-shell.c:1155: shell shutdown complete
     (21:02:52) [0x20fff60] [main] main.c:346: out of toplevel loop
     (21:02:52) [0x20fff60] [main] main.c:355: THE END
     mafoelffen@maf-ubuntu-01:~/Documents$
   [/HTML]
Remember that these are only the last of what scrolled by the screen.

---

### Post by BicyclerBoy on 2011-01-13
I have firm ideas. Thought the debug verbose messages would be more illuminating.

Guessing but this should do no warn...
I would remove all rhythmbox package via synaptic:
Remove any 3rd party ppa you used for other rhythmbox source.
reload
Remove rhythmbox package version forcing.
Remove all rhythmbox
Reload
Mark all updates
update

In synaptic
Re-install python
Re-install anything to do with gstreamer.
You should probably have the good bad & ugly gstreamer plug-ins..AFAIK

---

### Post by MAFoElffen on 2011-01-13
> **BicyclerBoy said:**
> I have firm ideas. Thought the debug verbose messages would be more illuminating.

Guessing but this should do no warn...
I would remove all rhythmbox package via synaptic:
Remove any 3rd party ppa you used for other rhythmbox source.
reload
Remove rhythmbox package version forcing.
Remove all rhythmbox
Reload
Mark all updates
update

I've done all the above twice.  In fact, the above was after the second uninstall/install fresh.  Afterwards, I had to remove the Ubuntu One Music store plugin for it to even come up.

I haven't done the below though... 
> **BicyclerBoy said:**
> In synaptic
Re-install python
Re-install anything to do with gstreamer.
You should probably have the good bad & ugly gstreamer plug-ins..AFAIK
I'll re-install python and the gstreamer pluggins and see if that helps.

---

### Post by MAFoElffen on 2011-01-13
Did the above -- No change. 

As it did before:
- It plays fine.
- Can create Playlists and burn CD's through Brasero. 
 - I can update and edit the music libray with newly added dl'ed music....
- Jamendo and Magnatune pluggins work.

What it doesn't do (or problems):
 - Will not even start if the Ubuntu One Music Store pluggin is loaded/installed.
 - Crashes when you put an Audio CD in the CD/DVD Drive.
 - Crashes if you select the LastFM pluggin.
 
Re-installs don't seem to change it.  Upgrades to next gnu stable doesn't change it... but then I lose the desktop integration also. (since it is not yet Ubuntu supported)

So... IIt resally sucks that I can't play or rip from my own CD's (using rhtembox).  I've been bumping into one of my other OS'es and ripping to a shared drive and then playing them in Ubuntu/Rhythembox.

I really like how Rthythbox is integrated into the desktop... and keeps me entertained while I work and play... editing code, waiting for compiles and playing games.  This problem is really getting frustrating and annoying!

What makes this most frustrating "is" that my laptop is also running Ubuntu 10,10 and Rhythembox works great wuth "all" the bells and whistles!!! (Even the Ubuntu One Music Store pluggin)  This laptop does not have all the dev tools, dev librabraries and games that my Desktop has.  My desktop has also been release upgraded from version to version -- The laptop was a fresh OS install.

You think maybe it might be a prefrence file somewhere in my account or another pluggin besides the Ubuntu One Music Store pluggin?  I'm thinking if I could backup the prefence file, and put in a geberic/fresh profile/prefrence file... Just trying to come up with any  ideas...

---

### Post by MAFoElffen on 2011-01-13
Did the above -- No change. 

As it did before:
- It plays fine.
- Can create Playlists and burn CD's through Brasero. 
 - I can update and edit the music libray with newly added dl'ed music....

What it doesn't do (or problems):
 - Will not even start if the Ubuntu One Music Store pluggin is loaded/installed.
 - Crashes when you put an Audio CD in the CD/DVD Drive.
 - Crashes if you select the LastFM pluggin.
 - Jamendo and Magnatune pluggins don't work.  They come up and display their catalogs, but if you they to play anything it crashes Rhthymbox.

Re-installs don't seem to change it.  Upgrades to next gnu stable doesn't change it... but then I lose the desktop integration also. (since it is not yet Ubuntu supported)

So... IIt resally sucks that I can't play or rip from my own CD's (using rhtembox).  I've been bumping into one of my other OS'es and ripping to a shared drive and then playing them in Ubuntu/Rhythembox.

I really like how Rthythbox is integrated into the desktop... and keeps me entertained while I work and play... editing code, waiting for compiles and playing games.  This problem is really getting frustrating and annoying!

What makes this most frustrating "is" that my laptop is also running Ubuntu 10,10 and Rhythembox works great wuth "all" the bells and whistles!!! (Even the Ubuntu One Music Store pluggin)  This laptop does not have all the dev tools, dev librabraries and games that my Desktop has.  My desktop has also been release upgraded from version to version -- The laptop was a fresh OS install.

You think maybe it might be a prefrence file somewhere in my account or another pluggin besides the Ubuntu One Music Store pluggin?  I'm thinking if I could backup the prefence file, and put in a geberic/fresh profile/prefrence file... Just trying to come up with any  ideas...

---

### Post by MAFoElffen on 2011-01-13
In the next posts I will add more info...

DistroRelease: Ubuntu 10.10
Package: rhythmbox 0.13.1-0ubuntu6
ProcVersionSignature: Ubuntu 2.6.35-24.42-generic 2.6.35.8
Uname: Linux 2.6.35-24-generic x86_64
NonfreeKernelModules: nvidia
Architecture: amd64
Date: Thu Jan 13 19:56:18 2011
ExecutablePath: /usr/bin/rhythmbox
InstallationMedia: Ubuntu 10.04 LTS "Lucid Lynx" - Release amd64 (20100429)
ProcEnviron:
 SHELL=/bin/bash
 LANG=en_US.utf8
SourcePackage: rhythmbox

---

### Post by MAFoElffen on 2011-01-13
Dependencies:
[HTML]
adduser 3.112ubuntu1
base-files 5.0.0ubuntu23
base-passwd 3.5.22
busybox-initramfs 1:1.15.3-1ubuntu5
coreutils 8.5-1ubuntu3
cpio 2.11-4ubuntu1
cpp 4:4.4.4-1ubuntu2
cpp-4.4 4.4.4-14ubuntu5
dbus 1.4.0-0ubuntu1
dbus-x11 1.4.0-0ubuntu1
debconf 1.5.32ubuntu3
debconf-i18n 1.5.32ubuntu3
debianutils 3.2.3
defoma 0.11.11ubuntu1
dpkg 1.15.8.4ubuntu3.1
file 5.03-5ubuntu1
findutils 4.4.2-1ubuntu1
fontconfig 2.8.0-2ubuntu1
fontconfig-config 2.8.0-2ubuntu1
gamin 0.1.10-1ubuntu3
gcc-4.4-base 4.4.4-14ubuntu5
gcc-4.5-base 4.5.1-7ubuntu2
gconf2 2.31.91-0ubuntu3.1
gconf2-common 2.31.91-0ubuntu3.1
gir1.0-glib-2.0 0.9.3-0ubuntu4
gnome-icon-theme 2.31.0-0ubuntu1
gnome-media-common 2.31.6-0ubuntu2
gnome-mime-data 2.18.0-1
gstreamer0.10-alsa 0.10.30-2
gstreamer0.10-plugins-base 0.10.30-2
gstreamer0.10-plugins-good 0.10.25-4ubuntu2
gstreamer0.10-x 0.10.30-2
hicolor-icon-theme 0.11-1
ifupdown 0.6.10ubuntu3.1
initramfs-tools 0.98.1ubuntu6
initramfs-tools-bin 0.98.1ubuntu6
initscripts 2.87dsf-4ubuntu19
insserv 1.14.0-2
iso-codes 3.17-1
klibc-utils 1.5.20-1
libaa1 1.4p5-38build1
libacl1 2.2.49-3
libart-2.0-2 2.3.21-1
libasound2 1.0.23-1ubuntu2.1
libaspell15 0.60.6-4ubuntu1
libatk1.0-0 1.32.0-0ubuntu1
libattr1 1:2.4.44-2
libavahi-client3 0.6.27-2ubuntu3
libavahi-common-data 0.6.27-2ubuntu3
libavahi-common3 0.6.27-2ubuntu3
libavahi-glib1 0.6.27-2ubuntu3
libavc1394-0 0.5.3-1build4
libblkid1 2.17.2-0ubuntu1
libbonobo2-0 2.32.0-0ubuntu1
libbonobo2-common 2.32.0-0ubuntu1
libbonoboui2-0 2.24.3-1ubuntu1
libbonoboui2-common 2.24.3-1ubuntu1
libbz2-1.0 1.0.5-4ubuntu1
libc-bin 2.12.1-0ubuntu10.1
libc6 2.12.1-0ubuntu10.1
libcaca0 0.99.beta17-1
libcairo2 1.10.0-1ubuntu3
libcanberra0 0.25-0ubuntu1
libcdparanoia0 3.10.2+debian-9
libcomerr2 1.41.12-1ubuntu2
libcroco3 0.6.2-1
libcups2 1.4.4-6ubuntu2.3
libdatrie1 0.2.3-1
libdb4.8 4.8.30-1
libdbus-1-3 1.4.0-0ubuntu1
libdbus-glib-1-2 0.88-2
libdrm-intel1 2.4.21-1ubuntu2.1
libdrm-nouveau1 2.4.21-1ubuntu2.1
libdrm-radeon1 2.4.21-1ubuntu2.1
libdrm2 2.4.21-1ubuntu2.1
libdv4 1.0.0-2ubuntu2
libenchant1c2a 1.6.0-1
libexpat1 2.0.1-7ubuntu1
libffi5 3.0.9-2ubuntu2
libflac8 1.2.1-3
libfontconfig1 2.8.0-2ubuntu1
libfreetype6 2.4.2-2ubuntu0.1
libgail18 2.22.0-0ubuntu1
libgamin0 0.1.10-1ubuntu3
libgcc1 1:4.5.1-7ubuntu2
libgconf2-4 2.31.91-0ubuntu3.1
libgcrypt11 1.4.5-2ubuntu1
libgdbm3 1.8.3-9
libgdk-pixbuf2.0-0 2.22.0-0ubuntu1
libgirepository1.0-1 0.9.3-0ubuntu4
libglade2-0 1:2.6.4-1build1
libgladeui-1-9 3.7.0.is.3.6.7-0ubuntu2
libglib2.0-0 2.26.0-0ubuntu1
libgmime-2.4-2 2.4.14-1+nmu1
libgmp3c2 2:4.3.2+dfsg-1ubuntu1
libgnome-keyring0 2.31.92-0ubuntu1
libgnome-media0 2.31.6-0ubuntu2
libgnome2-0 2.32.0-0ubuntu1
libgnome2-common 2.32.0-0ubuntu1
libgnomecanvas2-0 2.30.2-0ubuntu1
libgnomecanvas2-common 2.30.2-0ubuntu1
libgnomeui-0 2.24.4-0ubuntu1
libgnomeui-common 2.24.4-0ubuntu1
libgnomevfs2-0 1:2.24.3-1ubuntu1
libgnomevfs2-common 1:2.24.3-1ubuntu1
libgnutls26 2.8.6-1
libgpg-error0 1.6-1ubuntu2
libgpm2 1.20.4-3.3ubuntu1
libgssapi-krb5-2 1.8.1+dfsg-5ubuntu0.2
libgstreamer-plugins-base0.10-0 0.10.30-2
libgstreamer0.10-0 0.10.30-1build2
libgtk2.0-0 2.22.0-0ubuntu1
libgtk2.0-bin 2.22.0-0ubuntu1
libgtk2.0-common 2.22.0-0ubuntu1
libgudev-1.0-0 1:162-2.2
libhunspell-1.2-0 1.2.11-1ubuntu1
libice6 2:1.0.6-1
libicu42 4.2.1-3
libidl0 0.8.14-0.1
libiec61883-0 1.2.0-0.1build1
libjasper1 1.900.1-7
libjpeg62 6b-16.1
libk5crypto3 1.8.1+dfsg-5ubuntu0.2
libkeyutils1 1.4-1
libklibc 1.5.20-1
libkrb5-3 1.8.1+dfsg-5ubuntu0.2
libkrb5support0 1.8.1+dfsg-5ubuntu0.2
liblaunchpad-integration1 0.1.38
libldap-2.4-2 2.4.23-0ubuntu3.4
liblocale-gettext-perl 1.05-6
libltdl7 2.2.6b-2ubuntu1
liblzma2 4.999.9beta+20100527-1
libmagic1 5.03-5ubuntu1
libmpfr4 3.0.0-2
libncurses5 5.7+20100626-0ubuntu1
libncursesw5 5.7+20100626-0ubuntu1
libnewt0.52 0.52.11-1
libnih-dbus1 1.0.2-1ubuntu2
libnih1 1.0.2-1ubuntu2
libnotify1 0.5.0-2ubuntu1
libogg0 1.2.0~dfsg-1
liborbit2 1:2.14.18-0.1
liborc-0.4-0 0.4.6-1
libpam-modules 1.1.1-4ubuntu2
libpam0g 1.1.1-4ubuntu2
libpango1.0-0 1.28.1-1ubuntu3
libpango1.0-common 1.28.1-1ubuntu3
libpcre3 8.02-1
libpixman-1-0 0.18.4-1
libplymouth2 0.8.2-2ubuntu5.1
libpng12-0 1.2.44-1
libpopt0 1.16-1
libproxy0 0.3.1-1ubuntu1
libpython2.6 2.6.6-5ubuntu1
libraw1394-11 2.0.5-2ubuntu1
libreadline6 6.1-3
librsvg2-2 2.32.0-0ubuntu1
librsvg2-common 2.32.0-0ubuntu1
libsasl2-2 2.1.23.dfsg1-5ubuntu2
libselinux1 2.0.94-1
libsepol1 2.0.41-1
libshout3 2.2.2-5ubuntu1
libslang2 2.2.2-4ubuntu1
libsm6 2:1.1.1-1
libsoup-gnome2.4-1 2.31.92-0ubuntu1
libsoup2.4-1 2.31.92-0ubuntu1
libspeex1 1.2~rc1-1ubuntu1
libsqlite3-0 3.7.2-1ubuntu0.1
libssl0.9.8 0.9.8o-1ubuntu4.3
libstdc++6 4.5.1-7ubuntu2
libtag1-vanilla 1.6.3-1
libtag1c2a 1.6.3-1
libtasn1-3 2.7-1
libtdb1 1.2.1-2
libtext-charwidth-perl 0.04-6
libtext-iconv-perl 1.7-2
libtext-wrapi18n-perl 0.06-7
libthai-data 0.1.14-2
libthai0 0.1.14-2
libtheora0 1.1.1+dfsg.1-3
libtiff4 3.9.4-2
libtotem-plparser17 2.30.3-0ubuntu1
libudev0 162-2.2
libusb-0.1-4 2:0.1.12-15ubuntu2
libuuid1 2.17.2-0ubuntu1
libv4l-0 0.6.4-1ubuntu1
libvisual-0.4-0 0.4.0-3
libvorbis0a 1.3.1-1
libvorbisenc2 1.3.1-1
libvorbisfile3 1.3.1-1
libwavpack1 4.60.1-1
libwebkit-1.0-2 1.2.5-0ubuntu0.10.10.1
libwebkit-1.0-common 1.2.5-0ubuntu0.10.10.1
libx11-6 2:1.3.3-3ubuntu1
libx11-data 2:1.3.3-3ubuntu1
libxau6 1:1.0.6-1
libxcb-render0 1.6-1
libxcb-shm0 1.6-1
libxcb1 1.6-1
libxcomposite1 1:0.4.2-1
libxcursor1 1:1.1.10-2
libxdamage1 1:1.1.3-1
libxdmcp6 1:1.0.3-2
libxext6 2:1.1.2-1
libxfixes3 1:4.0.5-1
libxft2 2.1.14-2ubuntu1
libxi6 2:1.3-4
libxinerama1 2:1.1-3
libxml2 2.7.7.dfsg-4ubuntu0.1
libxrandr2 2:1.3.0-3
libxrender1 1:0.9.6-1
libxslt1.1 1.1.26-6
libxt6 1:1.0.7-1
libxv1 2:1.0.5-1
lsb-base 4.0-0ubuntu8
makedev 2.3.1-89ubuntu1
media-player-info 10-1
mime-support 3.48-1ubuntu2
module-init-tools 3.12-1ubuntu2
mount 2.17.2-0ubuntu1
mountall 2.19
ncurses-bin 5.7+20100626-0ubuntu1
net-tools 1.60-23ubuntu3
passwd 1:4.1.4.2-1ubuntu3
perl 5.10.1-12ubuntu2
perl-base 5.10.1-12ubuntu2
perl-modules 5.10.1-12ubuntu2
plymouth 0.8.2-2ubuntu5.1
procps 1:3.2.8-9ubuntu3
psmisc 22.11-1
python 2.6.6-2ubuntu2
python-cairo 1.8.8-1
python-central 0.6.15ubuntu2
python-gconf 2.28.1-1ubuntu2
python-gnome2 2.28.1-1ubuntu2
python-gnomecanvas 2.28.1-1ubuntu2
python-gobject 2.21.5-0ubuntu3
python-gst0.10 0.10.19-2
python-gtk2 2.21.0-0ubuntu1
python-libxml2 2.7.7.dfsg-4ubuntu0.1
python-minimal 2.6.6-2ubuntu2
python-pyorbit 2.24.0-5ubuntu3
python-support 1.0.9ubuntu1
python2.6 2.6.6-5ubuntu1
python2.6-minimal 2.6.6-5ubuntu1
readline-common 6.1-3
sed 4.2.1-7
sensible-utils 0.0.4ubuntu1
shared-mime-info 0.71-3
sysv-rc 2.87dsf-4ubuntu19
sysvinit-utils 2.87dsf-4ubuntu19
ttf-dejavu-core 2.31-1
tzdata 2010o-0ubuntu0.10.10
ucf 3.0025
udev 162-2.2
upstart 0.6.6-3
util-linux 2.17.2-0ubuntu1 [modified: sbin/fdisk sbin/cfdisk usr/share/man/man8/fdisk.8.gz usr/share/man/man8/cfdisk.8.gz]
whiptail 0.52.11-1
x11-common 1:7.5+6ubuntu3
xz-utils 4.999.9beta+20100527-1
zlib1g 1:1.2.3.4.dfsg-3ubuntu1
[/HTML]

---

### Post by MAFoElffen on 2011-01-13
GConfNonDefault:
[HTML]
/apps/rhythmbox/audioscrobbler/password=##MASKED##
/apps/rhythmbox/audioscrobbler/username=##MASKED##
/apps/rhythmbox/first_time_flag=true
/apps/rhythmbox/library_locations=##MASKED##
/apps/rhythmbox/monitor_library=true
/apps/rhythmbox/player/transition_time=0
/apps/rhythmbox/plugins/daap/active=false
/apps/rhythmbox/plugins/jamendo/sorting=,ascending
/apps/rhythmbox/plugins/lyrics/folder=
/apps/rhythmbox/plugins/magnatune/paned_position=98
/apps/rhythmbox/plugins/magnatune/sorting=,ascending
/apps/rhythmbox/plugins/power-manager/active=true
/apps/rhythmbox/plugins/replaygain/preamp=0
/apps/rhythmbox/plugins/status-icon/status-icon-mode=0
/apps/rhythmbox/plugins/status-icon/window-visible=false
/apps/rhythmbox/plugins/visualizer/element=libvisual_corona
/apps/rhythmbox/sharing/share_name=##MASKED##
/apps/rhythmbox/sharing/share_password=##MASKED##
/apps/rhythmbox/state/add_dir=##MASKED##
/apps/rhythmbox/state/burn_device=
/apps/rhythmbox/state/library/paned_position=181
/apps/rhythmbox/state/library/sorting=Title,ascending
/apps/rhythmbox/state/podcast/download_next_time=1294980958
/apps/rhythmbox/state/podcast/download_prefix=##MASKED##
/apps/rhythmbox/state/volume=1
/apps/rhythmbox/state/window_maximized=true
/apps/rhythmbox/ui/toolbar_style=1
[/HTML]

---

### Post by MAFoElffen on 2011-01-13
GstreamerVersions:
[HTML]gstreamer-tools N/A
gstreamer0.10-plugins-ugly-dbg N/A
gstreamer0.10-plugins-cutter N/A
gstreamer0.10-gnomevfs N/A
gstreamer0.10-plugins-bad-multiverse-dbg N/A
gstreamer0.10-plugins-bad 0.10.20-1ubuntu1
gstreamer0.10-alsa 0.10.30-2
gstreamer0.10-esd 0.10.25-4ubuntu2
gstreamer0.10-plugins-ugly-multiverse-dbg N/A
gstreamer0.10-plugins-good-doc N/A
gstreamer0.10-plugins-bad-dbg N/A
gstreamer0.10-ffmpeg 0.10.11-1
gstreamer0.10-x 0.10.30-2
gstreamer0.10-ffmpeg-dbg N/A
gstreamer0.10-gnonlin-dbg N/A
gstreamer0.10-plugins-bad-doc N/A
gstreamer0.10-plugins-good-dbg 0.10.25-4ubuntu2
gstreamer0.10-pulseaudio 0.10.25-4ubuntu2
gstreamer0.10-plugins-bad-multiverse N/A
gstreamer0.10-plugins-ugly 0.10.16-1
gstreamer0.10-doc N/A
gstreamer-dbus-media-service N/A
gstreamer0.10-pocketsphinx N/A
gstreamer0.10-fluendo-mp3 N/A
gstreamer0.10-fluendo-plugins-mp3-partner 7.0.20100316-3
gstreamer0.10-plugins-base-apps 0.10.30-2
gstreamer0.10-gnonlin-doc N/A
gstreamer0.10-sdl N/A
gstreamer0.10-plugins-good 0.10.25-4ubuntu2
gstreamer0.10-nice 0.0.12-1
gstreamer0.10-buzztard-doc N/A
gstreamer0.10-buzztard N/A
gstreamer0.10-gnonlin 0.10.16-1
gstreamer0.10-plugins-base 0.10.30-2
gstreamer0.10-tools 0.10.30-1build2
gstreamer0.10-plugins-base-doc N/A
gstreamer0.10-plugins-ugly-multiverse N/A
gstreamer0.10-plugins-base-dbg 0.10.30-2
gstreamer0.10-plugins-ugly-doc N/A
gstreamer0.10-packagekit N/A[/HTML]

---

### Post by MAFoElffen on 2011-01-13
LogAlsaMixer:
[HTML]Simple mixer control 'Master',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 124 [48%] [-33.00dB] Capture 205 [80%] [-12.75dB]
  Front Right: Playback 124 [48%] [-33.00dB] Capture 205 [80%] [-12.75dB]
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 205 [80%] [-12.75dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] Capture 205 [80%] [-12.75dB] [on]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Center/LFE',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Line-in',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'S/PDIF-in',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
Simple mixer control 'S/PDIF-out',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off][/HTML]

---

### Post by MAFoElffen on 2011-01-13
ProcMaps:
[HTML]00400000-00408000 r-xp 00000000 08:13 4981098                            /usr/bin/rhythmbox
00607000-00608000 r--p 00007000 08:13 4981098                            /usr/bin/rhythmbox
00608000-00609000 rw-p 00008000 08:13 4981098                            /usr/bin/rhythmbox
017bf000-02eda000 rw-p 00000000 00:00 0                                  [heap]
7effdbc54000-7effdbc55000 ---p 00000000 00:00 0 
7effdbc55000-7effdc455000 rw-p 00000000 00:00 0 
7effdc455000-7effdc456000 ---p 00000000 00:00 0 
7effdc456000-7effdcc56000 rw-p 00000000 00:00 0 
7effdcc56000-7effdccb6000 rw-s 00000000 00:04 116424733                  /SYSV00000000 (deleted)
7effdccb6000-7effdccf6000 r-xp 00000000 08:13 4982031                    /usr/lib/libibus.so.2.0.0
7effdccf6000-7effdcef6000 ---p 00040000 08:13 4982031                    /usr/lib/libibus.so.2.0.0
7effdcef6000-7effdcef7000 r--p 00040000 08:13 4982031                    /usr/lib/libibus.so.2.0.0
7effdcef7000-7effdcef8000 rw-p 00041000 08:13 4982031                    /usr/lib/libibus.so.2.0.0
7effdcef8000-7effdcef9000 rw-p 00000000 00:00 0 
7effdcef9000-7effdcefe000 r-xp 00000000 08:13 4986911                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7effdcefe000-7effdd0fd000 ---p 00005000 08:13 4986911                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7effdd0fd000-7effdd0fe000 r--p 00004000 08:13 4986911                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7effdd0fe000-7effdd0ff000 rw-p 00005000 08:13 4986911                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7effdd0ff000-7effdd100000 ---p 00000000 00:00 0 
7effdd100000-7effdd900000 rw-p 00000000 00:00 0 
7effdd900000-7effdd90e000 r-xp 00000000 08:13 8785493                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7effdd90e000-7effddb0d000 ---p 0000e000 08:13 8785493                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7effddb0d000-7effddb0e000 r--p 0000d000 08:13 8785493                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7effddb0e000-7effddb0f000 rw-p 0000e000 08:13 8785493                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7effddb0f000-7effddb18000 r-xp 00000000 08:13 8785486                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7effddb18000-7effddd17000 ---p 00009000 08:13 8785486                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7effddd17000-7effddd18000 r--p 00008000 08:13 8785486                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7effddd18000-7effddd19000 rw-p 00009000 08:13 8785486                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7effddd19000-7effddd1b000 r-xp 00000000 08:13 8785461                    /usr/lib/rhythmbox/plugins/power-manager/libpower-manager.so
7effddd1b000-7effddf1a000 ---p 00002000 08:13 8785461                    /usr/lib/rhythmbox/plugins/power-manager/libpower-manager.so
7effddf1a000-7effddf1b000 r--p 00001000 08:13 8785461                    /usr/lib/rhythmbox/plugins/power-manager/libpower-manager.so
7effddf1b000-7effddf1c000 rw-p 00002000 08:13 8785461                    /usr/lib/rhythmbox/plugins/power-manager/libpower-manager.so
7effddf1c000-7effddf23000 r-xp 00000000 08:13 10357165                   /lib/libusb-0.1.so.4.4.4
7effddf23000-7effde122000 ---p 00007000 08:13 10357165                   /lib/libusb-0.1.so.4.4.4
7effde122000-7effde123000 r--p 00006000 08:13 10357165                   /lib/libusb-0.1.so.4.4.4
7effde123000-7effde125000 rw-p 00007000 08:13 10357165                   /lib/libusb-0.1.so.4.4.4
7effde125000-7effde164000 r-xp 00000000 08:13 4981104                    /usr/lib/libmtp.so.8.3.3
7effde164000-7effde363000 ---p 0003f000 08:13 4981104                    /usr/lib/libmtp.so.8.3.3
7effde363000-7effde36b000 r--p 0003e000 08:13 4981104                    /usr/lib/libmtp.so.8.3.3
7effde36b000-7effde36d000 rw-p 00046000 08:13 4981104                    /usr/lib/libmtp.so.8.3.3
7effde36d000-7effde37f000 r-xp 00000000 08:13 8785457                    /usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so
7effde37f000-7effde57e000 ---p 00012000 08:13 8785457                    /usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so
7effde57e000-7effde57f000 r--p 00011000 08:13 8785457                    /usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so
7effde57f000-7effde580000 rw-p 00012000 08:13 8785457                    /usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so
7effde580000-7effde587000 r-xp 00000000 08:13 8785453                    /usr/lib/rhythmbox/plugins/mpris/libmpris.so
7effde587000-7effde787000 ---p 00007000 08:13 8785453                    /usr/lib/rhythmbox/plugins/mpris/libmpris.so
7effde787000-7effde788000 r--p 00007000 08:13 8785453                    /usr/lib/rhythmbox/plugins/mpris/libmpris.so
7effde788000-7effde789000 rw-p 00008000 08:13 8785453                    /usr/lib/rhythmbox/plugins/mpris/libmpris.so
7effde789000-7effde78c000 r-xp 00000000 08:13 8785450                    /usr/lib/rhythmbox/plugins/mmkeys/libmmkeys.so
7effde78c000-7effde98b000 ---p 00003000 08:13 8785450                    /usr/lib/rhythmbox/plugins/mmkeys/libmmkeys.so
7effde98b000-7effde98c000 r--p 00002000 08:13 8785450                    /usr/lib/rhythmbox/plugins/mmkeys/libmmkeys.so
7effde98c000-7effde98d000 rw-p 00003000 08:13 8785450                    /usr/lib/rhythmbox/plugins/mmkeys/libmmkeys.so
7effde98d000-7effde997000 r-xp 00000000 08:13 5125638                    /usr/lib/pyshared/python2.6/gtk-2.0/gnomekeyring.so
7effde997000-7effdeb97000 ---p 0000a000 08:13 5125638                    /usr/lib/pyshared/python2.6/gtk-2.0/gnomekeyring.so
7effdeb97000-7effdeb98000 r--p 0000a000 08:13 5125638                    /usr/lib/pyshared/python2.6/gtk-2.0/gnomekeyring.so
7effdeb98000-7effdeb99000 rw-p 0000b000 08:13 5125638                    /usr/lib/pyshared/python2.6/gtk-2.0/gnomekeyring.so
7effdeb99000-7effdeb9a000 rw-p 00000000 00:00 0 
7effdeb9a000-7effdeba9000 r-xp 00000000 08:13 4980933                    /usr/lib/libavahi-client.so.3.2.7
7effdeba9000-7effdeda8000 ---p 0000f000 08:13 4980933                    /usr/lib/libavahi-client.so.3.2.7
7effdeda8000-7effdeda9000 r--p 0000e000 08:13 4980933                    /usr/lib/libavahi-client.so.3.2.7
7effdeda9000-7effdedaa000 rw-p 0000f000 08:13 4980933                    /usr/lib/libavahi-client.so.3.2.7
7effdedaa000-7effdedb5000 r-xp 00000000 08:13 4980931                    /usr/lib/libavahi-common.so.3.5.2
7effdedb5000-7effdefb4000 ---p 0000b000 08:13 4980931                    /usr/lib/libavahi-common.so.3.5.2
7effdefb4000-7effdefb5000 r--p 0000a000 08:13 4980931                    /usr/lib/libavahi-common.so.3.5.2
7effdefb5000-7effdefb6000 rw-p 0000b000 08:13 4980931                    /usr/lib/libavahi-common.so.3.5.2
7effdefb6000-7effdefb9000 r-xp 00000000 08:13 4983667                    /usr/lib/libavahi-glib.so.1.0.2
7effdefb9000-7effdf1b8000 ---p 00003000 08:13 4983667                    /usr/lib/libavahi-glib.so.1.0.2
7effdf1b8000-7effdf1b9000 r--p 00002000 08:13 4983667                    /usr/lib/libavahi-glib.so.1.0.2
7effdf1b9000-7effdf1ba000 rw-p 00003000 08:13 4983667                    /usr/lib/libavahi-glib.so.1.0.2
7effdf1ba000-7effdf220000 r-xp 00000000 08:13 4980811                    /usr/lib/libgnomevfs-2.so.0.2400.3
7effdf220000-7effdf41f000 ---p 00066000 08:13 4980811                    /usr/lib/libgnomevfs-2.so.0.2400.3
7effdf41f000-7effdf422000 r--p 00065000 08:13 4980811                    /usr/lib/libgnomevfs-2.so.0.2400.3
7effdf422000-7effdf424000 rw-p 00068000 08:13 4980811                    /usr/lib/libgnomevfs-2.so.0.2400.3
7effdf424000-7effdf425000 rw-p 00000000 00:00 0 
7effdf425000-7effdf430000 r-xp 00000000 08:13 10357143                   /lib/libpopt.so.0.0.0
7effdf430000-7effdf62f000 ---p 0000b000 08:13 10357143                   /lib/libpopt.so.0.0.0
7effdf62f000-7effdf630000 r--p 0000a000 08:13 10357143                   /lib/libpopt.so.0.0.0
7effdf630000-7effdf631000 rw-p 0000b000 08:13 10357143                   /lib/libpopt.so.0.0.0
7effdf631000-7effdf646000 r-xp 00000000 08:13 4984943                    /usr/lib/libgnome-2.so.0.3200.0
7effdf646000-7effdf845000 ---p 00015000 08:13 4984943                    /usr/lib/libgnome-2.so.0.3200.0
7effdf845000-7effdf846000 r--p 00014000 08:13 4984943                    /usr/lib/libgnome-2.so.0.3200.0
7effdf846000-7effdf847000 rw-p 00015000 08:13 4984943                    /usr/lib/libgnome-2.so.0.3200.0
7effdf847000-7effdf851000 r-xp 00000000 08:13 5130483                    /usr/lib/pyshared/python2.6/gtk-2.0/gnome/_gnome.so
7effdf851000-7effdfa51000 ---p 0000a000 08:13 5130483                    /usr/lib/pyshared/python2.6/gtk-2.0/gnome/_gnome.so
7effdfa51000-7effdfa52000 r--p 0000a000 08:13 5130483                    /usr/lib/pyshared/python2.6/gtk-2.0/gnome/_gnome.so
7effdfa52000-7effdfa53000 rw-p 0000b000 08:13 5130483                    /usr/lib/pyshared/python2.6/gtk-2.0/gnome/_gnome.so
7effdfa53000-7effdfa5d000 r-xp 00000000 08:13 8785412                    /usr/lib/rhythmbox/plugins/iradio/libiradio.so
7effdfa5d000-7effdfc5c000 ---p 0000a000 08:13 8785412                    /usr/lib/rhythmbox/plugins/iradio/libiradio.so
7effdfc5c000-7effdfc5d000 r--p 00009000 08:13 8785412                    /usr/lib/rhythmbox/plugins/iradio/libiradio.so
7effdfc5d000-7effdfc5e000 rw-p 0000a000 08:13 8785412                    /usr/lib/rhythmbox/plugins/iradio/libiradio.so
7effdfc5e000-7effdfc63000 r-xp 00000000 08:13 4984366                    /usr/lib/libusbmuxd.so.1.0.4
7effdfc63000-7effdfe62000 ---p 00005000 08:13 4984366                    /usr/lib/libusbmuxd.so.1.0.4
7effdfe62000-7effdfe63000 r--p 00004000 08:13 4984366                    /usr/lib/libusbmuxd.so.1.0.4
7effdfe63000-7effdfe64000 rw-p 00005000 08:13 4984366                    /usr/lib/libusbmuxd.so.1.0.4
7effdfe64000-7effdfe7a000 r-xp 00000000 08:13 4981385                    /usr/lib/libimobiledevice.so.1.0.1
7effdfe7a000-7effe0079000 ---p 00016000 08:13 4981385                    /usr/lib/libimobiledevice.so.1.0.1
7effe0079000-7effe007a000 r--p 00015000 08:13 4981385                    /usr/lib/libimobiledevice.so.1.0.1
7effe007a000-7effe007b000 rw-p 00016000 08:13 4981385                    /usr/lib/libimobiledevice.so.1.0.1
7effe007b000-7effe0083000 r-xp 00000000 08:13 4982241                    /usr/lib/libplist.so.1.1.3
7effe0083000-7effe0282000 ---p 00008000 08:13 4982241                    /usr/lib/libplist.so.1.1.3
7effe0282000-7effe0283000 r--p 00007000 08:13 4982241                    /usr/lib/libplist.so.1.1.3
7effe0283000-7effe0284000 rw-p 00008000 08:13 4982241                    /usr/lib/libplist.so.1.1.3
7effe0284000-7effe02f2000 r-xp 00000000 08:13 4982078                    /usr/lib/libgpod.so.4.3.0
7effe02f2000-7effe04f1000 ---p 0006e000 08:13 4982078                    /usr/lib/libgpod.so.4.3.0
7effe04f1000-7effe04f7000 r--p 0006d000 08:13 4982078                    /usr/lib/libgpod.so.4.3.0
7effe04f7000-7effe04f8000 rw-p 00073000 08:13 4982078                    /usr/lib/libgpod.so.4.3.0
7effe04f8000-7effe04f9000 rw-p 00000000 00:00 0 
7effe04f9000-7effe050a000 r-xp 00000000 08:13 8785406                    /usr/lib/rhythmbox/plugins/ipod/libipod.so
7effe050a000-7effe070a000 ---p 00011000 08:13 8785406                    /usr/lib/rhythmbox/plugins/ipod/libipod.so
7effe070a000-7effe070b000 r--p 00011000 08:13 8785406                    /usr/lib/rhythmbox/plugins/ipod/libipod.so
7effe070b000-7effe070c000 rw-p 00012000 08:13 8785406                    /usr/lib/rhythmbox/plugins/ipod/libipod.so
7effe070c000-7effe0719000 r-xp 00000000 08:13 5122768                    /usr/lib/python2.6/lib-dynload/pyexpat.so
7effe0719000-7effe0918000 ---p 0000d000 08:13 5122768                    /usr/lib/python2.6/lib-dynload/pyexpat.so
7effe0918000-7effe0919000 r--p 0000c000 08:13 5122768                    /usr/lib/python2.6/lib-dynload/pyexpat.so
7effe0919000-7effe091b000 rw-p 0000d000 08:13 5122768                    /usr/lib/python2.6/lib-dynload/pyexpat.so
7effe091b000-7effe2bc5000 r--p 00000000 08:13 5273507                    /usr/share/icons/gnome/icon-theme.cache
7effe2bc5000-7effe2be8000 r-xp 00000000 08:13 4981405                    /usr/lib/libbrasero-media.so.1.2.0
7effe2be8000-7effe2de8000 ---p 00023000 08:13 4981405                    /usr/lib/libbrasero-media.so.1.2.0
7effe2de8000-7effe2de9000 r--p 00023000 08:13 4981405                    /usr/lib/libbrasero-media.so.1.2.0
7effe2de9000-7effe2dea000 rw-p 00024000 08:13 4981405                    /usr/lib/libbrasero-media.so.1.2.0
7effe2dea000-7effe2def000 r-xp 00000000 08:13 8785332                    /usr/lib/rhythmbox/plugins/cd-recorder/libcd-recorder.so
7effe2def000-7effe2fee000 ---p 00005000 08:13 8785332                    /usr/lib/rhythmbox/plugins/cd-recorder/libcd-recorder.so
7effe2fee000-7effe2fef000 r--p 00004000 08:13 8785332                    /usr/lib/rhythmbox/plugins/cd-recorder/libcd-recorder.so
7effe2fef000-7effe2ff0000 rw-p 00005000 08:13 8785332                    /usr/lib/rhythmbox/plugins/cd-recorder/libcd-recorder.so
7effe2ff0000-7effe3000000 r-xp 00000000 08:13 5112336                    /usr/lib/python2.6/dist-packages/gst-0.10/gst/interfaces.so
7effe3000000-7effe31ff000 ---p 00010000 08:13 5112336                    /usr/lib/python2.6/dist-packages/gst-0.10/gst/interfaces.so
7effe31ff000-7effe3201000 r--p 0000f000 08:13 5112336                    /usr/lib/python2.6/dist-packages/gst-0.10/gst/interfaces.so
7effe3201000-7effe3203000 rw-p 00011000 08:13 5112336                    /usr/lib/python2.6/dist-packages/gst-0.10/gst/interfaces.so
7effe3203000-7effe3207000 r-xp 00000000 08:13 4988521                    /usr/lib/libgstdataprotocol-0.10.so.0.26.0
7effe3207000-7effe3406000 ---p 00004000 08:13 4988521                    /usr/lib/libgstdataprotocol-0.10.so.0.26.0
7effe3406000-7effe3407000 r--p 00003000 08:13 4988521                    /usr/lib/libgstdataprotocol-0.10.so.0.26.0
7effe3407000-7effe3408000 rw-p 00004000 08:13 4988521                    /usr/lib/libgstdataprotocol-0.10.so.0.26.0
7effe3408000-7effe340e000 r-xp 00000000 08:13 4988522                    /usr/lib/libgstnet-0.10.so.0.26.0
7effe340e000-7effe360d000 ---p 00006000 08:13 4988522                    /usr/lib/libgstnet-0.10.so.0.26.0
7effe360d000-7effe360e000 r--p 00005000 08:13 4988522                    /usr/lib/libgstnet-0.10.so.0.26.0
7effe360e000-7effe360f000 rw-p 00006000 08:13 4988522                    /usr/lib/libgstnet-0.10.so.0.26.0
7effe360f000-7effe3692000 r-xp 00000000 08:13 5112335                    /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so
7effe3692000-7effe3891000 ---p 00083000 08:13 5112335                    /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so
7effe3891000-7effe3899000 r--p 00082000 08:13 5112335                    /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so
7effe3899000-7effe38a4000 rw-p 0008a000 08:13 5112335                    /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so
7effe38a4000-7effe38f4000 r-xp 00000000 08:13 5113205                    /usr/lib/pyshared/python2.6/libxml2mod.so
7effe38f4000-7effe3af3000 ---p 00050000 08:13 5113205                    /usr/lib/pyshared/python2.6/libxml2mod.so
7effe3af3000-7effe3af4000 r--p 0004f000 08:13 5113205                    /usr/lib/pyshared/python2.6/libxml2mod.so
7effe3af4000-7effe3afe000 rw-p 00050000 08:13 5113205                    /usr/lib/pyshared/python2.6/libxml2mod.so
7effe3afe000-7effe3b02000 r-xp 00000000 08:13 5135795                    /usr/lib/pyshared/python2.6/gtk-2.0/pangocairo.so
7effe3b02000-7effe3d01000 ---p 00004000 08:13 5135795                    /usr/lib/pyshared/python2.6/gtk-2.0/pangocairo.so
7effe3d01000-7effe3d02000 r--p 00003000 08:13 5135795                    /usr/lib/pyshared/python2.6/gtk-2.0/pangocairo.so
7effe3d02000-7effe3d03000 rw-p 00004000 08:13 5135795                    /usr/lib/pyshared/python2.6/gtk-2.0/pangocairo.so
7effe3d03000-7effe3d27000 r--p 00000000 08:13 4987518                    /usr/lib/girepository-1.0/GLib-2.0.typelib
7effe3d27000-7effe3d68000 rw-p 00000000 00:00 0 
7effe3d68000-7effe3d79000 r-xp 00000000 08:13 5121421                    /usr/lib/python2.6/lib-dynload/datetime.so
7effe3d79000-7effe3f79000 ---p 00011000 08:13 5121421                    /usr/lib/python2.6/lib-dynload/datetime.so
7effe3f79000-7effe3f7a000 r--p 00011000 08:13 5121421                    /usr/lib/python2.6/lib-dynload/datetime.so
7effe3f7a000-7effe3f7e000 rw-p 00012000 08:13 5121421                    /usr/lib/python2.6/lib-dynload/datetime.so
7effe3f7e000-7effe3f95000 r-xp 00000000 08:13 4983879                    /usr/lib/libgirepository-1.0.so.1.0.0
7effe3f95000-7effe4194000 ---p 00017000 08:13 4983879                    /usr/lib/libgirepository-1.0.so.1.0.0
7effe4194000-7effe4195000 r--p 00016000 08:13 4983879                    /usr/lib/libgirepository-1.0.so.1.0.0
7effe4195000-7effe4196000 rw-p 00017000 08:13 4983879                    /usr/lib/libgirepository-1.0.so.1.0.0
7effe41b8000-7effe41ca000 r-xp 00000000 08:13 5637256                    /usr/lib/pyshared/python2.6/gtk-2.0/gi/_gi.so
7effe41ca000-7effe43ca000 ---p 00012000 08:13 5637256                    /usr/lib/pyshared/python2.6/gtk-2.0/gi/_gi.so
7effe43ca000-7effe43cb000 r--p 00012000 08:13 5637256                    /usr/lib/pyshared/python2.6/gtk-2.0/gi/_gi.so
7effe43cb000-7effe43ce000 rw-p 00013000 08:13 5637256                    /usr/lib/pyshared/python2.6/gtk-2.0/gi/_gi.so
7effe43ce000-7effe440b000 r-xp 00000000 08:13 5134793                    /usr/lib/pyshared/python2.6/gtk-2.0/atk.so
7effe440b000-7effe460a000 ---p 0003d000 08:13 5134793                    /usr/lib/pyshared/python2.6/gtk-2.0/atk.so
7effe460a000-7effe460d000 r--p 0003c000 08:13 5134793                    /usr/lib/pyshared/python2.6/gtk-2.0/atk.so
7effe460d000-7effe4612000 rw-p 0003f000 08:13 5134793                    /usr/lib/pyshared/python2.6/gtk-2.0/atk.so
7effe4612000-7effe4634000 r-xp 00000000 08:13 5134794                    /usr/lib/pyshared/python2.6/gtk-2.0/pango.so
7effe4634000-7effe4834000 ---p 00022000 08:13 5134794                    /usr/lib/pyshared/python2.6/gtk-2.0/pango.so
7effe4834000-7effe4837000 r--p 00022000 08:13 5134794                    /usr/lib/pyshared/python2.6/gtk-2.0/pango.so
7effe4837000-7effe483c000 rw-p 00025000 08:13 5134794                    /usr/lib/pyshared/python2.6/gtk-2.0/pango.so
7effe483c000-7effe4842000 r-xp 00000000 08:13 5128272                    /usr/lib/pyshared/python2.6/gtk-2.0/gio/unix.so
7effe4842000-7effe4a41000 ---p 00006000 08:13 5128272                    /usr/lib/pyshared/python2.6/gtk-2.0/gio/unix.so
7effe4a41000-7effe4a42000 r--p 00005000 08:13 5128272                    /usr/lib/pyshared/python2.6/gtk-2.0/gio/unix.so
7effe4a42000-7effe4a43000 rw-p 00006000 08:13 5128272                    /usr/lib/pyshared/python2.6/gtk-2.0/gio/unix.so
7effe4a43000-7effe4b04000 rw-p 00000000 00:00 0 
7effe4b04000-7effe4b55000 r-xp 00000000 08:13 5128273                    /usr/lib/pyshared/python2.6/gtk-2.0/gio/_gio.so
7effe4b55000-7effe4d54000 ---p 00051000 08:13 5128273                    /usr/lib/pyshared/python2.6/gtk-2.0/gio/_gio.so
7effe4d54000-7effe4d5a000 r--p 00050000 08:13 5128273                    /usr/lib/pyshared/python2.6/gtk-2.0/gio/_gio.so
7effe4d5a000-7effe4d64000 rw-p 00056000 08:13 5128273                    /usr/lib/pyshared/python2.6/gtk-2.0/gio/_gio.so
7effe4d64000-7effe4da5000 rw-p 00000000 00:00 0 
7effe4da5000-7effe4dba000 r-xp 00000000 08:13 5117567                    /usr/lib/pyshared/python2.6/cairo/_cairo.so
7effe4dba000-7effe4fba000 ---p 00015000 08:13 5117567                    /usr/lib/pyshared/python2.6/cairo/_cairo.so
7effe4fba000-7effe4fbb000 r--p 00015000 08:13 5117567                    /usr/lib/pyshared/python2.6/cairo/_cairo.so
7effe4fbb000-7effe4fc0000 rw-p 00016000 08:13 5117567                    /usr/lib/pyshared/python2.6/cairo/_cairo.so
7effe4fc0000-7effe5203000 r-xp 00000000 08:13 5134791                    /usr/lib/pyshared/python2.6/gtk-2.0/gtk/_gtk.so
7effe5203000-7effe5402000 ---p 00243000 08:13 5134791                    /usr/lib/pyshared/python2.6/gtk-2.0/gtk/_gtk.so
7effe5402000-7effe5426000 r--p 00242000 08:13 5134791                    /usr/lib/pyshared/python2.6/gtk-2.0/gtk/_gtk.so
7effe5426000-7effe5458000 rw-p 00266000 08:13 5134791                    /usr/lib/pyshared/python2.6/gtk-2.0/gtk/_gtk.so
7effe5458000-7effe5478000 r-xp 00000000 08:13 5128274                    /usr/lib/pyshared/python2.6/gtk-2.0/gobject/_gobject.so
7effe5478000-7effe5677000 ---p 00020000 08:13 5128274                    /usr/lib/pyshared/python2.6/gtk-2.0/gobject/_gobject.so
7effe5677000-7effe5678000 r--p 0001f000 08:13 5128274                    /usr/lib/pyshared/python2.6/gtk-2.0/gobject/_gobject.so
7effe5678000-7effe567b000 rw-p 00020000 08:13 5128274                    /usr/lib/pyshared/python2.6/gtk-2.0/gobject/_gobject.so
7effe567b000-7effe56bd000 rw-p 00000000 00:00 0 
7effe56bd000-7effe56c4000 r-xp 00000000 08:13 4980984                    /usr/lib/libffi.so.5.0.10
7effe56c4000-7effe58c3000 ---p 00007000 08:13 4980984                    /usr/lib/libffi.so.5.0.10
7effe58c3000-7effe58c4000 r--p 00006000 08:13 4980984                    /usr/lib/libffi.so.5.0.10
7effe58c4000-7effe58c5000 rw-p 00007000 08:13 4980984                    /usr/lib/libffi.so.5.0.10
7effe58c5000-7effe58c8000 r-xp 00000000 08:13 4987521                    /usr/lib/libpyglib-2.0-python2.6.so.0.0.0
7effe58c8000-7effe5ac8000 ---p 00003000 08:13 4987521                    /usr/lib/libpyglib-2.0-python2.6.so.0.0.0
7effe5ac8000-7effe5ac9000 r--p 00003000 08:13 4987521                    /usr/lib/libpyglib-2.0-python2.6.so.0.0.0
7effe5ac9000-7effe5aca000 rw-p 00004000 08:13 4987521                    /usr/lib/libpyglib-2.0-python2.6.so.0.0.0
7effe5aca000-7effe5ad9000 r-xp 00000000 08:13 5128271                    /usr/lib/pyshared/python2.6/gtk-2.0/glib/_glib.so
7effe5ad9000-7effe5cd8000 ---p 0000f000 08:13 5128271                    /usr/lib/pyshared/python2.6/gtk-2.0/glib/_glib.so
7effe5cd8000-7effe5cd9000 r--p 0000e000 08:13 5128271                    /usr/lib/pyshared/python2.6/gtk-2.0/glib/_glib.so
7effe5cd9000-7effe5cdc000 rw-p 0000f000 08:13 5128271                    /usr/lib/pyshared/python2.6/gtk-2.0/glib/_glib.so
7effe5cdc000-7effe5d5e000 rw-p 00000000 00:00 0 
7effe5d5e000-7effe5d5f000 ---p 00000000 00:00 0 
7effe5d5f000-7effe655f000 rw-p 00000000 00:00 0 
7effe655f000-7effe6564000 r-xp 00000000 08:13 7478228                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
7effe6564000-7effe6763000 ---p 00005000 08:13 7478228                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
7effe6763000-7effe6764000 r--p 00004000 08:13 7478228                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
7effe6764000-7effe6765000 rw-p 00005000 08:13 7478228                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
7effe6765000-7effe679b000 r-xp 00000000 08:13 4983769                    /usr/lib/libcroco-0.6.so.3.0.1
7effe679b000-7effe699a000 ---p 00036000 08:13 4983769                    /usr/lib/libcroco-0.6.so.3.0.1
7effe699a000-7effe699b000 r--p 00035000 08:13 4983769                    /usr/lib/libcroco-0.6.so.3.0.1
7effe699b000-7effe699e000 rw-p 00036000 08:13 4983769                    /usr/lib/libcroco-0.6.so.3.0.1
7effe699e000-7effe69d1000 r-xp 00000000 08:13 4981186                    /usr/lib/librsvg-2.so.2.32.0
7effe69d1000-7effe6bd1000 ---p 00033000 08:13 4981186                    /usr/lib/librsvg-2.so.2.32.0
7effe6bd1000-7effe6bd2000 r--p 00033000 08:13 4981186                    /usr/lib/librsvg-2.so.2.32.0
7effe6bd2000-7effe6bd3000 rw-p 00034000 08:13 4981186                    /usr/lib/librsvg-2.so.2.32.0
7effe6bd3000-7effe6bd5000 r-xp 00000000 08:13 7478212                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7effe6bd5000-7effe6dd4000 ---p 00002000 08:13 7478212                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7effe6dd4000-7effe6dd5000 r--p 00001000 08:13 7478212                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7effe6dd5000-7effe6dd6000 rw-p 00002000 08:13 7478212                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7effe6dd6000-7effe6dd8000 r-xp 00000000 08:13 5121199                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7effe6dd8000-7effe6fd7000 ---p 00002000 08:13 5121199                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7effe6fd7000-7effe6fd8000 r--p 00001000 08:13 5121199                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7effe6fd8000-7effe6fd9000 rw-p 00002000 08:13 5121199                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7effe6fd9000-7effe6fec000 r-xp 00000000 08:13 4987745                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7effe6fec000-7effe71ec000 ---p 00013000 08:13 4987745                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7effe71ec000-7effe71ed000 r--p 00013000 08:13 4987745                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7effe71ed000-7effe71ee000 rw-p 00014000 08:13 4987745                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7effe71ee000-7effe7204000 r-xp 00000000 08:13 4980976                    /usr/lib/libgvfscommon.so.0.0.0
7effe7204000-7effe7404000 ---p 00016000 08:13 4980976                    /usr/lib/libgvfscommon.so.0.0.0
7effe7404000-7effe7405000 r--p 00016000 08:13 4980976                    /usr/lib/libgvfscommon.so.0.0.0
7effe7405000-7effe7406000 rw-p 00017000 08:13 4980976                    /usr/lib/libgvfscommon.so.0.0.0
7effe7441000-7effe74a1000 rw-s 00000000 00:04 116391964                  /SYSV00000000 (deleted)
7effe74a1000-7effe74ee000 r--p 00000000 08:13 6953218                    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf
7effe74ee000-7effe7506000 r-xp 00000000 08:13 5117554                    /usr/lib/pyshared/python2.6/_dbus_bindings.so
7effe7506000-7effe7706000 ---p 00018000 08:13 5117554                    /usr/lib/pyshared/python2.6/_dbus_bindings.so
7effe7706000-7effe7707000 r--p 00018000 08:13 5117554                    /usr/lib/pyshared/python2.6/_dbus_bindings.so
7effe7707000-7effe7714000 rw-p 00019000 08:13 5117554                    /usr/lib/pyshared/python2.6/_dbus_bindings.so
7effe7714000-7effe7721000 r-xp 00000000 08:13 8785397                    /usr/lib/rhythmbox/plugins/generic-player/libgeneric-player.so
7effe7721000-7effe7920000 ---p 0000d000 08:13 8785397                    /usr/lib/rhythmbox/plugins/generic-player/libgeneric-player.so
7effe7920000-7effe7921000 r--p 0000c000 08:13 8785397                    /usr/lib/rhythmbox/plugins/generic-player/libgeneric-player.so
7effe7921000-7effe7922000 rw-p 0000d000 08:13 8785397                    /usr/lib/rhythmbox/plugins/generic-player/libgeneric-player.so
7effe7922000-7effe7932000 r-xp 00000000 08:13 4983669                    /usr/lib/libdbusmenu-glib.so.1.0.17
7effe7932000-7effe7b32000 ---p 00010000 08:13 4983669                    /usr/lib/libdbusmenu-glib.so.1.0.17
7effe7b32000-7effe7b33000 r--p 00010000 08:13 4983669                    /usr/lib/libdbusmenu-glib.so.1.0.17
7effe7b33000-7effe7b34000 rw-p 00011000 08:13 4983669                    /usr/lib/libdbusmenu-glib.so.1.0.17
7effe7b34000-7effe7df0000 r-xp 00000000 08:13 4981961                    /usr/lib/libvala-0.10.so.0.0.0
7effe7df0000-7effe7ff0000 ---p 002bc000 08:13 4981961                    /usr/lib/libvala-0.10.so.0.0.0
7effe7ff0000-7effe7ffa000 r--p 002bc000 08:13 4981961                    /usr/lib/libvala-0.10.so.0.0.0
7effe7ffa000-7effe7fff000 rw-p 002c6000 08:13 4981961                    /usr/lib/libvala-0.10.so.0.0.0
7effe7fff000-7effe8000000 rw-p 00000000 00:00 0 
7effe8000000-7effe8234000 rw-p 00000000 00:00 0 
7effe8234000-7effec000000 ---p 00000000 00:00 0 
7effec020000-7effec0a2000 rw-p 00000000 00:00 0 
7effec0a2000-7effec0a9000 r--s 00000000 08:13 4987390                    /usr/lib/gconv/gconv-modules.cache
7effec0a9000-7effec0ea000 rw-p 00000000 00:00 0 
7effec0ea000-7effec140000 r--p 00000000 08:13 6953511                    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-I.ttf
7effec140000-7effec15c000 r--s 00000000 08:13 5112465                    /usr/share/mime/mime.cache
7effec15c000-7effec1ab000 r--p 00000000 08:13 5120429                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
7effec1ab000-7effec1d3000 r-xp 00000000 08:13 4987744                    /usr/lib/gio/modules/libgvfsdbus.so
7effec1d3000-7effec3d3000 ---p 00028000 08:13 4987744                    /usr/lib/gio/modules/libgvfsdbus.so
7effec3d3000-7effec3d4000 r--p 00028000 08:13 4987744                    /usr/lib/gio/modules/libgvfsdbus.so
7effec3d4000-7effec3d5000 rw-p 00029000 08:13 4987744                    /usr/lib/gio/modules/libgvfsdbus.so
7effec3e3000-7effec3f2000 r-xp 00000000 08:13 4982081                    /usr/lib/libindicate.so.4.0.3
7effec3f2000-7effec5f1000 ---p 0000f000 08:13 4982081                    /usr/lib/libindicate.so.4.0.3
7effec5f1000-7effec5f2000 r--p 0000e000 08:13 4982081                    /usr/lib/libindicate.so.4.0.3
7effec5f2000-7effec5f3000 rw-p 0000f000 08:13 4982081                    /usr/lib/libindicate.so.4.0.3
7effec5f3000-7effec5f5000 r-xp 00000000 08:13 8785366                    /usr/lib/rhythmbox/plugins/ayatana/libayatana.so
7effec5f5000-7effec7f4000 ---p 00002000 08:13 8785366                    /usr/lib/rhythmbox/plugins/ayatana/libayatana.so
7effec7f4000-7effec7f5000 r--p 00001000 08:13 8785366                    /usr/lib/rhythmbox/plugins/ayatana/libayatana.so
7effec7f5000-7effec7f6000 rw-p 00002000 08:13 8785366                    /usr/lib/rhythmbox/plugins/ayatana/libayatana.so
7effec7f6000-7effec809000 r-xp 00000000 08:13 8785362                    /usr/lib/rhythmbox/plugins/audioscrobbler/libaudioscrobbler.so
7effec809000-7effeca08000 ---p 00013000 08:13 8785362                    /usr/lib/rhythmbox/plugins/audioscrobbler/libaudioscrobbler.so
7effeca08000-7effeca09000 r--p 00012000 08:13 8785362                    /usr/lib/rhythmbox/plugins/audioscrobbler/libaudioscrobbler.so
7effeca09000-7effeca0a000 rw-p 00013000 08:13 8785362                    /usr/lib/rhythmbox/plugins/audioscrobbler/libaudioscrobbler.so
7effeca0a000-7effeca33000 r-xp 00000000 08:13 4984268                    /usr/lib/libmusicbrainz.so.4.0.3
7effeca33000-7effecc32000 ---p 00029000 08:13 4984268                    /usr/lib/libmusicbrainz.so.4.0.3
7effecc32000-7effecc33000 r--p 00028000 08:13 4984268                    /usr/lib/libmusicbrainz.so.4.0.3
7effecc33000-7effecc34000 rw-p 00029000 08:13 4984268                    /usr/lib/libmusicbrainz.so.4.0.3
7effecc34000-7effecc3c000 r-xp 00000000 08:13 4984053                    /usr/lib/libgstcdda-0.10.so.0.21.0
7effecc3c000-7effece3b000 ---p 00008000 08:13 4984053                    /usr/lib/libgstcdda-0.10.so.0.21.0
7effece3b000-7effece3c000 r--p 00007000 08:13 4984053                    /usr/lib/libgstcdda-0.10.so.0.21.0
7effece3c000-7effece3d000 rw-p 00008000 08:13 4984053                    /usr/lib/libgstcdda-0.10.so.0.21.0
7effece5f000-7effece6f000 r-xp 00000000 08:13 8785356                    /usr/lib/rhythmbox/plugins/audiocd/libaudiocd.so
7effece6f000-7effed06e000 ---p 00010000 08:13 8785356                    /usr/lib/rhythmbox/plugins/audiocd/libaudiocd.so
7effed06e000-7effed06f000 r--p 0000f000 08:13 8785356                    /usr/lib/rhythmbox/plugins/audiocd/libaudiocd.so
7effed06f000-7effed070000 rw-p 00010000 08:13 8785356                    /usr/lib/rhythmbox/plugins/audiocd/libaudiocd.so
7effed070000-7effed081000 r-xp 00000000 08:13 5117587                    /usr/lib/pyshared/python2.6/gtk-2.0/gconf.so
7effed081000-7effed280000 ---p 00011000 08:13 5117587                    /usr/lib/pyshared/python2.6/gtk-2.0/gconf.so
7effed280000-7effed282000 r--p 00010000 08:13 5117587                    /usr/lib/pyshared/python2.6/gtk-2.0/gconf.so
7effed282000-7effed284000 rw-p 00012000 08:13 5117587                    /usr/lib/pyshared/python2.6/gtk-2.0/gconf.so
7effed284000-7effede7e000 r--p 00000000 08:13 5249687                    /usr/share/icons/hicolor/icon-theme.cache
7effede7e000-7effede7f000 ---p 00000000 00:00 0 
7effede7f000-7effee67f000 rw-p 00000000 00:00 0 
7effee67f000-7effee680000 ---p 00000000 00:00 0 
7effee680000-7effeee80000 rw-p 00000000 00:00 0 
7effeee80000-7effeee89000 r-xp 00000000 08:13 4982594                    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
7effeee89000-7effef089000 ---p 00009000 08:13 4982594                    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
7effef089000-7effef08a000 r--p 00009000 08:13 4982594                    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
7effef08a000-7effef08b000 rw-p 0000a000 08:13 4982594                    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
7effef08b000-7effef0ba000 r-xp 00000000 08:13 4983467                    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
7effef0ba000-7effef2ba000 ---p 0002f000 08:13 4983467                    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
7effef2ba000-7effef2bb000 r--p 0002f000 08:13 4983467                    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
7effef2bb000-7effef2bc000 rw-p 00030000 08:13 4983467                    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
7effef2bc000-7effef2c1000 r-xp 00000000 08:13 4983580                    /usr/lib/libORBitCosNaming-2.so.0.1.0
7effef2c1000-7effef4c1000 ---p 00005000 08:13 4983580                    /usr/lib/libORBitCosNaming-2.so.0.1.0
7effef4c1000-7effef4c2000 r--p 00005000 08:13 4983580                    /usr/lib/libORBitCosNaming-2.so.0.1.0
7effef4c2000-7effef4c3000 rw-p 00006000 08:13 4983580                    /usr/lib/libORBitCosNaming-2.so.0.1.0
7effef4c3000-7effef4d9000 r-xp 00000000 08:13 4982908                    /usr/lib/libbonobo-activation.so.4.0.0
7effef4d9000-7effef6d9000 ---p 00016000 08:13 4982908                    /usr/lib/libbonobo-activation.so.4.0.0
7effef6d9000-7effef6db000 r--p 00016000 08:13 4982908                    /usr/lib/libbonobo-activation.so.4.0.0
7effef6db000-7effef6dd000 rw-p 00018000 08:13 4982908                    /usr/lib/libbonobo-activation.so.4.0.0
7effef6dd000-7effef73f000 r-xp 00000000 08:13 4982851                    /usr/lib/libbonobo-2.so.0.0.0
7effef73f000-7effef93f000 ---p 00062000 08:13 4982851                    /usr/lib/libbonobo-2.so.0.0.0
7effef93f000-7effef945000 r--p 00062000 08:13 4982851                    /usr/lib/libbonobo-2.so.0.0.0
7effef945000-7effef950000 rw-p 00068000 08:13 4982851                    /usr/lib/libbonobo-2.so.0.0.0
7effef950000-7effef9a4000 r-xp 00000000 08:13 4983608                    /usr/lib/libspi.so.0.10.11
7effef9a4000-7effefba3000 ---p 00054000 08:13 4983608                    /usr/lib/libspi.so.0.10.11
7effefba3000-7effefba8000 r--p 00053000 08:13 4983608                    /usr/lib/libspi.so.0.10.11
7effefba8000-7effefbb4000 rw-p 00058000 08:13 4983608                    /usr/lib/libspi.so.0.10.11
7effefbb4000-7effefbbb000 r-xp 00000000 08:13 4988020                    /usr/lib/gtk-2.0/modules/libatk-bridge.so
7effefbbb000-7effefdba000 ---p 00007000 08:13 4988020                    /usr/lib/gtk-2.0/modules/libatk-bridge.so
7effefdba000-7effefdbb000 r--p 00006000 08:13 4988020                    /usr/lib/gtk-2.0/modules/libatk-bridge.so
7effefdbb000-7effefdbc000 rw-p 00007000 08:13 4988020                    /usr/lib/gtk-2.0/modules/libatk-bridge.so
7effefdbc000-7effefe06000 r-xp 00000000 08:13 4982591                    /usr/lib/gtk-2.0/modules/libgail.so
7effefe06000-7efff0005000 ---p 0004a000 08:13 4982591                    /usr/lib/gtk-2.0/modules/libgail.so
7efff0005000-7efff0006000 r--p 00049000 08:13 4982591                    /usr/lib/gtk-2.0/modules/libgail.so
7efff0006000-7efff0008000 rw-p 0004a000 08:13 4982591                    /usr/lib/gtk-2.0/modules/libgail.so
7efff0008000-7efff0010000 r-xp 00000000 08:13 4984231                    /usr/lib/libltdl.so.7.2.1
7efff0010000-7efff0210000 ---p 00008000 08:13 4984231                    /usr/lib/libltdl.so.7.2.1
7efff0210000-7efff0211000 r--p 00008000 08:13 4984231                    /usr/lib/libltdl.so.7.2.1
7efff0211000-7efff0212000 rw-p 00009000 08:13 4984231                    /usr/lib/libltdl.so.7.2.1
7efff0212000-7efff0220000 r-xp 00000000 08:13 4983945                    /usr/lib/libtdb.so.1.2.1
7efff0220000-7efff041f000 ---p 0000e000 08:13 4983945                    /usr/lib/libtdb.so.1.2.1
7efff041f000-7efff0420000 r--p 0000d000 08:13 4983945                    /usr/lib/libtdb.so.1.2.1
7efff0420000-7efff0421000 rw-p 0000e000 08:13 4983945                    /usr/lib/libtdb.so.1.2.1
7efff0421000-7efff0427000 r-xp 00000000 08:13 4983886                    /usr/lib/libogg.so.0.7.0
7efff0427000-7efff0626000 ---p 00006000 08:13 4983886                    /usr/lib/libogg.so.0.7.0
7efff0626000-7efff0627000 r--p 00005000 08:13 4983886                    /usr/lib/libogg.so.0.7.0
7efff0627000-7efff0628000 rw-p 00006000 08:13 4983886                    /usr/lib/libogg.so.0.7.0
7efff0628000-7efff0653000 r-xp 00000000 08:13 4984405                    /usr/lib/libvorbis.so.0.4.4
7efff0653000-7efff0852000 ---p 0002b000 08:13 4984405                    /usr/lib/libvorbis.so.0.4.4
7efff0852000-7efff0853000 r--p 0002a000 08:13 4984405                    /usr/lib/libvorbis.so.0.4.4
7efff0853000-7efff0854000 rw-p 0002b000 08:13 4984405                    /usr/lib/libvorbis.so.0.4.4
7efff0854000-7efff085b000 r-xp 00000000 08:13 4984411                    /usr/lib/libvorbisfile.so.3.3.2
7efff085b000-7efff0a5a000 ---p 00007000 08:13 4984411                    /usr/lib/libvorbisfile.so.3.3.2
7efff0a5a000-7efff0a5b000 r--p 00006000 08:13 4984411                    /usr/lib/libvorbisfile.so.3.3.2
7efff0a5b000-7efff0a5c000 rw-p 00007000 08:13 4984411                    /usr/lib/libvorbisfile.so.3.3.2
7efff0a5c000-7efff0a6b000 r-xp 00000000 08:13 4984554                    /usr/lib/libcanberra.so.0.2.4
7efff0a6b000-7efff0c6a000 ---p 0000f000 08:13 4984554                    /usr/lib/libcanberra.so.0.2.4
7efff0c6a000-7efff0c6b000 r--p 0000e000 08:13 4984554                    /usr/lib/libcanberra.so.0.2.4
7efff0c6b000-7efff0c6c000 rw-p 0000f000 08:13 4984554                    /usr/lib/libcanberra.so.0.2.4
7efff0c6c000-7efff0c70000 r-xp 00000000 08:13 4983429                    /usr/lib/libcanberra-gtk.so.0.1.6
7efff0c70000-7efff0e6f000 ---p 00004000 08:13 4983429                    /usr/lib/libcanberra-gtk.so.0.1.6
7efff0e6f000-7efff0e70000 r--p 00003000 08:13 4983429                    /usr/lib/libcanberra-gtk.so.0.1.6
7efff0e70000-7efff0e71000 rw-p 00004000 08:13 4983429                    /usr/lib/libcanberra-gtk.so.0.1.6
7efff0e71000-7efff0e76000 r-xp 00000000 08:13 4987922                    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
7efff0e76000-7efff1076000 ---p 00005000 08:13 4987922                    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
7efff1076000-7efff1077000 r--p 00005000 08:13 4987922                    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
7efff1077000-7efff1078000 rw-p 00006000 08:13 4987922                    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
7efff1078000-7efff1084000 r-xp 00000000 08:13 10357753                   /lib/libnss_files-2.12.1.so
7efff1084000-7efff1283000 ---p 0000c000 08:13 10357753                   /lib/libnss_files-2.12.1.so
7efff1283000-7efff1284000 r--p 0000b000 08:13 10357753                   /lib/libnss_files-2.12.1.so
7efff1284000-7efff1285000 rw-p 0000c000 08:13 10357753                   /lib/libnss_files-2.12.1.so
7efff1285000-7efff128f000 r-xp 00000000 08:13 10357758                   /lib/libnss_nis-2.12.1.so
7efff128f000-7efff148e000 ---p 0000a000 08:13 10357758                   /lib/libnss_nis-2.12.1.so
7efff148e000-7efff148f000 r--p 00009000 08:13 10357758                   /lib/libnss_nis-2.12.1.so
7efff148f000-7efff1490000 rw-p 0000a000 08:13 10357758                   /lib/libnss_nis-2.12.1.so
7efff1490000-7efff1498000 r-xp 00000000 08:13 10357751                   /lib/libnss_compat-2.12.1.so
7efff1498000-7efff1697000 ---p 00008000 08:13 10357751                   /lib/libnss_compat-2.12.1.so
7efff1697000-7efff1698000 r--p 00007000 08:13 10357751                   /lib/libnss_compat-2.12.1.so
7efff1698000-7efff1699000 rw-p 00008000 08:13 10357751                   /lib/libnss_compat-2.12.1.so
7efff1699000-7efff193d000 r--p 00000000 08:13 4984542                    /usr/lib/locale/locale-archive
7efff193d000-7efff1952000 r-xp 00000000 08:13 10357036                   /lib/libgcc_s.so.1
7efff1952000-7efff1b51000 ---p 00015000 08:13 10357036                   /lib/libgcc_s.so.1
7efff1b51000-7efff1b52000 r--p 00014000 08:13 10357036                   /lib/libgcc_s.so.1
7efff1b52000-7efff1b53000 rw-p 00015000 08:13 10357036                   /lib/libgcc_s.so.1
7efff1b53000-7efff2a98000 r--p 00000000 08:13 4984154                    /usr/lib/libicudata.so.42.1
7efff2a98000-7efff2c97000 ---p 00f45000 08:13 4984154                    /usr/lib/libicudata.so.42.1
7efff2c97000-7efff2c98000 r--p 00f44000 08:13 4984154                    /usr/lib/libicudata.so.42.1
7efff2c98000-7efff2c9b000 r-xp 00000000 08:13 10357065                   /lib/libgpg-error.so.0.4.0
7efff2c9b000-7efff2e9a000 ---p 00003000 08:13 10357065                   /lib/libgpg-error.so.0.4.0
7efff2e9a000-7efff2e9b000 r--p 00002000 08:13 10357065                   /lib/libgpg-error.so.0.4.0
7efff2e9b000-7efff2e9c000 rw-p 00003000 08:13 10357065                   /lib/libgpg-error.so.0.4.0
7efff2e9c000-7efff2eac000 r-xp 00000000 08:13 4981033                    /usr/lib/libtasn1.so.3.1.9
7efff2eac000-7efff30ab000 ---p 00010000 08:13 4981033                    /usr/lib/libtasn1.so.3.1.9
7efff30ab000-7efff30ac000 r--p 0000f000 08:13 4981033                    /usr/lib/libtasn1.so.3.1.9
7efff30ac000-7efff30ad000 rw-p 00010000 08:13 4981033                    /usr/lib/libtasn1.so.3.1.9
7efff30ad000-7efff30b2000 r-xp 00000000 08:13 4983095                    /usr/lib/libXdmcp.so.6.0.0
7efff30b2000-7efff32b1000 ---p 00005000 08:13 4983095                    /usr/lib/libXdmcp.so.6.0.0
7efff32b1000-7efff32b2000 r--p 00004000 08:13 4983095                    /usr/lib/libXdmcp.so.6.0.0
7efff32b2000-7efff32b3000 rw-p 00005000 08:13 4983095                    /usr/lib/libXdmcp.so.6.0.0
7efff32b3000-7efff32b5000 r-xp 00000000 08:13 4982584                    /usr/lib/libXau.so.6.0.0
7efff32b5000-7efff34b4000 ---p 00002000 08:13 4982584                    /usr/lib/libXau.so.6.0.0
7efff34b4000-7efff34b5000 r--p 00001000 08:13 4982584                    /usr/lib/libXau.so.6.0.0
7efff34b5000-7efff34b6000 rw-p 00002000 08:13 4982584                    /usr/lib/libXau.so.6.0.0
7efff34b6000-7efff34cd000 r-xp 00000000 08:13 10357750                   /lib/libnsl-2.12.1.so
7efff34cd000-7efff36cc000 ---p 00017000 08:13 10357750                   /lib/libnsl-2.12.1.so
7efff36cc000-7efff36cd000 r--p 00016000 08:13 10357750                   /lib/libnsl-2.12.1.so
7efff36cd000-7efff36ce000 rw-p 00017000 08:13 10357750                   /lib/libnsl-2.12.1.so
7efff36ce000-7efff36d0000 rw-p 00000000 00:00 0 
7efff36d0000-7efff37b8000 r-xp 00000000 08:13 4982493                    /usr/lib/libstdc++.so.6.0.14
7efff37b8000-7efff39b7000 ---p 000e8000 08:13 4982493                    /usr/lib/libstdc++.so.6.0.14
7efff39b7000-7efff39bf000 r--p 000e7000 08:13 4982493                    /usr/lib/libstdc++.so.6.0.14
7efff39bf000-7efff39c1000 rw-p 000ef000 08:13 4982493                    /usr/lib/libstdc++.so.6.0.14
7efff39c1000-7efff39d6000 rw-p 00000000 00:00 0 
7efff39d6000-7efff3a34000 r-xp 00000000 08:13 4983629                    /usr/lib/libXt.so.6.0.0
7efff3a34000-7efff3c34000 ---p 0005e000 08:13 4983629                    /usr/lib/libXt.so.6.0.0
7efff3c34000-7efff3c35000 r--p 0005e000 08:13 4983629                    /usr/lib/libXt.so.6.0.0
7efff3c35000-7efff3c3a000 rw-p 0005f000 08:13 4983629                    /usr/lib/libXt.so.6.0.0
7efff3c3a000-7efff3c3b000 rw-p 00000000 00:00 0 
7efff3c3b000-7efff3d83000 r-xp 00000000 08:13 4984166                    /usr/lib/libicuuc.so.42.1
7efff3d83000-7efff3f83000 ---p 00148000 08:13 4984166                    /usr/lib/libicuuc.so.42.1
7efff3f83000-7efff3f91000 r--p 00148000 08:13 4984166                    /usr/lib/libicuuc.so.42.1
7efff3f91000-7efff3f94000 rw-p 00156000 08:13 4984166                    /usr/lib/libicuuc.so.42.1
7efff3f94000-7efff3f96000 rw-p 00000000 00:00 0 
7efff3f96000-7efff4140000 r-xp 00000000 08:13 4984156                    /usr/lib/libicui18n.so.42.1
7efff4140000-7efff4340000 ---p 001aa000 08:13 4984156                    /usr/lib/libicui18n.so.42.1
7efff4340000-7efff434a000 r--p 001aa000 08:13 4984156                    /usr/lib/libicui18n.so.42.1
7efff434a000-7efff434d000 rw-p 001b4000 08:13 4984156                    /usr/lib/libicui18n.so.42.1
7efff434d000-7efff434e000 rw-p 00000000 00:00 0 
7efff434e000-7efff4387000 r-xp 00000000 08:13 4983789                    /usr/lib/libxslt.so.1.1.26
7efff4387000-7efff4586000 ---p 00039000 08:13 4983789                    /usr/lib/libxslt.so.1.1.26
7efff4586000-7efff4587000 r--p 00038000 08:13 4983789                    /usr/lib/libxslt.so.1.1.26
7efff4587000-7efff4588000 rw-p 00039000 08:13 4983789                    /usr/lib/libxslt.so.1.1.26
7efff4588000-7efff45ab000 r-xp 00000000 08:13 4981175                    /usr/lib/libjpeg.so.62.0.0
7efff45ab000-7efff47aa000 ---p 00023000 08:13 4981175                    /usr/lib/libjpeg.so.62.0.0
7efff47aa000-7efff47ab000 r--p 00022000 08:13 4981175                    /usr/lib/libjpeg.so.62.0.0
7efff47ab000-7efff47ac000 rw-p 00023000 08:13 4981175                    /usr/lib/libjpeg.so.62.0.0
7efff47ac000-7efff47b3000 r-xp 00000000 08:13 4988525                    /usr/lib/libgstvideo-0.10.so.0.21.0
7efff47b3000-7efff49b3000 ---p 00007000 08:13 4988525                    /usr/lib/libgstvideo-0.10.so.0.21.0
7efff49b3000-7efff49b4000 r--p 00007000 08:13 4988525                    /usr/lib/libgstvideo-0.10.so.0.21.0
7efff49b4000-7efff49b5000 rw-p 00008000 08:13 4988525                    /usr/lib/libgstvideo-0.10.so.0.21.0
7efff49b5000-7efff49bf000 r-xp 00000000 08:13 4984049                    /usr/lib/libgstapp-0.10.so.0.21.0
7efff49bf000-7efff4bbf000 ---p 0000a000 08:13 4984049                    /usr/lib/libgstapp-0.10.so.0.21.0
7efff4bbf000-7efff4bc0000 r--p 0000a000 08:13 4984049                    /usr/lib/libgstapp-0.10.so.0.21.0
7efff4bc0000-7efff4bc1000 rw-p 0000b000 08:13 4984049                    /usr/lib/libgstapp-0.10.so.0.21.0
7efff4bc1000-7efff4bc8000 r-xp 00000000 08:13 4982592                    /usr/lib/libgailutil.so.18.0.1
7efff4bc8000-7efff4dc7000 ---p 00007000 08:13 4982592                    /usr/lib/libgailutil.so.18.0.1
7efff4dc7000-7efff4dc8000 r--p 00006000 08:13 4982592                    /usr/lib/libgailutil.so.18.0.1
7efff4dc8000-7efff4dc9000 rw-p 00007000 08:13 4982592                    /usr/lib/libgailutil.so.18.0.1
7efff4dc9000-7efff4dd3000 r-xp 00000000 08:13 4984141                    /usr/lib/libenchant.so.1.6.0
7efff4dd3000-7efff4fd2000 ---p 0000a000 08:13 4984141                    /usr/lib/libenchant.so.1.6.0
7efff4fd2000-7efff4fd3000 r--p 00009000 08:13 4984141                    /usr/lib/libenchant.so.1.6.0
7efff4fd3000-7efff4fd4000 rw-p 0000a000 08:13 4984141                    /usr/lib/libenchant.so.1.6.0
7efff4fd4000-7efff4fd8000 r-xp 00000000 08:13 10357167                   /lib/libuuid.so.1.3.0
7efff4fd8000-7efff51d7000 ---p 00004000 08:13 10357167                   /lib/libuuid.so.1.3.0
7efff51d7000-7efff51d8000 r--p 00003000 08:13 10357167                   /lib/libuuid.so.1.3.0
7efff51d8000-7efff51d9000 rw-p 00004000 08:13 10357167                   /lib/libuuid.so.1.3.0
7efff51d9000-7efff533c000 r-xp 00000000 08:13 10355113                   /lib/libcrypto.so.0.9.8
7efff533c000-7efff553c000 ---p 00163000 08:13 10355113                   /lib/libcrypto.so.0.9.8
7efff553c000-7efff5549000 r--p 00163000 08:13 10355113                   /lib/libcrypto.so.0.9.8
7efff5549000-7efff5562000 rw-p 00170000 08:13 10355113                   /lib/libcrypto.so.0.9.8
7efff5562000-7efff5565000 rw-p 00000000 00:00 0 
7efff5565000-7efff55b0000 r-xp 00000000 08:13 10355485                   /lib/libssl.so.0.9.8
7efff55b0000-7efff57af000 ---p 0004b000 08:13 10355485                   /lib/libssl.so.0.9.8
7efff57af000-7efff57b1000 r--p 0004a000 08:13 10355485                   /lib/libssl.so.0.9.8
7efff57b1000-7efff57b7000 rw-p 0004c000 08:13 10355485                   /lib/libssl.so.0.9.8
7efff57b7000-7efff57d3000 r-xp 00000000 08:13 10361640                   /lib/libselinux.so.1
7efff57d3000-7efff59d2000 ---p 0001c000 08:13 10361640                   /lib/libselinux.so.1
7efff59d2000-7efff59d3000 r--p 0001b000 08:13 10361640                   /lib/libselinux.so.1
7efff59d3000-7efff59d4000 rw-p 0001c000 08:13 10361640                   /lib/libselinux.so.1
7efff59d4000-7efff59d5000 rw-p 00000000 00:00 0 
7efff59d5000-7efff59eb000 r-xp 00000000 08:13 10357766                   /lib/libresolv-2.12.1.so
7efff59eb000-7efff5bea000 ---p 00016000 08:13 10357766                   /lib/libresolv-2.12.1.so
7efff5bea000-7efff5beb000 r--p 00015000 08:13 10357766                   /lib/libresolv-2.12.1.so
7efff5beb000-7efff5bec000 rw-p 00016000 08:13 10357766                   /lib/libresolv-2.12.1.so
7efff5bec000-7efff5bee000 rw-p 00000000 00:00 0 
7efff5bee000-7efff5c1e000 r-xp 00000000 08:13 10357590                   /lib/libpcre.so.3.12.1
7efff5c1e000-7efff5e1d000 ---p 00030000 08:13 10357590                   /lib/libpcre.so.3.12.1
7efff5e1d000-7efff5e1e000 r--p 0002f000 08:13 10357590                   /lib/libpcre.so.3.12.1
7efff5e1e000-7efff5e1f000 rw-p 00030000 08:13 10357590                   /lib/libpcre.so.3.12.1
7efff5e1f000-7efff5e3c000 r-xp 00000000 08:13 4981277                    /usr/lib/libgnome-keyring.so.0.1.1
7efff5e3c000-7efff603b000 ---p 0001d000 08:13 4981277                    /usr/lib/libgnome-keyring.so.0.1.1
7efff603b000-7efff603c000 r--p 0001c000 08:13 4981277                    /usr/lib/libgnome-keyring.so.0.1.1
7efff603c000-7efff603d000 rw-p 0001d000 08:13 4981277                    /usr/lib/libgnome-keyring.so.0.1.1
7efff603d000-7efff60cf000 r-xp 00000000 08:13 4985857                    /usr/lib/libsqlite3.so.0.8.6
7efff60cf000-7efff62ce000 ---p 00092000 08:13 4985857                    /usr/lib/libsqlite3.so.0.8.6
7efff62ce000-7efff62d0000 r--p 00091000 08:13 4985857                    /usr/lib/libsqlite3.so.0.8.6
7efff62d0000-7efff62d2000 rw-p 00093000 08:13 4985857                    /usr/lib/libsqlite3.so.0.8.6
7efff62d2000-7efff62d9000 r-xp 00000000 08:13 4984389                    /usr/lib/libproxy.so.0.0.0
7efff62d9000-7efff64d8000 ---p 00007000 08:13 4984389                    /usr/lib/libproxy.so.0.0.0
7efff64d8000-7efff64d9000 r--p 00006000 08:13 4984389                    /usr/lib/libproxy.so.0.0.0
7efff64d9000-7efff64da000 rw-p 00007000 08:13 4984389                    /usr/lib/libproxy.so.0.0.0
7efff64da000-7efff654e000 r-xp 00000000 08:13 10357023                   /lib/libgcrypt.so.11.5.3
7efff654e000-7efff674e000 ---p 00074000 08:13 10357023                   /lib/libgcrypt.so.11.5.3
7efff674e000-7efff674f000 r--p 00074000 08:13 10357023                   /lib/libgcrypt.so.11.5.3
7efff674f000-7efff6752000 rw-p 00075000 08:13 10357023                   /lib/libgcrypt.so.11.5.3
7efff6752000-7efff67ed000 r-xp 00000000 08:13 4981299                    /usr/lib/libgnutls.so.26.14.12
7efff67ed000-7efff69ed000 ---p 0009b000 08:13 4981299                    /usr/lib/libgnutls.so.26.14.12
7efff69ed000-7efff69f3000 r--p 0009b000 08:13 4981299                    /usr/lib/libgnutls.so.26.14.12
7efff69f3000-7efff69f4000 rw-p 000a1000 08:13 4981299                    /usr/lib/libgnutls.so.26.14.12
7efff69f4000-7efff6a1a000 r-xp 00000000 08:13 10357052                   /lib/libexpat.so.1.5.2
7efff6a1a000-7efff6c1a000 ---p 00026000 08:13 10357052                   /lib/libexpat.so.1.5.2
7efff6c1a000-7efff6c1c000 r--p 00026000 08:13 10357052                   /lib/libexpat.so.1.5.2
7efff6c1c000-7efff6c1d000 rw-p 00028000 08:13 10357052                   /lib/libexpat.so.1.5.2
7efff6c1d000-7efff6c38000 r-xp 00000000 08:13 4983136                    /usr/lib/libxcb.so.1.1.0
7efff6c38000-7efff6e38000 ---p 0001b000 08:13 4983136                    /usr/lib/libxcb.so.1.1.0
7efff6e38000-7efff6e39000 r--p 0001b000 08:13 4983136                    /usr/lib/libxcb.so.1.1.0
7efff6e39000-7efff6e3a000 rw-p 0001c000 08:13 4983136                    /usr/lib/libxcb.so.1.1.0
7efff6e3a000-7efff6e41000 r-xp 00000000 08:13 4983154                    /usr/lib/libxcb-render.so.0.0.0
7efff6e41000-7efff7041000 ---p 00007000 08:13 4983154                    /usr/lib/libxcb-render.so.0.0.0
7efff7041000-7efff7042000 r--p 00007000 08:13 4983154                    /usr/lib/libxcb-render.so.0.0.0
7efff7042000-7efff7043000 rw-p 00008000 08:13 4983154                    /usr/lib/libxcb-render.so.0.0.0
7efff7043000-7efff7045000 r-xp 00000000 08:13 4983156                    /usr/lib/libxcb-shm.so.0.0.0
7efff7045000-7efff7244000 ---p 00002000 08:13 4983156                    /usr/lib/libxcb-shm.so.0.0.0
7efff7244000-7efff7245000 r--p 00001000 08:13 4983156                    /usr/lib/libxcb-shm.so.0.0.0
7efff7245000-7efff7246000 rw-p 00002000 08:13 4983156                    /usr/lib/libxcb-shm.so.0.0.0
7efff7246000-7efff72a1000 r-xp 00000000 08:13 4980887                    /usr/lib/libpixman-1.so.0.18.4
7efff72a1000-7efff74a0000 ---p 0005b000 08:13 4980887                    /usr/lib/libpixman-1.so.0.18.4
7efff74a0000-7efff74a4000 r--p 0005a000 08:13 4980887                    /usr/lib/libpixman-1.so.0.18.4
7efff74a4000-7efff74a5000 rw-p 0005e000 08:13 4980887                    /usr/lib/libpixman-1.so.0.18.4
7efff74a5000-7efff74aa000 r-xp 00000000 08:13 4982470                    /usr/lib/libXfixes.so.3.1.0
7efff74aa000-7efff76a9000 ---p 00005000 08:13 4982470                    /usr/lib/libXfixes.so.3.1.0
7efff76a9000-7efff76aa000 r--p 00004000 08:13 4982470                    /usr/lib/libXfixes.so.3.1.0
7efff76aa000-7efff76ab000 rw-p 00005000 08:13 4982470                    /usr/lib/libXfixes.so.3.1.0
7efff76ab000-7efff76ad000 r-xp 00000000 08:13 4982476                    /usr/lib/libXdamage.so.1.1.0
7efff76ad000-7efff78ac000 ---p 00002000 08:13 4982476                    /usr/lib/libXdamage.so.1.1.0
7efff78ac000-7efff78ad000 r--p 00001000 08:13 4982476                    /usr/lib/libXdamage.so.1.1.0
7efff78ad000-7efff78ae000 rw-p 00002000 08:13 4982476                    /usr/lib/libXdamage.so.1.1.0
7efff78ae000-7efff78b0000 r-xp 00000000 08:13 4982472                    /usr/lib/libXcomposite.so.1.0.0
7efff78b0000-7efff7aaf000 ---p 00002000 08:13 4982472                    /usr/lib/libXcomposite.so.1.0.0
7efff7aaf000-7efff7ab0000 r--p 00001000 08:13 4982472                    /usr/lib/libXcomposite.so.1.0.0
7efff7ab0000-7efff7ab1000 rw-p 00002000 08:13 4982472                    /usr/lib/libXcomposite.so.1.0.0
7efff7ab1000-7efff7be2000 r-xp 00000000 08:13 4983152                    /usr/lib/libX11.so.6.3.0
7efff7be2000-7efff7de2000 ---p 00131000 08:13 4983152                    /usr/lib/libX11.so.6.3.0
7efff7de2000-7efff7de3000 r--p 00131000 08:13 4983152                    /usr/lib/libX11.so.6.3.0
7efff7de3000-7efff7de7000 rw-p 00132000 08:13 4983152                    /usr/lib/libX11.so.6.3.0
7efff7de7000-7efff7df0000 r-xp 00000000 08:13 4982474                    /usr/lib/libXcursor.so.1.0.2
7efff7df0000-7efff7fef000 ---p 00009000 08:13 4982474                    /usr/lib/libXcursor.so.1.0.2
7efff7fef000-7efff7ff0000 r--p 00008000 08:13 4982474                    /usr/lib/libXcursor.so.1.0.2
7efff7ff0000-7efff7ff1000 rw-p 00009000 08:13 4982474                    /usr/lib/libXcursor.so.1.0.2
7efff7ff1000-7efff7ff9000 r-xp 00000000 08:13 4983623                    /usr/lib/libXrandr.so.2.2.0
7efff7ff9000-7efff81f8000 ---p 00008000 08:13 4983623                    /usr/lib/libXrandr.so.2.2.0
7efff81f8000-7efff81f9000 r--p 00007000 08:13 4983623                    /usr/lib/libXrandr.so.2.2.0
7efff81f9000-7efff81fa000 rw-p 00008000 08:13 4983623                    /usr/lib/libXrandr.so.2.2.0
7efff81fa000-7efff8208000 r-xp 00000000 08:13 4982478                    /usr/lib/libXi.so.6.1.0
7efff8208000-7efff8408000 ---p 0000e000 08:13 4982478                    /usr/lib/libXi.so.6.1.0
7efff8408000-7efff8409000 r--p 0000e000 08:13 4982478                    /usr/lib/libXi.so.6.1.0
7efff8409000-7efff840a000 rw-p 0000f000 08:13 4982478                    /usr/lib/libXi.so.6.1.0
7efff840a000-7efff840c000 r-xp 00000000 08:13 4982480                    /usr/lib/libXinerama.so.1.0.0
7efff840c000-7efff860b000 ---p 00002000 08:13 4982480                    /usr/lib/libXinerama.so.1.0.0
7efff860b000-7efff860c000 r--p 00001000 08:13 4982480                    /usr/lib/libXinerama.so.1.0.0
7efff860c000-7efff860d000 rw-p 00002000 08:13 4982480                    /usr/lib/libXinerama.so.1.0.0
7efff860d000-7efff8616000 r-xp 00000000 08:13 4983158                    /usr/lib/libXrender.so.1.3.0
7efff8616000-7efff8815000 ---p 00009000 08:13 4983158                    /usr/lib/libXrender.so.1.3.0
7efff8815000-7efff8816000 r--p 00008000 08:13 4983158                    /usr/lib/libXrender.so.1.3.0
7efff8816000-7efff8817000 rw-p 00009000 08:13 4983158                    /usr/lib/libXrender.so.1.3.0
7efff8817000-7efff8828000 r-xp 00000000 08:13 4982466                    /usr/lib/libXext.so.6.4.0
7efff8828000-7efff8a27000 ---p 00011000 08:13 4982466                    /usr/lib/libXext.so.6.4.0
7efff8a27000-7efff8a28000 r--p 00010000 08:13 4982466                    /usr/lib/libXext.so.6.4.0
7efff8a28000-7efff8a29000 rw-p 00011000 08:13 4982466                    /usr/lib/libXext.so.6.4.0
7efff8a29000-7efff8a85000 r-xp 00000000 08:13 4983576                    /usr/lib/libORBit-2.so.0.1.0
7efff8a85000-7efff8c85000 ---p 0005c000 08:13 4983576                    /usr/lib/libORBit-2.so.0.1.0
7efff8c85000-7efff8c94000 r--p 0005c000 08:13 4983576                    /usr/lib/libORBit-2.so.0.1.0
7efff8c94000-7efff8c97000 rw-p 0006b000 08:13 4983576                    /usr/lib/libORBit-2.so.0.1.0
7efff8c97000-7efff8ce4000 r-xp 00000000 08:13 4983959                    /usr/lib/libgmime-2.4.so.2.4.14
7efff8ce4000-7efff8ee3000 ---p 0004d000 08:13 4983959                    /usr/lib/libgmime-2.4.so.2.4.14
7efff8ee3000-7efff8ee7000 r--p 0004c000 08:13 4983959                    /usr/lib/libgmime-2.4.so.2.4.14
7efff8ee7000-7efff8efb000 rw-p 00050000 08:13 4983959                    /usr/lib/libgmime-2.4.so.2.4.14
7efff8efb000-7efff8efc000 rw-p 00000000 00:00 0 
7efff8efc000-7efff8efe000 r-xp 00000000 08:13 10357775                   /lib/libutil-2.12.1.so
7efff8efe000-7efff90fd000 ---p 00002000 08:13 10357775                   /lib/libutil-2.12.1.so
7efff90fd000-7efff90fe000 r--p 00001000 08:13 10357775                   /lib/libutil-2.12.1.so
7efff90fe000-7efff90ff000 rw-p 00002000 08:13 10357775                   /lib/libutil-2.12.1.so
7efff90ff000-7efff9101000 r-xp 00000000 08:13 10357747                   /lib/libdl-2.12.1.so
7efff9101000-7efff9301000 ---p 00002000 08:13 10357747                   /lib/libdl-2.12.1.so
7efff9301000-7efff9302000 r--p 00002000 08:13 10357747                   /lib/libdl-2.12.1.so
7efff9302000-7efff9303000 rw-p 00003000 08:13 10357747                   /lib/libdl-2.12.1.so
7efff9303000-7efff931f000 r-xp 00000000 08:13 4987789                    /usr/lib/libgsttag-0.10.so.0.21.0
7efff931f000-7efff951e000 ---p 0001c000 08:13 4987789                    /usr/lib/libgsttag-0.10.so.0.21.0
7efff951e000-7efff9520000 r--p 0001b000 08:13 4987789                    /usr/lib/libgsttag-0.10.so.0.21.0
7efff9520000-7efff9521000 rw-p 0001d000 08:13 4987789                    /usr/lib/libgsttag-0.10.so.0.21.0
7efff9521000-7efff9546000 r-xp 00000000 08:13 4988520                    /usr/lib/libgstcontroller-0.10.so.0.26.0
7efff9546000-7efff9745000 ---p 00025000 08:13 4988520                    /usr/lib/libgstcontroller-0.10.so.0.26.0
7efff9745000-7efff9746000 r--p 00024000 08:13 4988520                    /usr/lib/libgstcontroller-0.10.so.0.26.0
7efff9746000-7efff9747000 rw-p 00025000 08:13 4988520                    /usr/lib/libgstcontroller-0.10.so.0.26.0
7efff9747000-7efff9753000 r-xp 00000000 08:13 4984066                    /usr/lib/libgstpbutils-0.10.so.0.21.0
7efff9753000-7efff9953000 ---p 0000c000 08:13 4984066                    /usr/lib/libgstpbutils-0.10.so.0.21.0
7efff9953000-7efff9955000 r--p 0000c000 08:13 4984066                    /usr/lib/libgstpbutils-0.10.so.0.21.0
7efff9955000-7efff9956000 rw-p 0000e000 08:13 4984066                    /usr/lib/libgstpbutils-0.10.so.0.21.0
7efff9956000-7efffa9d3000 r-xp 00000000 08:13 4982111                    /usr/lib/libwebkit-1.0.so.2.17.7
7efffa9d3000-7efffabd2000 ---p 0107d000 08:13 4982111                    /usr/lib/libwebkit-1.0.so.2.17.7
7efffabd2000-7efffad12000 r--p 0107c000 08:13 4982111                    /usr/lib/libwebkit-1.0.so.2.17.7
7efffad12000-7efffad1f000 rw-p 011bc000 08:13 4982111                    /usr/lib/libwebkit-1.0.so.2.17.7
7efffad1f000-7efffad48000 rw-p 00000000 00:00 0 
7efffad48000-7efffad4e000 r-xp 00000000 08:13 4981109                    /usr/lib/libgudev-1.0.so.0.0.1
7efffad4e000-7efffaf4e000 ---p 00006000 08:13 4981109                    /usr/lib/libgudev-1.0.so.0.0.1
7efffaf4e000-7efffaf4f000 r--p 00006000 08:13 4981109                    /usr/lib/libgudev-1.0.so.0.0.1
7efffaf4f000-7efffaf50000 rw-p 00007000 08:13 4981109                    /usr/lib/libgudev-1.0.so.0.0.1
7efffaf50000-7efffaf5b000 r-xp 00000000 08:13 10357354                   /lib/libudev.so.0.9.1
7efffaf5b000-7efffb15b000 ---p 0000b000 08:13 10357354                   /lib/libudev.so.0.9.1
7efffb15b000-7efffb15c000 r--p 0000b000 08:13 10357354                   /lib/libudev.so.0.9.1
7efffb15c000-7efffb15d000 rw-p 0000c000 08:13 10357354                   /lib/libudev.so.0.9.1
7efffb15d000-7efffb174000 r-xp 00000000 08:13 4983555                    /usr/lib/libICE.so.6.3.0
7efffb174000-7efffb373000 ---p 00017000 08:13 4983555                    /usr/lib/libICE.so.6.3.0
7efffb373000-7efffb374000 r--p 00016000 08:13 4983555                    /usr/lib/libICE.so.6.3.0
7efffb374000-7efffb375000 rw-p 00017000 08:13 4983555                    /usr/lib/libICE.so.6.3.0
7efffb375000-7efffb378000 rw-p 00000000 00:00 0 
7efffb378000-7efffb380000 r-xp 00000000 08:13 4983584                    /usr/lib/libSM.so.6.0.1
7efffb380000-7efffb57f000 ---p 00008000 08:13 4983584                    /usr/lib/libSM.so.6.0.1
7efffb57f000-7efffb580000 r--p 00007000 08:13 4983584                    /usr/lib/libSM.so.6.0.1
7efffb580000-7efffb581000 rw-p 00008000 08:13 4983584                    /usr/lib/libSM.so.6.0.1
7efffb581000-7efffb589000 r-xp 00000000 08:13 4981279                    /usr/lib/libnotify.so.1.2.3
7efffb589000-7efffb789000 ---p 00008000 08:13 4981279                    /usr/lib/libnotify.so.1.2.3
7efffb789000-7efffb78a000 r--p 00008000 08:13 4981279                    /usr/lib/libnotify.so.1.2.3
7efffb78a000-7efffb78b000 rw-p 00009000 08:13 4981279                    /usr/lib/libnotify.so.1.2.3
7efffb78b000-7efffb905000 r-xp 00000000 08:13 10357744                   /lib/libc-2.12.1.so
7efffb905000-7efffbb04000 ---p 0017a000 08:13 10357744                   /lib/libc-2.12.1.so
7efffbb04000-7efffbb08000 r--p 00179000 08:13 10357744                   /lib/libc-2.12.1.so
7efffbb08000-7efffbb09000 rw-p 0017d000 08:13 10357744                   /lib/libc-2.12.1.so
7efffbb09000-7efffbb0e000 rw-p 00000000 00:00 0 
7efffbb0e000-7efffbb24000 r-xp 00000000 08:13 10356158                   /lib/libz.so.1.2.3.4
7efffbb24000-7efffbd24000 ---p 00016000 08:13 10356158                   /lib/libz.so.1.2.3.4
7efffbd24000-7efffbd25000 r--p 00016000 08:13 10356158                   /lib/libz.so.1.2.3.4
7efffbd25000-7efffbd26000 rw-p 00017000 08:13 10356158                   /lib/libz.so.1.2.3.4
7efffbd26000-7efffbf63000 r-xp 00000000 08:13 4988936                    /usr/lib/libpython2.6.so.1.0
7efffbf63000-7efffc162000 ---p 0023d000 08:13 4988936                    /usr/lib/libpython2.6.so.1.0
7efffc162000-7efffc164000 r--p 0023c000 08:13 4988936                    /usr/lib/libpython2.6.so.1.0
7efffc164000-7efffc1c6000 rw-p 0023e000 08:13 4988936                    /usr/lib/libpython2.6.so.1.0
7efffc1c6000-7efffc1d5000 rw-p 00000000 00:00 0 
7efffc1d5000-7efffc2b5000 r-xp 00000000 08:13 10357116                   /lib/libglib-2.0.so.0.2600.0
7efffc2b5000-7efffc4b4000 ---p 000e0000 08:13 10357116                   /lib/libglib-2.0.so.0.2600.0
7efffc4b4000-7efffc4b5000 r--p 000df000 08:13 10357116                   /lib/libglib-2.0.so.0.2600.0
7efffc4b5000-7efffc4b6000 rw-p 000e0000 08:13 10357116                   /lib/libglib-2.0.so.0.2600.0
7efffc4b6000-7efffc4b7000 rw-p 00000000 00:00 0 
7efffc4b7000-7efffc4be000 r-xp 00000000 08:13 10357768                   /lib/librt-2.12.1.so
7efffc4be000-7efffc6bd000 ---p 00007000 08:13 10357768                   /lib/librt-2.12.1.so
7efffc6bd000-7efffc6be000 r--p 00006000 08:13 10357768                   /lib/librt-2.12.1.so
7efffc6be000-7efffc6bf000 rw-p 00007000 08:13 10357768                   /lib/librt-2.12.1.so
7efffc6bf000-7efffc6c3000 r-xp 00000000 08:13 4983585                    /usr/lib/libgthread-2.0.so.0.2600.0
7efffc6c3000-7efffc8c2000 ---p 00004000 08:13 4983585                    /usr/lib/libgthread-2.0.so.0.2600.0
7efffc8c2000-7efffc8c3000 r--p 00003000 08:13 4983585                    /usr/lib/libgthread-2.0.so.0.2600.0
7efffc8c3000-7efffc8c4000 rw-p 00004000 08:13 4983585                    /usr/lib/libgthread-2.0.so.0.2600.0
7efffc8c4000-7efffc90d000 r-xp 00000000 08:13 4981624                    /usr/lib/libgobject-2.0.so.0.2600.0
7efffc90d000-7efffcb0d000 ---p 00049000 08:13 4981624                    /usr/lib/libgobject-2.0.so.0.2600.0
7efffcb0d000-7efffcb0e000 r--p 00049000 08:13 4981624                    /usr/lib/libgobject-2.0.so.0.2600.0
7efffcb0e000-7efffcb0f000 rw-p 0004a000 08:13 4981624                    /usr/lib/libgobject-2.0.so.0.2600.0
7efffcb0f000-7efffcb10000 rw-p 00000000 00:00 0 
7efffcb10000-7efffcb28000 r-xp 00000000 08:13 10357764                   /lib/libpthread-2.12.1.so
7efffcb28000-7efffcd27000 ---p 00018000 08:13 10357764                   /lib/libpthread-2.12.1.so
7efffcd27000-7efffcd28000 r--p 00017000 08:13 10357764                   /lib/libpthread-2.12.1.so
7efffcd28000-7efffcd29000 rw-p 00018000 08:13 10357764                   /lib/libpthread-2.12.1.so
7efffcd29000-7efffcd2d000 rw-p 00000000 00:00 0 
7efffcd2d000-7efffcd6d000 r-xp 00000000 08:13 10357050                   /lib/libdbus-1.so.3.5.2
7efffcd6d000-7efffcf6d000 ---p 00040000 08:13 10357050                   /lib/libdbus-1.so.3.5.2
7efffcf6d000-7efffcf6e000 r--p 00040000 08:13 10357050                   /lib/libdbus-1.so.3.5.2
7efffcf6e000-7efffcf6f000 rw-p 00041000 08:13 10357050                   /lib/libdbus-1.so.3.5.2
7efffcf6f000-7efffcf90000 r-xp 00000000 08:13 4983065                    /usr/lib/libdbus-glib-1.so.2.1.0
7efffcf90000-7efffd190000 ---p 00021000 08:13 4983065                    /usr/lib/libdbus-glib-1.so.2.1.0
7efffd190000-7efffd191000 r--p 00021000 08:13 4983065                    /usr/lib/libdbus-glib-1.so.2.1.0
7efffd191000-7efffd192000 rw-p 00022000 08:13 4983065                    /usr/lib/libdbus-glib-1.so.2.1.0
7efffd192000-7efffd1a1000 r-xp 00000000 08:13 4988529                    /usr/lib/libgstinterfaces-0.10.so.0.21.0
7efffd1a1000-7efffd3a1000 ---p 0000f000 08:13 4988529                    /usr/lib/libgstinterfaces-0.10.so.0.21.0
7efffd3a1000-7efffd3a2000 r--p 0000f000 08:13 4988529                    /usr/lib/libgstinterfaces-0.10.so.0.21.0
7efffd3a2000-7efffd3a3000 rw-p 00010000 08:13 4988529                    /usr/lib/libgstinterfaces-0.10.so.0.21.0
7efffd3a3000-7efffd4e7000 r-xp 00000000 08:13 4981703                    /usr/lib/libxml2.so.2.7.7
7efffd4e7000-7efffd6e6000 ---p 00144000 08:13 4981703                    /usr/lib/libxml2.so.2.7.7
7efffd6e6000-7efffd6ee000 r--p 00143000 08:13 4981703                    /usr/lib/libxml2.so.2.7.7
7efffd6ee000-7efffd6f0000 rw-p 0014b000 08:13 4981703                    /usr/lib/libxml2.so.2.7.7
7efffd6f0000-7efffd6f1000 rw-p 00000000 00:00 0 
7efffd6f1000-7efffd6f4000 r-xp 00000000 08:13 4983486                    /usr/lib/libgmodule-2.0.so.0.2600.0
7efffd6f4000-7efffd8f3000 ---p 00003000 08:13 4983486                    /usr/lib/libgmodule-2.0.so.0.2600.0
7efffd8f3000-7efffd8f4000 r--p 00002000 08:13 4983486                    /usr/lib/libgmodule-2.0.so.0.2600.0
7efffd8f4000-7efffd8f5000 rw-p 00003000 08:13 4983486                    /usr/lib/libgmodule-2.0.so.0.2600.0
7efffd8f5000-7efffd9c4000 r-xp 00000000 08:13 4988523                    /usr/lib/libgstreamer-0.10.so.0.26.0
7efffd9c4000-7efffdbc3000 ---p 000cf000 08:13 4988523                    /usr/lib/libgstreamer-0.10.so.0.26.0
7efffdbc3000-7efffdbc8000 r--p 000ce000 08:13 4988523                    /usr/lib/libgstreamer-0.10.so.0.26.0
7efffdbc8000-7efffdbca000 rw-p 000d3000 08:13 4988523                    /usr/lib/libgstreamer-0.10.so.0.26.0
7efffdbca000-7efffdbcc000 rw-p 00000000 00:00 0 
7efffdbcc000-7efffdc06000 r-xp 00000000 08:13 4988518                    /usr/lib/libgstbase-0.10.so.0.26.0
7efffdc06000-7efffde05000 ---p 0003a000 08:13 4988518                    /usr/lib/libgstbase-0.10.so.0.26.0
7efffde05000-7efffde06000 r--p 00039000 08:13 4988518                    /usr/lib/libgstbase-0.10.so.0.26.0
7efffde06000-7efffde07000 rw-p 0003a000 08:13 4988518                    /usr/lib/libgstbase-0.10.so.0.26.0
7efffde07000-7efffdf0c000 r-xp 00000000 08:13 4983589                    /usr/lib/libgio-2.0.so.0.2600.0
7efffdf0c000-7efffe10c000 ---p 00105000 08:13 4983589                    /usr/lib/libgio-2.0.so.0.2600.0
7efffe10c000-7efffe10f000 r--p 00105000 08:13 4983589                    /usr/lib/libgio-2.0.so.0.2600.0
7efffe10f000-7efffe111000 rw-p 00108000 08:13 4983589                    /usr/lib/libgio-2.0.so.0.2600.0
7efffe111000-7efffe112000 rw-p 00000000 00:00 0 
7efffe112000-7efffe163000 r-xp 00000000 08:13 4987544                    /usr/lib/libsoup-2.4.so.1.3.0
7efffe163000-7efffe362000 ---p 00051000 08:13 4987544                    /usr/lib/libsoup-2.4.so.1.3.0
7efffe362000-7efffe364000 r--p 00050000 08:13 4987544                    /usr/lib/libsoup-2.4.so.1.3.0
7efffe364000-7efffe365000 rw-p 00052000 08:13 4987544                    /usr/lib/libsoup-2.4.so.1.3.0
7efffe365000-7efffe366000 rw-p 00000000 00:00 0 
7efffe366000-7efffe36c000 r-xp 00000000 08:13 4981290                    /usr/lib/libsoup-gnome-2.4.so.1.3.0
7efffe36c000-7efffe56b000 ---p 00006000 08:13 4981290                    /usr/lib/libsoup-gnome-2.4.so.1.3.0
7efffe56b000-7efffe56c000 r--p 00005000 08:13 4981290                    /usr/lib/libsoup-gnome-2.4.so.1.3.0
7efffe56c000-7efffe56d000 rw-p 00006000 08:13 4981290                    /usr/lib/libsoup-gnome-2.4.so.1.3.0
7efffe56d000-7efffe5a0000 r-xp 00000000 08:13 4983882                    /usr/lib/libfontconfig.so.1.4.4
7efffe5a0000-7efffe7a0000 ---p 00033000 08:13 4983882                    /usr/lib/libfontconfig.so.1.4.4
7efffe7a0000-7efffe7a1000 r--p 00033000 08:13 4983882                    /usr/lib/libfontconfig.so.1.4.4
7efffe7a1000-7efffe7a2000 rw-p 00034000 08:13 4983882                    /usr/lib/libfontconfig.so.1.4.4
7efffe7a2000-7efffe823000 r-xp 00000000 08:13 4982540                    /usr/lib/libfreetype.so.6.6.0
7efffe823000-7efffea23000 ---p 00081000 08:13 4982540                    /usr/lib/libfreetype.so.6.6.0
7efffea23000-7efffea28000 r--p 00081000 08:13 4982540                    /usr/lib/libfreetype.so.6.6.0
7efffea28000-7efffea29000 rw-p 00086000 08:13 4982540                    /usr/lib/libfreetype.so.6.6.0
7efffea29000-7efffea6e000 r-xp 00000000 08:13 4982456                    /usr/lib/libpango-1.0.so.0.2800.1
7efffea6e000-7efffec6e000 ---p 00045000 08:13 4982456                    /usr/lib/libpango-1.0.so.0.2800.1
7efffec6e000-7efffec70000 r--p 00045000 08:13 4982456                    /usr/lib/libpango-1.0.so.0.2800.1
7efffec70000-7efffec71000 rw-p 00047000 08:13 4982456                    /usr/lib/libpango-1.0.so.0.2800.1
7efffec71000-7efffec97000 r-xp 00000000 08:13 10361632                   /lib/libpng12.so.0.44.0
7efffec97000-7efffee96000 ---p 00026000 08:13 10361632                   /lib/libpng12.so.0.44.0
7efffee96000-7efffee97000 r--p 00025000 08:13 10361632                   /lib/libpng12.so.0.44.0
7efffee97000-7efffee98000 rw-p 00026000 08:13 10361632                   /lib/libpng12.so.0.44.0
7efffee98000-7efffef4f000 r-xp 00000000 08:13 4980959                    /usr/lib/libcairo.so.2.11000.0
7efffef4f000-7effff14e000 ---p 000b7000 08:13 4980959                    /usr/lib/libcairo.so.2.11000.0
7effff14e000-7effff150000 r--p 000b6000 08:13 4980959                    /usr/lib/libcairo.so.2.11000.0
7effff150000-7effff151000 rw-p 000b8000 08:13 4980959                    /usr/lib/libcairo.so.2.11000.0
7effff151000-7effff154000 rw-p 00000000 00:00 0 
7effff154000-7effff1d6000 r-xp 00000000 08:13 10357748                   /lib/libm-2.12.1.so
7effff1d6000-7effff3d5000 ---p 00082000 08:13 10357748                   /lib/libm-2.12.1.so
7effff3d5000-7effff3d6000 r--p 00081000 08:13 10357748                   /lib/libm-2.12.1.so
7effff3d6000-7effff3d7000 rw-p 00082000 08:13 10357748                   /lib/libm-2.12.1.so
7effff3d7000-7effff3f1000 r-xp 00000000 08:13 4982643                    /usr/lib/libgdk_pixbuf-2.0.so.0.2200.0
7effff3f1000-7effff5f1000 ---p 0001a000 08:13 4982643                    /usr/lib/libgdk_pixbuf-2.0.so.0.2200.0
7effff5f1000-7effff5f2000 r--p 0001a000 08:13 4982643                    /usr/lib/libgdk_pixbuf-2.0.so.0.2200.0
7effff5f2000-7effff5f3000 rw-p 0001b000 08:13 4982643                    /usr/lib/libgdk_pixbuf-2.0.so.0.2200.0
7effff5f3000-7effff5fe000 r-xp 00000000 08:13 4982457                    /usr/lib/libpangocairo-1.0.so.0.2800.1
7effff5fe000-7effff7fd000 ---p 0000b000 08:13 4982457                    /usr/lib/libpangocairo-1.0.so.0.2800.1
7effff7fd000-7effff7fe000 r--p 0000a000 08:13 4982457                    /usr/lib/libpangocairo-1.0.so.0.2800.1
7effff7fe000-7effff7ff000 rw-p 0000b000 08:13 4982457                    /usr/lib/libpangocairo-1.0.so.0.2800.1
7effff7ff000-7effff826000 r-xp 00000000 08:13 4982458                    /usr/lib/libpangoft2-1.0.so.0.2800.1
7effff826000-7effffa26000 ---p 00027000 08:13 4982458                    /usr/lib/libpangoft2-1.0.so.0.2800.1
7effffa26000-7effffa27000 r--p 00027000 08:13 4982458                    /usr/lib/libpangoft2-1.0.so.0.2800.1
7effffa27000-7effffa28000 rw-p 00028000 08:13 4982458                    /usr/lib/libpangoft2-1.0.so.0.2800.1
7effffa28000-7effffa45000 r-xp 00000000 08:13 4982462                    /usr/lib/libatk-1.0.so.0.3209.1
7effffa45000-7effffc45000 ---p 0001d000 08:13 4982462                    /usr/lib/libatk-1.0.so.0.3209.1
7effffc45000-7effffc47000 r--p 0001d000 08:13 4982462                    /usr/lib/libatk-1.0.so.0.3209.1
7effffc47000-7effffc48000 rw-p 0001f000 08:13 4982462                    /usr/lib/libatk-1.0.so.0.3209.1
7effffc48000-7effffcf1000 r-xp 00000000 08:13 4982636                    /usr/lib/libgdk-x11-2.0.so.0.2200.0
7effffcf1000-7effffef1000 ---p 000a9000 08:13 4982636                    /usr/lib/libgdk-x11-2.0.so.0.2200.0
7effffef1000-7effffef5000 r--p 000a9000 08:13 4982636                    /usr/lib/libgdk-x11-2.0.so.0.2200.0
7effffef5000-7effffef7000 rw-p 000ad000 08:13 4982636                    /usr/lib/libgdk-x11-2.0.so.0.2200.0
7effffef7000-7f0000309000 r-xp 00000000 08:13 4982635                    /usr/lib/libgtk-x11-2.0.so.0.2200.0
7f0000309000-7f0000508000 ---p 00412000 08:13 4982635                    /usr/lib/libgtk-x11-2.0.so.0.2200.0
7f0000508000-7f000050f000 r--p 00411000 08:13 4982635                    /usr/lib/libgtk-x11-2.0.so.0.2200.0
7f000050f000-7f0000513000 rw-p 00418000 08:13 4982635                    /usr/lib/libgtk-x11-2.0.so.0.2200.0
7f0000513000-7f0000515000 rw-p 00000000 00:00 0 
7f0000515000-7f000054c000 r-xp 00000000 08:13 4981139                    /usr/lib/libgconf-2.so.4.1.5
7f000054c000-7f000074b000 ---p 00037000 08:13 4981139                    /usr/lib/libgconf-2.so.4.1.5
7f000074b000-7f000074d000 r--p 00036000 08:13 4981139                    /usr/lib/libgconf-2.so.4.1.5
7f000074d000-7f0000750000 rw-p 00038000 08:13 4981139                    /usr/lib/libgconf-2.so.4.1.5
7f0000750000-7f000075e000 r-xp 00000000 08:13 4981218                    /usr/lib/libgnome-media-profiles.so.0.0.0
7f000075e000-7f000095d000 ---p 0000e000 08:13 4981218                    /usr/lib/libgnome-media-profiles.so.0.0.0
7f000095d000-7f000095e000 r--p 0000d000 08:13 4981218                    /usr/lib/libgnome-media-profiles.so.0.0.0
7f000095e000-7f000095f000 rw-p 0000e000 08:13 4981218                    /usr/lib/libgnome-media-profiles.so.0.0.0
7f000095f000-7f0000962000 r-xp 00000000 08:13 4980779                    /usr/lib/liblaunchpad-integration.so.1.0.0
7f0000962000-7f0000b61000 ---p 00003000 08:13 4980779                    /usr/lib/liblaunchpad-integration.so.1.0.0
7f0000b61000-7f0000b62000 r--p 00002000 08:13 4980779                    /usr/lib/liblaunchpad-integration.so.1.0.0
7f0000b62000-7f0000b63000 rw-p 00003000 08:13 4980779                    /usr/lib/liblaunchpad-integration.so.1.0.0
7f0000b63000-7f0000b7e000 r-xp 00000000 08:13 4984057                    /usr/lib/libtotem-plparser.so.17.0.0
7f0000b7e000-7f0000d7e000 ---p 0001b000 08:13 4984057                    /usr/lib/libtotem-plparser.so.17.0.0
7f0000d7e000-7f0000d7f000 r--p 0001b000 08:13 4984057                    /usr/lib/libtotem-plparser.so.17.0.0
7f0000d7f000-7f0000d80000 rw-p 0001c000 08:13 4984057                    /usr/lib/libtotem-plparser.so.17.0.0
7f0000d80000-7f0000ec9000 r-xp 00000000 08:13 4981100                    /usr/lib/librhythmbox-core.so.1.1.0
7f0000ec9000-7f00010c9000 ---p 00149000 08:13 4981100                    /usr/lib/librhythmbox-core.so.1.1.0
7f00010c9000-7f00010d0000 r--p 00149000 08:13 4981100                    /usr/lib/librhythmbox-core.so.1.1.0
7f00010d0000-7f00010da000 rw-p 00150000 08:13 4981100                    /usr/lib/librhythmbox-core.so.1.1.0
7f00010da000-7f00010db000 rw-p 00000000 00:00 0 
7f00010db000-7f00010fb000 r-xp 00000000 08:13 10357738                   /lib/ld-2.12.1.so
7f00010ff000-7f000110c000 r--p 00000000 08:13 4987517                    /usr/lib/girepository-1.0/GObject-2.0.typelib
7f000110c000-7f000115a000 r--p 00000000 08:13 6953510                    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
7f000115a000-7f000115b000 r--s 00000000 08:13 1443309                    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le64.cache-3
7f000115b000-7f0001164000 r--s 00000000 08:13 1441862                    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
7f0001164000-7f0001168000 r--s 00000000 08:13 1443267                    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le64.cache-3
7f0001168000-7f000116b000 r--s 00000000 08:13 1443254                    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le64.cache-3
7f000116b000-7f000116e000 r--s 00000000 08:13 1443220                    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le64.cache-3
7f000116e000-7f000116f000 r--s 00000000 08:13 1443174                    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le64.cache-3
7f000116f000-7f0001173000 r--s 00000000 08:13 1443170                    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le64.cache-3
7f0001173000-7f0001174000 r--s 00000000 08:13 1443045                    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le64.cache-3
7f0001174000-7f0001175000 r--s 00000000 08:13 1442996                    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le64.cache-3
7f0001175000-7f0001176000 r--s 00000000 08:13 1442975                    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le64.cache-3
7f0001176000-7f000117c000 r--s 00000000 08:13 1442946                    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le64.cache-3
7f000117c000-7f0001185000 r--s 00000000 08:13 1442939                    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le64.cache-3
7f0001185000-7f0001195000 r--s 00000000 08:13 1442911                    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le64.cache-3
7f0001195000-7f0001198000 r--s 00000000 08:13 1442910                    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le64.cache-3
7f0001198000-7f0001199000 r--s 00000000 08:13 1442893                    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le64.cache-3
7f0001199000-7f00011c7000 r--s 00000000 08:13 1442890                    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le64.cache-3
7f00011c7000-7f00011d1000 r--s 00000000 08:13 1442806                    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le64.cache-3
7f00011d1000-7f00011dc000 r--s 00000000 08:13 1445240                    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le64.cache-3
7f00011dc000-7f00012ad000 r--p 00000000 08:13 5245376                    /usr/share/icons/Humanity/icon-theme.cache
7f00012ad000-7f00012d7000 rw-p 00000000 00:00 0 
7f00012e0000-7f00012e1000 r--s 00000000 08:13 2102694                    /home/mafoelffen/.local/share/mime/mime.cache
7f00012e1000-7f00012e5000 r--s 00000000 08:13 1441867                    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le64.cache-3
7f00012e5000-7f00012ef000 r--p 00000000 08:13 5244646                    /usr/share/icons/Humanity-Dark/icon-theme.cache
7f00012ef000-7f00012f9000 r--p 00000000 08:13 5273716                    /usr/share/icons/ubuntu-mono-dark/icon-theme.cache
7f00012f9000-7f00012fb000 rw-p 00000000 00:00 0 
7f00012fb000-7f00012fc000 r--p 00020000 08:13 10357738                   /lib/ld-2.12.1.so
7f00012fc000-7f00012fd000 rw-p 00021000 08:13 10357738                   /lib/ld-2.12.1.so
7f00012fd000-7f00012fe000 rw-p 00000000 00:00 0 
7fff98b02000-7fff98b2b000 rw-p 00000000 00:00 0                          [stack]
7fff98b6b000-7fff98b6c000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
[/HTML]

---

### Post by MAFoElffen on 2011-01-13
ProcStatus:
[HTML]
Name:	rhythmbox
State:	S (sleeping)
Tgid:	24202
Pid:	24202
PPid:	1
TracerPid:	0
Uid:	1000	1000	1000	1000
Gid:	1000	1000	1000	1000
FDSize:	64
Groups:	4 20 24 25 46 104 105 112 119 122 1000 1001 
VmPeak:	  636164 kB
VmSize:	  636160 kB
VmLck:	       0 kB
VmHWM:	   60920 kB
VmRSS:	   60920 kB
VmData:	  141892 kB
VmStk:	     168 kB
VmExe:	      32 kB
VmLib:	   61364 kB
VmPTE:	     976 kB
VmSwap:	       0 kB
Threads:	4
SigQ:	0/16382
SigPnd:	0000000000000000
ShdPnd:	0000000000000000
SigBlk:	0000000000000000
SigIgn:	0000000001001000
SigCgt:	0000000180010000
CapInh:	0000000000000000
CapPrm:	0000000000000000
CapEff:	0000000000000000
CapBnd:	ffffffffffffffff
Cpus_allowed:	3
Cpus_allowed_list:	0-1
Mems_allowed:	00000000,00000001
Mems_allowed_list:	0
voluntary_ctxt_switches:	3861
nonvoluntary_ctxt_switches:	573
[/HTML]

---

### Post by MAFoElffen on 2011-01-13
XorgLog:
[HTML]
[    21.787] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    21.787] X Protocol Version 11, Revision 0
[    21.787] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    21.787] Current Operating System: Linux maf-ubuntu-01 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[    21.787] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro quiet splash
[    21.787] Build Date: 23 November 2010  11:54:56PM
[    21.787] xorg-server 2:1.9.0-0ubuntu7.1 (For technical support please see http://www.ubuntu.com/support) 
[    21.787] Current version of pixman: 0.18.4
[    21.787] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    21.787] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.787] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 11 14:27:42 2011
[    21.787] (==) Using config file: "/etc/X11/xorg.conf"
[    21.787] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.788] (==) ServerLayout "Layout0"
[    21.788] (**) |-->Screen "Screen0" (0)
[    21.788] (**) |   |-->Monitor "Monitor0"
[    21.788] (**) |   |-->Device "Device0"
[    21.788] (**) |-->Screen "Screen1" (1)
[    21.788] (**) |   |-->Monitor "Monitor1"
[    21.788] (**) |   |-->Device "Device1"
[    21.788] (**) |-->Input Device "Keyboard0"
[    21.788] (**) |-->Input Device "Mouse0"
[    21.788] (**) Option "Xinerama" "0"
[    21.788] (==) Automatically adding devices
[    21.788] (==) Automatically enabling devices
[    21.788] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.788] 	Entry deleted from font path.
[    21.788] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.788] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.788] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    21.788] (WW) Disabling Keyboard0
[    21.788] (WW) Disabling Mouse0
[    21.788] (II) Loader magic: 0x7d17a0
[    21.788] (II) Module ABI versions:
[    21.788] 	X.Org ANSI C Emulation: 0.4
[    21.788] 	X.Org Video Driver: 8.0
[    21.788] 	X.Org XInput driver : 11.0
[    21.788] 	X.Org Server Extension : 4.0
[    21.789] (--) PCI: (0:3:0:0) 10de:00f9:1682:2120 rev 162, Mem @ 0xd7000000/16777216, 0xb0000000/268435456, 0xd6000000/16777216, BIOS @ 0x????????/131072
[    21.790] (--) PCI:*(0:6:0:0) 10de:00f9:1682:2120 rev 162, Mem @ 0xdf000000/16777216, 0xc0000000/268435456, 0xde000000/16777216, BIOS @ 0x????????/131072
[    21.790] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    21.790] (II) LoadModule: "extmod"
[    21.816] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.816] (II) Module extmod: vendor="X.Org Foundation"
[    21.816] 	compiled for 1.9.0, module version = 1.0.0
[    21.816] 	Module class: X.Org Server Extension
[    21.816] 	ABI class: X.Org Server Extension, version 4.0
[    21.816] (II) Loading extension MIT-SCREEN-SAVER
[    21.816] (II) Loading extension XFree86-VidModeExtension
[    21.816] (II) Loading extension XFree86-DGA
[    21.816] (II) Loading extension DPMS
[    21.816] (II) Loading extension XVideo
[    21.816] (II) Loading extension XVideo-MotionCompensation
[    21.816] (II) Loading extension X-Resource
[    21.816] (II) LoadModule: "dbe"
[    21.817] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.817] (II) Module dbe: vendor="X.Org Foundation"
[    21.817] 	compiled for 1.9.0, module version = 1.0.0
[    21.817] 	Module class: X.Org Server Extension
[    21.817] 	ABI class: X.Org Server Extension, version 4.0
[    21.817] (II) Loading extension DOUBLE-BUFFER
[    21.817] (II) LoadModule: "glx"
[    21.817] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    21.833] (II) Module glx: vendor="NVIDIA Corporation"
[    21.833] 	compiled for 4.0.2, module version = 1.0.0
[    21.833] 	Module class: X.Org Server Extension
[    21.833] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[    21.833] (II) Loading extension GLX
[    21.833] (II) LoadModule: "record"
[    21.834] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.834] (II) Module record: vendor="X.Org Foundation"
[    21.834] 	compiled for 1.9.0, module version = 1.13.0
[    21.834] 	Module class: X.Org Server Extension
[    21.834] 	ABI class: X.Org Server Extension, version 4.0
[    21.834] (II) Loading extension RECORD
[    21.834] (II) LoadModule: "dri"
[    21.834] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.835] (II) Module dri: vendor="X.Org Foundation"
[    21.835] 	compiled for 1.9.0, module version = 1.0.0
[    21.835] 	ABI class: X.Org Server Extension, version 4.0
[    21.835] (II) Loading extension XFree86-DRI
[    21.835] (II) LoadModule: "dri2"
[    21.835] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.835] (II) Module dri2: vendor="X.Org Foundation"
[    21.835] 	compiled for 1.9.0, module version = 1.2.0
[    21.835] 	ABI class: X.Org Server Extension, version 4.0
[    21.835] (II) Loading extension DRI2
[    21.835] (II) LoadModule: "nvidia"
[    21.835] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    21.836] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.836] 	compiled for 4.0.2, module version = 1.0.0
[    21.836] 	Module class: X.Org Video Driver
[    21.836] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[    21.836] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.836] (++) using VT number 7

[    21.838] (II) Loading sub module "fb"
[    21.838] (II) LoadModule: "fb"
[    21.838] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.839] (II) Module fb: vendor="X.Org Foundation"
[    21.839] 	compiled for 1.9.0, module version = 1.0.0
[    21.839] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.839] (II) Loading sub module "wfb"
[    21.839] (II) LoadModule: "wfb"
[    21.840] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.840] (II) Module wfb: vendor="X.Org Foundation"
[    21.840] 	compiled for 1.9.0, module version = 1.0.0
[    21.840] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.840] (II) Loading sub module "ramdac"
[    21.840] (II) LoadModule: "ramdac"
[    21.840] (II) Module "ramdac" already built-in
[    21.840] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    21.840] (==) NVIDIA(0): RGB weight 888
[    21.840] (==) NVIDIA(0): Default visual is TrueColor
[    21.840] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.840] (**) NVIDIA(0): Option "TwinView" "0"
[    21.840] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[    21.840] (**) NVIDIA(0): Enabling RENDER acceleration
[    21.840] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    21.840] (II) NVIDIA(0):     enabled.
[    23.631] (II) NVIDIA(0): NVIDIA GPU GeForce 6800 Ultra (NV40) at PCI:6:0:0 (GPU-0)
[    23.631] (--) NVIDIA(0): Memory: 262144 kBytes
[    23.631] (--) NVIDIA(0): VideoBIOS: 05.40.02.36.08
[    23.631] (II) NVIDIA(0): Detected PCI Express Link width: 0X
[    23.631] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    23.631] (--) NVIDIA(0): Connected display device(s) on GeForce 6800 Ultra at
[    23.631] (--) NVIDIA(0):     PCI:6:0:0
[    23.631] (--) NVIDIA(0):     HSP LM02 (DFP-0)
[    23.631] (--) NVIDIA(0): HSP LM02 (DFP-0): 165.0 MHz maximum pixel clock
[    23.631] (--) NVIDIA(0): HSP LM02 (DFP-0): External Single Link TMDS
[    23.632] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    23.632] (II) NVIDIA(0): Validated modes:
[    23.632] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[    23.632] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    23.634] (--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
[    23.644] (--) NVIDIA(0):     option
[    23.644] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    23.644] (**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
[    23.644] (==) NVIDIA(1): RGB weight 888
[    23.644] (==) NVIDIA(1): Default visual is TrueColor
[    23.644] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[    23.644] (**) NVIDIA(1): Option "TwinView" "0"
[    23.644] (**) NVIDIA(1): Option "MetaModes" "nvidia-auto-select +0+0"
[    23.644] (**) NVIDIA(1): Enabling RENDER acceleration
[    25.544] (II) NVIDIA(1): NVIDIA GPU GeForce 6800 Ultra (NV40) at PCI:3:0:0 (GPU-1)
[    25.544] (--) NVIDIA(1): Memory: 262144 kBytes
[    25.544] (--) NVIDIA(1): VideoBIOS: 05.40.02.36.08
[    25.544] (II) NVIDIA(1): Detected PCI Express Link width: 0X
[    25.544] (--) NVIDIA(1): Interlaced video modes are supported on this GPU
[    25.544] (--) NVIDIA(1): Connected display device(s) on GeForce 6800 Ultra at
[    25.544] (--) NVIDIA(1):     PCI:3:0:0
[    25.544] (--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
[    25.544] (--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 285.0 MHz maximum pixel clock
[    25.544] (--) NVIDIA(1): TV encoder: NVIDIA
[    25.544] (II) NVIDIA(1): Assigned Display Device: TV-0
[    25.544] (II) NVIDIA(1): Validated modes:
[    25.544] (II) NVIDIA(1):     "nvidia-auto-select+0+0"
[    25.544] (II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
[    25.544] (==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
[    25.545] (==) NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
[    25.545] (--) Depth 24 pixmap format is 32 bpp
[    25.545] (II) NVIDIA(0): Initialized GPU GART.
[    25.558] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[    25.683] (II) Loading extension NV-GLX
[    25.722] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    25.731] (==) NVIDIA(0): Disabling shared memory pixmaps
[    25.731] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    25.731] (==) NVIDIA(0): Backing store disabled
[    25.731] (==) NVIDIA(0): Silken mouse enabled
[    25.731] (**) NVIDIA(0): DPMS enabled
[    25.748] (II) Loading extension NV-CONTROL
[    25.749] (II) Loading extension XINERAMA
[    25.749] (II) Loading sub module "dri2"
[    25.749] (II) LoadModule: "dri2"
[    25.749] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.749] (II) NVIDIA(0): [DRI2] Setup complete
[    25.749] (==) RandR enabled
[    25.750] (II) NVIDIA(1): Initialized GPU GART.
[    25.762] (II) NVIDIA(1): Setting mode "nvidia-auto-select+0+0"
[    25.897] (II) NVIDIA(1): Initialized OpenGL Acceleration
[    25.912] (==) NVIDIA(1): Disabling shared memory pixmaps
[    25.912] (II) NVIDIA(1): Initialized X Rendering Acceleration
[    25.912] (==) NVIDIA(1): Backing store disabled
[    25.912] (==) NVIDIA(1): Silken mouse enabled
[    25.912] (==) NVIDIA(1): DPMS enabled
[    25.912] (II) Loading sub module "dri2"
[    25.912] (II) LoadModule: "dri2"
[    25.913] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.913] (II) NVIDIA(1): [DRI2] Setup complete
[    25.913] (==) RandR enabled
[    25.913] (II) Initializing built-in extension Generic Event Extension
[    25.913] (II) Initializing built-in extension SHAPE
[    25.913] (II) Initializing built-in extension MIT-SHM
[    25.913] (II) Initializing built-in extension XInputExtension
[    25.913] (II) Initializing built-in extension XTEST
[    25.913] (II) Initializing built-in extension BIG-REQUESTS
[    25.913] (II) Initializing built-in extension SYNC
[    25.913] (II) Initializing built-in extension XKEYBOARD
[    25.913] (II) Initializing built-in extension XC-MISC
[    25.913] (II) Initializing built-in extension SECURITY
[    25.913] (II) Initializing built-in extension XINERAMA
[    25.913] (II) Initializing built-in extension XFIXES
[    25.913] (II) Initializing built-in extension RENDER
[    25.913] (II) Initializing built-in extension RANDR
[    25.913] (II) Initializing built-in extension COMPOSITE
[    25.913] (II) Initializing built-in extension DAMAGE
[    25.913] (II) Initializing built-in extension GESTURE
[    25.915] (II) Initializing extension GLX
[    25.952] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.962] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.962] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.962] (II) LoadModule: "evdev"
[    25.963] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.964] (II) Module evdev: vendor="X.Org Foundation"
[    25.964] 	compiled for 1.9.0, module version = 2.3.2
[    25.964] 	Module class: X.Org XInput Driver
[    25.964] 	ABI class: X.Org XInput driver, version 11.0
[    25.964] (**) Power Button: always reports core events
[    25.964] (**) Power Button: Device: "/dev/input/event1"
[    25.982] (II) Power Button: Found keys
[    25.982] (II) Power Button: Configuring as keyboard
[    25.982] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.982] (**) Option "xkb_rules" "evdev"
[    25.982] (**) Option "xkb_model" "pc105"
[    25.982] (**) Option "xkb_layout" "us"
[    25.984] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    25.984] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.984] (**) Power Button: always reports core events
[    25.984] (**) Power Button: Device: "/dev/input/event0"
[    26.000] (II) Power Button: Found keys
[    26.000] (II) Power Button: Configuring as keyboard
[    26.000] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.000] (**) Option "xkb_rules" "evdev"
[    26.000] (**) Option "xkb_model" "pc105"
[    26.000] (**) Option "xkb_layout" "us"
[    26.008] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    26.008] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.008] (**) AT Translated Set 2 keyboard: always reports core events
[    26.008] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    26.021] (II) AT Translated Set 2 keyboard: Found keys
[    26.021] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    26.021] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    26.021] (**) Option "xkb_rules" "evdev"
[    26.021] (**) Option "xkb_model" "pc105"
[    26.021] (**) Option "xkb_layout" "us"
[    26.022] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event3)
[    26.022] (**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
[    26.022] (**) ImExPS/2 Generic Explorer Mouse: always reports core events
[    26.022] (**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event3"
[    26.040] (II) ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
[    26.040] (II) ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
[    26.040] (II) ImExPS/2 Generic Explorer Mouse: Found relative axes
[    26.040] (II) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
[    26.040] (II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
[    26.040] (**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
[    26.040] (**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.040] (II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
[    26.041] (II) ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
[    26.041] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse0)
[    26.041] (II) No input driver/identifier specified (ignoring)
[/HTML]

---

### Post by MAFoElffen on 2011-01-13
XsessionErrors:
[HTML]
(polkit-gnome-authentication-agent-1:4708): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
(gnome-settings-daemon:4663): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
(gnome-settings-daemon:4663): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(nautilus:4695): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(npviewer.bin:10419): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(npviewer.bin:10419): Gtk-WARNING **: Loading IM context type 'ibus' failed
(npviewer.bin:10419): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(npviewer.bin:10419): Gtk-WARNING **: Loading IM context type 'ibus' failed
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(npviewer.bin:12241): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(npviewer.bin:12241): Gtk-WARNING **: Loading IM context type 'ibus' failed
(npviewer.bin:12241): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(npviewer.bin:12241): Gtk-WARNING **: Loading IM context type 'ibus' failed
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(npviewer.bin:14326): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(npviewer.bin:14326): Gtk-WARNING **: Loading IM context type 'ibus' failed
(npviewer.bin:14326): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(npviewer.bin:14326): Gtk-WARNING **: Loading IM context type 'ibus' failed
(npviewer.bin:14326): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(npviewer.bin:14326): Gtk-WARNING **: Loading IM context type 'ibus' failed
(npviewer.bin:14326): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(npviewer.bin:14326): Gtk-WARNING **: Loading IM context type 'ibus' failed
(npviewer.bin:14326): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(npviewer.bin:14326): Gtk-WARNING **: Loading IM context type 'ibus' failed
(npviewer.bin:14326): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(npviewer.bin:14326): Gtk-WARNING **: Loading IM context type 'ibus' failed
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(npviewer.bin:15068): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(npviewer.bin:15068): Gtk-WARNING **: Loading IM context type 'ibus' failed
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(process:16197): Gtk-CRITICAL **: set_table: assertion `buffer->tag_table == NULL' failed
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(npviewer.bin:18871): Gdk-WARNING **: XID collision, trouble ahead
(npviewer.bin:18871): Gdk-WARNING **: XID collision, trouble ahead
(npviewer.bin:18871): Gdk-WARNING **: XID collision, trouble ahead
(npviewer.bin:18871): Gdk-WARNING **: XID collision, trouble ahead
(npviewer.bin:18871): Gdk-WARNING **: XID collision, trouble ahead
(npviewer.bin:18871): Gdk-WARNING **: XID collision, trouble ahead
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(acroread:21007): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(acroread:21007): Gtk-WARNING **: Loading IM context type 'ibus' failed
(acroread:21007): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(acroread:21007): Gtk-WARNING **: Loading IM context type 'ibus' failed
(acroread:21007): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(acroread:21007): Gtk-WARNING **: Loading IM context type 'ibus' failed
(acroread:21007): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(acroread:21007): Gtk-WARNING **: Loading IM context type 'ibus' failed
(acroread:21007): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(acroread:21007): Gtk-WARNING **: Loading IM context type 'ibus' failed
(acroread:21007): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(acroread:21007): Gtk-WARNING **: Loading IM context type 'ibus' failed
(acroread:21007): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(acroread:21007): Gtk-WARNING **: Loading IM context type 'ibus' failed
(acroread:21007): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(acroread:21007): Gtk-WARNING **: Loading IM context type 'ibus' failed
(acroread:21007): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(acroread:21007): Gtk-WARNING **: Loading IM context type 'ibus' failed
(acroread:21007): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(acroread:21007): Gtk-WARNING **: Loading IM context type 'ibus' failed
(acroread:21007): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(acroread:21007): Gtk-WARNING **: Loading IM context type 'ibus' failed
(acroread:21007): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(acroread:21007): Gtk-WARNING **: Loading IM context type 'ibus' failed
(acroread:21007): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(acroread:21007): Gtk-WARNING **: Loading IM context type 'ibus' failed
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c00406 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c00401 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003f4 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003f3 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c00403 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c00402 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003f1 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003f2 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003e5 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003e6 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c00405 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c00404 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003e4 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003e2 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003e1 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003e0 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003db unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c0040a unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c00408 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c00409 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c00407 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003e3 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003df unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003de unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003dd unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003dc unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003d9 unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c003da unexpectedly destroyed
(acroread:21007): Gdk-WARNING **: GdkWindow 0x7c00230 unexpectedly destroyed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_get_chars: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_get_chars: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_delete_text: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_insert_text: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_set_editable: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_entry_get_layout: assertion `GTK_IS_ENTRY (entry)' failed
(acroread:21007): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_get_chars: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_get_chars: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_delete_text: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_insert_text: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_set_editable: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_entry_get_layout: assertion `GTK_IS_ENTRY (entry)' failed
(acroread:21007): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_size_request: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_get_chars: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_delete_text: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_insert_text: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_set_editable: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_get_chars: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_delete_text: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_insert_text: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_editable_set_editable: assertion `GTK_IS_EDITABLE (editable)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
(acroread:21007): Gtk-CRITICAL **: IA__gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(npviewer.bin:21651): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
(npviewer.bin:21651): Gtk-WARNING **: Loading IM context type 'ibus' failed
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(gdu-notification-daemon:4864): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda5 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda7 is a logical partition but no extended partition exists
(update-notifier:4912): libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sda6 is a logical partition but no extended partition exists

[/HTML]

---

### Post by MAFoElffen on 2011-01-15
The Ubuntu Bigzilla team looked through the info and really rather wanted info on the crashes themsleves,  The above info was how it setup and how it's running, but was missing info on what happened when it crashes.  They instructed me to enable apport and send them the particular crash dump reports... so for FYI to others here, I include this info.

[QUOTE=Ubuntu Bugzilla Team] Please follow these instructions to have apport report a new bug  about your crash that can be dealt with by the automatic retracer. 

If you are running the Ubuntu Stable Release you might need to enable apport in /etc/default/apport and restart.[/QUOTE]
 Done by Open Terminal session:
```

cd /etc/default
gedit apport

```Change apport=0 to a 1, uncomment the max dump file size line... save and exit... restart the OS.
[QUOTE=Ubuntu Bugzilla Team]
Now open your file manager, navigate to your /var/crash directory and open the crash report you wish to submit.

If this fails you will have to open a terminal and file your report with 'ubuntu-bug /var/crash/_my_crash_report.crash' where _my_crash_report.crash  is the crash you would like to report. If you get an error that you  aren't allowed to access this report you will have to file it with 'sudo  ubuntu-bug /var/crash/_my_crash_report.crash'.[/QUOTE]So that's what I'm doing at the moment.

---

### Post by MAFoElffen on 2011-01-20
I'm going round and round on launchpad / bugzilla.  At present they mis-ID'ed this problem in with the Ubuntu One Music Store Bug... which this PC does not evven have that pluggin installed...

I knew that was a known bug and even though this PV has that bug... it will not even start with that pluggin installed.  I tried to make sure that I was reporting these problems as "other problems" but it still got mis-ID'ed in their triage process.

I did find that this PC is not catching these crashes in "appert"... but I can cause a crash in another system to verify that apport "is" working-- so I've been having to manually ran traces to report this.

I "am" trying to remain patient.

---

### Post by MAFoElffen on 2011-01-20
I'm going round and round on launchpad / bugzilla.  At present they mis-ID'ed this problem in with the Ubuntu One Music Store Bug... which this PC does not evven have that pluggin installed...

I knew that was a known bug and even though this PC has that bug... it will not even start with that pluggin installed.  I tried to make sure that I was reporting these problems as "other problems" but it still got mis-ID'ed in their triage process.

I did find that this PC is not catching these crashes in "appert"... but I can cause a crash in another system to verify that apport "is" working-- so I've been having to manually ran traces to report this.

I "am" trying to remain patient.

---

### Post by MAFoElffen on 2011-01-20
I'm going round and round on launchpad / bugzilla.  At present they  mis-ID'ed this problem in with the Ubuntu One Music Store Bug... which  this PC does not evven have that pluggin installed...

I knew that was a known bug and even though this PC has that bug... it  will not even start with that pluggin installed.  I tried to make sure  that I was reporting these problems as "other problems" but it still got  mis-ID'ed in their triage process.

I did find that this PC is not catching these crashes in "appert"... but  I can cause a crash in another system to verify that apport "is"  working-- so I've been having to manually ran traces to report this.

I "am" trying to remain patient.

---

### Post by MAFoElffen on 2011-01-20
I'm going round and round on launchpad / bugzilla.  At present they  mis-ID'ed this problem in with (as a duplicate) the Ubuntu One Music Store Bug... which  this PC does not even have that pluggin installed...

I knew that was a known bug and even though this PC has that bug... it  will not even start with that pluggin installed.  I tried to make sure  that I was reporting these problems as "other problems" but it still got  mis-ID'ed in their triage process.

I did find that this PC is not catching these crashes in "appert"... but  I can cause a crash in another system to verify that apport "is"  working-- so I've been having to manually ran traces to report this.

I "am" trying to remain patient.](*,)

---

### Post by MAFoElffen on 2011-01-20
I'm going round and round on launchpad / bugzilla.  At present they  mis-ID'ed this problem in with (as a duplicate) the Ubuntu One Music Store Bug... which  this PC does not even have that pluggin installed...

I knew that was a known bug and even though this PC has that bug... it  will not even start with that pluggin installed.  I tried to make sure  that I was reporting these problems as "other problems" but it still got  mis-ID'ed in their triage process.

I did find that this PC is not catching these crashes in "appert"... but  I can cause a crash in another system to verify that apport "is"  working-- so I've been having to manually ran traces to report this.

I "am" trying to remain patient.](*,)

---

