---
title: "Microsoft Lifechat LX-3000 Microsoft Issue"
date: 2010-06-28
forum: Multimedia Software
---

### Post by JuKen on 2010-06-28
The audio coming into the headset works just fine; however, the microphone stopped working after I rebooted a few days ago. I would appreciate any help towards finding a solution to this issue. Please let me know if you need any screenshots or command outputs. 

I am running Ubuntu 10.04.

---

### Post by Cypher1101 on 2010-08-09
Mine just stopped working completely. I've rebooted and tried switching ports. My pulse applets show sound going through perfectly fine, and my Windows install plays through them normally too. It's really starting to look like a clean reinstall is in my future.

---

### Post by thomson65 on 2010-08-09
Hi,

The audio coming into the headset works just fine; however, the microphone stopped working after I rebooted a few days ago. I would appreciate any help towards finding a solution to this issue. Please let me know if you need any screenshots or command outputs.I've rebooted and tried switching ports. My pulse applets show sound going through perfectly fine, and my Windows install plays through them normally too. It's really starting to look like a clean reinstall is in my future. 

[Company Name Ideas]("http://www.squadhelp.com")

---

### Post by Pereirao on 2010-09-10
[QUOTE="Cypher1101"]Mine just stopped working completely. I've rebooted and tried switching ports. My pulse applets show sound going through perfectly fine, and my Windows install plays through them normally too. It's really starting to look like a clean reinstall is in my future.
[/QUOTE]
Try:

> **[FONT="Courier New"]aplay -l[/FONT]**

The output should include the LifeChat card number (ex. "card 1")

then run:

> **[FONT="Courier New"]alsamixer -c 1[/FONT]** [SIZE="1"](replace "1" with the number you got in previous command)[/SIZE]

In alsamixer, turn the "speaker" volume up.

If you got sound, save the mixer state with:

> **[FONT="Courier New"]sudo alsactl store 1[/FONT]**

Good luck!

---

### Post by technointellects on 2010-09-13
Awesome, Worked like a charm.

Thanks

---

### Post by rhittmann on 2010-11-29
just did it here and worked perfectly.

tyvm, i was getting desperate. :-)

---

### Post by firesock on 2011-01-30
hi!!!

Thank you very much!!!

It's been the finest solution :)

---

### Post by ratius on 2011-08-04
Worked like a charm, thanks a bunch!

---

