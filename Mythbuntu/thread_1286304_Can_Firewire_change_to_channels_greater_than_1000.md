---
title: "Can Firewire change to channels greater than 1000"
date: 2009-10-08
forum: Mythbuntu
---

### Post by dmfrey on 2009-10-08
My cable company, RCN, just shut off their analog signal in my area.  I record with firewire as one of my inputs.  Most of the HD channels that I can record over firewire are on channels above 1000.

From what I can tell, when I enter 1006 (local HD ABC), it changes to 006 (local SD ABC).

Is there a setting I can adjust that will allow firewire to send all 4 digits of the channel?

Thanks.

---

### Post by dmfrey on 2009-10-09
Anyone know if the ch6200 script can handle channel changes above 1000?

---

### Post by dmfrey on 2009-10-10
Anyone have any ideas?

---

### Post by dmfrey on 2009-10-10
Solved.  I used the new script from majoridiot

[http://ubuntuforums.org/showthread.php?t=977820&page=2](http://ubuntuforums.org/showthread.php?t=977820&page=2)

I had to add -f 6 to the command to force motorola stb fast.

For anyone who is interested in the external script command
```

/usr/bin/mythchanger -f 6 -c

```

---

