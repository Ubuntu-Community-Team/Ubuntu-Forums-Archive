---
title: "[SOLVED] sound has unexpectedly gone! desperate for help!"
date: 2008-08-09
forum: Multimedia Software
---

### Post by Choad on 2008-08-09
my laptop was left on last night... i fell asleep watching some scrubs. there was something fishy going on last night tho, as when i tried to play music in rhythmbox from a different partition, it went spaz and said they didn't exist, which was quite clearly a lie. but anyway, scrubs was playing fine in vlc so i didn't care.

woke up this...afternoon... and now almost nothing works. avi's will play in vlc, video fine but no audio. in gstreamer they play very, very choppy and still no sound. none of my music will play. the ONLY thing that works is defcon, and that's because it is a maverick among applications and uses SDL sound, which usually causes a headache but today it is at least useful in ruling out my hardware being toast.

i restarted the computer... now it doesn't complain that the music files are missing, but simply won't play them. it doesn't throw an error. you can see the progress slider is not moving so the music is not even trying to play 

please, i am at the mercy of the forums today, i have no idea how to sort this out and it's my primary OS.

---

### Post by ProbablyX on 2008-08-09
Have you tried to update the system?

If you have, try running "sudo alsconf" and have it redetect your sound devices.

---

### Post by Choad on 2008-08-09
system is up to date.

alsconf is not installed. hardy uses pulseaudio.

one more wierd thing, i remember last night that it played the login sound for no reason at all. i have all login sounds disabled! why would it play the login sound?!?!?

i am really losing it atm. *pulls hair out* linux isn't supposed to just mess up for no reason!!

---

### Post by Choad on 2008-08-09
ok the reason for these errors, rather inexplicably, is that i installed cdemu from their sourceforge ubuntu binaries. 

i went back there because it's literally the only modification i made to the system in the last few days... noted the names of the packages, apt-get removed them and it all works now.

what the hell? oh well, at least it works now :)

*puts on some music very loud to relieve the stress that this has caused*

---

