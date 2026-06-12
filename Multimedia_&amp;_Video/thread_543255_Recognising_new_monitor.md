---
title: "Recognising new monitor"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by Mad_Max_1412 on 2007-09-04
Hi Guys,

I had my Ubuntu box (which has a nVidia 6600 graphic card) set up to use my CM771 CRT monitor.  This was set up in a spare room, and I mostly accessed the box via UltraVNC.  This was because I was mainly using the box as a NAS for my video files whilst I found time to learn about Ubuntu.

Now I've decided to move the box into my computer room and use it with my Acer AL2216W widescreen monitor via a KVM switch.

All works fine except I have 2 problems:

1.  I didn't have a 1680x1050 resolution, so after reading some forums, I modified my xorg.conf file by adding those settings in.  After a re-boot, the only resolutions I have are 1024x768, 832x624, 800x600 and 640x480.  The section in the xorg.conf reads:

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "CM771"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


Why don't I have these resolutions?


Question 2:  It might be related to the above question, but my xorg.conf has the monitor  as the CM771 which it originally was.  Do I simply change this to "AL2216W" or do I need to have something specific?  How, or where, do I get Ubuntu to select the name/model of my monitor?

By the way, when I go to Applications --> System Tools --> Nvidia Settings, the dialogue box doesn't really show anything other than 5 check boxes.  Isn't it supposed to show resolutions, brightness, etc and allow me to change them?

Thanks

---

