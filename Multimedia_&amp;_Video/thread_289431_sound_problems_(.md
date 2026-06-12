---
title: "sound problems :("
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by weird_c00kie on 2006-10-30
about a week ago, out of the blue, i started having problems with my sound. whenever i tried listening to music, the sound would come out all crackly and cheap-sounding. there's nothing wrong with my speakers, because when i play video clips or music from my ipod, the sound quality is perfectly fine.

a friend suggested reinstalling lame, which i did, but that didn't fix anything.
then, yesterday, i lost sound altogether. i followed the Dapper guide for troubleshooting sound ([http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_configure_sound_to_work_properly_in_GNOME)) but that didn't do anything either.

i'm new to linux, so i don't know if there's anything obvious that i'm missing, so any help you can offer would be greatly appreciated.

i don't know if this is relevant or not, but i can't play DVDs anymore either. MPlayer plays them, but the video looks all scrambled, and xine, which used to play them perfectly fine, won't play anymore :(



for the record, i'm running 6.06 on an amd64, in case that affects your comment

---

### Post by weird_c00kie on 2006-10-30
also for the record, my sound card is nothing fancy. it's an integrated one that ubuntu automatically recognised and dealt with when i first installed it without any problems

---

### Post by weird_c00kie on 2006-10-30
well, i used [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449) and got the sound working again

but the crappy quality of music played from the computer is still there :(
any ideas on how to fix that?

i tried "Getting the ALSA drivers from a *fresh* kernel" as described in the thread mentioned above, but that didn't do anything either. the sound is still bad. it also seems to have created some conflict with Beryl, so that doesn't work anymore

---

### Post by weird_c00kie on 2006-11-03
*bump*

problem still there... any ideas anyone?

---

### Post by tommcd on 2006-11-03
Just a guess, but have you considered the possibility that Beryl might be causing the problem? Beryl has been known to be problematic for a lot of people. If all else fails, try uninstalling Beryl to see if that helps.

---

### Post by weird_c00kie on 2006-11-03
well, i don't think it's beryl's fault. beryl stopped working a week or so ago, so i don't run it anymore and the sound is still crap :(

on top of that, it seems to like going out completely randomly, like it did just now

---

### Post by tommcd on 2006-11-04
I don't know why the sound would go in and out randomly. The only thing that comes to mind is a bad speaker wire somewhere, or a poor connection. Or if the sound goes out, try doing 'killall esd' in terminal and starting the audio app again. (This sometimes happened to me with Doom3).
As for the crackly sound, try turning down the volume levels in alsamixer, or just right-click on the speaker icon on the upper-right part of the screen and set the volume to 70-80%. I have noticed distorted sound on some music files and on XMMS with the sound level on 100%.

---

### Post by weird_c00kie on 2006-11-04
thanks for that tommcd. unfortunately, i've run into more problems ([http://ubuntuforums.org/showthread.php?t=292506](http://ubuntuforums.org/showthread.php?t=292506)) so i don't even have access to the terminal now :/


the speakers are fine. they work flawlessly with my ipod, no matter how long i play it for

---

### Post by weird_c00kie on 2006-11-05
well, the problem was fixed. i think it's more or less all explained in my other post here: [http://ubuntuforums.org/showpost.php?p=1720544&postcount=8](http://ubuntuforums.org/showpost.php?p=1720544&postcount=8)

sound seems to be working fine now :) i haven't heard any crackling yet :D



*edit*
YUP! it seems to be working perfectly fine!
i tried some of the songs which sounded REALLY bad before, and they're perfect now :D
WOOT!

---

