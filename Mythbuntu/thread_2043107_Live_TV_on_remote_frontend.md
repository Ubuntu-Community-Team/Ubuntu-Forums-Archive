---
title: "Live TV on remote frontend"
date: 2012-08-15
forum: Mythbuntu
---

### Post by Billsputters on 2012-08-15
This has been puzzling me for a few days now.

I have a BE/FE in my loft, works well, storage groups defined, can watch live tv, videos, music etc.

FE only in lounge, can watch videos and recorded programmes, but no live tv! I can't fathom it at all. Can anyone enlighten me. I bet it is a simple fault I've overlooked

---

### Post by nickrout on 2012-08-15
what does your frontend log tell you?

---

### Post by Billsputters on 2012-08-15
This this is the bit we are interested in

```
Aug 16 02:51:13 Mythtv-fe1 mythfrontend[1649]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
Aug 16 02:51:13 Mythtv-fe1 mythfrontend[1649]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.200:6543 (try 1 of 1)
Aug 16 02:51:13 Mythtv-fe1 mythfrontend[1649]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Aug 16 02:51:13 Mythtv-fe1 mythfrontend[1649]: N CoreContext tv_play.cpp:2186 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
Aug 16 02:51:14 Mythtv-fe1 mythfrontend[1649]: N CoreContext tv_play.cpp:2193 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
Aug 16 02:51:14 Mythtv-fe1 mythfrontend[1649]: E CoreContext livetvchain.cpp:270 (GetEntryAt) GetEntryAt(-1) failed.
Aug 16 02:51:14 Mythtv-fe1 mythfrontend[1649]: E CoreContext livetvchain.cpp:277 (GetEntryAt) It appears that your backend may be misconfigured.  Check your backend logs to determine whether your capture cards, lineups, channels, or storage configuration are reporting errors.  This issue is commonly caused by failing to complete all setup steps properly.  You may wish to review the documentation for mythtv-setup.
```

Still don't understand how it works on the combined BE/FE but not a FE only

---

### Post by nickrout on 2012-08-16
What is the IP address of backend and frontend?

What IP addresses are set in mythtv-setup, 1st section?

you might try running mythfrontend with greater verbosity (see ```
mythfrontend -v help 
```for details) or do as it suggests already and look at the backend logs.

---

