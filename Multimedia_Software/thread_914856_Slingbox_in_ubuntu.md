---
title: "Slingbox in ubuntu"
date: 2008-09-09
forum: Multimedia Software
---

### Post by fraswesseltet on 2008-09-09
Kubuntu Feisty Fawn

I tried using [these instructions]("http://www.cyberpunkcafe.com/page.php?74") for getting SlingPlayer to work.  I was able to install it (using wine), but got the following error(s) when trying to run it:

err:module:import_dll Library gdiplus.dll (which is needed by L"C:\\Program Files\\Sling Media\\SlingPlayer\\SBCore.dll") not found
err:module:import_dll Library SBCore.dll (which is needed by L"C:\\Program Files\\Sling Media\\SlingPlayer\\SlingPlayer.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Sling Media\\SlingPlayer\\SlingPlayer.exe" failed, status c0000135

Anyone have success with Slingbox and able to make some suggestions?  I'm fairly green with Linux.

---

### Post by RDV on 2008-09-09
The error message says you are missing the "gdiplus.dll". You can download the gdiplus.dll from [http://www.dll-files.com/dllindex/dll-files.shtml?gdiplus](http://www.dll-files.com/dllindex/dll-files.shtml?gdiplus) 

Once downloaded put the dll in WINE's 
"/home/USRNAME/.wine/drive_c/windows/system32" directory
Remember to substitute "USRNAME" for your own user name. 

The gliplus.dll is the most common dll that needs be added to WINE for some Windows programs to work.

Good Luck

---

### Post by fraswesseltet on 2008-09-09
So is the SBcore.dll also needed?  I'll try them out when I get home from work.  Thanks.

---

### Post by RDV on 2008-09-09
From how I read the error message SBCore.dll was calling gdiplus.dll and could not find gdiplus.dll so Slingbox aborted. I believe that SBCore.dll is a Slingbox dll so was installed with Slingbox.

Good luck.

---

### Post by formol on 2008-09-23
hello

i got the very same problem.  the solution is to install Windows Media Player 9 into Wine with the instruction on the Wine DataBase.  a .ddl is missing, i don,t remember witch one, but it's on the WineDB website.

after that, it will work, it's very slow to connect, but once it connected, it's great.  i can watch TV on my laptop while washing the dishes!

---

### Post by knattlhuber on 2008-09-29
You should try this:

[http://www.slingcommunity.com/group/discussion/26840/Slingplayer-Linux-Install-Script-1.0xb]("http://www.slingcommunity.com/group/discussion/26840/Slingplayer-Linux-Install-Script-1.0xb")

You need an old version (< 1.0) of Wine to make it work, but then it works great.

---

