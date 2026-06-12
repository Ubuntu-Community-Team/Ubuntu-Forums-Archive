---
title: "which graphic driver should i choose for wine"
date: 2013-05-13
forum: Multimedia Software
---

### Post by borabinbas on 2013-05-13
Hello, i am using samsung r580 (i5 cpu, 8gb ram, nvidia 330m gpu) notebook, and i am playing games  (diablo 3, starcraft 2, some steam games not ported linux) and using some windows applications with wine but i can't decide which driver should i use? i am having problem with graphic mostly my screen turns pink/ pink and screen images etc. Thanks for your answers.


here is my driver list:

[ATTACH=CONFIG]242553[/ATTACH]

ps: sorry, english not my native language

---

### Post by QIII on 2013-05-13
*Moved to **Multimedia & Video***

Hello and welcome to the forums!

The driver you should use is the one best suited to your Linux distribution.  Wine does not use the Windows graphics drivers, so don't get confused.

Right now you are using the default Nouveau driver.

If you are having difficulty with your driver, that needs to be addressed in the context of the Linux environment.

Cheers!

---

### Post by borabinbas on 2013-05-13
so i have to try some tricks with winetricks and wine registry, right?

---

### Post by QIII on 2013-05-13
Not necessarily, but that may be needed.

What I am saying is that the default Nouveau driver may not be up to some task being asked of it by the application.

Remember that Wine is not a Windows emulator (hence, it's name:  **W**ine **I**s **N**ot an **E**mulator).

Wine provides a compatibility layer with specifically designed alternative implementations of what would be DLLs in Windows and APIs that work natively in Linux to replace the APIs the application would normally hook in Windows.  Sometimes this works well, sometimes it does not.

Winetricks can provide some components like Microsoft DLLs and fonts, but the graphics issue may not be related to that at all.  I am not sure, but I think what you are encountering is related to your Linux video driver and you need to try something other than Nouveau.

Since I am not as familiar with Nvidia as others here, I will let others who use Wine applications with Nvidia drivers help you from here.

Cheers!

---

