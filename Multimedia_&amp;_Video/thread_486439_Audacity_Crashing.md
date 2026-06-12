---
title: "Audacity Crashing"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by deadgobby on 2007-06-28
After upgrading from edgy to feisty. Audacity is crashing. I check in the Ubies bug report and find no solution. It seems to be worst on so to be new version of Ubie. I found no solution to this bug. Some say it may be a 
glibc issue, yet no resolve. When I run Audacity from the terminal to see why it crashes with no warning. I get

audacity: src/hostapi/oss/pa_unix_oss.c:1611: PaOSS_AudioThreadProc: Assertion `frames == framesAvail' failed.
Aborted (core dumped)

 Can any one tell me how to resolve this issue? I really want to take some old 4 track and records and dub down to MP3's. Most I can record it up to 3 minutes and poof a crash. Same with ReZound. It crashes too. Shorter than Audacity. I can't even get Sound recorder to record at all. 

Gobby

---

### Post by deadgobby on 2007-06-28
bump

---

### Post by dabl on 2007-06-28
> **deadgobby said:**
> 

audacity: src/hostapi/oss/pa_unix_oss.c:1611: PaOSS_AudioThreadProc: Assertion `frames == framesAvail' failed.
Aborted (core dumped)


I run mine as an ALSA sound system, and Audacity doesn't crash (much).  Looks like you are running as OSS, and that is related to the crashing.  Maybe you want to try it as ALSA?  :???:

---

### Post by deadgobby on 2007-06-29
I will try that and see if that helps. Thank you for the tip. I am sure others are looking at this as well. Well report back on the out come.
GObby

---

### Post by deadgobby on 2007-06-30
I owe you one. That did the trick! I was able to take 90 minutes of tape with out one crash. I do a happy dance in your honor. \\:D/:guitar:

---

