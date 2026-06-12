---
title: "Integrated VIA 82xx Audio problem"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by Myrgen on 2006-08-11
I am new to Linux, and installed Ubuntu 5. I was very happy with it, no problems at all. Then I upgraded to Dapper Drake 6.06, and problems started popping up.
1) Video started 'hiccuping'
2) Audio was hiccuping too
3) Mouse pointer is sluggish, making it a nightmare to do anything
4) Eventhough the system recognizes a blank disk inserted, when trying to burn it, it asks me to insert a new blank disk, eventhough I tried even with a very little file.
After doing a full reinstall, I added updates and apps one by one, changing some settings, one by one, rebooting each time. I finally found out that the source of the problem was: the sound card:
The system set the 'camera' as the default sound card, (Logitech webcam), shows only the microphone properties in the toolbar, and when I changed it to the VIA 82XX integrated sound card I have and rebooted, the sluggishness of the mouse came back with all the other issues.
I reset the default to 'camera', rebooted, and everything was fine again.
Everything except that I have no sound, hence no video either ](*,) 

Any idea, advice, suggestion? any help would be greatly appreciated.

***UPDATE*****
I followed the steps in the Comprehensive Sound Problem Solutions Guide, [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")
up and including point (4). Everything looked fine. Then I rebooted... and the problems listed above returned. :(
Hence, I'm back to square one..

---

