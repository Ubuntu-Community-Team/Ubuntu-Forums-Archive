---
title: "Blue tinted video when using TV-out"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by visionviper on 2007-04-12
I have a nVidia 6200 LE video card and I just recently started having this problem. When I use a regular monitor using the VGA out on the video card there is nothing wrong. When I use the TV-out on my video card, the display is all tinted blue. I have nvidia-glx installed. I have tried removing it completely and reinstalling it. It could very well be my video card, but I am hoping it is just a setting that got mixed up somewhere. I am running Ubuntu 6.10.

---

### Post by NT4usB on 2007-04-12
I had this same issue using component out to my TV.
Not much on google about it either. (Shouldn't have any problem finding my post over on the Nvidia forums though, there's only two on the subject.*g*)

The fix for me was setting the tv standard to HD480i in xorg.conf.
Check out what your TV supports and season to taste.
```
Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    Option         "TVOutFormat" "Composite" #or SVIDEO, Component, etc...
    Option         "TVStandard" "HD480i" # "NTSC"
    Option         "ConnectedMonitor" "Monitor[1]"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_60" "720x576_60" "720x480_60" "640x480_60" "480x320_60"
    EndSubSection
EndSection

```

**Disclaimer**
Be very careful, back up, and learn a bit about what you're doing before you go editing xorg.conf.
It's pretty easy to break and end up at a black screen with a blinking cursor...

---

### Post by visionviper on 2007-04-12
This is what I have in my xorg.conf file:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Monitor        "Q7b"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x4$
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x4$
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x4$
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x4$
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x4$
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x4$
    EndSubSection

```

Where do I make the modifications? I have backed up the file, so I am ready to make the appropriate changes.

---

### Post by NT4usB on 2007-04-12
First, I'm assuming you're using the TVout to a TV, not a monitor. And it's a standalone display.
Find out what format(s) the TV supports.
You'll need to choose which 'TVOutFormat' to use, depending on how you're connecting and which 'TVStandard' your TV supports.
Then add the options after default depth:
```
DefaultDepth    24
    Option         "TVOutFormat" "Composite" #or SVIDEO, Component, etc...
    Option         "TVStandard" "HD480i" # "NTSC"
    Option         "ConnectedMonitor" "Monitor[1]"
```
The info in quotes is what's working. The stuff after the # are things I tried that didn't work for me.
I found lots of good info on what all these things do and how to use them at the Nvidia site.
[readme]("http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=177&p_created=1101837165&p_sid=lW6IBYyi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSZwX3Byb2RzPTImcF9jYXRzPTYwJnBfcHY9MS4yJnBfY3Y9MS42MCZwX3NlYXJjaF90eXBlPWFuc3dlcnMuc2VhcmNoX25sJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9bGludXggVFZPdXRGb3JtYXQgVFZTdGFuZGFyZA**&p_li=&p_topview=1")
Not sure about the 'ConnectedMonitor' part as this xorg.conf is(was) a dual monitor setup to my LCD and TV while I was setting up MythTV. I commented out a bunch of stuff when I put it in it's permanent home under the TV.
I can post the whole thing tonight if that will help.

---

### Post by visionviper on 2007-04-12
It worked. Thanks a bunch for your help! I just need to get it working in 1080i now. :) I tried, but the screen came out horizontally squished. About a 14th in on each side. But vertically it was fine... :-/

---

