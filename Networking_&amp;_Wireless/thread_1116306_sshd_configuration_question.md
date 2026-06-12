---
title: "sshd configuration question"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by yavorpap on 2009-04-04
I actually have two questions:
#1: how can I make sshd take username/password information from a database rather than the actual Linux users or a file and
#2: is there a way to reroute all commands sent through ssh so that when the user writes "X" as a command in the shell the action done on the server to be "commandhandler -command X" or something like it.
As you might have guessed I want to make sshd to work as a server that only pretends to do the commands sent rather than actually doing them.
I have read that it is possible to make a command execute differently by "alias"-ing it in the shell rc file, but how can that be done to all commands?
Last, sorry if I have posted in the wrong category, I'm new here.
Thanks a lot.

---

