---
title: "[SOLVED] Getting my WinTV PVR-150 to work"
date: 2008-07-08
forum: Multimedia Software
---

### Post by SuperPudge on 2008-07-08
Hello,
  I have searched through a few posts, but none have fixed my problem.  I'm trying to backup some VHS tapes onto DVD/my computer but have not been successful.  I have ivtv installed, as well as the CSMonkeyTVRemote (which appears to work).  I prefer to use a GUI vs command line, but setting up is fine with the command line as long as I have complete instructions.  Are there any other softwares out there that I can use?  What about the software that came with the card and use wine?  I have tried Myth, but wasn't able to get that to work either.

I have the capture card hooked up with composite/RCA cables to my VCR, is this possible or do I *Have* to use a coaxial cable?

I'm running 8.04, AM2 3500+, 250Gb SATA, Asus M2NPV-VM, w/ 1.5gb DDR2.

---

### Post by wolfen69 on 2008-07-08
i suggest hooking up your vcr by coax cable. then:
```
ivtv-tune -c3
``` (i'm assuming it will use channel 3) then: ```
cat /dev/video0 > /tmp/any_name.mpg
``` and it should record it to the /tmp directory. remember to leave the terminal open while recording. to stop it, do ctrl-c. good luck. let us know how it turned out.

---

### Post by SuperPudge on 2008-07-09
Ok, I have the video working now - but no sound.  Is there a simple way of starting to record while I'm watching a video? like a record button add on for my CSMonkeyTVRemote?

---

