---
title: "Fruity Loops"
date: 2007-08-28
forum: Multimedia Production
---

### Post by thealex on 2007-08-28
Is there anyway for me to run Fruity Loops on Ubuntu

---

### Post by FakeOutdoorsman on 2007-08-29
As of last month, Fruity Loops has about 60% functionality under [Wine]("https://help.ubuntu.com/community/Wine"). Not all of the plugins and samples are working.  You might look into [LMMS]("http://lmms.sourceforge.net/"), which is considered the Fruity Loops for Linux, although it is still "young" compared to Fruity Loops.

---

### Post by orange2k on 2007-08-29
You also might want to consider Energy XT2. Its now completely ported to linux, but many people work with the wine-windows version of it in linux, because this way they can run all the VST plug-ins on linux.
But some instruments and plug-ins have already been developed for the linux version of Energy XT, so the future of it seems quite bright...

Even in windows, I much more prefer Energy XT (1.4 or 2) to FL Studio...

---

### Post by rcsarver on 2007-08-29
Have you tried lmms?

---

### Post by orange2k on 2007-08-29
No, I havent, but I will...
Thanks for the tip...:)

---

### Post by 99bluefoxx on 2007-10-22
can i bug anyone for a port over for fl?i dont want to have to buy windows to make music, and fl is laggy in linux
it works but the edges hide behind my panels, ill post a screenshot

---

### Post by Locutux on 2007-12-12
I couldn't get FL Studio 2006 to work on Wine. It runs only the demo version. I just copied the FL Studio 2006 folder from my NTFS/Windows Program Files folder to the virtual one in Wine. It didn't worked because the crack for FLS 2006 is a registry entry.

Can anyone help me with this?

What is the Linux equivalent for FL Studio? I need a similar software, just to try it.

Thanks.

---

### Post by dreamsR4living on 2007-12-12
In the beginning of this thread FakeOutdoorsman typed the following message;

> You might look into LMMS, which is considered the Fruity Loops for Linux, although it is still "young" compared to Fruity Loops.

I think LMMS is the only Linux equivalent, but compared to FL Studio it is just a nice try-out, but not with real functionality.

I'm still looking for a solution too.

---

### Post by Locutux on 2007-12-12
I know about LMMS, I was not asking for LMMS. :/ I guess there's nothing else that is good.

---

### Post by Magnes on 2007-12-12
Well, for Music Making I still have WinXP (and it's the only reason I have it). I'm waiting for VSTi like those from East West for Linux (I know, I could be forced to wait forever).
This HOWTO for energyXT2 with WINE  is interesting though: [http://www.kvraudio.com/forum/viewtopic.php?t=182682&sid=373d25c80ad701db33c49cca4d29edc4](http://www.kvraudio.com/forum/viewtopic.php?t=182682&sid=373d25c80ad701db33c49cca4d29edc4)

---

### Post by 99bluefoxx on 2007-12-12
> **Locutux said:**
> I couldn't get FL Studio 2006 to work on Wine. It runs only the demo version. I just copied the FL Studio 2006 folder from my NTFS/Windows Program Files folder to the virtual one in Wine. It didn't worked because the crack for FLS 2006 is a registry entry.

Can anyone help me with this?

What is the Linux equivalent for FL Studio? I need a similar software, just to try it.

Thanks.
my best suggestion is open the .reg file in gedit and create the lines in your winefile's registry, with regedit, worked for me, although rather tedious...
i dont know when WINE will implement .reg files as executables, although it would be nice...

---

### Post by stmiller on 2007-12-12
Check out the [FL Studio page]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=178") in the wine database. Looks like some have had success.

---

