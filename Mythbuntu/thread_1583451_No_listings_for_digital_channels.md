---
title: "No listings for digital channels"
date: 2010-09-27
forum: Mythbuntu
---

### Post by embolalia1187 on 2010-09-27
My dorm has basic analog cable, with the local digital broadcast channels on the same line. I have the analog channels working perfectly. But I can't seem to get the program listings to work for the digital channels.

It finds the channels fine, and I can watch them live. But for some reason, I can't get the program listings in, so I can't set it up to automatically record shows on the digital channels.

They're both through the same pchdtv 5500 card, but I set up different inputs for the analog and digital channels, as I saw in a guide somewhere (but now can't find for the life of me). I've tried using the same SchedulesDirect lineup as for the analog and adding just digital channels, and I've tried setting it up to use the local broadcast lineup.

Anyone have any ideas? (or a link to a guide on setting up the 5500?)

---

### Post by hineas on 2010-09-27
Have you tried setting up two line-ups in schedulesdirect.org, one for analog and one for the digital? If not, I would do that and then in the video sources in mythtv-setup make two entries,  one for analog and one for digital.  Then in input connections assign the analog listings for the analog  input and the digital listings for tge digital input.

---

### Post by LowSky on 2010-09-28
You will need two profiles on schedules direct, one for analog and one for digital. Just to warn you, you may need to rename the channels that double on the analog frequency from the channel editor from the backend. That way to avoid double recording if its possible on your tuner card. For instance if lets say one channel is NBC, name the digital version NBC-HD.

---

### Post by embolalia1187 on 2010-09-28
I've tried that. Does anyone know where there might be a good guide for the 5500? I know I saw one around that worked perfectly the last time I set it up, but my Google-fu is failing me.

---

### Post by novellahub on 2010-09-29
I have used Mythweb's channel editor in the past with success with Digital QAM channels.  You enter the XML TV id provided by schedules direct.

---

### Post by embolalia1187 on 2010-09-29
It wasn't working last night. I go on this morning, and it's suddenly working. I haven't changed anything in the mean time... Gotta love Heisenbugs, eh?

Two more questions: 
The channel numbers are very awkward. For example, FOX is analog channel 8 but digital channel 28_1 and CNN is analog channel 28. Is there any way of "mapping" the channel to something else, at least for the program guide (and possibly live TV) without messing up the listings? (For example, it'd be nice to have FOX show up in the same place for analog and digital. At the very least, it'd be nice to be able to use a - rather than _, to make it easier to change channels when watching live TV)

Secondly, is there a way of telling MythTV that a digital and analog channel (or a show on those channels) are the same, and to prefer recording on the digital input? Or do I just have to make sure I always schedule recording on the digital channel? Is there a way to "re-name" the channel, so that rather than the call signs of WBNS and WBNSTV, I might see something like CBS and CBS HD?

---

### Post by LowSky on 2010-09-29
from the Chanel editor on the back end you can change the channels number to anything you like as long as it doesn't interfere with another channel number

Also rename the digital channel to something like Fox-HD, and always select the HD channel for recording this way the backend knows there is a difference in the two channels and does not try to record both at the same time unless you specify to record based on show name an not on channel.

---

### Post by novellahub on 2010-09-29
Also defining your HD tuners before the SD ones will give them priority to record first.

---

### Post by embolalia1187 on 2010-09-29
LowSky: Okay.

> **novellahub said:**
> Also defining your HD tuners before the SD ones will give them priority to record first.
I'm not entirely sure what you mean by this...

---

### Post by LowSky on 2010-09-29
> **embolalia1187 said:**
> LowSky: Okay.


I'm not entirely sure what you mean by this...

When you add the tuners on the mythtv backend, adding the digital tuners before the analog one will give the digital tuner priority when recording and when watching live TV.

---

### Post by lviperz on 2010-09-29
> **LowSky said:**
> When you add the tuners on the mythtv backend, adding the digital tuners before the analog one will give the digital tuner priority when recording and when watching live TV.

Correct me if I'm wrong, but can't you set the priority of the tuners regardless of the order you set them up?

---

### Post by LowSky on 2010-09-29
Priority is set by the order in which they are added to the MythTV backend.


Its talked about here:
[http://www.gossamer-threads.com/lists/mythtv/users/419275](http://www.gossamer-threads.com/lists/mythtv/users/419275)

It can also be found in many other forums when I search google to confirm my answer.

---

### Post by lviperz on 2010-09-29
> **LowSky said:**
> Priority is set by the order in which they are added to the MythTV backend.


Its talked about here:
[http://www.gossamer-threads.com/lists/mythtv/users/419275](http://www.gossamer-threads.com/lists/mythtv/users/419275)

It can also be found in many other forums when I search google to confirm my answer.

Ah, thanks for the thread. That makes things a whole lot clearer.

---

### Post by embolalia1187 on 2010-09-29
> **LowSky said:**
> When you add the tuners on the mythtv backend, adding the digital tuners before the analog one will give the digital tuner priority when recording and when watching live TV.

Ah, okay. I already set them up. I don't remember the order, but I think I did digital first...

Anyway, that seems to solve it. Thanks everyone!

---

