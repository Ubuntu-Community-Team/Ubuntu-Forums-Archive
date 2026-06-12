---
title: "USB-Soundcard poltergeist problem?"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by HardHaley on 2007-08-17
Hello, I'm new to Ubuntu, and I think that it's definitely the best option for people leaving Windows. But I have been having a slight issue with my USB soundcard. See first it wasn't working at all, but I was happy that Ubuntu worked fine, and I wouldn't have to change back to Windows again... but then I rebooted, and it worked, simple as that, I could listen to music and watch movies no problem. After a couple of weeks, I start experiencing weird issues like when I boot up the OS, I get no sound. Fine, I thought, I'll just reboot again. And tadaa, it worked :). But maybe a week later I wanted to test my webcam and see if it worked under this OS, accidentally pulling out my soundcard(no violence!) from it's slot for a while. After this incident, I can only listen to music in Rhythmbox(I checked), plus movieclips are without sound. 
My soundcard is an Icemat C-Media USB soundcard. Don't know if it will help, but I can listen to music in my headphones also, only from Rhythmbox. x)
Using Ubuntu Feisty Fawn. Had problem since Dapper I think.

Please help, I'm powerless in this OS. -_-

---

### Post by HardHaley on 2007-08-18
Well I'm glad to say I solved this by going in to BIOS and in to Advanced->Chipset->Southbridge and telling it that I had no AC97 soundcard...  For some reason the computer thought I had and set that option by itself(since I did definitely not do that).

Maybe this should be sticky. =):guitar:

---

