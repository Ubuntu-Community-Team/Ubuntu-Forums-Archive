---
title: "[Mythbuntu 10.04 x64] Will not record back-to-back programs."
date: 2010-07-09
forum: Mythbuntu
---

### Post by thrylax on 2010-07-09
I recently installed a Mythbuntu box using Mythbuntu 10.04 x64 and its mostly working properly. I still have some IR blaster issues, but what I'm stuck on now, is that whenever I try to record shows that run back-to-back, it will record the first show just fine, but the second show does not get recorded at all. At first I though it was just some sort of glitch or something. But on repeated tries, any time I try to record shows that run back-to-back, the first show always gets recorded, but the second never does.
I have tried searching the forums for this issue, but came up with nothing. Has anybody else had this issue? and if so can somebody please tell me how to fix it?
Thanks in advance.

---

### Post by ian dobson on 2010-07-10
Hi,

What tuner card are you using? Mythtv add afew extra minutes to the start/end of every recording and cannot record more than one recording per tuner. All is not lost, if your using digital tuners (dvb-X) you can enable multirec which turns each tuner into several "virtual tuners". This will allow you to record several programs at the same time when they are on the same multiplex.

So just start myth-setup and enable multirec from each of your tuners.

Regards
Ian Dobson

---

### Post by thrylax on 2010-07-11
Thanks for the reply.
In answer to your questions, I am using an old Hauppauge PVR-150 Tuner. I am pretty sure its analogue, not digital. So I guess I'm outta luck.
As for the record settings. I have made sure that all recordings are set to start and end on-time, so there must be something else going on. Any ideas about that?
Once more, Thanks in advance for the help.

---

### Post by ian dobson on 2010-07-11
Hi,

The PVR150 is an analog recorder, so your out of luck. You can only record one program at the same time (even if the second program is on the same channel, sorry).

You'll need to get a second PVR150 or PVR500 to record multiple programs.

Where abouts are you? I think I have a PAL PVR150 gathering dust here somewhere.

Regards
Ian Dobson

---

### Post by thrylax on 2010-07-12
Again, thanks for the help, it is greatly appreciated.
I live in Ashland ,KY and I really appreciate the thought here, but really I'm not worried about being able to record two things at one time. Although I'm sure that be extension, this means my problem is fixed. All I really need to be able to do is record two shows back-to-back. I watch both the Daily Show and the Colbert Report, which always run back to back and I never get to watch the latter because Myth never seems to want to record it. They are both on the same channel so I'm not sure if a second tuner will even help in this particular case.
I already made sure my recording options were set so that all programs begin and end recording on-time, so I'm not sure whats going on with it.
Is this some sort of bug or is there some way to fix it? Has anybody else had this issue before?

---

### Post by ian dobson on 2010-07-12
Hi,

Ashland ,KY doesn't really mean that much to me. I assume your in the USA.
It's just the same as when I say that I come from Birsfelden,BL (Switzerland).

You can just set the extra start/end times for all recordings.


Regards
Ian Dobson

---

### Post by thrylax on 2010-07-12
Yes, I live in the US, sorry bout that.
Anyway, I suppose I could just manually set it to record everything for the whole hour, its just annoying that I have to do that at all. I'd like to be able to identify the problem and fix it if I could. I was wondering, does anybody else have this problem as well?
Thanks again for the help. Much appreciated.

---

### Post by LowSky on 2010-07-12
Just set one program to end a minute early or the other to start a minute later. You can do that from the shows recording options. I used to do this for certain shows because they had a tendency to run a bit off schedule.

Go to the upcoming recording screen, pick one of the programs, press M, go to job options. There should be an option to edit the start or end time in 1 min increments.

---

### Post by tgm4883 on 2010-07-12
> **LowSky said:**
> Just set one program to end a minute early or the other to start a minute later. You can do that from the shows recording options. I used to do this for certain shows because they had a tendency to run a bit off schedule.

Go to the upcoming recording screen, pick one of the programs, press M, go to job options. There should be an option to edit the start or end time in 1 min increments.

+1 for this fix

---

### Post by Colonelguf on 2010-07-12
> **thrylax said:**
> Again, thanks for the help, it is greatly appreciated.
I live in Ashland ,KY and I really appreciate the thought here, but really I'm not worried about being able to record two things at one time. Although I'm sure that be extension, this means my problem is fixed. All I really need to be able to do is record two shows back-to-back. I watch both the Daily Show and the Colbert Report, which always run back to back and I never get to watch the latter because Myth never seems to want to record it. They are both on the same channel so I'm not sure if a second tuner will even help in this particular case.
I already made sure my recording options were set so that all programs begin and end recording on-time, so I'm not sure whats going on with it.
Is this some sort of bug or is there some way to fix it? Has anybody else had this issue before?
What I do is set the Daily Show recording to end 30 minutes late, then I get both shows. My setup would record both, but some of one or the other would get cut off, and this way I get all of both shows.

---

### Post by afljafa on 2010-07-14
> **ian dobson said:**
> Hi,

The PVR150 is an analog recorder, so your out of luck. You can only record one program at the same time (**even if the second program is on the same channel, sorry**).

You'll need to get a second PVR150 or PVR500 to record multiple programs.

Where abouts are you? I think I have a PAL PVR150 gathering dust here somewhere.

Regards
Ian Dobson

That doesn't sound right to me. If you are using hard padding then yes but if not it should simply stop recording the first and start recording the second. That's how it's always worked for me (thankfully we just went completely digital so I no longer have to worry).

---

### Post by tgm4883 on 2010-07-14
> **afljafa said:**
> That doesn't sound right to me. If you are using hard padding then yes but if not it should simply stop recording the first and start recording the second. That's how it's always worked for me (thankfully we just went completely digital so I no longer have to worry).

It is correct. You cannot record 2 programs at the same time with an analog tuner, even if they are on the same channel. You can record one after the other. Please show me where you can do this if you think I am incorrect.

---

### Post by afljafa on 2010-07-14
> **tgm4883 said:**
> It is correct. You cannot record 2 programs at the same time with an analog tuner, even if they are on the same channel. You can record one after the other. Please show me where you can do this if you think I am incorrect.

Of course - but that's not what I was refering to (I simply read it a little differently to you).

The OP made the comment that he cannot record shows back to back. Even with one analogue tuner you can record shows back to back and you shouldn't have to set times to finish earlier and start later or overrun the first show. Just set the two to record and the first one will finish at a certain point and the second will start. You will always get an overlap somewhere but it's fine so long as you watch the overlap before deleting the recording.

If this is not happening for the OP and the second show does not start recording then they have some problem with their setup (probably hard padding set)

---

### Post by tgm4883 on 2010-07-14
> **afljafa said:**
> Of course - but that's not what I was refering to (I simply read it a little differently to you).

The OP made the comment that he cannot record shows back to back. Even with one analogue tuner you can record shows back to back and you shouldn't have to set times to finish earlier and start later or overrun the first show. Just set the two to record and the first one will finish at a certain point and the second will start. You will always get an overlap somewhere but it's fine so long as you watch the overlap before deleting the recording.

If this is not happening for the OP and the second show does not start recording then they have some problem with their setup (probably hard padding set)

Could be hard padding. Could also be Scheduled Direct if he is in the US. I've had it show that shows were starting or ending a few minutes before or after the hour

---

### Post by LowSky on 2010-07-15
removed

---

### Post by thrylax on 2010-07-15
I am in the US and I am using Schedules Direct for my program guide data. I read something about Hard Padding.....is there a way to fix this issue? How do I check? and if confirmed, how do I fix it?
Once more, thanks in advance for all the help.

---

### Post by LowSky on 2010-07-15
> **thrylax said:**
> I am in the US and I am using Schedules Direct for my program guide data. I read something about Hard Padding.....is there a way to fix this issue? How do I check? and if confirmed, how do I fix it?
Once more, thanks in advance for all the help.

What I mentioned earlier is your best option. You can even find out if shows are conflicting by the schedule records menu, so you can adjust from there is needed. But if your in the US you should really consider a digital tuner, like the HVR-2250, this way you can use multirec and have an additional tuner for just in case or watching live TV. Keep the HVR-150 if you like for even more capabilities.

---

