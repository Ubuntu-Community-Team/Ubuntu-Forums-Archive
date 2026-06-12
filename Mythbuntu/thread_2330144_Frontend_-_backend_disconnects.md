---
title: "Frontend - backend disconnects"
date: 2016-07-08
forum: Mythbuntu
---

### Post by jwmeyer on 2016-07-08
Every 12-16 seconds the following messages are posted to my mythbackend log while the frontend is idle.


Jul  8 10:17:56 zbox mythbackend: mythbackend[13536]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Frontend
Jul  8 10:17:56 zbox mythbackend: mythbackend[13536]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: zbox(2298c00) as a client (events: 0)
Jul  8 10:17:56 zbox mythbackend: mythbackend[13536]: I ProcessRequest backendcontext.cpp:56 (SetFrontendConnected) BackendContext: Frontend 'zbox' connected.
Jul  8 10:17:56 zbox mythbackend: mythbackend[13536]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Monitor
Jul  8 10:17:56 zbox mythbackend: mythbackend[13536]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: zbox(229c1b0) as a client (events: 1)
Jul  8 10:20:08 zbox mythbackend: mythbackend[13536]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Monitor
Jul  8 10:20:08 zbox mythbackend: mythbackend[13536]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: zbox(229cdb0) as a client (events: 0)
Jul  8 10:20:08 zbox mythbackend: mythbackend[13536]: I MythSocketThread(61) mainserver.cpp:7629 (connectionClosed) Monitor sock(229cdb0) 'zbox' disconnected

mythbuntu 14.04
mythtv .28 combined FE/BE

Is there a fix for this problem? The logs are filling up.

Update 7-9-16: After using xset noblank the disconnect is logging every 10 minutes. Better but the question still remains "why the disocnnects?".

---

