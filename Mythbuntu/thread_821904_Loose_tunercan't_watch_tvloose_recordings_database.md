---
title: "Loose tuner/can't watch tv/loose recordings database"
date: 2008-06-07
forum: Mythbuntu
---

### Post by steve909 on 2008-06-07
Hello all,
Pentium 4HT 3.2/1Gb ram, sata disk. Mythbuntu 8.04 Nova-T-500 onboard graphics.

The problem: I've installed myhtbuntu and got the Nova-T working, both tuners record fine if I record programs about an hour or two in the future. I've also set up and use a hauppauge mvp as a front end. I'm using over the air program details, ie no xmltv etc.
If I leave the computer running overnight, if I select 'watch tv' the next day the menu blinks and nothing happens. If I select 'watch recordings' then I get a message saying there are no recordings to watch ie the database does not exist, which is not true.
I have run mythfilldatabase straight after the tuners stop working and it runs but at the end returns:
unexpected response to MYTH_PROTO_VERSION: 2ACCEPT

Mythfilldatabase will run usually at other times, so i think this is the big clue, but it means nothing to me.

Running mythbuntu control centre has restarted things and a reboot always cures it but I can't trust mythbuntu to make recordings, which is the whole reason I've installed it. (I was using sagetv).

I followed a post which suggested that USB might be going to sleep, but that hasn't made any difference. Help please, I'd be very grateful.

Steve

---

### Post by nasha on 2008-06-08
When you say the tuners stop working... Are they still recognised under linux, and MythTV isnt able to interface them, or they are 'gone' from both?

Check your MythTV logs after you notice the problem has occurred (the blink you said you were experiencing), and look for what went wrong. You'll find your answer here for sure

---

### Post by steve909 on 2008-06-08
Thanks,
I think thats probably wrong of me to say I loose the tuners, as I'm sure the database of old recordings would still be there. I suspect mysql but I'm not sure. I will check as you suggest though.
I'm not sure how to check the logs, would it be something along the lines of dmesg | grep mythtv?

Thanks for any further help.
Steve

---

### Post by nasha on 2008-06-08
Look in /var/log/mythtv/ this is where the logs are kept.
mythbackend.log will probably provide you with the information you need. Its hard to speculate what the issue is without consulting the logs. Post back with your progress

---

