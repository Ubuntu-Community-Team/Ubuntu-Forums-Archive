---
title: "Video streaming online"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by vradovic on 2007-05-05
What i need to watch this streaming ?

URL
mms://212.200.190.28/k2bb?ctrl=fncJK%2FFVnrZ%40vqKx7dX0P6jDg3K1DTiMIaJXE4pZCpAV%2Fy%2FmonSiqQ%3D%3D

please help

---

### Post by yabbadabbadont on 2007-05-05
That isn't a valid MRL.  Post the correct one.  (every variation I tried of what you posted returned a 404: file not found error)  I would guess that you need the win32codecs installed (they won't work on amd64) though as "mms:" is usually a WMV stream of some kind.  Otherwise, make sure that you have the "bad" and "ugly" gstreamer plugins installed.

---

### Post by vradovic on 2007-05-05
[http://velikibrat07.nadlanu.com/live_stream/#%20Mix%20Kamera%201%20-%20Brza%20Konekcija](http://velikibrat07.nadlanu.com/live_stream/#%20Mix%20Kamera%201%20-%20Brza%20Konekcija)!!

then you need to click on "brza konekcija" (that is big brother in Serbia)


i have installed VLC, totem etc...but i cant open ...i have also mplayer plugin for FF. ...

---

### Post by yabbadabbadont on 2007-05-05
I think their site is broken...
```
/home/daffy $ mplayer mms://212.200.190.25/k1bb?ctrl=fncJK%2FFVnray%2FdTpE6pTi5GQJBKRMW0FG9C36QwTgf0Xuj6dCoFkcg%3D%3D
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(TM) XP 2800+ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://212.200.190.25/k1bb?ctrl=fncJK%2FFVnray%2FdTpE6pTi5GQJBKRMW0FG9C36QwTgf0Xuj6dCoFkcg%3D%3D.
STREAM_ASF, URL: mms://212.200.190.25/k1bb?ctrl=fncJK%2FFVnray%2FdTpE6pTi5GQJBKRMW0FG9C36QwTgf0Xuj6dCoFkcg%3D%3D
Resolving 212.200.190.25 for AF_INET6...
Couldn't resolve name for AF_INET6: 212.200.190.25
Connecting to server 212.200.190.25[212.200.190.25]: 1755...
connection timeout
Resolving 212.200.190.25 for AF_INET6...
Couldn't resolve name for AF_INET6: 212.200.190.25
Connecting to server 212.200.190.25[212.200.190.25]: 80...
Server returned 404:Not Found
Failed to parse header.
Failed, exiting.
Resolving 212.200.190.25 for AF_INET6...
Couldn't resolve name for AF_INET6: 212.200.190.25
Connecting to server 212.200.190.25[212.200.190.25]: 80...
Server returned 404: Not Found
File not found: '212.200.190.25/k1bb?ctrl=fncJK%2FFVnray%2FdTpE6pTi5GQJBKRMW0FG9C36QwTgf0Xuj6dCoFkcg%3D%3D'
Failed to open mms://212.200.190.25/k1bb?ctrl=fncJK%2FFVnray%2FdTpE6pTi5GQJBKRMW0FG9C36QwTgf0Xuj6dCoFkcg%3D%3D.


Exiting... (End of file)

```
Edit: That is the MRL that was embedded in the page to which I was directed.

---

### Post by vradovic on 2007-05-05
but that link works for meny people on windows :(((((((

what can i do?

---

### Post by yabbadabbadont on 2007-05-05
> **vradovic said:**
> but that link works for meny people on windows :(((((((

what can i do?

Use windows....  ;)

---

### Post by rockingmtranch on 2007-05-05
> **yabbadabbadont said:**
> Use windows....  ;)

LMAO  :)

---

### Post by vradovic on 2007-05-05
no i dont want to use windows.


please someone geave me some solution :)

any ideas?

---

### Post by rockingmtranch on 2007-05-05
It won't work for me either. 'Player not responding' each time. I tried.

---

### Post by vradovic on 2007-05-05
i got same message....


can you try with this URL
[http://www.mtsmondo.com/velikibrat/index.php](http://www.mtsmondo.com/velikibrat/index.php)

---

### Post by rockingmtranch on 2007-05-05
> **vradovic said:**
> i got same message....


can you try with this URL
[http://www.mtsmondo.com/velikibrat/index.php](http://www.mtsmondo.com/velikibrat/index.php)

Same result.

---

### Post by vradovic on 2007-05-05
but there is more then 1000 viewer in this moment :((( over windows media player...

do you have any solution for this?

thanks for replays anyway

---

### Post by yabbadabbadont on 2007-05-05
> **vradovic said:**
> but there is more then 1000 viewer in this moment :((( over windows media player...

do you have any solution for this?

thanks for replays anyway

Use windows...  wait for it...  inside of VirtualBox or VMWare.  :D  (A little better solution than my last proposal)

---

### Post by vradovic on 2007-05-05
uffffff that is boring

mebie i can try with windows media player over WINE? but what about codec.....
but i am sure there MUST be solution for this on LINUX!

---

### Post by rockingmtranch on 2007-05-05
> **vradovic said:**
> uffffff that is boring

mebie i can try with windows media player over WINE? but what about codec.....
but i am sure there MUST be solution for this on LINUX!

You would think. I, however, don't know what it is.

---

### Post by yabbadabbadont on 2007-05-05
> **vradovic said:**
> uffffff that is boring

mebie i can try with windows media player over WINE? but what about codec.....
but i am sure there MUST be solution for this on LINUX!

Contact the website owner and (politely) complain about lack of non-windows OS support.  Who knows, maybe they will actually listen.  (there is a first time for everything)

---

### Post by vradovic on 2007-05-05
i ALLREADY TRY THAT. They have live OP on IRC. But they don't know anything about Linux. :(

---

### Post by vradovic on 2007-05-05
any help about this?

---

### Post by rasha on 2007-05-06
I'm looking solution too...
In Windows there are many players that can play this url, but in Feisty none.. I tried many.
Anyway if  I find solution, i will post here...

Veliki Brat rulez!!!!

---

### Post by vradovic on 2007-05-06
really disapointing :((

anyone have some idea?

---

### Post by vradovic on 2007-05-06
anyone here with UBUNTU can watch this mms:// video streaming online?

please report if you can and HOW?

---

### Post by SOME1 on 2007-05-06
This is the solution I found for streaming video: 

first, install this plug in for firefox
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

second, open terminal and run this command
sudo apt-get install  totem-xine

hope it will help you.

---

### Post by vradovic on 2007-05-06
I try that but not work :((((

Can you (or someone) try this for me mebie i miss something :(

mms://212.200.190.24/K1lb

---

### Post by sxtynnmach1 on 2007-05-07
When I was trying to look at a video stream, I right-clicked where the image was supposed to be showing and said "Open in Movie Player"

Movie Player promptly alerted me that a required codec was missing and asked if I would like to search for one.  I said yes and it gave me one option.  I clicked the option and said "OK" to install it.
The video stream worked fine after that.  Make sure that the "Universe" repositories are marked in your Apt/Synaptic options.

Hope that might help.

---

### Post by SOME1 on 2007-05-07
after the 2 steps i wrote you before, I clck right click on the movie in firefox -> mediapalyerconectivity -> choose what I want to see. 
another option is to configure that every time there is media on a web page, the totem player automaticly open. 
if thats what you want, go to tools->MediaplayerConnectivity->options
in the new window choose option and then you will see 2 tabs -> in the second tab you will find an option for automatic play when a media found in a web page. 

I also recommend in the players section to make sure that you configure well the player. 
for example, I configure totem with the command 
/usr/bin/X11/totem
for all the media execept ogg and flash.

good luck.

---

### Post by moonliter on 2007-05-10
Is anyone solved this problem! Help please

---

### Post by moonliter on 2007-05-19
Please help,I am tired of windows!!

---

### Post by moonliter on 2007-05-24
beep! help

---

