---
title: "no recording level monitor"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by Dr_Snapid on 2007-11-28
My 7.04 has no recording level monitor in applications > sound & video.

I have checked in Add/Remove and the recording level monitor is ticked... but I have no icon, so how can I run it?

---

### Post by Dr_Snapid on 2007-12-11
Can't anybody tell me where I can run the recording level monitor from?

---

### Post by neelpartymar on 2008-05-07
I have the same problem with UBUNTU Studio 8.04. I Just want to be able to turn the onboard mic on my laptop on and off.
Wait I found this.

Open Accessories -> Terminal
use this to open recording monitor         vumeter -r &
use this to open volume monitor            vumeter -v &

I found this using                         vumeter --help
even though the vumeter -v version is labeled as a vertical version of the meter it is clearly the volume monitor.
After getting these programs open i realized that they are totally useless.

If you want to make an icon from these. Right click on your desktop and create a launcher. Just put that code in Command: space.
Hope this works for Ubuntu 7.04.

---

