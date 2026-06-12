---
title: "Randomize MAC Address on Boot"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by driftless on 2010-07-30
Greetings, I found / home-brewed a solution to this, and wanted to both a) share my findings and b) crowd-check my solution.

SCENARIO: Every time my Ubuntu box loads, I want to spoof a new and random MAC address for my connection.**

SOLUTION:

1) load macchanger from the repositories

This is a simple, well documented, self-explanatory program that requires manual running - we want to automate it.

2) write a small script:
```

#!/bin/sh
# run macchanger at boot
    
    sudo service network-manager stop

    sudo macchanger -A eth1
    sudo macchanger -A wlan1

    sudo service network-manager start

exit 0
```[I]
Note the wlan / eth codes might need tweaking[/I]

3) Save this as macrotator in /etc/init.d/ and make it executable

4) Register the script by running: ```
sudo update-rc.d macrotator defaults
```5) Reboot

As I said above - this is just my attempt that seems to be working on my machine. I would be happy to hear of more elegant solutions.

-Peace, and Net Freedom


** My reasons for this are my own, and not the subject of this thread, but here is one "possible" scenario: One lives / works / travels in a country that heavily monitors / censors / tracks internet usage. A spoofed MAC is one way to help "anonymize" their activity - or at least create a little white noise. Granted it's not a full solution, but its one link in a chain. Another scenario: one just doesn't want a hard-coded address to their machine being broadcast because that concept just bugs them.

---

### Post by Iowan on 2010-07-30
> **driftless said:**
> ** My reasons for this are my own, and not the subject of this thread, but here is one "possible" scenario: One lives / works / travels in a country that heavily monitors / censors / tracks internet usage. A spoofed MAC is one way to help "anonymize" their activity - or at least create a little white noise. Granted it's not a full solution, but its one link in a chain. Another scenario: one just doesn't want a hard-coded address to their machine being broadcast because that concept just bugs them.
Unfortunately, both scenerios fall under "bypassing restrictions" so these forums cannot be used for support.

---

