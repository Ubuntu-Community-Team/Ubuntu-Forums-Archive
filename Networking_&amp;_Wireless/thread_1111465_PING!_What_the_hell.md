---
title: "PING?! What the hell?"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by killerclick on 2009-03-30
Every time I type in the prompt

ping [www.google.com](www.google.com)

I never see the prompt again. It just says:

PING [www.l.google.com](www.l.google.com) (74.125.43.99) 56(84) bytes of data.



and then it doesn't return to the prompt and I can only reboot to see the prompt again. What the HELL?!?

---

### Post by damis648 on 2009-03-30
Press Ctrl+C or close the terminal.

---

### Post by drs305 on 2009-03-30
Or use: 
```
ping google.com -c 1
```

---

### Post by killerclick on 2009-03-30
CTRL+C doesn't work and it's a Ubuntu server without the GUI, the whole interface is a terminal. 

And I don't really care about the fancy dot nerd dot com workarounds, I'm wondering what idiot would make a ping that works in this idiotic way.


Edit: LEFT CTRL + C works. Linux sucks. I spent fifteen minutes on this.

---

### Post by Iowan on 2009-03-30
Unlike Windows - which defaults to (the equivalent of) **ping -c4**, Ubuntu keeps pinging until you tell it to stop (unless you specify the count with -c option).

I suspect that when the world was young and Unix was THE OS, infinite pinging by default made sense to troubleshooters.

---

### Post by golliwog on 2009-03-30
Well what version of Ubuntu are you using?

---

### Post by killerclick on 2009-03-30
> **golliwog said:**
> Well what version of Ubuntu are you using?

I think it's the Forty Year Old Virgin Living In His Mother's Basement Edition.


It's actually 8.04 Server.

As for the ping utility, it doesn't display the ping results until AFTER the pinging is over so I don't think how useful it can be.


Anyway thanks for your help. I guess I'll have a shot of Wild Turkey every half hour to keep me calm and composed until I figure out all this.

---

