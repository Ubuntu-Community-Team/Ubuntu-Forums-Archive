---
title: "Continued problems with Jack D-bus error - Ubuntu Studio 12.04"
date: 2013-05-17
forum: Multimedia Software
---

### Post by jukingeo on 2013-05-17
Hello all,

I have been an avid user of Ubuntu Studio since version 8.04 and I had always stuck with with the LTS version only.  I only upgraded when the support expired, so all in all I only had three versions of Ubuntu Studio: 8.04, 10.04 and now I have 12.04.

I was considering leaving Ubuntu Studio in favor of regular Ubuntu and just loaded up the sound programs I needed.   However, being that Ubuntu Studio is meant for audio/video work, I stuck with it.  However the thing I have the biggest qualm about is the main necessary item needed to connect all the sound related programs together and that is Jack.   While I will say that the idea behind Jack is great, the trouble is in the execution of the program.   The thing is just very buggy and requires a ton of hoop jumping just to get it going.  It's great when it runs, but it is a royal pain in the rear when it doesn't.   Generally out of the box, (or install) it doesn't work.   I was hoping version 12.04 would be different since this version has gotten decent reviews, but low and behold, I started up Jack upon installation and I get this lovely string of error messages:


22:41:59.876 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Fri May 17 22:41:59 2013: Starting jack server...
Fri May 17 22:41:59 2013: JACK server starting in non-realtime mode
Fri May 17 22:41:59 2013: control device hw:0
Fri May 17 22:41:59 2013: control device hw:0
Fri May 17 22:41:59 2013: [1m[31mERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory[0m
Fri May 17 22:41:59 2013: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
Fri May 17 22:41:59 2013: [1m[31mERROR: Cannot initialize driver[0m
Fri May 17 22:41:59 2013: [1m[31mERROR: JackServer::Open() failed with -1[0m
Fri May 17 22:41:59 2013: [1m[31mERROR: Failed to open server[0m
Fri May 17 22:42:01 2013: Saving settings to "/home/geo/.config/jack/conf.xml" ...
22:42:06.516 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

Needless to say, I would like to get this fixed so I can use Jack, but I am curious if somewhere down the road, someone or a group of someones is working on some kind of replacement for Jack.  In the meantime, I have noticed that some programs such as Mixxx and Ardour no longer rely on a Jack connection, and I am wondering if this might be a growing trend...but there still remains the issue of how to connect the programs together, AND there still is a great number of programs that do rely on Jack.

Any help / information would be appreciated.

Thank You,
Geo

---

### Post by jukingeo on 2013-05-18
Anyway have an idea of how to solve this issue?  Anyone? Anybody?  Bueller? Bueller?

I will say at this point in time, if there IS something that can be used other than Jack, I am all ears...or eyes rather.

Thank You,
Geo

---

### Post by jukingeo on 2013-05-19
Hello All,

Ok, as it turned out, I was trying out a new desktop called 'Cinnamon' as I didn't particularly like the bland Xfce desktop that came with Ubuntu Studio.   Anyway, the install, which needed Gnome to install made some changes that I didn't like.   Some things such as dragging and dropping icons to the desktop screen wouldn't work.   Changing themes didn't work properly and there were a bunch more problems.   Upon removal of Cinnamon/Gnome, there was an issue which rendered U-S inoperable.  Needless to say, I had to do a reinstall.   So now I have a fully working desktop back, but an unexpected suprise is that I checked Jack and it is now working.  Hmmmmph!   I guess something must have went wrong with Jack in regards to the Cinnamon install.

Well, I have learned my lesson with changing things and I am going to stick with the Xfce desktop that came with U-S.  As it is, one of the main reasons why I wanted to change the desktop is because it was on top.   Unlike with Unity-Gnome, which my wife has and you CAN'T move the taskbar, last night I found out with Xfce, you CAN put the taskbar back on the bottom.

So I guess this is somewhat solved.   As I am reinstalling my key applications, I am keeping a check on Jack to make sure nothing changes it. 

What I am surprised is that how could the desktop environment affect an audio server?  I would like an answer to that (if possible).

Geo

---

### Post by zequence on 2013-05-30
The desktop doesn't affect jack. 
There are several possible reasons why jack would not start. 
1. pulseaudio is using the card that you are trying to start jack with (this will begin to work smoothly any day now - once the next update to pulseaudio comes through - a bugfix).
2. you are tryingt to start jack with the wrong card (the order of the cards may change at each boot, so you need to select it specifically after each boot)
3. you have both jackd and jackdbus running at the same time (check that with the command: ps -eo comm | grep jack)

Also, I recommend you to to post about Ubuntu Studio stuff in the Ubuntu Studio section of the forum. A much higher chance for you to get help [http://ubuntuforums.org/forumdisplay.php?f=335](http://ubuntuforums.org/forumdisplay.php?f=335)

---

