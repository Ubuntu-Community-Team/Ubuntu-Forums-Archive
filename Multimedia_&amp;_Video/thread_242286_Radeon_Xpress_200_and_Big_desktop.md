---
title: "Radeon Xpress 200 and Big desktop"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by omegta on 2006-08-23
Hi,

I have a ATI Technologies, Inc. Radeon Xpress 200 (RS480) card with VGA and DVI input and I am trying to get this to work in big desktop mode in Dapper. Has anyone been able to do this? If yes, could you please post your xorg.conf file?

Thanks,

---

### Post by gmcauley on 2006-08-23
Hi Omegta,

I also have Radeon Xpress 200 onboard video:
```
(--) fglrx(0): Chipset: "RADEON XPRESS 200 (RS480 5954)" (Chipset = 0x5954)
```
I am also having trouble: [see here]("http://www.ubuntuforums.org/showthread.php?p=1414018#post1414018")

I am curious:
1) Are you using CRT/LCD or LCD/LCD or CRT/CRT?
2) Which monitor is your primary monitor?
3) What is your primary symptom?  (with me, it is although a specify "horizontal,reverse", I get Clone mode)
4) What version of fglrx? (I am using 8.28.8 )

Please let me know.

---

### Post by omegta on 2006-08-23
Hi gmcauley,

To answer your questions:

1. LCD/LCD
2. My primary monitor is VGA
3. I can only get the monitors to work in clone mode.
4. Im using fglrx version 8.25.18. I havent tried upgrading to the new version.

---

### Post by gmcauley on 2006-08-23
Are your LCDs identical?

---

### Post by omegta on 2006-08-23
No, the primary is DELL E173FP and the other is DELL 1707FP

---

### Post by gmcauley on 2006-08-23
I am curious.  What is your output from this:
```
sudo aticonfig --query-monitor
```

---

### Post by omegta on 2006-08-24
```
sudo aticonfig --query-monitor:
Connected monitors: none
Enabled monitors: none

```

I am using the "radeon" driver.

---

### Post by gmcauley on 2006-08-25
Ok, it looks like you are using the open source drivers.

For open source drivers you could try using the 'MergedFB' option ('Big Desktop' is terminology that ATI uses for their single frame buffer mode for their proprietory 'fglrx' drivers).

You might try [here.]("http://ubuntuforums.org/showthread.php?t=221174")

---

