---
title: "Small LCD on my PVR"
date: 2007-11-07
forum: Mythbuntu
---

### Post by ljbeng on 2007-11-07
When I first built my pvr and had XP and GBPVR installed, I wrote a program in vb.net that would send data out the serial port and my external 2X16 character lcd would display the text.  I sent date, time and either "STANDBY" or the first few characters of any .mpg file that was being written to..

Ex:  RECORD CSI LV---

I monitored the directory for any file where the size was changing and I would then send the first few characters of the file name out the serial port.  The entire string would look like:

```

11/07/2007   09:46RECORD CSI LV   (0xA)

```

0xA would indicate the end of line and then my lcd would display the text shown.

What would be required to do something similar in mythbuntu?  I send data once ever 2 seconds at 9600,8,n,1.  Thanks...again....

---

### Post by superm1 on 2007-11-07
Well you've got a few options what to do here.  First you should investigate if your LCD is supported by lcdproc.  If it is, the amount of work you need to custom do will be fairly low.

If it isn't supported, i'll recommend that you write something similar in python + pySerial.  Should be a pretty straightforward app.

---

