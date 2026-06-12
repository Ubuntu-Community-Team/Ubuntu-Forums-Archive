---
title: "Mythbuntu Hardware"
date: 2011-01-28
forum: Mythbuntu
---

### Post by 1234321 on 2011-01-28
I have already done loads of research, but am still unsure on what processor to buy for my mythbuntu system. I was considering an intel atom, since they are low power, and my system will be on 24/7. Will an atom d510 or d525 be sufficient for running a backend, with one analog tuner which has hardware encoding? I might use this as a frontend also, but intend on mostly using a remote frontend. This will also be used as a small home server for both windows and mac machines. Any advice/ suggestions? This is my first post, and I have little linux experience.

---

### Post by 1234321 on 2011-01-28
I am planning on visiting the computer store tomorrow, so any advice, however small, is helpful. Thanks!

---

### Post by PhilWig on 2011-01-31
Have you seen the comments by Slate8?
 
[http://ubuntuforums.org/showthread.php?t=566529&page=32](http://ubuntuforums.org/showthread.php?t=566529&page=32)

You will have seen that choice of graphics and is very important - 
he uses a mobo with Nvidea graphics which avoids lots of heartache with myth.

Sorry but I cannot comment on your specific query about cpu load with analogue encoding - I run DVB where it isn't such an issue.

regards
Phil

---

### Post by can2002 on 2011-01-31
Not sure if the reply is too late, but if you're not intending on using it as a frontend you can probably do without the nvidia graphics.

If you plan to transcode regularly (e.g. archiving MPEG2 to X264, etc.) then the processor choice could be important.  My master backend has a dual-core pentium (E5300) and the maximum encode rates I see for X264 (on the high quality profile) is 10fps.

Good luck!
Chris

---

### Post by newlinux on 2011-01-31
> **1234321 said:**
> I have already done loads of research, but am still unsure on what processor to buy for my mythbuntu system. I was considering an intel atom, since they are low power, and my system will be on 24/7. Will an atom d510 or d525 be sufficient for running a backend, with one analog tuner which has hardware encoding? I might use this as a frontend also, but intend on mostly using a remote frontend. This will also be used as a small home server for both windows and mac machines. Any advice/ suggestions? This is my first post, and I have little linux experience.

sorry I didn't see this. But unless you are doing a lot of transcoding, with 1 analog hardware encoding tuner an Atom should be fine as CPU for a backend. If you are going to use it as a frontend try to get a nvidia GPU,

---

### Post by 1234321 on 2011-01-31
Thanks for all the answers. It is not too late, as I decided that I would just browse and get more information from the computer store. I plan on transcoding the recordings into both a high quality recording for the mythtv system, and a low quality recording to stream to my ipod touch. Also, most of the atom motherboards I have seen only have one pci slot. I have decided not to use an atom, but to instead use a more powerful processor to give me expandability options in the future., since I might use two capture cards. Any suggestions as to which processor I might use? I want something relatively low power, although I know nothing can achieve the atoms power usage. It also needs to be relatively inexpensive.

Thanks

---

