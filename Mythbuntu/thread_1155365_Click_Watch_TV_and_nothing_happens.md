---
title: "Click Watch TV and nothing happens"
date: 2009-05-10
forum: Mythbuntu
---

### Post by bgolpmp on 2009-05-10
When I click watch tv, the screen goes blank and then the screen comes back on. Everything worked great last night. I am running a hauppauge 500 card. Here is my log.
2009-05-10 17:55:38.223 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-10 17:55:38.442 Using protocol version 40
2009-05-10 17:55:38.609 TV: Attempting to change from None to WatchingLiveTV
2009-05-10 17:55:38.640 Using protocol version 40
2009-05-10 17:55:45.647 MythSocket(a0df958:29): readStringList: Error, timeout (quick).
2009-05-10 17:55:45.648 RemoteEncoder::SendReceiveStringList(): No response.
2009-05-10 17:55:45.648 GetEntryAt(-1) failed.
2009-05-10 17:55:45.650 EntryToProgram([EMAIL="0@Wed"]0@Wed[/EMAIL] Dec 31 18:00:00 1969) failed to get pginfo
2009-05-10 17:55:45.650 TV Error: LiveTV not successfully started
2009-05-10 17:55:45.650 TV Error: LiveTV not successfully started
2009-05-10 17:55:45.697 TV: Deleting TV Chain in destructor
2009-05-10 17:55:45.927 DPMS Deactivated 
2009-05-10 17:55:45.928 DPMS Reactivated.
 
Thanks
Andy

---

### Post by uncle hammy on 2009-05-11
The only time I have seen that problem, my tuners weren't working.  When that is happening, go into INFO CENTER>SYSTEM INFO and check your the status of your tuners.

In my case, I have HDHomeRuns, and the network had come up after the backend, which caused the backend to "think" the tuners weren't available.  As soon as I resolved that issue, I was fine again.

---

### Post by mtbdrew on 2009-05-11
Have you had any power glitches? My MCE180 did this sometimes before I started using a UPS for the Mythbox. Have you tried completely powering down, waiting 15 seconds and then turning back on the box?

---

### Post by ReddogOne on 2009-05-12
Wild guess. Check the initial channel in the backend setup is an actual channel.

---

