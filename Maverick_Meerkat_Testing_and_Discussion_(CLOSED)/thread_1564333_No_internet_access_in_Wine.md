---
title: "No internet access in Wine"
date: 2010-08-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2010-08-30
I have been using a poker program for some time now through wine and it has run flawlessly, up until I upgraded to Maverick. Now the program loads but never makes a connection with the server. I have just installed a different poker program with the same results. Can anyone confirm this as a bug? Or maybe am I being stupid and overlooking something obvious.

---

### Post by Sam on 2010-08-30
Not a solution but a suggestion: try to run your application from the terminal. You'll get output if anything goes wrong.
```
wine "C:\Program Files\PathTo\YourApp.exe"
```

---

### Post by macroshaft on 2010-08-30
It outputs:

> gareth@gareth-laptop:~$ wine "C:\Program Files\PokerStars\PokerStars.exe"
fixme:heap:HeapSetInformation 0x942000 0 0x32fd6c 4
fixme:resource:GetGuiResources (0xffffffff,1): stub

> **Sam said:**
> Not a solution but a suggestion: try to run your application from the terminal. You'll get output if anything goes wrong.
```
wine "C:\Program Files\PathTo\YourApp.exe"
```

---

### Post by dino99 on 2010-08-30
remove/purge then reinstall

---

### Post by omgbots on 2010-08-31
I'm seeing the same exact issue.  There is internet access because the PokerStars Updater works, but there is definitely some other issue which is causing the behavior we're seeing.

---

