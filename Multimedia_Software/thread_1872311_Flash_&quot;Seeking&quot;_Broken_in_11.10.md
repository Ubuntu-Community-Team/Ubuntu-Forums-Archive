---
title: "Flash &quot;Seeking&quot; Broken in 11.10"
date: 2011-10-30
forum: Multimedia Software
---

### Post by promet on 2011-10-30
Hello,

I am having problems getting Flash video to "seek" (Fast-forward, Rewind) while maintaining video. Each time I attempt to seek in Flash, the audio will adjust to the seek, but the video will stay frozen at the moment of the last frame played, before trying to seek. If restarted the video will resume play normally from the beginning but, again, video "breaks" on seek.

I have tried various versions of the Flash Player, Adobe 11 from Adobe.com, adobe-flashplugin from the repos, etc. (purging/removing prior versions with each new attempt) each seems to work the same, but exhibits the same seeking problem.

I'd like to know if anyone else is experiencing this issue and has any thoughts/solutions.

I am running on 11.10, 64bit, with the proprietary Nvidia Driver ( 280.13 ). Any thoughts would be appreciated.

Thanks!

---

### Post by EchoTech on 2011-10-31
Same here. Ubuntu 11.10, 64-bit, Flash updated with Flash-Aid didn't fix it.

---

### Post by Steeperton on 2011-10-31
Turn off HWVideodecode when using Flashaid - it seems there's an issue with the Nvidia drivers and Hardware decoding (possibly only on 64 bit?)

That's what worked for me, anyway! :)

---

### Post by lovinglinux on 2011-10-31
> **Steeperton said:**
> Turn off HWVideodecode when using Flashaid - it seems there's an issue with the Nvidia drivers and Hardware decoding (possibly only on 64 bit?)

That's what worked for me, anyway! :)

That's good to know. Thanks for sharing the solution.

---

### Post by EchoTech on 2011-11-01
Just to confirm...    fix works for me.

---

### Post by promet on 2011-11-24
> **Steeperton said:**
> Turn off HWVideodecode when using Flashaid - it seems there's an issue with the Nvidia drivers and Hardware decoding (possibly only on 64 bit?)

That's what worked for me, anyway! :)

Verified. Steeperton thanks very much for your help! Marking this one "SOLVED"

---

### Post by mercgt73 on 2011-12-08
My searches led me here, trying to solve a repeatable crash when Firefox tries to load certain flash videos.  I am running 64-bit 11.10 and I have an nVidia driver.  This makes me believe the HWVideo could be my problem.  FlashAid does not remedy the problem.

I do not have the Tweak option to disable HWVideo, only GPU Validation.  So I tried to change and run
```
cat /etc/adobe/mms.cfg | sed '/EnableLinuxHWVideoDecode=1/d' | sudo tee /etc/adobe/mms.cfg
```to
```
cat /etc/adobe/mms.cfg | sed '/EnableLinuxHWVideoDecode=0/d' | sudo tee /etc/adobe/mms.cfg
```and
```
cat /etc/adobe/mms.cfg | sed '/EnableLinuxHWVideoDecode=false/d' | sudo tee /etc/adobe/mms.cfg
``` with no results.

Any help is appreciated.

---

### Post by wolfen69 on 2011-12-08
Can you give us an example of a flash video that will not play correctly? I also run 11.10 64 with nvidia, and havn't had any problems.

---

### Post by mercgt73 on 2011-12-09
The most recent; this link would crash Firefox, everytime, yesterday evening:
[http://sports.yahoo.com/mlb/blog/big_league_stew/post/Video-Man-falls-into-fountain-near-MLB-Network-?urn=mlb-wp28337](http://sports.yahoo.com/mlb/blog/big_league_stew/post/Video-Man-falls-into-fountain-near-MLB-Network-?urn=mlb-wp28337)

I crashed Firefox about 12 times in a row using this link, trying to debug the source the of crash.  Firefox would crash as soon as the video frame would appear.

Unfortunately, now the link works (hours later, and after a hard reboot).  So it could have been a link problem, and not my own.  Argh!

My wife can also get continuous crashes when trying to login into Facebook (as she did during the same session as the Yahoo link crash above).  I do not use Facebook, so I cannot verify just yet.  When I tried to login with her creds, it works fine. :neutral:

When the crash happens, is the dump provided by Firefox of any value?  I can save the dump the next time it happens, which I suspect will be today.  I will also note the exact link.

Thanks for your help,

---

### Post by mercgt73 on 2011-12-16
I have learned that my crash is not Flash related, or so I think.  Firefox crashed twice today on eBay, with no flash insight.  Going to move on to general Firefox crashes for now.  Thanks for the help.

---

