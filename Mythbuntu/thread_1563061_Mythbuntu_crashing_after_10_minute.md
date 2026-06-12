---
title: "Mythbuntu crashing after 10 minute"
date: 2010-08-28
forum: Mythbuntu
---

### Post by cmadooly on 2010-08-28
I tried searching through the forums for something but since the issue is so generic, I don't know where to begin. Any assistance is appreciated.

I have a working mythbuntu set up that I pretty much use just to watch videos, not TV.

If I leave the computer running without a video playing, then the machine is fine. I can SSH into it, leave it running over night then see that it's still working the next day.

What I have noticed is that if I watch a video, and don't touch the remote for almost exactly 10 minutes, the entire machine just craps out. The TV says 'No signal found' and I can't even ping the machine. I have to perform a cold shut down and power it back up to access it again.

If, however, I watch a video and consistently adjust the sound or rewind/fw/skip every so often, then I can watch it for as long as I like.

Initially I thought it was gnome's screen saver, so I removed the whole package. The screen saver doesn't kick in if I leave the machine on so I don't think that's it. Then I thought it was the video card heating up to a point where it's crashing the machine but that doesn't make sense since it runs for more than 10 minutes as long as I give the device some input using the remote.

If you can advise on which logs to check to get a better idea then I'd be more than happy to provide more information to get to the bottom of this.

Video card is an Nvideo Geforce 8400GS connected via HDMI although the same thing happens when connected via VGA

---

### Post by DemonBob on 2010-08-28
Check the logs under, /var/log/mythtv/mythfrontend.log and /var/log/mythtv/mythbackend.log

---

