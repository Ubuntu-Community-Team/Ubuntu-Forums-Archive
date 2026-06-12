---
title: "sudo error in mythwelcome log..."
date: 2009-12-21
forum: Mythbuntu
---

### Post by djm-uk on 2009-12-21
Posting this in case it helps someone else!!

I had trouble getting shutdown from mythwelcome to work (Mythbuntu 9.10 / Mythtv 0.22 installation). It would sometimes work and sometimes do nothing. Looking in the mythwelcome logs there was a sudo error like 'no tty and no askpass configured' but the commands (set wakeup time, shutdown command & restart command) configured in the mythwelcome setup were in the sudoers file and tested fine from a command prompt.. FINALLY realised that the backend runs a 'sneaky' 'sudo mythshutdown..' from within it's code (Not even set by one of the configurable options) so once /usr/bin/mythshutdown was added to sudoers it was OK. 

Shouldn't this be setup by the installer or at least documented??!!

David

---

