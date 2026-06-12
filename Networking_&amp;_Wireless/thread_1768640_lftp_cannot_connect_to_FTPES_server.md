---
title: "lftp: cannot connect to FTPES server"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by AugustinMa on 2011-05-27
Hello,


My host has enabled FTPES (See: [http://ouvaton.coop/spip.php?article376](http://ouvaton.coop/spip.php?article376)).
I would like to use lftp to securely upload my files to the host.
However, lfpt hangs at "`ls' at 0 [Connecting...]" when trying to connect. See report here:
[http://linux.overshoot.tv/ticket/176](http://linux.overshoot.tv/ticket/176)

I've already search this forum and the web for days, but there does not seem to be any explicit tutorial for lftp + FTPES.

I've tested filezilla and I can connect without any problems via FTPES. I'd rather use a command line tool like lftp, however.

From what I've gathered, the problem may be with the passive mode, and the fact that the response from the server does not reach my machine.

My machine is running Kubuntu and is behind a d-link router. I don't seem to be running any firewall (is that a problem for a personal computer?). I checked: the router's built-in firewall is disabled. I am not sure about the port forwarding issues, though.

I'd like to use your replies to write a small tutorial: I have found many posts by people experiencing similar problems, but none with an actual answer.

Another question: how can I make sure that any successful connection is indeed made via a secure channel. I can use lftp without problems when I don't use SSH/secure channels. Obviously, I don't want that. What tell-tale signs can I look to to ascertain that I am really securely connected?

Thanks.

Augustin.

---

### Post by AugustinMa on 2011-05-29
I am still searching... :-/

---

### Post by AugustinMa on 2011-06-06
Ok, with some precious help from the lftp mailing list, I managed to solve my problem.

Together with the solution, I have documented a lot of previously undocumented lftp features here:
[http://linux.overshoot.tv/wiki/networking/lftp](http://linux.overshoot.tv/wiki/networking/lftp)

I hope it helps someone.

A.

---

