---
title: "PXE install - desktop vs server"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by paulciv on 2009-04-09
I have had a fully working PXE network installation for some time and I understand how all that works.

What I can't work out is how to perform a server edition install versus a desktop edition install?

Are there any simple switches or flags that can be passed to the kernel for this?

I read a comment that this can be done with a preseed file, what kind of definitions are needed?  Or where can I find a sample file?

---

### Post by paulciv on 2009-04-09
For the moment I have solved this with a preseed file.

Added to the APPEND in pxelinux.cfg:

preseed/url=http://nn.nn.nn.nn/ubuntu-server.seed

The preeseed file was obtained from the server ISO in /preseed.

This all works but seems like quite a convoluted way to achieve this, ie. having to download the whole ISO, set up an HTTP server, etc.

It would be nice if there was a simple flag that could be added instead of having to do a whole preseed set-up.

---

