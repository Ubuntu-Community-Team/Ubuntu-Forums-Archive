---
title: "no sound in flash"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by Strannik on 2006-10-25
Hello All,

I suddenly found out today that flash on my computer runs with no sound. All sounds in the system work, and in alsamixer, everything needed is not muted. mp3, avi anything you name works fine, but flash does not. I originally installed the flash player using automatix and everything worked fine. i tried to deinstall flash player from automatix and then install flash through firefox, but it didn't help at all. 

Where can I look to figure this out?

Thanks in advance.

---

### Post by divague on 2006-10-25
try installing alsa-oss and edit this file /etc/firefox/firefoxrc

change:

FIREFOX_DSP=""

for

FIREFOX_DSP="aoss"

---

