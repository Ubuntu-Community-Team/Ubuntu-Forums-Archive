---
title: "which graphics card?"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by rarstar on 2006-07-25
I've currently got an old ATI Radeon 7000 in my machine, it works with the default drivers (no others work) but performance is terrible... DVD playback stutters, etc.

I like Ubuntu though and I think it's worth replacing the card rather than going back to Windows.

Can anyone recommend a decent card? Don't need anything too expensive as I don't play games etc.

I've been told a an Nvida 6200 128mb would be ideal... any opinions?

Cheers,
rar

---

### Post by Ares Drake on 2006-07-25
It currently seems to me that Nvidia cards are better supported with linux. Be sure however not to get one of these TurboCache / Hypermemory versions, wich use part of your RAM, these wont be much faster than your previous one.

However maybe your problems aren't hardware related - enabeling xv-overlay might help. To enable check for the line:

Option	    "VideoOverlay" "on"

in your xorg.conf and be sure the playback software uses XV overlay. Good luck!

---

### Post by rarstar on 2006-07-25
Thanks, i'll try that.

I'm pretty sure it's software rather than hardware related as the card worked well in Windows XP.

When I've edited xorg.conf do I have to do anything to compile it, or just restart?

Cheers,
rar

---

### Post by cracker on 2006-07-25
I recommend a 6600 or 6600GT. I currently have a 6600 256MB, and it works with nvidia-glx out of the box, supports full 3D acceleration, and has not caused one bit of trouble.

---

### Post by Ares Drake on 2006-07-26
> **rarstar said:**
> When I've edited xorg.conf do I have to do anything to compile it, or just restart?

No, just edit it (make a backup copy before!), then close all open applications and restart your xserver with strg+alt+backspace.

Be sure to have everything set right in your xorg.conf, if you miss sth like a ", your graphical desktop wont start. In this case you can copy over the backup with the mv - command.

---

