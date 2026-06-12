---
title: "ATI OSS Drivers - No Video Playback"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by Malicious Adversary on 2006-08-05
Hi all,

Before my update to Dapper Drake, I was using the open source "ati" video drivers, and I was able to play movies and DVDs, regardless of file format. Since the upgrade, I haven't been able to get video playback with the ati driver. I've got direct rendering:

[INDENT]$ glxinfo | grep direct
direct rendering: Yes[/INDENT]

I can get (very choppy) video playback with the vesa driver or the fglrx driver. I'd rather avoid the fglrx driver since I've got an R200 ATI video card, and the workarounds for doing it make me nervous.

Although I don't get video playback, I *can* successfully take screenshots of the videos I'm playing. So the information's getting decoded, just not making it to the screen somehow.

Has anyone had a similar problem? Any ideas on how to fix it?

Thanks,

~ Malicious Adversary

---

