---
title: "Problems with JACK"
date: 2008-11-04
forum: Multimedia Software
---

### Post by semitone36 on 2008-11-04
Hey all

I recently installed Ardour along with qjackctl and everything was working fine for a while.  But just yesterday I noticed a lot of static coming from my speakers and deterimined that there seems to be a steady connection between the input from my computer's mic to the output of my speakers.  

I opened up the JACK control but i cant find any connections between system in - system out to disable and Im pretty new to managing sound ports.  Any ideas? I cant use Ardour until this is fixed! :(

---

### Post by markbuntu on 2008-11-04
Jack uses the alsa-mixer so in the volume control you can mute the mic and mic boost and it will stop playing through your speakers. It is only the capture settings in the mixer that matter for recording and those are separate.

---

### Post by semitone36 on 2008-11-04
thank you that got the hissing to stop but now if I want to record with Ardour I need to turn my mike back on and I stillget that hissing in my recordings. 

Do you know of a more permanent fix?

---

### Post by semitone36 on 2008-11-05
bump

---

### Post by semitone36 on 2008-11-06
bump 

cmon I know there are a ton of people out there with experience with JACK

---

### Post by markbuntu on 2008-11-06
> **semitone36 said:**
> thank you that got the hissing to stop but now if I want to record with Ardour I need to turn my mike back on and I stillget that hissing in my recordings. 

Do you know of a more permanent fix?

You should not need to have the mic turned on in the playback section of your mixer to record into ardour. Also, if you have other captures tuned on they can generate noise even with nothing connected to them which will show up in the mic input. If you have a mic boost capture option you should turn that on.

You can also set the jack default input to your hardware, hw0 or hw0,0 or whatever instead of default, that might help. You could also try a different/better mic if you have one handy.

---

### Post by semitone36 on 2008-11-06
> **markbuntu said:**
> 
You could also try a different/better mic if you have one handy.

Thank you again for the reply.  Unfortunately I dont have the funds at the moment for a new mic so I am stuck with the one on my laptop.  My only concern for now is that I dont want my speakers hiss whenever I turn on my mic, its very annoying! lol

---

### Post by markbuntu on 2008-11-07
Many of the drivers for HDA sound chips which are used in most laptops are incomplete in ALSA 1.0.15 and 1.0.16 which is used in Hardy. 

Some people with these devices have had better luck using ALSA 1.0.17 and Intrepid. ALSA 1.0.17 has improved drivers for many HDA devices including better mic control and more switch options. There is a thread around here about getting ALSA 1.0.17 or 1.0.18rc for Hardy if you do not care to upgrade to Intrepid.

---

### Post by semitone36 on 2008-11-09
Oh I should have mentioned that I am using Intrepid.  I upgraded last week and everything was as it was with hardy.  It was just when I started using Ardour that somehow a connection was made between system-in and system-out.  If ALSA 1.0.17 comes with Intrepid then I should have it...

---

### Post by chez17 on 2008-12-09
Anyone come up with a solution to this? I get a lot of static and crackles when I play something back through Ardour. If I export the file, then the sound is fine, so it's not a data issue. Any help is most appreciated.

---

### Post by semitone36 on 2008-12-09
Unfortunately, no.  Ive just stuck to keeping my mic and mic boost turned off when Im not recording.

---

### Post by chez17 on 2008-12-09
I got mine working! I have been tinkering with this all day and I finally got it working. Here is what I did:

As many people have suggested, start here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Go down to the packages section and follow the instructions for ALSA, Pulse Audio and Jack. Go to synaptic and install everything that he tells you to install. After all that make sure you are booting from the linux-rt kernel that you downloaded. Once you have booted, you should have a JACK Control option in your Sound & Video menu. Open that up and click Setup. All I did was change the Period/Buffers from 2 to 3 and I clicked the "Realtime" option and set the priority to 70. Then I started JACK _*BEFORE*_(this is important for some reason) I started Ardour. And now it works! I get playback with no crackle or buzz.

I am no expert so I can't tell you why this works, just that it does. I have been all over the web today trying to get this to work and this combination was the one that fit. I'll check this thread later today to see if there are any questions. Give it a try and good luck!

Edit: I should add I set the JACK sample rate at 44,100.

---

### Post by semitone36 on 2008-12-10
Holy ****!! That is a ton of info all at once! Haha well thank you for the link but it's gonna be a while before I am able to try any of it out.  Finals week is coming and I wont be having much free time to tinker

---

### Post by chez17 on 2008-12-10
By setting my Frames/Period to 128, Sample to 44,100, and Periods/Buffer to 3, I now have a latency of 2.9ms.

If someone reads this and knows what "Periods/Buffer" means, could they please post it. I have no idea.

---

### Post by markbuntu on 2008-12-10
If you go here, near the end of the OP are some links in the jack section. You should read them:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

