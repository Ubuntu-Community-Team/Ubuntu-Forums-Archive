---
title: "TerraTec Cinergy T Pcie Dual Problem"
date: 2012-05-03
forum: Mythbuntu
---

### Post by rrofes on 2012-05-03
Hello,
I have a new TerraTec Cinergy T Pcie Dual with two tuners. Trying to test this card with mythbuntu 11.10: I had to download & compile drivers to get this card recognised.
Now mythtv sees the two tuners. They are slightly different:
Tuner with chipset DRX-3913K: DVB-C + DVB-T
Tuner with chipset DRX-3916K: DVB-T + analog
For one of the tuners (not sure which of both), I can configure it properly for DVB-T and make a channel scan, I choose "Spain" and finds all the channels.
The problem is with the other tuner: it seems that is recognised by mythtv only as DVB-C capable, because when I try to make the scan I can only choose "germany" or "UK" as countries, and if I do the scan with any of these two countries it finds nothing.
That's it. Can someone give advice of what am I missing? A little lost right now...
Thanks,

---

### Post by Sctmon on 2012-05-03
It did work for me and it found 2 dvb-t tuners. I just downloaded 12.04 yesterday and was going to start installing today so I will see how I get on.
Strangely though I did a fresh install of 11.10 and built the drivers 3 times in a row and it only loaded the drivers properly on the 3rd try. Can't figure out why.

---

### Post by Sctmon on 2012-05-03
I have had a lot of trouble getting it to work today. I did a fresh install of 12.04 and then built the Linux TV drivers, rebooted and the drivers didn't load. I tried a couple more times and finally got them to work but the second tuner does seem be initialising as DVB-C.

It is beyond me how to set it to DVB-T manually so hopefully someone else can help.

---

### Post by rrofes on 2012-05-04
That's exactly what happens to me!!! If it worked for you some weeks ago with two tuners maybe there's been some difference in the driver or in mythtv since then. I think we're quite lost right now... Help from someone more experienced would be great!

---

### Post by Sctmon on 2012-05-04
I think I must have just gotten lucky. I repeatedly re installed 11.10, then the drivers and eventually after a number of attempts the card just worked. I have not been able to get the card to work at all with fresh installs of 12.04 then building the drivers but did manage to upgrade the working 11.10 system I had to 12.04 but that is when the second tuner stopped initialising to DVB-T.

More help from someone who knows about this please!

---

### Post by rrofes on 2012-05-04
I just got an answer from what I think is the developer of the driver for my card (Stefan Ringel):

### quote ###
Hello Roger,
the driver use the new DVB-v5-API. It use a frontend pro tuner (not all apps using the right call to switch between dvb-c and dvb-t - i.e. mythtv).
### unquote ###

Then this suggests that it is a mythtv bug, if I understand well.
Some mythtv-guru knows something about that?
Is there any way to override mythtv wrong setting and force the tuner to DVB-T "mode"?

---

### Post by Sctmon on 2012-05-04
The problem with the driver has been mentioned in the mythtv-dev mailing list so I may post that info and see what happens.

---

### Post by rrofes on 2012-05-04
More information from Stefan Ringel, just in case someone finds it useful:

dvb-v3-api:
tuner0 -> frontend 0 -> dvb-c
tuner0 -> frontend 1 -> dvb-t
tuner1 -> frontend 0 -> dvb-t

in dvb-v5-api:
tuner0 - > frontend 0 -> all (for terratec cinergyt pcie dual -> dvb-c and dvb-t)
tuner1 ->  frontend 0 -> all (for terratec cinergyt pcie dual -> dvb-t)
----------------------------- =^ "a frontend per tuner"

that is the difference between both apis.

---

### Post by Sctmon on 2012-05-07
OK, I got it to work finally.

intstall dvb-utils from here [http://packages.debian.org/sid/amd64/dvb-tools/download](http://packages.debian.org/sid/amd64/dvb-tools/download)
If you dont have amd64 start [here]("http://packages.debian.org/sid/dvb-tools")

You need to stop the backend running to change the adapter settings so I just ran the backend setup then 
In terminal type:

```
dvb-fe-tools --adapter=1 --frontend=0 --set-delsys=DVBT


```Now the second tuner should work normally set to DVB-T

I just need to figure out how to get that to happen at startup before the backend runs.

---

### Post by rrofes on 2012-05-07
Many thanks Sctmon. I walked the same path on my side last weekend, I got the 2nd tuner working too, they told me about dvb-fe-tools at mythtv maling lists. I still have not tried to automatically do it, so if you find a way to make it before the backend starts, just let me know! I suppose one way would be /etc/rc.local, or I think that there are some folders where to put scripts you want executed at each runlevel: rc0.d rc1.d ... rc6.d. I will make some tests these days.

---

### Post by Sctmon on 2012-05-07
It is actually easier than I though.


edit (as root) /etc/init/myth-backend.conf

immediatly after "pre-start script"(ie next line) add this:
dvb-fe-tools --adapter=1 --frontend=0 --set-delsys=DVBT
save and reboot!

---

### Post by rrofes on 2012-05-08
Many thanks Sctmon.
A couple of minor corrections after doing what you told me, just for people following our same path:

a) edit (as root) /etc/init/myth-backend.conf
-> name of file is /etc/init/mythtv-backend.conf

b) immediatly after "pre-start script"(ie next line) add this:
dvb-fe-tools --adapter=1 --frontend=0 --set-delsys=DVBT
save and reboot!
-> name of tool is "dvb-fe-tool"

Now that I solved the big problems there is another minor issue that I would like to understand better. I put it in a separate thread:
[http://ubuntuforums.org/showthread.php?t=1975975](http://ubuntuforums.org/showthread.php?t=1975975)

---

### Post by Sctmon on 2012-05-08
Thanks for correcting the typos, I was writing the post on a different computer reading from the screen of the myth system.

I have also noticed that Myth TV is reporting 4 tuners, dev/dvb/adapter0/frontend0 twice as tuner 1 and 2 and dev/dvb/adapter1/frontend0 twice as tuner 3 and 4. Perhaps it is detecting the DVB-T/DVB-C capabilities of each tuner?

I won't get a chance to look at it again until next week as I will be away but if you solve the issue on the other thread you started can you post a fix?

Scott

---

### Post by rrofes on 2012-05-08
Or maybe it is because they are allowed to make 2 simultaneous recordings from the same multiplex? I mean in the configuration of each tuner. I don't know for sure.

Don't worry Scott. I will post my conclusions regarding my other new post. Could you write there if you observed the same behaviour?

Roger

---

### Post by Sctmon on 2012-05-08
That is interesting, I did not know that was possible. I may get some time later today to try it out but other than that it will be next week.

---

### Post by steiner858 on 2012-06-03
Did you find any solution to make the remote control work ?

I didn't find yet how to make it work...

---

### Post by Sctmon on 2012-06-03
> **steiner858 said:**
> Did you find any solution to make the remote control work ?

I didn't find yet how to make it work...

Ii have not tried using it. I use mythmote on an android tablet and my phone to control it. Sorry I can't be of any help

---

### Post by rrofes on 2012-06-04
> **steiner858 said:**
> Did you find any solution to make the remote control work ?

I didn't find yet how to make it work...

Sorry, I can't give much help, I'm using a hybrid remote I bought apart that has a wireless keyboard + mouse and IR emitter for the TV. By the way, this is a great solution for remote.

---

