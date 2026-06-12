---
title: "PulseAudio Protocol Mismatch"
date: 2010-10-01
forum: Mythbuntu
---

### Post by thefrozenpenguin on 2010-10-01
I have myth running as a backend on 10.04 which is also the house's main server.

I install 10.10 beta on one of the laptops and mythfrontend fails to start correctly with the following error in the terminal:

2010-10-01 07:48:23.371 MythContext: Connecting to backend server: 192.168.1.10:6543 (try 1 of 1)
2010-10-01 07:48:23.431 Protocol version mismatch (frontend=23056,backend=56)

The frontend does start but reports this error in a notification box with only and "OK" which closes the frontend down.

Any thoughts?

---

### Post by LowSky on 2010-10-01
where does PulseAudio come into play?

The problem is you have an older version of MythTV on the backend

10.10 comes with .23.1 and isn't backwards compatable with 10.04's .23.

you can upgrade your backend to .23.1 for the 10.04 backend using the mythbuntu autobuilds package found here: [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by thefrozenpenguin on 2010-10-06
Thanks LowSky :D

---

### Post by joama on 2010-10-19
Hi, 
I have the same problem, but I am the only laptop in the house that is running Ubuntu 10.10, upgrading all the mythtvs on the rest of the computers in the house would be a little bit hard especially that it took us 3 months to get it all working. So can I just downgrade my mythtvfrontend on my 10.10 laptop to 0.23 ?

Thanks

---

### Post by superm1 on 2010-10-19
> **joama said:**
> Hi, 
I have the same problem, but I am the only laptop in the house that is running Ubuntu 10.10, upgrading all the mythtvs on the rest of the computers in the house would be a little bit hard especially that it took us 3 months to get it all working. So can I just downgrade my mythtvfrontend on my 10.10 laptop to 0.23 ?

Thanks

Adding autobuilds on earlier boxes shouldn't be very difficult at all.
```
http://www.mythbuntu.org/auto-builds
```

---

### Post by joama on 2010-10-22
Hi superm1,

I did the auto build on the computer that has the backend and it worked, I checked everything and it was working, then the real test was trying to start mythtv on my Ubuntu 10.10 laptop. It did start but when I picked watch tv, live tv doesn't have a picture I see my desktop instead, I do hear the TV and when I press s I do get the guide but with no picture in the small frame. So I really don't know what went wrong!!! 

I ran mythtvfrontend from terminal to try to see the error and this is what i get:
```
2010-10-22 01:40:31.960 NVP(1): Enabling Audio
2010-10-22 01:40:31.974 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2010-10-22 01:40:31.975 VideoOutputXv: ProcessFrameXvMC: Called without frame
2010-10-22 01:40:32.024 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2010-10-22 01:40:32.025 VideoOutputXv: ProcessFrameXvMC: Called without frame
2010-10-22 01:40:32.075 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2010-10-22 01:40:32.075 VideoOutputXv: ProcessFrameXvMC: Called without frame
2010-10-22 01:40:32.491 NVP(1): prebuffering pause

```

Thanks

---

### Post by superm1 on 2010-10-22
> **joama said:**
> Hi superm1,

I did the auto build on the computer that has the backend and it worked, I checked everything and it was working, then the real test was trying to start mythtv on my Ubuntu 10.10 laptop. It did start but when I picked watch tv, live tv doesn't have a picture I see my desktop instead, I do hear the TV and when I press s I do get the guide but with no picture in the small frame. So I really don't know what went wrong!!! 

I ran mythtvfrontend from terminal to try to see the error and this is what i get:
```
2010-10-22 01:40:31.960 NVP(1): Enabling Audio
2010-10-22 01:40:31.974 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2010-10-22 01:40:31.975 VideoOutputXv: ProcessFrameXvMC: Called without frame
2010-10-22 01:40:32.024 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2010-10-22 01:40:32.025 VideoOutputXv: ProcessFrameXvMC: Called without frame
2010-10-22 01:40:32.075 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2010-10-22 01:40:32.075 VideoOutputXv: ProcessFrameXvMC: Called without frame
2010-10-22 01:40:32.491 NVP(1): prebuffering pause

```

Thanks
You'll want to mess with your playback profile a little bit. Go into Settings->TV Settings->Playback.  Set the profile (page 3) to Normal.

---

### Post by joama on 2010-10-22
Hi superm1,
I think the update got all the computers screwed up, I did 

> **superm1 said:**
> You'll want to mess with your playback profile a little bit. Go into Settings->TV Settings->Playback. Set the profile (page 3) to Normal. 

The error is now gone but the no video at all is still the same. Now I am having a problem with all 3 computers the backend and the other frontend that are both Ubuntu 10.04 and my laptop, but each one is having a different problem. So I wonder if I should just give up and downgrade everybody to mythtv 0.23.

---

### Post by superm1 on 2010-10-22
> **joama said:**
> Hi superm1,
I think the update got all the computers screwed up, I did 

 

The error is now gone but the no video at all is still the same. Now I am having a problem with all 3 computers the backend and the other frontend that are both Ubuntu 10.04 and my laptop, but each one is having a different problem. So I wonder if I should just give up and downgrade everybody to mythtv 0.23.

Just to rule out a problem with your tuner that's cropped up, can you try playing a recording that you know is good first?

---

### Post by joama on 2010-10-24
Ok, 
I got the backend to record couple of things and they work fine viewing them from the front end on the same computer. I tried to play it on my laptop and exactly the same I get the sound but all I see is my desktop even when I press m for menu it doesn't appear.
The other frontend doesn't even want to play the recordings. Note that before I moved to mythtv 0.23.1 the backend and the other frontend were working fine :( I hope I wont need to format all of them and start from scratch again :'(

---

