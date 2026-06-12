---
title: "hauppauge PVR-150 Remote not working"
date: 2009-05-26
forum: Mythbuntu
---

### Post by swraman on 2009-05-26
I know theres a million threads on this, but like everyone esle i have tried everything and nothing seems to work.

I just did a fresh install of mythbuntu (latest version) and got everything setup.

My remote doesn't work.  Im using this remote (and the card is a "Wintv-pvr-150"):
[http://dark.ellende.eu/htpc/specs/tvkaart.jpg](http://dark.ellende.eu/htpc/specs/tvkaart.jpg)

I chose "Hauppauge TV Card" during setup, and thats what it is in mt MCC.

I tried running "irw" to see if there is any connection to the remote, but I get the error:
> xxx@media-machine:~/Desktop$ irw
connect: Connection refused


The remote connects through the ~1/8" jack on the Hauppauge card, not via USB.

This has been bothering me for months now, id appreciate any suggestions.

THanks

---

### Post by swraman on 2009-05-26
Bump.

Does anyone have Mythbuntu running with the Hauppauge PVR-150 and a working remote:

[IMG]http://gbpvr.com/pmwiki/uploads/Hardware/new_remote_medium.jpg[/IMG]

Appreciate any help, Id much rather use Ubuntu than Mythdora or windows (which both have their own problems with my setup as well).

Thanks

---

### Post by donjski on 2009-06-12
I have the same problem in version 9.

---

### Post by donjski on 2009-06-12
I just got it to work in version 9. In the myth control center under IR transmiters, don't enable one. Make sure you have Hauppauge TC Card set for your remote. I don't have dynamic button mapping checked.

---

