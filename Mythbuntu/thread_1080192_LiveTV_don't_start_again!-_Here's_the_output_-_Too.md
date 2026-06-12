---
title: "LiveTV don't start again!- Here's the output - Too many BUG"
date: 2009-02-25
forum: Mythbuntu
---

### Post by impossibilechecisiaquesto on 2009-02-25
I'm very disappointed, every week i have to fix somthing on my mythtv system.

Now Live tv don't start, it go on black screen for a whike and return to the menu.
 Here's the output.

```


2009-02-25 12:37:01.116 Connecting to backend server: 192.168.1.1:6543 (try 1 of 5)
2009-02-25 12:37:01.117 Using protocol version 40
2009-02-25 12:37:01.176 TV: Attempting to change from None to WatchingLiveTV
2009-02-25 12:37:01.176 Using protocol version 40
2009-02-25 12:37:08.199 MythSocket(82c0da0:32): readStringList: Error, timeout (quick).
2009-02-25 12:37:08.200 RemoteEncoder::SendReceiveStringList(): No response.
2009-02-25 12:37:08.201 GetEntryAt(-1) failed.
2009-02-25 12:37:08.203 EntryToProgram(0@gio gen 1 01:00:00 1970) failed to get pginfo
2009-02-25 12:37:08.203 TV Error: LiveTV not successfully started
2009-02-25 12:37:08.203 TV Error: LiveTV not successfully started
2009-02-25 12:37:08.292 TV: Deleting TV Chain in destructor
2009-02-25 12:37:08.301 DPMS Deactivated 
2009-02-25 12:37:08.302 DPMS Reactivated.


```

---

### Post by newlinux on 2009-02-25
Have you changed anything in your system? Have you installed any updates? what hardware are you using (tuner, vid card, etc.) what is in your backend log? Can you still schedule and successfully record shows?

---

