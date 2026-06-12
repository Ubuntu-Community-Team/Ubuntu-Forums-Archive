---
title: "Upstart delaying shutdown of mythbackend"
date: 2009-10-21
forum: Multimedia Software
---

### Post by frkstein on 2009-10-21
This weekend I put mythbuntu 9.10 beta onto a new media machine. The problem I have run into is that when issuing the halt command, the shutdown process is delayed as upstart (I think that is what is causing it) tries to keep myhtbackend from terminating. It will attempt about 20 respawns of the process before giving up thus allowing the machine to complete shutdown. How can I get upstart to recognize that this is a shutdown event and not try and respawn the process?

---

