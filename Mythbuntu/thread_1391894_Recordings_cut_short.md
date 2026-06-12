---
title: "Recordings cut short"
date: 2010-01-27
forum: Mythbuntu
---

### Post by mookie60 on 2010-01-27
Using:
Mythbuntu 9.04
1 - Hauppauge 1600
1 - Hauppauge 150


I've been reliably running mythbuntu on an old Dell optiplex with a 2.6 ghz processor.   Recently I acquired a slightly newer HP/compaq dc7100 with a 3.6 ghz cpu.   

With everything swapped over to the "new" HP, all seems to operate perfectly.   It's even doing a pretty fair job of recording HD channels.   For some reason, however, some recordings are prematurely terminated while recording (a 60 minute program records for something less than 60 minutes, the amount varies).  It doesn't seem to matter which channel, or tuner, is being used.  The segment that is recorded plays back fine.

A couple weeks back I gave up and put everything back in the old Dell, just to have a working machine.   When using the "new" HP as a plain pc (as a ubuntu openvpn server), no odd behaviors are noticed. 

Any suggestions on what may cause this problem.   I've considered the possibility of a weak power supply, but I'm not sure how to test the theory without buying a new supply.

Thanks for any help,

---

### Post by mookie60 on 2010-02-03
bump

---

### Post by larsolav on 2010-02-03
Long shot, but do you still have the backend logs on the HP machine? Maybe some of the backup logs are from the time when the recordings cut short. The logs may be able to shed some light.
Just a thought....

---

### Post by mookie60 on 2010-02-03
Yes, I should have thought to mention the lack of logs.  The HP machine was briefly needed for openvpn duty a few weeks back, and was wiped.

In the meantime, I'd still be open to anyone willing to speculate on possible causes.

As I need to travel for work, I hate to have the working mythbox (Dell) out of service for very long.  So in a couple weeks I should be able to give the switch to the HP another try . . . then, of course, wait for it to error again.

I'm not very familiar with the myth/linux log files; is there one main one, or a particular one I should pay attention to?   I'll be sure to re-post with this info when available . . .

At this point, even guesses are welcome,

Thanks

---

### Post by movieman on 2010-02-04
Are you using 0.21 or 0.22? I've been having the opposite problem on 0.22, with a one-hour scheduled recording sometimes continuing to record for eight hours or more... so there seems to be something odd going on somewhere.

---

### Post by mookie60 on 2010-02-04
I've been using 9.04/.21 without any problems like you described.   The newer .22, on both 9.04 and 9.10 would not scan channels with either the Hauppauge 150 or 1600 (neither digital or analog).  So, I never reached the point where I could record anything at all with .22 

My attempts with .22 were made when 9.10 was first released and I haven't tried it since.   I just switched back to 9.04 and thought I'd try again when 10.04 comes out.

---

### Post by azmyth on 2010-02-04
I was running into this as well but it was only clipping like 10-15 seconds of the show. There are two things you can do. You can set a hard show time ending extender but this will create conflicts and was bumping shows to another tuner which I didn't like. What works best for me is setting a soft ending time extender. Under Settings -> TV Settings -> General (3rd or 4th screen in) I changed time to record past show to 30 seconds. This setting won't create conflicts and bump shows to other tuners.

---

### Post by nickrout on 2010-02-04
try checking that your database is not corrupt.

---

