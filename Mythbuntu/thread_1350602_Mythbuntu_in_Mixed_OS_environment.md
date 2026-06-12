---
title: "Mythbuntu in Mixed OS environment?"
date: 2009-12-09
forum: Mythbuntu
---

### Post by pkasin on 2009-12-09
I am interested in using Mythbuntu in a mixed OS environment.  I know that the host software is Ubuntu, but is it possible to run the client software (or another client software) on a Mac or PC?  Or would I have to install Mythbuntu in VMs on each system?

I have 
3 Macs running OSX Snow Leopard or Bootcamp WinXP
1 PC running WinXP (the one I would convert to the Mythbuntu server

Any ideas or suggestions?

---

### Post by gordintoronto on 2009-12-09
According to mythtv.org, it only runs under Linux.  That probably means it would work in a virtual machine, as long as the tuner device can be allocated to the VM.

---

### Post by klc5555 on 2009-12-09
Can't speak to the Mac situation. Mythtv for Windows sort of exists. Discussion, links to source code and to binaries here: [http://www.mythtv.org/wiki/MythTV_on_Windows](http://www.mythtv.org/wiki/MythTV_on_Windows) 
Caution might be in order.

There is also a Windows player app for Mythtv content, "Mythtv Player". It works well enough. It was widely reported as no longer under development, but lo and behold, the author published a new version as recently as 10/29. [http://www.sudu.dk/mythtvplayer/index.php?page=home](http://www.sudu.dk/mythtvplayer/index.php?page=home)

For my own occasional use on my house's one surviving Windows machine, I usually prefer to interact with Mythtv master backend however I need to (scheduling, maintenance, etc.) on a Firefox browser using Mythweb, and stream whatever I want to watch to my Windows player of choice also via Mythweb. No myth frontend software at all. Seems to do better on HD content that way (much less stuttering over fast ethernet) than happens using Mythtv Player (my second choice), but suitable only for watching prerecorded material, not live TV. Mythtv Player can more-or-less do liveTV from a backend as well as recorded material.

---

### Post by newlinux on 2009-12-09
I assume you are talking about frontends.

for info on mythtv on MACs:

[http://www.mythtv.org/wiki/MythTV_on_Mac_OS_X](http://www.mythtv.org/wiki/MythTV_on_Mac_OS_X)
in VMs due to the 
I'd be a little leary of running the frontend in VMs due to video issues, especially if you can use a native client.

---

