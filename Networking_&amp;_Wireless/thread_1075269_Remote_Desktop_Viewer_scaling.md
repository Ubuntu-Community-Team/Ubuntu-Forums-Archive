---
title: "Remote Desktop Viewer scaling"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by garbetjie on 2009-02-20
Hey guys and girls.

I'm wondering, is there a bug with the remote desktop scaling available in the default remote desktop client that ships with Ubuntu?

I've tried to enable it on mine, but I keep getting an error message stating that "Scaling does not work properly on composited windows. Disable the visual effects and try again.".

Anyone else encountered this? If so, how did you overcome this issue?

Really appreciate any help.

PS: For the record, I'm connecting to a Windows XP Home machine through my Ubuntu 8.10 installation, and my laptop's resolution is 1280x800, with the Windows machine having a 1280x1024 resolution.

---

### Post by win2456 on 2009-02-25
Same problem here... I've researched a lot but did not find a solution.  I too am running 1280x800 and connecting to a windows machine.

I think the issue maybe specific to the NVIDIA card shipped with our laptops.  Scaling doesn't work for me even if I use xvnc4viewer, tightvnc, or other clients.  There is no issues with the Windows machine as scaling works perfectly when I connect from other Ubuntu/Linux and Windows workstations.  I have a D830.  Anyone else facing the same issue?

---

### Post by SkarpHedinn on 2009-03-11
I'm facing the same problem. Most of the research I've done on the issue result in folks suggesting ssh with X forwarding. While this is a fine solution for accessing programs installed only on the remote computer, it's not particularly helpful in aiding a remote user (girlfriend) who you may want to teach (explain for the millionth time) how to do something. I feel bad complaining about it, but the scroll bars are a real nuisance.

---

### Post by SkarpHedinn on 2009-03-11
Found one: KRDC. Tested it on my laptop and it works well. Of course, it will require installing all the KDE dependencies. :-k

---

### Post by openhacker on 2009-10-10
I have a similar problem -- its very frustrating.

I had no problem running ubuntu 7.10 -- upgrading to 8.10 I have a problem.

So I copied the one over from 7.10 (along with all the attendant libraries I needed).
[INDENT]leisner@asus:~$ cat ~/bin/krdc
#! /bin/bash

export LD_LIBRARY_PATH=/home/leisner/lib:$LD_LIBRARY_PATH
exec krdc.old.bin $*
leisner@asus:~$ krdc --version
Qt: 3.3.7
KDE: 3.5.8
Remote Desktop Connection: 3.5.8

[/INDENT]

I haven't found a good solution to this -- and I don't think its a GOOD error message, since the old software seems to work...

ugh!!

marty

---

### Post by erkorb on 2010-09-19
Can you explain what libraries you added to support this.  I'm not using KDE at my main desktop manager.  I'm using GNOME.

Thanks.
Erok

---

