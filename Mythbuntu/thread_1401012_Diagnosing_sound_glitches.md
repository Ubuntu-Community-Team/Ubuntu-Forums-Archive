---
title: "Diagnosing sound glitches"
date: 2010-02-07
forum: Mythbuntu
---

### Post by tonycollinet on 2010-02-07
Am getting frequent (a few every 20 to 30 seconds or so then nothing for a few minutes) sound glitches (like a short high pitched squeak) on playing back recordings. Often accompanied by macro blocking.

I've confirmed that it is in the recorded stream, by playing a section again, and getting the glitches in the same place.

I don't think (still to be confirmed) that these happen on live playback.

What is the best way to diagnose the reason.

Might a drive defrag help (is that even needed/possible with xfs?)


Thanks.

---

### Post by azmyth on 2010-02-07
If it's a mpg stream, I'd play it in VLC or mplayer to confirm that the recorded file has a glitch. What I usually do is ssh into MB and export the display and then start the frontend in the console and watch tv or recording and when you see a glitch look at the terminal output to see if it gives you any type of errors or warnings you can research.

---

### Post by tonycollinet on 2010-02-07
I've just tried copying the file to my windows machine. It is pretty much unplayable - constant video skipping in two different players. This has worked fine previously.


EDIT: but another smaller file is ok.

---

### Post by gwagchunks on 2010-02-08
I've had this happen a quite a lot lately. It's usually on most ITV channels or channel 5. I think it's to do with signal strength from the aerial. I used to get around 67-68% which seemed to cope, but recently these channels have gone to around 64-62% and this seems to make a big difference. I'm going to upgrade my aerial and see if this helps.

---

### Post by tonycollinet on 2010-02-09
It did turn out to be fragmentation. Drive was 99.8% fragmented :o

Followed the tips [[COLOR="Blue"]here for a solution[/COLOR]]("http://www.mythtv.org/wiki/Optimizing_Performance#Combat_Fragmentation")

---

### Post by geekyhawkes on 2010-02-13
Thanks for this post / link.  I had not even thought the clitches could be because of myth and put it down to poor aerial etc.

All fixed now and a cron job runs each night for about 30mins.

Ace (+higher waf!)

---

### Post by azmyth on 2010-02-13
Yes, thanks for this info. I never would've thought of this.

---

### Post by geekyhawkes on 2010-04-03
So i have set anauto defrag up each night and fragmentation is now under control, but i am still getting fairly frequent audio glitches.  Is there anything else i can do that would help to reduce these annoying high pitched squeaks (often followed by pixcelation).?

---

