---
title: "Error encountered while displaying video?"
date: 2008-03-27
forum: Mythbuntu
---

### Post by caviidae on 2008-03-27
I've just setup mythbuntu 7.10. After much tinkering everything seems to work well, multiple front-ends, LVM, recording, EIC info, HDTV, and the remotes.  **Except....**

When watching live TV when changeing the channel it will sometimes kick me back to the menu with the error:
> Error encountered while displaying video 
With some channels this happens [very very close to] every time. I get the over the air EIC programing information for these channels just fine though.

Using the Pinnacle PCTV HD (800i) PCI tuner.

Here are the log snips of the problem occurring when going from 20_3 "The Create Channel" to 23_1 "The 700 Club"

Frontend log
> 2008-03-27 14:23:17.829 MythSocket(997f6a8:28): readStringList: Error, timeout (quick).
2008-03-27 14:23:17.830 RemoteEncoder::SendReceiveStringList(): No response.
2008-03-27 14:23:17.832 NVP, Error: Unknown error, exiting decoder
2008-03-27 14:23:17.851 TV: Attempting to change from WatchingLiveTV to None
2008-03-27 14:23:17.875 MythSocket(997f6a8:-1): writeStringList: Error, called with unconnected socket.
2008-03-27 14:23:17.875 MythSocket(997f6a8:-1): readStringList: Error, called with unconnected socket.
2008-03-27 14:23:17.875 RemoteEncoder::SendReceiveStringList(): No response.
 

Backend log
> 2008-03-27 14:23:10.913 TVRec(1): HW Tuner: 1->1
2008-03-27 14:23:15.569 Finished recording The Create Channel: channel 2203
2008-03-27 14:23:16.128 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-27 14:23:16.142 Empty LocalHostName.
2008-03-27 14:23:16.143 Using localhost value of movie
2008-03-27 14:23:16.189 New DB connection, total: 1
2008-03-27 14:23:16.203 Connected to database 'mythconverg' at host: localhost
2008-03-27 14:23:16.213 Closing DB connection named 'DBManager0'
2008-03-27 14:23:16.242 Connected to database 'mythconverg' at host: localhost
2008-03-27 14:23:16.251 New DB connection, total: 2
2008-03-27 14:23:16.254 Connected to database 'mythconverg' at host: localhost
2008-03-27 14:23:16.264 Current Schema Version: 1214
2008-03-27 14:23:18.622 AutoExpire: CalcParams(): Max required Free Space: 202.0 GB w/freq: 15 min
2008-03-27 14:23:18.723 TVRec(1): Changing from WatchingLiveTV to None
2008-03-27 14:23:18.787 Finished recording The 700 Club: channel 2231
2008-03-27 14:23:18.868 Finished recording The 700 Club: channel 2231
2008-03-27 14:23:18.877 MythSocket(ab523800:-1): writeStringList: Error, socket went unconnected.
2008-03-27 14:23:18.937 AFD: Opened codec 0x82a77f0, id(MPEG2VIDEO) type(Video)
2008-03-27 14:23:18.942 AFD: codec AC3 has 2 channels
No accelerated IMDCT transform found
2008-03-27 14:23:18.947 AFD: Opened codec 0x82a7de0, id(AC3) type(Audio)


Could old cheap amplified bunny ears be the problem? Or is it a MythTV problem? Could someone point me in the right direction before I throw time or money at this [hopefully last] problem.

---

### Post by caseyd on 2008-03-27
I am getting an error "almost" identical to the one you are getting however instead of kicking me back out to the menu it just kills the frontend.

2008-03-26 18:35:42.049 MythSocket(82ddeb0:26): readStringList: Error, timeout (quick).
2008-03-26 18:35:42.049 RemoteEncoder::SendReceiveStringList(): No response.
2008-03-26 18:35:42.050 NVP, Error: Unknown error, exiting decoder
2008-03-26 18:35:42.065 MythSocket(82ddeb0:-1): writeStringList: Error, called with unconnected socket.
2008-03-26 18:35:42.065 MythSocket(82ddeb0:-1): readStringList: Error, called with unconnected socket.
2008-03-26 18:35:42.066 RemoteEncoder::SendReceiveStringList(): No response.
2008-03-26 18:35:42.068 TV: Attempting to change from WatchingLiveTV to None
2008-03-26 18:35:42.068 MythSocket(82ddeb0:-1): writeStringList: Error, called with unconnected socket.
2008-03-26 18:35:42.068 MythSocket(82ddeb0:-1): readStringList: Error, called with unconnected socket.
2008-03-26 18:35:42.068 RemoteEncoder::SendReceiveStringList(): No response.

---

### Post by caviidae on 2008-05-05
Just thought I come back and say this was a reception problem. Adjusting my antenna could change the problem. Purchasing a better one fixed the problem.

---

