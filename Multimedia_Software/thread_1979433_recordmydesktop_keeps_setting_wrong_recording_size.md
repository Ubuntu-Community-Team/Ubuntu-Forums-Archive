---
title: "recordmydesktop keeps setting wrong recording size"
date: 2012-05-13
forum: Multimedia Software
---

### Post by Benni1000 on 2012-05-13
Hi,
I have an issue with recordmydesktop.
The Program keeps setting the wrong monitor size, therefore not the whole screen is recorded. 
I tried starting recordmydesktop with the real size of the monitor:
```
recordmydesktop --width=1920 --height=1080
```
But it still sets the wrong recording size.
Here is what the Console tells me:
```
Initial recording window is set to:
X:0   Y:0    Width:1920    Height:1080
Adjusted recording window is set to:
X:0   Y:4    Width:1920    Height:1072
Your window manager appears to be compiz

```
Could someone help me with this Problem? 


~I apologise for my bad english but my native language is German.~

---

### Post by Bonster on 2012-05-13
Is a bug that has never been fix.
Go use something else to record like *ffmpeg x11grab* or *kazam*

---

### Post by Benni1000 on 2012-05-13
Hmm thanks.
I tried a bunch of other recording-programs but nothing really worked except for xvidcap. 
But xvidcap recorded everything in highspeed. 
I really want to use recordmydesktop, is there any chance to get this fixed?
I tried setting the window heigth to my screensize + 8 to override this bug.
But the Program complained about wrong resolution.

---

