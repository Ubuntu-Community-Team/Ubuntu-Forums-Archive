---
title: "Gnomad2 shuts down"
date: 2009-11-25
forum: Multimedia Software
---

### Post by simon_gj on 2009-11-25
I just bought a used Zen Mozaic, so I started deleting and transferring songs and it was working unexpectedly smooth. But then it suddenly just disappeared on me. The program just shuts down, and it shuts down when I try over again. 

Any suggestions?

---

### Post by Mze on 2009-11-25
run it from the terminal and see what errors it spits out

---

### Post by simon_gj on 2009-11-26
gj@simongj-laptop:~$ gksu gnomad2
Device 0 (VID=041e and PID=4161) is UNKNOWN.Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session

then it just shuts down and goes back to:
simongj@simongj-laptop:~$


Aaand, I just realized that it only quits when the Mozaic is plugged in.

---

### Post by Mze on 2009-11-26
suggestions on the web.

1. run gnomad2 as root

2. see if there's an updated libmtp

---

### Post by simon_gj on 2009-12-18
OK I descided to try again today and the terminal output has changed. It now says:

simongj@simongj-laptop:~$ sudo gnomad2
PDE device NULL.
PDE device NULL.
Device 0 (VID=041e and PID=4161) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
Segmentation fault

---

