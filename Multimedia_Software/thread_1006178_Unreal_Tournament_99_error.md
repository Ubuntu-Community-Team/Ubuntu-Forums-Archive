---
title: "Unreal Tournament 99 error"
date: 2008-12-09
forum: Multimedia Software
---

### Post by sonalswaroop on 2008-12-09
Hi all,.
I am very new to Linux. However i used the Loki installer for Unreal Tournament 99 to install it in ubuntu 8.10. It successfully installed. But if i try to play it i get an error in terminal which goes something like this:

Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Bound to Fire.so
Case-insensitive search: Botpack -> ..\System\BotPack.u
Bound to IpDrv.so
appError called:
Class Actor Member Owner problem: Script=48 C++=52
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down

I love this game and I love ubuntu too. So neither i can go back to XP nor leave this game behind. So please help me. 
Thanks

---

### Post by sonalswaroop on 2008-12-09
is no 1 going to help me out??

---

### Post by sonalswaroop on 2008-12-09
what a forum is dis.......
no one turns up to help
ok i m sorry i got a bit angry. 

But sumone shud reply...............

---

### Post by sep332 on 2008-12-09
Patience sonalswaroop!

This isn't an IRC, responses are not instantaneous :-)
This looks like an issue with the Loki installer, or maybe just a library mismatch (the Loki installer is pretty old, IIRC). You would probably have better luck running the game under a recent version of WINE which you can install from the regular Ubuntu package manager.

---

### Post by Matt Yun on 2008-12-09
> **sonalswaroop said:**
> Hi all,.
I am very new to Linux. However i used the Loki installer for Unreal Tournament 99 to install it in ubuntu 8.10. It successfully installed. But if i try to play it i get an error in terminal ...

Unreal 1999 works fine for me under Hardy.  Your problem sounds like the one in this thread:  [http://ubuntuforums.org/showthread.php?t=8053](http://ubuntuforums.org/showthread.php?t=8053)

Another informal "how-to" is at [http://ubuntuforums.org/showthread.php?t=74623](http://ubuntuforums.org/showthread.php?t=74623). That thread deals with UT1999 GoTY (Game of the Year) edition, but you might find it helpful.

Here are some more references:

[Unreal Tournament 1999 - How to Play UT in Linux on Newer Computers]("http://fingel.com/ut/howtos/utonlinux.html")

[http://pressworthly.wordpress.com/2007/05/27/unreal-tournament-goty-on-ubuntu-feisty/](http://pressworthly.wordpress.com/2007/05/27/unreal-tournament-goty-on-ubuntu-feisty/)

[http://www.princessleia.com/UT.php](http://www.princessleia.com/UT.php)

---

### Post by sonalswaroop on 2008-12-10
sorry guys no improvement : i got exactly the same errors
 however thanks for replying
i m sorry i was bit of a ...... out of order....
sorry
just keep the good work on
thanks

---

### Post by sep332 on 2008-12-10
You might have better luck if you ask in the winehq.com forums.

The Wine application database says Unreal should run perfectly, so it should be possible to get this running.

[http://appdb.winehq.org/appview.php?iAppId=90](http://appdb.winehq.org/appview.php?iAppId=90)

---

