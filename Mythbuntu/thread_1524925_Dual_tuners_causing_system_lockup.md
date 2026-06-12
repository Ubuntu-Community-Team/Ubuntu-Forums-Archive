---
title: "Dual tuners causing system lockup"
date: 2010-07-06
forum: Mythbuntu
---

### Post by gdselzer on 2010-07-06
I've been running mythbuntu 9.10 with a Hauppauge 850 (using OTA) for several months now and it's been ROCK SOLID.  So I decided to go dual tuner.  I bought a second Hauppauge 850 and added to the mix.  Now the system completely locks up every 2-10 hours.  No ssh, no nothing.  Only way to get it back is a hard reboot.

I have tried running with only the new tuner to see if the tuner is the problem.  It ran for 3 days with no lockups.  It's only the dual tuners that cause the problem.

I've checked the usual logs and can't find anything that looks suspicious.

Can anyone help me troubleshoot this?  Anyone seen the same thing?

Thanks in advance.

---

### Post by LowSky on 2010-07-06
I found these:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-850](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-850)

Basically looks as if they are labeled the same but could be potentially three differrent models depending on when it was purchased. the newest model may not work at all.

[http://www.linuxtv.org/wiki/index.php/Talk:Hauppauge_WinTV-HVR-850](http://www.linuxtv.org/wiki/index.php/Talk:Hauppauge_WinTV-HVR-850)

---

### Post by gdselzer on 2010-07-06
LowSky, I appreciate the reply.  I might be a little confused.  As I said in the original post, when I try using only the new tuner the system runs without a problem.  Is it possible that there is something wrong with the new tuner even though the system runs fine with it by itself?

Thanks

---

### Post by ian dobson on 2010-07-07
Hi,

Do you have EIT (epg over the wire/air) enabled for both cards? 
1) The database updates put the system under quite a heavy load even when your not recording anything. maybe try disabling EIT for one of the cards.

2) Is your powersupply OK? Adding a second tuner puts the powersupply under load (extra if EIT is enabled) so try disabling EIT for one card.

3) If disabling EIT for one card works, then maybe try increasing the EIT timeout (The EIT scanner tunes to a new multiplex less often, reducing the number of database updates/retuning.

Another thing to try is move the cards round to different slots, some cards don't like sharing interrupts.

On my big backend (Quad Core, 8Gb Ram, 12Tb hard disks) I had to increase the eit timeout to about 5 minutes before I got the system 100% stable. Without the long delay I would get alarms from the hardware monitoring that the 12volt supply has dropped too low.

Regards
Ian Dobson

---

### Post by gdselzer on 2010-07-08
ian dobson, you are the MAN!  I disabled EIT on the second card and set the EIT timeout to 5 mins and it's been running solid for 18 hours now.  I'm not quite ready to declare victory yet, but it certainly seems like we are on the right track.

Digging into this a little last night I was surprised to find that EIT runs CONSTANTLY and there is no way to have it run only once an hour/day/etc.  I know that mileage may vary, but my guide data seems to be available for at least the next 24 hours and some channels provide 5 or 6 days out.  Seems like, if I had the option, running EIT once every 2 or 3 hours would be more than acceptable for my needs.  I noticed a few patches to correct this behavior, but I'm not adventurous enough to recompile myth.

If things change regarding my stability situation I'll repost, otherwise I will mark the thread "solved" in the next few days.  Thanks again!

---

### Post by ian dobson on 2010-07-08
Hi,

Glad to hear that my "pain" helped someone. I don't think you can say only update at these times. I seen afew posts on the dev mailing list that someone is workîng on a intelligent EIT scanner that only scans channels channels when there isn't enough EPG data for a channel/multiplex. Of these updates do make it into MythTV then it would be version 0.24.

Maybe try setting the EIT timeout to 10 minutes and enabling both tuners.

EIT problems are usually caused by dodgy hardware (powersupply or hardware conflicts) or the mysql database is overloading the system. I imagine it could be a power problem or an interrupt problem.
 
Regards
Ian Dobson

---

### Post by gdselzer on 2010-07-08
Ian, is there a need to enable EIT scanning on both tuners?  Won't the EPG data from the one be enough?

---

### Post by ian dobson on 2010-07-08
Hi,

One tuner is enough for you to get all the EPG, it'll just take longer for each multiplex. My TV provider only provides EPG for this/next for several channels and if I don't enable both tuners the system sometimes misses recordings as the EPG isn't updated.

I ended up solving the problem by writing a web page scraper/xmltv grabber for the "bad" channels. But this isn't a solution for everyone.

Also if you only enable EIT for one tuner then when the tuner is recording it can't grab the EIT, so maybe enable EIT for te second card.

Regards
Ian Dobson

---

