---
title: "Mythbuntu and Studio PCTV"
date: 2011-06-26
forum: Mythbuntu
---

### Post by shiman6 on 2011-06-26
Hello all. 
I am currently building a budget home media center, made out of stuff i have lying around, and i have this TV tuner card, a Pinnacle Studio PCTV. I'll make this short, the way to get it to work in tvtime, no audio (i do not know why) is to insert the module as follows
"sudo modprobe bttv card=39 tuner=8" card option 39 is the driver option for Pinnacle Studio PCTV and tuner option 8 corresponds to what is written on the card itsself, information from this website: [http://www.mythtv.org/wiki/Bttv](http://www.mythtv.org/wiki/Bttv) 

The backend for mythtv is configured to the tuner card with those options, and when i start a frontend on the same box, and go to watch tv, it never leaves the main menu. it only freezes for a second then unfreezes, with watch tv still highlighted. 

For tvtime, the video, and channel switching work great, but there is absolutely no audio. I tried plugging the audio out on the tv tuner card to the aux in on my sound card internally, and nothing happens. 

If you need more information to help me, just ask and i will get it for you.

---

### Post by nickrout on 2011-06-27
Have you been through the backend setup?

What do your frontend and backend logs say when you try to watch TV?

---

### Post by shiman6 on 2011-07-06
I have been through the backend setup, it says it works fine with the tv tuner card. I loaded the correct driver with the correct options to the driver, 
```
modprobe card=39 type=8
```
then while im setting the tv tuner to /dev/video0, mythtv backend recognizes the type of card and the driver based upon the driver. It recognizes the different inputs too.

Could you tell me where to find these logs? I will look them up then post them when i have time.

---

### Post by nickrout on 2011-07-06
/var/log/mythtv/mythfrontend.log and /var/log/mythtv/mythbackend.log

---

### Post by shiman6 on 2011-08-03
i have given up on this project because the hardware i have do not meet requirements for the project. Even with the tuner card working, i can only have one stream at a time.

---

### Post by nickrout on 2011-08-03
> **shiman6 said:**
> i have given up on this project because the hardware i have do not meet requirements for the project. Even with the tuner card working, i can only have one stream at a time.

That's because you only have one tuner!

---

### Post by shiman6 on 2011-08-13
> **nickrout said:**
> That's because you only have one tuner!

There are tuners that are made for single analog and digital input, but multiple output streams. Specifically for media servers.

---

### Post by nickrout on 2011-08-13
I am not sure what you mean by that, but if you have analogue TV, then it is one stream per tuner.

With digital you can get multiple streams per tuner because of multiplexing, and myth's use to multirec. However you referred to an analogue tuner so that doesn't relate to your situation.

---

