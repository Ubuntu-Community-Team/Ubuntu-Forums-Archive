---
title: "veoh web player"
date: 2009-07-07
forum: Multimedia Software
---

### Post by pokeyThePenguin on 2009-07-07
Veoh.com has a restriction where you must download their Web player in order to view videos longer than 20 minutes. Otherwise, you only get a 5 minute preview of the video.

The Web player is only available for Windows.

I've never used Wine before. I installed Firefox and the Veoh player using it. Whenever I tried opening up the player, I got the bug splat window asking if I wanted to send the error report or not.

I'm on Jaunty Jackalope.

Have any of you been able to get the Veoh player working? How?

---

### Post by pokeyThePenguin on 2009-07-10
Download the Veoh player: [http://ll-appserver.veoh.com/static/downloads/client/VeohVideoCompassSetup_eng.exe](http://ll-appserver.veoh.com/static/downloads/client/VeohVideoCompassSetup_eng.exe)

Grab two .dll's:
pdh.dll ([http://www.dlldump.com/download-dll-files_new.php/dllfiles/P/pdh.dll/5.1.2600.2180/download.html](http://www.dlldump.com/download-dll-files_new.php/dllfiles/P/pdh.dll/5.1.2600.2180/download.html))
odbcbcp.dll ([http://www.dlldump.com/download-dll-files.php/dllfiles/O/odbcbcp.dll/download.html](http://www.dlldump.com/download-dll-files.php/dllfiles/O/odbcbcp.dll/download.html))

Move those to your system32 directory.

That's all you need to do.

---

### Post by Ignotus Angelus on 2010-05-22
[FONT=Book Antiqua][SIZE=2][COLOR=Navy]Hello,

Is this fix still available with the new 10.04 version of Ubuntu?

Also, I tried to install the Veoh web player, but I'm being told that it is not an executable file (.exe doesn't work?)

Can anyone offer me some pointers about what to do?

Thank you in advance :)[/COLOR][/SIZE][/FONT]

---

### Post by Oriana on 2010-07-24
You have to right click the exe, go to permissions, check the box that says allow as executable. 

[rant] PS, Ubuntu Security Team, you really pissed me off when you sent me to that page. If I want to run an executable I downloaded from the internet, especially after I've gone through the trouble of installing WINE to run it, I very well will. I'm not a complete idiot. [/rant]

Best of luck!

EDIT: Also, success with the version 1.2.2.1112 installer from [http://www.veoh.com/download](http://www.veoh.com/download)

EDITx2: Unselect that success box, I've been working with my graphics and all of a sudden Veoh started seriously bugging me about wanting Flash installed, and even when the program is running it doesn't let me play more than 5 minutes.

---

### Post by luckyprince_pk on 2012-01-16
[B]VEOH player under Ubuntu...
 (Watch full length videos by Veoh) --- Prasad P Kulkarni
 
 The Veoh player now I'm using in Ubuntu!!!
 If you have Wine already installed and also Veoh player installed, the  another condition which is to be satisfied is that you have to install a  web browser in WINE also... And then the Veoh will be added to the  browser you installed under in Wine (Veoh will not work for browsers in  Ubuntu, it'll work for browsers installed under Wine!) That's the  secret...;)
 Though the Veoh player installation file is a windows  (.exe) file, it'll consider the web browser installed under WINE as a  browser under windows!!! So, it'll let you play full length VEOH  videos... Enjoy...[/B]

---

