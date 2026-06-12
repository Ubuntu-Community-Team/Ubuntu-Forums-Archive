---
title: "no gui on myth frontend"
date: 2017-01-31
forum: Multimedia Software
---

### Post by benlyboy on 2017-01-31
Hoping this is the right place to post this as there is no longer a dedicated mythbuntu page.

I have used myth for a number of years and for the most part its been great, it started off with a very simple system with the front and back ends on one pc. But over the year it grew in a system that had a single 4tb backend and four frontends. Well my backend was quite old and was in need of updating, so I built a replacement and installed mythbuntu 16.04. I transferred the database and media, all seemed to go well I have a front end on another pc in the room where the back end is. When I tried to connect it basically told me I needed to update my frontend so I did, and all worked great, so I headed up stairs to connect the other front ends. That's when it all went horrible wrong It again told me I needed to update my frontend so I did but now when I connect i get no GUI. I can look at the log for the backend and see that it is connecting but all I see is the desktop minus the cursor. if I hit ctrl+alt+D it will minimalise myth and I get my cursor back, so I know myth is opening a window its just has nothing in it. In case it was a bad update I did a clean install of 16.04 frontend  with no change.
, 
This is a snippet from the backend log that shows that the frontend seems to be connected 

> 
Jan 29 14:17:30 backend1 mythbackend: mythbackend[1759]: I ProcessRequest mainserver.cpp:1730 (HandleAnnounce) MainServer: MainServer::ANN Frontend
Jan 29 14:17:30 backend1 mythbackend: mythbackend[1759]: I ProcessRequest mainserver.cpp:1735 (HandleAnnounce) MainServer: adding: frontendbedroom(15ecff0) as a client (events: 0)
Jan 29 14:17:30 backend1 mythbackend: mythbackend[1759]: I ProcessRequest mainserver.cpp:1730 (HandleAnnounce) Main, Server: MainServer::ANN Monitor
Jan 29 14:17:30 backend1 mythbackend: mythbackend[1759]: I ProcessRequest mainserver.cpp:1735 (HandleAnnounce) MainServer: adding: frontendbedroom(15eddf0) as a client (events: 1)
Jan 29 14:17:54 backend1 mythbackend: mythbackend[1759]: I MythSocketThread(99) mainserver.cpp:7656 (connectionClosed) Playback sock(15ea820) 'frontendbedroom' disconnected
Jan 29 14:17:54 backend1 mythbackend: mythbackend[1759]: I MythSocketThread(101) mainserver.cpp:7656 (connectionClosed) Monitor sock(15f26a0) 'frontendbedroom' disconnected
Jan 29 14:19:50 backend1 mythbackend: mythbackend[1759]: I MythSocketThread(102) mainserver.cpp:7656 (connectionClosed) Monitor sock(15eddf0) 'frontendbedroom' disconnected
Jan 29 14:19:50 backend1 mythbackend: mythbackend[1759]: I MythSocketThread(76) backendcontext.cpp:102 (SetFrontendDisconnected) BackendContext: Frontend 'frontendbedroom' disconnected.


As im not even sure if I am dealing with a back or front end problem I would really appreciate any help

thanks

---

### Post by Keith_Helms on 2017-02-01
Anything revealing in the mythfrontend.log?

---

### Post by benlyboy on 2017-02-01
hi Keith 
No I didn't see anything that struck me, that's not to say there wasn't something. I'm fare from an expert at reading log files.
I wanted to include that log with my post but the wife was asleep in that room so I couldn't. I'm at work right now but will post it when I get home, maybe someone will see something I missed.

---

