---
title: "Reaper is playing up after gutsy install"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by daverich on 2007-10-20
I'm wondering has the upgrade to gutsy wiped my realtime kernel and borked my wineasio install.

It's a bit of a bugger really as I was lovin being able to work at home on linux as well as at the studio on windows.....

Anyone any clue as to what's gone wrong?

Reaper works, it just has alot of glitches and weird metering behaviour now.

Kind regards

Dave Rich

---

### Post by eric71 on 2007-10-24
I wish I was at home with my computer, but I can't check the details now. There seemed to be a bit of a difference in the jack files in /usr/lib in gutsy. The usual symlink command "sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so.0" as per the many available howto's, like [http://www.sandgreen.dk/xt2/wineasio.html](http://www.sandgreen.dk/xt2/wineasio.html) doesn't work in gutsy, because there is no libjack-0.100.0.so.0. There is a libjack.so.0.0.23 in gutsy. I think I just changed the command to use that instead and it worked. Maybe I deleted libjack.so.0 first and then ran the command. I may be remembering wrong, because I was a bit sleep deprived when I managed to fix it. Basically your libjack.so.0 is pointing to a file that is no longer there in gutsy's libjack installation, and needs to be made to point at the correct file.

---

