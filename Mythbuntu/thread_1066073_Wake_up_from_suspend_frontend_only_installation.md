---
title: "Wake up from suspend frontend only installation"
date: 2009-02-10
forum: Mythbuntu
---

### Post by Eldis on 2009-02-10
My problem is when I wakeup from suspend, my mythfrontend starts directly into setup or doesn't start at all. Most of the time it doesn't start. When it does start it goes directly into setup so I have to choose language etc. once I've done it seems to be fine it finds the master backend to which it connects over the lan. Then the frontend will crash and I have to start it up again manually. This requires me to have a keyboard connected to it which I don't want to have.

So if I understand my problem at all I would need to

a) find the correct script to make sure mythfrontend does start, and to start after my networking has started and most likely after my X-server has started (not sure about that).

b) Find a program or find a script to monitor if mythfrontend is running and if not to restart it. (Also would be nice if the script or program could figure out if the the process has become unresponsive and if so kill it and restart it.)

c) (Fixed see post below) Also I have problem with when I manually suspend via power button when I do the wakeup it requires me to enter the password for the user I would like to disable that requirement, just don't know where to do that. When the computer suspends because of idle and I do the wakeup it does not ask for a password.

Any help would be greatly appreciated

---

### Post by Eldis on 2009-02-10
I'd like to mentiom I've managed to fix c)
in /etc/default/acpi-support
```

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true
```

---

