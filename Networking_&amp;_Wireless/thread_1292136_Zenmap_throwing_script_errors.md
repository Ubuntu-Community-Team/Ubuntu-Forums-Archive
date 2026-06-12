---
title: "Zenmap throwing script errors"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by brianmc on 2009-10-15
I've installed zenmap, plus nmap dependencies.

I edited the menu so it does 'gksudo zenmap' and prompts for a password.

When scanning an IP today I got the following errors:

[FONT=Courier New]Completed Traceroute at 18:57, 0.93s elapsed
Initiating Parallel DNS resolution of 20 hosts. at 18:57
Completed Parallel DNS resolution of 20 hosts. at 18:57, 0.31s elapsed
SCRIPT ENGINE: Initiating script scanning.
SCRIPT ENGINE: '/usr/share/nmap/scripts/dns-test-open-recursion.nse' threw a run time error and could not be loaded.
SCRIPT ENGINE: '/usr/share/nmap/scripts/skype_v2-version.nse' threw a run time error and could not be loaded.
SCRIPT ENGINE: error while initializing script rules:
/usr/share/nmap/scripts/script.db:20: rpcinfo.nse is not a file!
stack traceback:
    [C]: in function 'Entry'
    /usr/share/nmap/scripts/script.db:20: in main chunk
    [C]: ?
    [C]: ?

SCRIPT ENGINE: Aborting script scan.
Host 116.71.50.244 appears to be up ... good.
Interesting ports on 116.71.50.244:
Not shown: 999 filtered ports
PORT     STATE  SERVICE VERSION
1723/tcp closed pptp[/FONT]

---

