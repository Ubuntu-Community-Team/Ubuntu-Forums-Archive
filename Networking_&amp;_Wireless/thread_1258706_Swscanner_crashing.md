---
title: "Swscanner crashing"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by Apex-jb on 2009-09-05
Whenever I try and scan on my wlan0 with swscanner it crashes and gives me this error in the console (I am launching it with the command sudo swscanner).

```
b6865000-b68670KCrash: Application 'swscanner' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
jake@lap:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x2e00107
ICE default IO error handler doing an exit(), pid = 12829, errno = 11

```
Anyone know how I can fix this?

---

### Post by Rhubarb on 2009-10-21
I get a very similar crash too.
When I change the interface from lo to wlan0 then start the scan I get:-

```
b6d7d000-b6d7e000 ---p 00KCrash: Application 'swscanner' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
rhubarb@rhubarb-laptop:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x4000107
```

- Running Ubuntu 9.04 32bit with intel iwl3945 wireless drivers.

---

### Post by siliconfalcon on 2009-11-19
There is a new SVN release available to fix this issue. At this time it is not available in the install software thinggie but I think you can get it from their website. [URL="http://www.swscanner.org/"]http://www.swscanner.org/
[/URL]

---

### Post by jim.guenzel on 2010-01-13
version 0.2.2 worked from [http://www.swscanner.org](http://www.swscanner.org)

---

### Post by dowcet on 2011-01-02
> **jim.guenzel said:**
> version 0.2.2 worked from [http://www.swscanner.org](http://www.swscanner.org)

Not for me... I removed the Ubuntu package of swscanner, replaced it with the version from their website, but am still getting the same error. Any suggestions?

---

