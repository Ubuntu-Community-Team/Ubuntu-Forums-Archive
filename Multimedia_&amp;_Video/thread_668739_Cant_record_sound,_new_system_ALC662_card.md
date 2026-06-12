---
title: "Cant record sound, new system ALC662 card"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by muzzer on 2008-01-15
Hi, I'm new to linux so sorry in advance if this is a dumb question.
I have a new PC  (new install of Kubuntu 7.10) with a gigabyte Motherbaord  GA-M61SME-S2L which has a ACL662 soundcard. I have sound output but cant get the mic to work.
Have tried altering the alsamixer, capture and mic settings but nothing. Please help - skype is my telephone!

How do I find out what version of alsa driver my system has? I've read an upgrade to this driver may help, but being a noob I have no idea how to go about finding my current version let alone installing a new one!

Any help would be great. I DO NOT want to have to go back to Windows OS so am desperate to solve this problem!

---

### Post by ar_victor on 2008-01-16
I have the same problem. To check the driver version :

cat /proc/asound/version

---

### Post by muzzer on 2008-01-16
Thanks for that, I have version 1.0.14. The latest is 1.0.15. Is it worth upgrading and if so howto? Anyone else experienced this problem?

---

### Post by muzzer on 2008-01-21
I'm gonna bump this. I can't be the only one with this motherboard using Ubuntu! Hell, there are so many incredibly knowledgable people on this forum, someone must have more clues than a beginner like me! :confused:

---

### Post by AmA212 on 2008-01-22
Hello muzzer,

I have also exactly the same problem, sound is ok but i can't record...

I use Debian, the sound card is ALC662.

I updated alsa and all the libraries (1.0.15) but it doesn't solve the problem.

At the begening i thought it was a material problem but when i tested with windows os everything was ok.

If you find a solution please report it here.

good luck !

---

### Post by trgreerca on 2008-01-22
I have a different motherboard, but same problem. 

 My motherboard is an ECS GeForce7050M-M.  It has the ALC662 on-board audio as well.   

I have located a thread that looks promising; but I am at work and cannot try these recommendations until I get home tonight.  But you may find a solution here.  

Here is the thread: [http://ubuntuforums.org/showthread.php?t=616845&highlight=alc662](http://ubuntuforums.org/showthread.php?t=616845&highlight=alc662)

If you solve your problem, please post a note here.

Tom

---

### Post by muzzer on 2008-01-25
OK, got my mic working in Skype. Downloaded the latest version and altered the sound options for "Sound In" from "default device" to "HDA NVidia (hw:NVidia,0)".

Being new to linux I'm unsure how Ubuntu sets up devices, but this seems to suggest Ubuntu has set the default device incorrectly?

Have not tested in other apps as yet but I suspect it will not work as I've only altered settings for Skype and not for the OS as a whole. How is this done under Ubuntu?

Hope this helps you other guys in some way.

---

### Post by AmA212 on 2008-01-25
Hi,

My micro works finally too :)

I just updated alsa libs, they corrected the bug in the new version.

Thanks !

---

### Post by muzzer on 2008-01-25
AmA212: You said previously that you had updated alsa to the latest and it didn't fix anything. So what did you do this time? How did you upgrade?
Thanks

---

### Post by muzzer on 2008-02-23
Alsa version 1.0.16 has fixes for the ALC662 card. I now seem to have mine working well, with this version of alsa. Follow instructions on [_this thread_]("http://ubuntuforums.org/showthread.php?t=205449"), and use instructions from subheading "Using Drivers from Alsa-project"

Also, I needed to type into shell:
asoundconf set-default-card NVidia

Hope this helps all :)

---

