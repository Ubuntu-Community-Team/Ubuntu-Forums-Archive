---
title: "Attempting config twin Hauppauge HVR-1600 tuners and QAM-256"
date: 2010-11-03
forum: Mythbuntu
---

### Post by stratoscape on 2010-11-03
All, I am trying to configure twin HVR-1600 and after getting the $@^#% kicked out of me I think I finally have them in and loading. Next I only want to record QAM-256 unencrypted from my provider COX Cable (ugh...) and believe I was able to scan, and lock in the free stuff which is all I want. Finally, did a

cat /dev/video0 > test.mpg

and this is where the wheels fall off the wagon :-( 
performed several of these test and once success short cat test yield 720x480 clear video but cannot repeat/duplicate results, I'm totally stuck. Also, have tried moving cable from TV -> Digital and vice versa, cannot pick up QAM-256 stuff on Digital port, wierd had to use analog side, same with my ATI cards

When I open frontend -> watch TV I get the Please Wait... Then nothing, back to selection. I have a strong feeling this is encoder or even player problem but I lack the advanced brain cells to figure this out. any advice or assistance greatly appreciated could not get more of log to post so this is what did

Frontend.log
[http://pastebin.com/utwbiE90](http://pastebin.com/utwbiE90)

Backend.log
[http://pastebin.com/RQMv0WNt](http://pastebin.com/RQMv0WNt)

cx18_info
[http://pastebin.com/Cy5UuBZ4](http://pastebin.com/Cy5UuBZ4)

thanks,

---

### Post by stratoscape on 2010-11-04
Ok, I now know that the /dev/video is for the analog side but I can't  figure out the equivalent for the dvb side.  I have tried cat /dev/dvb/adapter0/frontend0 with no success is there a capture test for the dvb port also tried vlc

Thanks,

---

