---
title: "Nvidia display issue"
date: 2012-04-07
forum: Multimedia Software
---

### Post by surge031 on 2012-04-07
Good afternoon all,

I have a Ubuntu x86 setup that I'm currently using as an HTPC. I am using Nvidia GT520 video card.

My issue is that when I install the driver from additional drivers, the display on my Panasonic Tv(720P) is chopped off at the top and bottom. I'm currently using 1280X720.

when I deactivate both drivers in the additional drivers section, the display is perfect, I can see the full screen, nothing chopped off. The draw back is I have no audio.

I have tried different resolutions but none so far has allowed to see the entire. I am attaching some pictures.

Any help will be greatly appreciated

[IMG]http://i63.photobucket.com/albums/h149/surge031/Additionaldrivers.png[/IMG]
[IMG]http://i63.photobucket.com/albums/h149/surge031/NvidiaxServersetting.png[/IMG]
[IMG]http://i63.photobucket.com/albums/h149/surge031/afterremovingnvidiadriver.png[/IMG]
[IMG]http://i63.photobucket.com/albums/h149/surge031/1280X720.png[/IMG]

---

### Post by Basher101 on 2012-04-07
did this occur from the moment you applied the drivers or did it "just happen"

---

### Post by surge031 on 2012-04-07
> **Basher101 said:**
> did this occur from the moment you applied the drivers or did it "just happen"

It occured from the moment I applied the driver.

---

### Post by Basher101 on 2012-04-07
hmm the only advise i can give you in this situation is either:

1. just not use the driver
2. try different versions of the driver until you find one that works
3. wait until someone with more knowledge sees your thread

regards and good luck..

---

### Post by BicyclerBoy on 2012-04-07
Could just be the nVidia driver is defaulting to overscan because it is connected to a TV.

The nvidia-settings GUI prgm has an over-scan slider control..

Ideally you would also set the TV to just-scan or 'direct pixel mapping' mode..Not sure if the budget models (720) have this setting.
Some of the Panasonic TV (plasma V20 VT20) have to in 'professional' mode to allow direct pixel mapping.

You could get better HDMI video PQ by using YUV color-space & limited color range .

---

