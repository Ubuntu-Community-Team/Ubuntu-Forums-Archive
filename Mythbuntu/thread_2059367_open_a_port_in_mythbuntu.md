---
title: "open a port in mythbuntu"
date: 2012-09-17
forum: Mythbuntu
---

### Post by linuxhippy on 2012-09-17
I am trying to get my Android player that has the mythremote app working in my installed mythbuntu.  Mythremote wants a port to communicate with my mythbuntu install and defaults to port 6546.  Mythbuntu has ufw enabled.  I googled around and found that this should work from any device on my sub-net:

sudo ufw --dry-run allow from 192.168.2.0/24 to any port 6546

I reset mythbuntu ufw with:

sudo ufw --dry-run reset

When I do a network scan from another pc I find that port 6546 is still blocked.  Am I going about this right?

---

### Post by steeldriver on 2012-09-17
did you really mean --dry-run or is that a typo?

```
 --dry-run
              **don't modify anything**, just show the changes
```

---

### Post by linuxhippy on 2012-09-17
ok, I took out the --dry-run switch and did this:

sudo ufw allow from 192.168.2.0/24 to any port 6546

Then I restarted my mythbuntu pc and then did a network scan from another pc and port 6546 wasn't open.  What am I still doing wrong?

---

### Post by nickrout on 2012-09-18
> **linuxhippy said:**
> ok, I took out the --dry-run switch and did this:

sudo ufw allow from 192.168.2.0/24 to any port 6546

Then I restarted my mythbuntu pc and then did a network scan from another pc and port 6546 wasn't open.  What am I still doing wrong?In mythfrontend you need to allow network control. I can't recall exactly where it is in the setup screens. You'll find it there though.

---

### Post by linuxhippy on 2012-09-18
Got it working-I went into the mythbuntu frontend setup:

Utilities/Setup>Setup>General>9th page>Enable Network Remote and indicate the port (6546).

Then I rebooted the pc.

The interesting thing is that nmap from a networked pc doesn't show port 6546 is down but the mythmote works!

---

### Post by nickrout on 2012-09-18
> **linuxhippy said:**
> Got it working-I went into the mythbuntu frontend setup:

Utilities/Setup>Setup>General>9th page>Enable Network Remote and indicate the port (6546).

Then I rebooted the pc.no need, just restart mythfrontend> 

The interesting thing is that nmap from a networked pc doesn't show port 6546 is down but the mythmote works!
I have noticed that too, and have no idea why!

---

