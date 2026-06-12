---
title: "MPlayer 1080p WMV file w/win32codecs: ERROR &quot;Too Many Packets in the Video Buffer&quot;?"
date: 2008-07-31
forum: Multimedia Software
---

### Post by plvick on 2008-07-31
I could really use some help here... I have a great 1080 wmv file that looks awesome when I play it in Totem or VLC on my Hardy box, but with those there is no audio. I had to use MPlayer and the win32codecs to get it to work with sound. Only now, MPlayer constantly displays a pop up with this Video Buffer error. It would be fine, as it is playing nicely with both audio and video working flawlessly... but this error keeps popping up like hundreds of times and crashes MPLayer. Can I just suppress this error? Or increase the size of my video buffer?

Please reply directly to: [email]sysop@ubuntuOUTFITTERS.com[/email] if you can help (or reply here I suppose). Thanks!

---

### Post by shirilover on 2008-07-31
Try adding -really-quiet to either the command for playing or to your ~/.mplayer/config file

---

