---
title: "Remote Desktop and NVIDIA drivers problem"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by mekazu on 2009-06-06
Background: I've recently installed ubuntu 9.04 with a clean install. Remote Desktop ran fine when I first installed ubuntu but since installing ```
NVIDIA accelerated graphics driver (version 173 or 96)
``` using Administration > Hardware Drivers there is a problem:

Problem: I can connect to the ubuntu machine (using screen sharing on my mac) and it brings up the screen, the menu, any windows, exactly as it should but after that it doesn't update and appears frozen. If I refer to the ubuntu machine's monitor I can see that the machine is still responding to the remote desktop cursor movements, mouse clicks and key presses. Basically this means I can control the ubuntu machine from the remote client's keyboard and mouse but I need to use the physical monitor to see what's happening on the screen. Make sense?

Is this a known issue? How do I get screen updates without uninstalling the driver?

---

### Post by Famine on 2009-06-08
Hey there.  Mine is doing the EXACT same thing.  Tried the latest 185 nvidia drivers too.  Same issue.  Screen sits there paused, but it still recieves mouse and keyboard actions from a remote computer.

=(

---

### Post by superprash2003 on 2009-06-08
go to system->pref->appearance and under effect select NONE.. also make sure that compiz etc is not running..its a bug
for reference : [http://www.prash-babu.com/2009/05/how-to-fix-vnc-error-page-does-not.html](http://www.prash-babu.com/2009/05/how-to-fix-vnc-error-page-does-not.html)

---

### Post by Famine on 2009-06-09
THANK YOU!! This has been bugging me for days!

---

### Post by jmap82 on 2009-06-09
I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.  I'm no wiz at this stuff, so it may not be the best script ever, but you're welcome to use it if you want.

You can copy and paste from my wiki, [_here_]("http://script.jmap82.com/doku.php?id=jmap82sscripts:monitor").

Hope it helps :)

---

### Post by tjes on 2010-03-13
Thanx guys
 

 I was about to give up, but it works great now :-)

---

