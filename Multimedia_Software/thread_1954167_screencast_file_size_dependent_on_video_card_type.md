---
title: "screencast file size dependent on video card type?"
date: 2012-04-07
forum: Multimedia Software
---

### Post by wayover13 on 2012-04-07
I recently migrated my heavily modified Ubuntu to a new machine with totally different hardware (swapped the HD into the "new" machine). It went without much of a hiccup and I'm up and running again.

I've noticed one oddity I'd like to ask about here, though. I've been doing screencasts on this/these machines, and the screencasts can run from 30 minutes to over 1 hour. On the old machine, those screencasts were coming out to be about 2 MB per minute. On the new machine, they're almost twice as large, at about 4 MB per minute. Seems weird to me that there would be such a difference in file size since I'm running the same command to make the screencast videos (recordmydesktop from the command line with some switches to designate the screen area to record and to degrade video quality a bit so as to reduce the video file's size).

The differences between the hardware in the two machines are pretty major: the new one's a dual-core, while the old one was a single-core p4; different sound hardware; different NIC; and different video card. I'm suspecting the file size difference might have to do with the video card.

The old card was an ATI Radeon RV100 QY, which is now a pretty dated card. The new one is not exactly a bleeding edge card either, being an nVidia Corporation G98 [GeForce 8400 GS]. I did have to switch over, of course, to using the nvidia module when I swapped the HD into this new machine.

Anyone have any theories explaining why I'm seeing larger file sizes for these screencast videos on this "new" machine? Think my idea about the differing video hardware could be the explanation for it?

Thanks,
James

---

### Post by wayover13 on 2012-04-09
I'm still kinda stumped by the way these video files have increased in size despite the fact that the same command is being issued to create the recording. I decided to try switching from the nvidia module to the vesa module to see whether that would affect the size. That change makes no difference: the files still come out to be about 4 MB per minute when using the vesa module as well.

Thoughts on this issue, anyone?

Thanks,
James

---

