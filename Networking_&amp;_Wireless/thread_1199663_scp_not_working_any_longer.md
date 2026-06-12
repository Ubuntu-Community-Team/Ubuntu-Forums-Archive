---
title: "scp not working any longer"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by sumpi on 2009-06-29
Hi all!

I just figured out, that my scp-connections do not work any longer. I am running ubuntu 9.04 netbook remix. I upgraded last week. Today I found out, that scp does not work any longer. I get an error message, when trying to copy files to different servers.
e.g.: scp -r -P 12345 ./localFolder [EMAIL="foo@bar.org"]foo@bar.org[/EMAIL]:/home/sumpi/ gives something like "rite failed: Borken pipe"
Using ssh to connect to the server works fine. Using another pc for connecting via ssh and scp files to the server also works. So there must be something wrong with my openssh-Client.

Thanks in advance for any hints!

Bye,
Sumpi

---

