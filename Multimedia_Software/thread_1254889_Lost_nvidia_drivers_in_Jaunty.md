---
title: "Lost nvidia drivers in Jaunty"
date: 2009-08-31
forum: Multimedia Software
---

### Post by xeddog on 2009-08-31
I have a machine that has both Jaunty and Karmic installed on it.  Jaunty on the first drive (sda) and Karmic on the second drive (sdb) and I switch between them using grub2.  I had been using Jaunty on it for a while but today I decided it's time to do some updates on Karmic.  So I restarted the machine, booted Karmic, and used the update manager to download and install all the latest updates for Karmic.  Part of the update included the nvidia 185.something drivers, and it all worked just fine.  Rebooted Karmic and all was well.

Then I decided to go back to Jaunty again.  When it booted, I apparently had no video drivers any more because it was up in "vga" mode at 640x480.  Just a tad lower resolution than the 1280x1024 I was running before.  For starters, I went to Preferences>Display to see if I could change it but my only two options were 640x480 and 320x240.  That kinda sucked a bit.

Then I went to System>Hardware Drivers to see what it said.  It said that no proprietary drivers were installed and it listed the 180 set that I wanted.  So I selected the 180 driver.  Now, how do you get to the install button when it is so far off the bottom of the screen that you cannot get to it??  After a few different tries using the tab key + enter, I finally got the 180 driver to install.

When I rebooted I thought that I had everything fixed, but not quite.  I went to nvidia-settings to get my 1280x1024 back, but it wasn't listed as an option.  Seems like a whole lot of resolution options are missing.  The top 4 shown are 1360x768, 1152x864 (which I am using now), 1024x768 and 800x600.  It used to go on up to 1600x1200.  What has happened to all of the other resolution options including my 1280x1024???


Thanks.

xeddog

---

### Post by xeddog on 2009-09-02
I just KNEW that I would get an answer to this question.  Oh well.  I guess you can't win the all.

Anyway, I manually edited the metamodes operand in the Screen section of my xorg.conf as shown below and it works.

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

