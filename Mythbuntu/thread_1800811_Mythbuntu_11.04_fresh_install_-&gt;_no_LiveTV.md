---
title: "Mythbuntu 11.04 fresh install -&gt; no LiveTV"
date: 2011-07-09
forum: Mythbuntu
---

### Post by macaronij on 2011-07-09
first of all, sorry for my english
Ok, i use mythbuntu 9.04 (mythtv 0.22) for 2 years now and i am very happy
now i have buy a new machjine to install mythbuntu 11.04 (mythTV 0.24.1) but i can t get live tv to wqork whit the same tv tuners that work in 9.04
iLive tv just fails whitout any error
logs frontend/backend:
[http://pastebin.com/uENQGueJ](http://pastebin.com/uENQGueJ)

tv tuners are analogic, v4l based
one is a kworld and the other is encore

any help, please?

---

### Post by nickrout on 2011-07-09
> **macaronij said:**
> first of all, sorry for my english
Ok, i use mythbuntu 9.04 (mythtv 0.22) for 2 years now and i am very happy
now i have buy a new machjine to install mythbuntu 11.04 (mythTV 0.24.1) but i can t get live tv to wqork whit the same tv tuners that work in 9.04
iLive tv just fails whitout any error
logs frontend/backend:
[http://pastebin.com/uENQGueJ](http://pastebin.com/uENQGueJ)

tv tuners are analogic, v4l based
one is a kworld and the other is encore

any help, please?

There are plenty of errors there, how about beiong unable to open the ringbuffer file - check permissions etc.

Also the reference to the DUMMY tuner, are you sure you have set things up with mythtv-setup?

---

### Post by macaronij on 2011-07-09
ok, i deleted and reconfigured the tv tunners in mythbackend, repair/optimize the tables and erased the channels and start over
same error
**it really seems a premition problem, but remember that this is a fresh install of mythbuntu 11.04, the only config i made is the tunners in the backend**
here the last try in mythbackend log


[LIST=1]
[*]2011-07-09 20:23:20.337 MainServer::ANN Playback
[*]2011-07-09 20:23:20.397 adding: mythbuntu as a client (events: 0)
[*]2011-07-09 20:23:20.440 TVRec(3): Changing from None to WatchingLiveTV
[*]2011-07-09 20:23:20.500 TVRec(3): HW Tuner: 3->3
[*]2011-07-09 20:23:20.544 LoadFromScheduler(): Error, called from backend.
[*]2011-07-09 20:23:20.546 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]2011-07-09 20:23:20.700 Finished recording Unknown: channel 1002
[*]2011-07-09 20:23:20.769 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
[*]2011-07-09 20:23:20.807 New DB connection, total: 4
[*]2011-07-09 20:23:20.857 Connected to database 'mythconverg' at host: localhost
[*]2011-07-09 20:23:20.860 LoadFromScheduler(): Error, called from backend.
[*]2011-07-09 20:23:20.894 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]2011-07-09 20:23:20.926 recording already exists...
[*]2011-07-09 20:23:20.999 Finished recording Unknown: channel 1002
[*]2011-07-09 20:23:31.172 TVRec(3): Changing from WatchingLiveTV to None
[*]2011-07-09 20:23:31.237 MainServer::ANN Playback
[*]2011-07-09 20:23:31.317 adding: mythbuntu as a client (events: 0)
[*]2011-07-09 20:23:31.352 TVRec(3): Changing from None to WatchingLiveTV
[*]2011-07-09 20:23:31.412 TVRec(3): HW Tuner: 3->3
[*]2011-07-09 20:23:31.455 LoadFromScheduler(): Error, called from backend.
[*]2011-07-09 20:23:31.457 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]2011-07-09 20:23:31.613 Finished recording Unknown: channel 1002
[*]2011-07-09 20:23:31.681 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
[*]2011-07-09 20:23:31.739 LoadFromScheduler(): Error, called from backend.
[*]2011-07-09 20:23:31.741 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]2011-07-09 20:23:31.772 recording already exists...
[*]2011-07-09 20:23:31.853 Finished recording Unknown: channel 1002
[*]2011-07-09 20:23:42.006 TVRec(3): Changing from WatchingLiveTV to None
[*]2011-07-09 20:23:42.049 MainServer::ANN Playback
[*]2011-07-09 20:23:42.077 adding: mythbuntu as a client (events: 0)
[*]2011-07-09 20:23:42.112 TVRec(3): Changing from None to WatchingLiveTV
[*]2011-07-09 20:23:42.147 TVRec(3): HW Tuner: 3->3
[*]2011-07-09 20:23:42.191 LoadFromScheduler(): Error, called from backend.
[*]2011-07-09 20:23:42.194 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]2011-07-09 20:23:42.252 TVRec(3): Changing from WatchingLiveTV to None
[/LIST]

and here the full log, just in case [http://pastebin.com/ei8zwK3a](http://pastebin.com/ei8zwK3a)
(just discovered mythloggrabber and i love it)

---

### Post by macaronij on 2011-07-10
ok, what i knwo is that mythtv use a dummy card, that why livetv fails
i have confiigured the cards in mythbackend more than 10 times and don t know why he use the DUMMY CARD

IT S THE DUMMY CARD A DEFAULT IN MYTHBUNTU 11.04?? HELP PLEASE!!!

LiveTVChain has 2 entries
   DUMMY: 1010 (19:26:19 to 19:26:19)
*    V4L: 1010 (19:26:20 to 19:30:00) discontinuous

2011-07-10 19:26:29.655 Player(1), Error: Unknown recorder error, exiting decoder
2011-07-10 19:26:29.713 VideoOutput: Created YV12 OSD.
2011-07-10 19:26:29.718 TV: Attempting to change from WatchingLiveTV to None
2011-07-10 19:26:29.780 TV: Changing from WatchingLiveTV to None
2011-07-10 19:26:29.782 MythSystemEventHandler ERROR: SendMythSystemPlayEvent() called with empty ProgramInfo
2011-07-10 19:26:29.786 TV: Attempting to change from None to WatchingLiveTV
2011-07-10 19:26:29.786 MythCoreContext: Connecting to backend server: localhost:6543 (try 1 of 1)
2011-07-10 19:26:29.786 Using protocol version 63
2011-07-10 19:26:29.868 Spawning LiveTV Recorder -- begin
2011-07-10 19:26:30.025 Spawning LiveTV Recorder -- end
2011-07-10 19:26:30.028 We have a playbackURL(/var/lib/mythtv/livetv/1010_20110710192630.nuv) & cardtype(DUMMY)
2011-07-10 19:26:30.028 We have a RingBuffer
2011-07-10 19:26:30.029 TV Error: LiveTV not successfully started

the full log:
[http://pastebin.com/4V4sp5QR](http://pastebin.com/4V4sp5QR)

---

### Post by nickrout on 2011-07-10
Why are you using the dummy card configuration? Choose the proper card type.

---

### Post by macaronij on 2011-07-11
Of curse!!! i configured my 2 tuner cards in mythbackend, but the frontend use a dummy card, i don t know why

here you can see that the frontend found 2 cards but use the dummy

LiveTVChain has 2 entries
   DUMMY: 1010 (19:26:19 to 19:26:19)
*    V4L: 1010 (19:26:20 to 19:30:00) discontinuous


what does "discontinuous" mean?
and why is a "*" before my v4l card?

---

### Post by agamotto on 2011-07-11
Your English is fine, so don't worry so much about it!  If you could tell us your native language, that might help us get some of the idiom you are missing across.

Try the following, just to see if it 'sticks.'

1. delete all capture cards on the backend.  Install (1) one of your tuner cards, running mythfilldatabase.

If the frontend is using the (1) tuner installed, then the frontend may be confused about the cards; if it still keeps using the DUMMY card, then there is something wrong in the IVTV config that doesn't recognize your tuners for some reason with 11.04.

At worst, you may have to drop to 10.04 LTS.  Can you please post the exact model numbers of your tuner cards to better help us figure out your analog problems?

---

