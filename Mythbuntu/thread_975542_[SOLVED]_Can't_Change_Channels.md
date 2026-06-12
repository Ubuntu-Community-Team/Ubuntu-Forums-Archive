---
title: "[SOLVED] Can't Change Channels"
date: 2008-11-08
forum: Mythbuntu
---

### Post by Meph1st0 on 2008-11-08
I just installed 8.10 on a new machine. Hardware config is as follows:

2.0 ghz dual core intel processor
PC-HDTV 5500 tuner
1TB Sata HD
2 GB RAM
Nvidia Geforce 8400 GS
On board audio works with ALSA:Default

When I go to watch liveTV it will bring up the first channel 3.1 and I can watch that channel just fine.  Once I try to change channels it appears to try to change to the channel but seems to fail upon buffering or even earlier.  I get an error message saying, "Error was encountered while displaying video".

I looked in the Log Grabber and toward the bottom of the mythfrontend.log it has the following errors:
```
2008-11-08 11:34:59.865 MythSocket(9c69348:31): readStringList: Error, timeout (quick).
2008-11-08 11:34:59.865 RemoteEncoder::SendReceiveStringList(): No response.
2008-11-08 11:34:59.866 NVP, Error: Unknown error, exiting decoder
2008-11-08 11:34:59.868 LiveTVChain(live-BrownDVR-2008-11-08T11:34:45): SwitchTo() not switching to current
2008-11-08 11:34:59.869 TV: Attempting to change from WatchingLiveTV to None
2008-11-08 11:34:59.881 MythSocket(9c69348:-1): writeStringList: Error, called with unconnected socket.
2008-11-08 11:34:59.881 MythSocket(9c69348:-1): readStringList: Error, called with unconnected socket.
2008-11-08 11:34:59.881 RemoteEncoder::SendReceiveStringList(): No response.
```

I'm not sure what else to look at.  I've never had a problem with the PC-HDTV 5500 tv tuner.  They've always been rock solid..

---

### Post by Meph1st0 on 2008-11-09
bump

---

### Post by foxbuntu on 2008-11-11
Are you using an external video tuner to feed video into your capture card (i.e. cable set-top-box)? If so, have you checked your "External Channel Change Command" is correct? If not have you made sure it is empty?

---

### Post by Meph1st0 on 2008-11-23
I just reinstalled and rather than using the default settings for the partition editor during the install, I specified my own settings.  For some reason that allowed me to change channels properly.

---

