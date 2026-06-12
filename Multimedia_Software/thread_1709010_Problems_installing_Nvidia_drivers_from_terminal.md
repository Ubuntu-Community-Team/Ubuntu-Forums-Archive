---
title: "Problems installing Nvidia drivers from terminal"
date: 2011-03-17
forum: Multimedia Software
---

### Post by tweezak on 2011-03-17
Ok...I created this thread in the General Help forum but it after bumping it once it has dropped down 6 pages with no replies. I've gotten great help here in Multimedia (and it is sort of multimedia related) so I'm going to try here. I'll apologize in advance if this is bad form but I need help.

Here's the context of my question:

Ubuntu 10.10

I'm trying to install Nvidia drivers and need to get out of X to do so. I hit Ctrl+Alt+F1 and am asked for my login.

I enter my login and password and get kicked right back to the login prompt after this message:

Cannot execute ksh: no such file or directory

I had switched to ksh by default back when I first installed Ubuntu. I  am afraid I don't remember what changes I had to make in order for it to  be default for me but there's obviously some script I edited that is  running at boot time.

I tried doing this:

```
sudo usermod -s bash username
```but then I just get the same complaint but it says it can't execute bash now.

Does anyone have any ideas where I might have set my configs for shell preference?

Thanks

---

### Post by tweezak on 2011-03-19
Nobody?

---

### Post by BicyclerBoy on 2011-03-19
Not a solution to the default shell..
But you can find the latest driver in 3rd party ppa as pre-compiled binary with full package management so no more kernel header/update dramas..

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=maverick]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates?field.series_filter=maverick")

---

### Post by tweezak on 2011-03-22
> **BicyclerBoy said:**
> Not a solution to the default shell..
But you can find the latest driver in 3rd party ppa as pre-compiled binary with full package management so no more kernel header/update dramas..

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=maverick]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates?field.series_filter=maverick")


I'll be trying that tonight! Thanks, BicyclerBoy! 

FWIW...I'm also an avid cyclist.

Current Fleet:
08 Salsa Moto Rapido (built up in 09)
09 Redline Conquest
09 Orbea Onix TDA

---

