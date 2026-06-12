---
title: "Quicktime .mov files not playing well"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by Harry789 on 2007-07-24
Hi,

Just installed 7.04, now beginning to add everything.

I have ATI x600 radeon graphics - hp zd8000 laptop with 17 widescreen display.

I am using the free graphics driver.

I have some quicktime movies that the system does not really play. I see distorted picture and it sort of stalls.

Where can I look for help?

---

### Post by crispy_420 on 2007-07-24
Do you have correct codecs installed?

---

### Post by Harry789 on 2007-07-25
I have installed all codecs i could find w32codecs, xine, xine-ui, ffmpeg etc. so I believe so.

Is there any particular codec you have in mind that I should check for?

---

### Post by Harry789 on 2007-07-25
Xine player comes up with an error message saying that the amount of dropped frames are too high.

What does that mean?

---

### Post by crispy_420 on 2007-08-10
Video driver not setup or system too slow are my first guesses.

Or go to settings and choose a different video driver.

---

### Post by Harry789 on 2007-08-14
hmm this must be a set up thing, because everything plays just fine in windows on the same machine. It is a laptop less than one year old. Should not have problems with video - at least not the hardware...

Need to look into driver/graphic setup, but do not know where to start or what to look for. 

3d acceleration is active and flgears shows nice output. 

L

---

### Post by RomeReactor on 2007-08-14
Hi. To find out details about your video card, enter the following command in the terminal (Applications->Accessories->Terminal):
```
sudo lshw -class display
```
Also you might want to try Mplayer to view wmv, mkv or mov files.

---

### Post by Harry789 on 2007-08-15
*-display               
       description: VGA compatible controller
       product: M24 1P [Radeon Mobility X600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@01:00.0
       version: 00
       size: 128MB
       width: 32 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list
       configuration: latency=0
       resources: iomemory:d0000000-d7ffffff ioport:4000-40ff iomemory:c8100000-c810ffff irq:16

---

### Post by Harry789 on 2007-08-15
so far I am not using the proprietary driver but have done so before without luck.

any ideas?

---

### Post by shad0w_walker on 2007-08-15
I have managed to get .mov files playing nicely with mplayer if you want to give that a shot. Not as nice as getting them playing in xine, vlc, whatever, but it works atleast.

---

### Post by Harry789 on 2007-08-15
I have w32 codecs installed and mplayer will play some files but not all. it usually stalls and picture pixelates or goes green. Sound works though.

When I try xine, i get an error message that the amount of dropped frames is too high.

L

---

### Post by Harry789 on 2007-08-16
Hi All,

try downloading the alanwake file on this page - I cannot play it regardless of what player I choose:

[http://www.advection.net/opinions/ct/2006/06/standalone_wmv9_advanced_profi.html](http://www.advection.net/opinions/ct/2006/06/standalone_wmv9_advanced_profi.html) - look for the download link on the page.

any ideas are welcome, thanx

---

### Post by Harry789 on 2007-08-16
see here for info:

[http://forum.videolan.org/viewtopic.php?p=74043](http://forum.videolan.org/viewtopic.php?p=74043)

how to play this in linux?

---

