---
title: "[SOLVED] Mythstream stutters"
date: 2007-12-09
forum: Mythbuntu
---

### Post by ahood on 2007-12-09
Hi All,

When watching a video that is first downloaded with Mythstream, the video stutters every two or three seconds. 

What file would I edit to try and correct this?

Is there a specific fix that might be known or to try?

---

### Post by ahood on 2007-12-09
I solved the stuttering issue by doing the following:

[LIST=1]
[*]Opened a terminal (Applications --> Accessories --> Terminal).
[*]Opened player.xml in the nano text editor
[*]> sudo nano /usr/share/mythtv/mythstream/player.xml
[*]Scrolled down to the following part
> <item>
      <name>-vo</name>
      <value>gl2</name>
</item>
[*]Replaced gl2 with gl
> <item>
      <name>-vo</name>
      <value>gl</name>
</item>
[*]Pressed **Ctrl+x** to save
[/LIST]

Changing from gl2 to gl seems to have fixed the stuttering in mythstream. If anyone knows why this has fixed the stuttering, it would be much appreciated.


The above was performed with Mythbuntu based on Ubuntu Gutsy (7.10),

_Hardware Specs:_
Video card: nVidia GeForce 8400 GS (PCIe)
RAM: 1 Gb
CPU: AMD Athlon (Socket 939)
Hard Drive: Maxtor 300 Gb ATA

---

