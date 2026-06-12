---
title: "Choppy sound in Skype 2.0"
date: 2008-05-06
forum: Multimedia Software
---

### Post by ericmitz on 2008-05-06
Hi all,

I have a problem with sound in skype. Playback is fine and I can hear other people talking clearly.

When I talk, however, my voice is very choppy, almost like I am on a 56k modem or something (which of course i'm not). 

I know my network can handle skype because it is clear as day on my windows machine.

I have seriously tried at least 10 different audio configurations, some are better, some are unusable. I've done ALSA, OSS, PluseAudio, etc. (and yes, i have tried disabling Pulse Audio all together)

Right now, the best configuration i've found is forcing PulseAudio to use DMIX as described in this thread:

[http://ubuntuforums.org/showpost.php?p=4526841&postcount=10](http://ubuntuforums.org/showpost.php?p=4526841&postcount=10)

It is ok, but is still noticeably choppy.

Can anyone point me in the right direction? I have tried the Skype forums with no success (even tried the statically linked OSS version).

---

### Post by windlea on 2008-07-09
you can try giving a boost to your mic. open up master volume control at the right top of your screen edit>preferences>mic boost (+20db) and click ok. from the new upper button on the master volume control choose switches and tick the box. that should do just fine.

---

### Post by psyke83 on 2008-07-09
> **ericmitz said:**
> It is ok, but is still noticeably choppy.

Can anyone point me in the right direction? I have tried the Skype forums with no success (even tried the statically linked OSS version).

There are a few possibilities:
1. Skype is not successfully forwarding a port on your router via uPnP. The Windows versions may be doing this correctly, but the Linux version may not for many reasons. The solution is to manually open a port via your router's configuration and make sure Skype uses that port via the Advanced options. Also, make sure you enable the technical call detail and see if it shows any warnings about network health.

2. If you're running Ubuntu Hardy and using PulseAudio, you *must* set the recording (Sound Out) device as your hardware device, otherwise there will be a lot of skipping for the other party. I recommend you follow my guide [here]("http://ubuntuforums.org/showthread.php?t=789578"). Follow Part A and C (don't mess with Flash in Part B yet, and don't enable the equalizer in Part D), then read the notes for Skype under Appendix A.

P.S. Use the ALSA version of Skype, it works with PulseAudio if configured correctly.

---

