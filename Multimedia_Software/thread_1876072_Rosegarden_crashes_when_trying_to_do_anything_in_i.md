---
title: "Rosegarden crashes when trying to do anything in it."
date: 2011-11-05
forum: Multimedia Software
---

### Post by ElectricTriangle on 2011-11-05
Just finishing upgrading to Ubuntu 11.10, and I discovered that Rosegarden 11.06 crashes when I attempt to open a file, play a file, cancel the file opening dialogue box, or anything at all for that matter. I am truly stumped. If anyone has any ideas, I'd love for them to help.

---

### Post by ElectricTriangle on 2011-11-09
*bump*

---

### Post by ElectricTriangle on 2011-11-30
If I'm missing something that people need in order to help me, I'd be glad to provide it... I'm just not exactly sure what to provide, since there's no direct indication as to what may be causing this problem.

---

### Post by two4two on 2011-12-01
I have the problem on Natty.  I believe it is Rose Garden 10.10.  I was able to open a MIDI file and copy some of the parts and save the project.  Now Rose Garden won't work any more.  It locks up my computer.  It is a 6-core AMD Phenom II X6 1100T on an ASUS M4A89GTD Pro USB3 mobo, with 12GB memory and 11.5 GB remaining in the system partition, and a 4 GB swap file.  When I installed Ubuntu Studio I chose not to allow real-time memory for Jackd.  But I was playing with Jack to try to get MIDI sounds to be heard in Rose Garden.  I got that to work and I don't recall changing the memory permissions to real-time for anything.  As the warning for Jack during the Ubuntu install tells us, if you allow real-time processing it could freeze the system.  Anyway, add me to the list of people who find Rose Garden freezing the system.  I didn't experience this for any of the other audio, video, MIDI or notation software.

---

### Post by two4two on 2011-12-02
OK, I checked Jac config and it looks like i DID set it to real-time processing.  I unchecked that, but still didn't get a chance to test Rosegarden.  I'll let you all know.  Thanks.

---

### Post by ElectricTriangle on 2011-12-02
Hmm... interesting... actually, I'd removed jack prior to upgrading because it was acting up, Rosegarden was acting funny then too... still worked, but really buggy. I just installed jack it yesterday to redirect some audio, and opening Rosegarden today suggested I may have fixed my problem, it seems to be working. I suppose the real question here is why jack isn't listed as a dependency if Rosegarden needs it installed to function... let's see if removing jack re-breaks it and then I can mark this thread solved.

---

### Post by ElectricTriangle on 2011-12-02
Well it doesn't take my system down anymore when it refuses to load a file, but yes, installing jack seems to be the answer. With jack removed, Rosegarden segfaults and crashes when I try to open a file. Kinda sounds like a bug to me. I think I'm going to mark this as solved. As for your problem, two4two, you could try a 'sudo apt-get --purge remove jack jackd' which should remove the frontend, the backend, and the configuration files and then 'sudo apt-get install jack jackd' which would re-install it.

---

### Post by two4two on 2011-12-05
I changed Jack to remove real-time memory use and it did not help.  RoseGarden still freezes the system.  Most times it freezes while it is coming up, a rare few times it comes up and freezes when I try to open my saved project, so far it never got so far as to be able to work with my saved project.  I'll do like ElectricTriangle suggests and uninstall/reinstall Jack.

---

