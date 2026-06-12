---
title: "Connection to master server timed out"
date: 2010-05-08
forum: Mythbuntu
---

### Post by mala88 on 2010-05-08
I just upgraded my myth backend from 8.04 to 10.04 and now my conection to the backend is timing out. The FE and BE are on the same machine and the mysql server appears to be running fine.

I can start playing a recorded program, but the timeout error keeps occuring every minute or so. Is anyone else having this problem and do you have any suggestions?

thanks!



mythfrontend.log
```
2010-05-08 14:15:05.457 MythContext: Connecting to backend server: 192.168.1.102:6543 (try 1 of 1)
2010-05-08 14:15:05.460 Using protocol version 56
2010-05-08 14:16:00.552 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-05-08 14:16:01.882 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Arclight/recordings-ui.xml
2010-05-08 14:16:05.682 TV: Attempting to change from None to WatchingPreRecorded
2010-05-08 14:16:06.731 AFD: Opened codec 0x9c508f0, id(MPEG2VIDEO) type(Video)
2010-05-08 14:16:06.731 AFD: codec AC3 has 6 channels
2010-05-08 14:16:06.732 AFD: Opened codec 0x9c51080, id(AC3) type(Audio)
2010-05-08 14:16:06.793 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-05-08 14:16:06.793 Opening ALSA audio device 'default'.
2010-05-08 14:16:06.834 mixer unable to find control Master 1
2010-05-08 14:16:07.100 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-05-08 14:16:07.255 OSD Theme Dimensions W: 640 H: 480
2010-05-08 14:16:07.339 Realtime priority would require SUID as root.
2010-05-08 14:16:07.341 TV: Changing from None to WatchingPreRecorded
2010-05-08 14:16:07.342 Couldn't load deinterlace filter none
2010-05-08 14:16:07.342 Video timing method: USleep with busy wait
2010-05-08 14:16:07.452 ScreenSaverX11Private: DPMS Deactivated 1
2010-05-08 14:16:07.487 MythContext: Connecting to backend server: 192.168.1.102:6543 (try 1 of 1)
2010-05-08 14:16:07.501 Using protocol version 56
2010-05-08 14:16:07.600 MythContext: Connecting to backend server: 192.168.1.102:6543 (try 1 of 1)
2010-05-08 14:16:07.609 Using protocol version 56
2010-05-08 14:16:07.774 Couldn't load deinterlace filter none
2010-05-08 14:16:07.774 Failed to enable deinterlacing
2010-05-08 14:16:08.456 Preview Error: Remote Preview failed, reason given: ERROR_UNKNOWN
2010-05-08 14:16:29.972 Event socket closed. No connection to the backend.
2010-05-08 14:16:30.088 MythSocket(ffffffffa67abed8:-1): writeStringList: Error, socket went unconnected.
                        We wrote 0 of 58 bytes with 1 errors
2010-05-08 14:16:30.089 MythSocket(ffffffffa67abed8:-1): readStringList: Error, called with unconnected socket.
2010-05-08 14:16:30.089 RemoteFile::Read(): No response from control socket.
2010-05-08 14:16:30.089 RingBuf(myth://192.168.1.102:6543/1041_20100508010900.mpg) Error: RingBuffer::safe_read(RemoteFile* .
2010-05-08 14:16:30.493 MythContext: Connecting to backend server: 192.168.1.102:6543 (try 1 of 1)
2010-05-08 14:16:30.495 Connection to master server timed out.
                        Either the server is down or the master server settings
                        in mythtv-settings does not contain the proper IP address
```

---

### Post by mala88 on 2010-05-08
I had monit running in the background and it was causing the timeout issues after the upgrade to lucid. The timeouts went away after I stopped that service.

---

