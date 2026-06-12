---
title: "Recordings quit after 5 to 10 minutes"
date: 2015-05-19
forum: Mythbuntu
---

### Post by Jim_Lemanek on 2015-05-19
All of my TV recordings quit after 5 to 10 minutes. All channels all TV shows. I looked at the recording files and VLC shows the length of the recordings to be 5 to ten minutes in length. I am using Mythbuntu 14.04 on a PC with an Intel Core i5 3.3 GHz processor, 16 GB Ram and a 240GB solid state drive with 200 BG Free. Any ideas as to what to look for would be appreciated.

---

### Post by khPWXxF on 2015-05-20
Hi jim,
I'd start with the backend log.
```
less /var/log/mythtv/mythbackend.log
```
If you see nothing at the time of the failure, you may need to look at the time the recording was scheduled to finish (because some failures are only recognised then).
You may need to give more details such as what you are trying to receive, your source of signal and your tuner card.  Are other receiving devices ok?  New installation or a mature one which has just started giving this problem?


Phil

---

### Post by Jim_Lemanek on 2015-05-20
I looked at the backend log and there are no errors. I am using a HD Homerun dual tuner attached to an over the air antenna. The backend is a month old and until now was working fine.

---

### Post by khPWXxF on 2015-05-20
OK, I don't use your device but my guess/prejudice is to look at signal strengths.  I do not know where you are (usa?) but radio waves work much the same everywhere.  My previously stable setup gave your symptoms after a period of heavy rain - a new downlead fixed it.  TV was OK throughout though.  Any clues here?

[https://www.mythtv.org/wiki/DVB-T_Reception_Problems](https://www.mythtv.org/wiki/DVB-T_Reception_Problems)

What is your signal strength like? Is this your device and how to find out?

[https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Prime](https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Prime)

Hth
Phil

---

### Post by Jim_Lemanek on 2015-05-21
Thank you for the idea. My TV has a signal strength function and my signal strength was under 60% and signal quality 80. I rotated the antenna and have 78% strength and quality 0f 100. I shall see how the recordings go this evening and let you know what happens.

---

### Post by benlyboy on 2015-05-23
Hi I'm having a similar problem my system. I'm using a HD homerun prime. When I record it looks like all is well, but a closer look will show that even though front end is showing that the program is recording it in fact stopped after a couple of minutes. My system is hooked to cable. It seem that I only have the problem on the higher channels, those requiring a cable card. Any ideas?

---

### Post by Jim_Lemanek on 2015-05-24
The rotating the antenna did not fix the problem. I used the HD Homerun Config and it shows my signal strenght was under 75% and was highlighted with yellow. I looked at all of my antenna cable connections and the antenna connector had some corrosion. I cleaned it up and now the signal is over 90% and highlighted in green. The recording problem is still there. I reinstalled Mythtv, using the package manager and the problem is still there. I ordered a new HDHomerun Extend. My current HDTuner Dual is 5 years old and maybe it is the problem. The tuner should be here by Wednesday and will post the results.

---

### Post by Lester_Burnham on 2015-05-25
Hi,

I wonder if it's something like a power supply failing after 5-10 mins once tuned. I thought I'd read on the mailing list about power supply issues with some of these things. Do you have another power supply you can try.

Lester

---

### Post by Jim_Lemanek on 2015-05-25
Thank you for the idea. I think if the power supply was the problem it would stop live TV watching. I can watch live TV with no problems.

---

### Post by khPWXxF on 2015-05-25
Jim,
  we've been looking at factors other than Mythtv software bcause that appeared to be the issue.
Are you saying that 
a)  you can regularly and reliably watch TV via the Mythtv menu but that recordings fail?  Or that
b)  your TV is reliable  or
c) both are true.

Phil

---

### Post by Jim_Lemanek on 2015-05-25
"a)  you can regularly and reliably watch TV via the Mythtv menu but that recordings fail?" is what is occurring.
Jim

---

### Post by khPWXxF on 2015-05-26
You have two tuners and I assume you have multirec with a total of four logical tuners.  Could you start four simultaneous manual recordings calling them (say) A B C and D.  All on same program. Note which tuner is being used for each on the forthcoming recordings page.
Do the failures follow your first physical tuner?
Phil

---

### Post by khPWXxF on 2015-05-26
PS Where are you getting your scheduling information from?  Is this relevant?
 [https://forum.mythtv.org/viewtopic.php?f=36&t=795](https://forum.mythtv.org/viewtopic.php?f=36&t=795)
Phil

---

### Post by Jim_Lemanek on 2015-05-26
I am using Schedules Direct and do not see how that would cause the recording to fail. I got an idea after you comment about two  tuners. I recorded two shows, selecting a different tuner for each show.  The recording from Tuner 1 was fine, the recording from Tuner 2 quit  after 4 minutes. I recorded one show using Tuner 1 and the recording was  good. Tried the same with Tuner 2 by itself and the recording quit  after 4 minutes. I switched the tuner antenna input connections and  Tuner 1 worked fine and Tuner 2 had a short recording time. The new  HDHomerun is scheduled for delivery on the 27th. I will post the results  after I get it set up.
Jim

---

### Post by khPWXxF on 2015-05-27
I was just trying to confirm that you were not using SD and EIT together.
As for your tuner, could it just be that one tuner has a slightly lower gain than the other and that your antenna and/or distribution system is weak?
Is there a signal strength & quality utility for your tuners?  What does that say.
Phil

---

### Post by Jim_Lemanek on 2015-05-27
HDHomerun has a utility that shows signal strength. With the old tuner I was getting signal strength readings in the low 90% range. I installed the new tuner and all channels now read 100% signal strength. I recorded two shows and let Mythtv select the tuner. Both recordings were error free. The problem was tuner 2 in the old HDhomerun device. Thank you all for the ideas.
Jim

---

