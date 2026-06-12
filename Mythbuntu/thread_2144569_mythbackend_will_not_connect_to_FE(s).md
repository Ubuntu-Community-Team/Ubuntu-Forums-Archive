---
title: "mythbackend will not connect to FE(s)"
date: 2013-05-12
forum: Mythbuntu
---

### Post by Neon612 on 2013-05-12
I have a mythbuntu setup with 0.25. Its a BE/FE combo, though the BE is the only part being used. I have a Raspberry Pi setup with Raspbmc that I plan to use for a FE of sorts. About 3 months ago or so I had everything setup and working fine, then school came along and I needed to use the Pi for something else. Plus we had lost power for a few hours during a storm and the Pi had received an upgrade to RaspBMC 12.2 (which I'm not sure if it worked correctly or not, but I have XBMC on other machines and they're experiencing the same problems), and now the UPnP menu shows absolutely nothing.

I have checked to make sure mythbackend starts on boot and it does. The FE on the same machine works correctly, as well.

Here is the tail on mythbackend.log:
```
May 12 16:45:06 localhost mythbackend[1326]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(9ab71d0:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 10 bytes with 1 errors#012#011#011#011starts with: 2       OK
May 12 16:45:07 localhost mythbackend[1326]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.0.109:6543
May 12 16:45:07 localhost mythbackend[1326]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
May 12 16:45:37 localhost mythbackend[1326]: E CoreContext mythsocket.cpp:534 (readStringList) MythSocket(9ab7468:23): readStringList: Error, timed out after 30000 ms.
May 12 16:45:37 localhost mythbackend[1326]: E CoreContext mainserver.cpp:6146 (reconnectTimeout) MainServer: Failed to open master server socket, timeout
May 12 16:45:37 localhost mythbackend[1326]: I ProcessRequest mainserver.cpp:1410 (HandleAnnounce) adding: computer-4 as a slave backend server
May 12 16:45:37 localhost mythbackend[1326]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9ab7468)
May 12 16:45:37 localhost mythbackend[1326]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(9ab7468:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 10 bytes with 1 errors#012#011#011#011starts with: 2       OK
May 12 16:45:38 localhost mythbackend[1326]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.0.109:6543
May 12 16:45:38 localhost mythbackend[1326]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully

```

What can I do to fix this?

Thank you

---

### Post by PhilWig on 2013-05-13
Since the combined FE/BE works then there are a couple of configuration settings to check which are needed for any FE.

1.  Is the backend IP address fixed - either set it static on your myth box or use DHCP but configure your router to always give the same address. 

2.  Is the BE set up correctly to allow a remote FE?  Check:
Backend address is set twice in backend setup>general.
Also there is a tick box to be set in control centre to allow remote FE access.

If those are right then perhaps the problem is one to take to an xbmc forum.
When I last looked there was a compatibility issue with xbmc - it didn't handle the new connection protocol keys introduced with (I think) 0.24 but xbmc is a fast moving product and things may have changed!

Phil

---

