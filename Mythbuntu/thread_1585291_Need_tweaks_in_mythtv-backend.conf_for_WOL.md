---
title: "Need tweaks in mythtv-backend.conf for WOL"
date: 2010-09-30
forum: Mythbuntu
---

### Post by huffcs on 2010-09-30
I have run into problems trying to get remote FE systems to successfully wake up the MBE from hibernation using WOL and connect to mythbackend.  Part of the problem appears to be that mythbackend is sometimes being started before "outside world" ethernet connections (e.g. eth0 and/or wlan0) are active and also before the ivtv driver has finished reconstructing the /dev/video* devices and changing their user/group ownerships to ones that mythbackend can access.  As a result, mythbackend may timeout and the MBE start shutting down before the network connection from the FE is even possible, or the mythbackend is running, but has looked too soon for video input devices and found none exist.  The solution would seem to be to adjust/add constraints in the mythtv-backend.conf start clause, but I can't find enough info to figure out how to do all of what's needed.

The current version of mythtv-backend.conf included with Mythbuntu 10.04 includes the clause:[INDENT]        start on (local-filesystems and net-device-up IFACE=lo)
[/INDENT]What I think needs to be there is something like the following:[INDENT]         start on (local-filesystems and net-device-up IFACE!=lo and started ivtv)
[/INDENT][except there is no upstart module named ivtv.conf]
or[INDENT]         start on (local-filesystems and net-device-up IFACE!=lo and device-added SUBSYSTEM=video DEVPATH=video*)
[/INDENT][except I don't know if that is syntactically correct and sufficient to ensure the device(s) /dev/video* has/have been defined and the user/group ownerships assigned]

Is there some kind of dictionary or catalog of upstart events and qualifiers that I missed, tucked away on the system somewhere?

Any help would be appreciated.

---

### Post by ian dobson on 2010-09-30
Hi,

Why not just add a pre-start script that just sits waiting until the /dev/videoX exists.

```
pre-start script
    # wait for listen on port 80
    while ! [ -e /dev/video0 ]; do
        sleep 1;
    done
end script
```

Note this is untested, but I think the syntax is correct.

Regards
Ian Dobson

---

### Post by huffcs on 2010-10-03
Thanks for the suggestion Ian.  I'll put that on my next-to-test list.

There's always (unlike my last boss' claim) more than one way to skin a cat.

I was hoping to gain more understanding of the upstart system and what can/can't be done with the start clause as well as fixing the immediate issue.  In the meantime, I have been trying to address the root problem in other ways (e.g. changing the wait times for mysql startup and mythbackend startup and the number of attempts for each in the MythTV DB).  Still looking for documentation that will better explain the upstart scheme.

---

### Post by ian dobson on 2010-10-03
Hi,

With upstart you can produce as complex startup chains (start this when that and the other is finished) as you want. Every conf file starts on the specified "start on" stanza and can emit events that other processes can consume.

I found the upstart documentation abit missing/too generalised and written more like a RFC and you need to add 1 to 1 and get 3 to understand how the whole thing is put together.

Regards
Ian Dobson

---

