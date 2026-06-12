---
title: "Nvidia 6600GT component video"
date: 2006-01-05
forum: Multimedia &amp; Video
---

### Post by reet on 2006-01-05
Hi, I have a small Philips TV that has component video input. I've been using the S-Video output on my video card for quite some time and have been happy with it, but I thought I would give this component video thing a try. I plugged in my TV through the component video output on my video card, and the picture is much clearer, but very blue.

I thought that maybe I had wired it up wrong, but no combination of connections will produce the proper colors. I should note that if I exit X-windows, the colors are fine in the terminal. I may be wrong in saying this, but I figure that if I plug any of the 3 color channels to the "Y" input on my TV I should get a grayscale image. I do get this with the Y and Pr, but I don't see anything on the Pb.

Any ideas to what's going on? I thought that the problem might be that the video card is out putting RGB to the component output, while my TV is expecting YPrPb, but the labels on the dongle have Y, Pr, and Pb labels so I don't know.> 

---

### Post by audax321 on 2006-01-05
Are you sure your video card has component???  Component video involves three cables...normally color coded Red, Green, and Blue. Most video cards use either S-Video or Composite.  Composite video cables also have three cables (one video is normally yellow, the other two are Red and White and used for audio). If your video card only has one output, it is probably composite and not component. I could be wrong, but I haven't seen a 6600GT that outputs in component before.

---

### Post by mmcmonster on 2006-01-05
I'm not sure what the problem is, but I had a similar problem with a DVD player which was first hooked up to the TV via S-video, and then via component video.  

The solution there was to tell the DVD player explicitely that I wanted to use component video output. (It was a menu option in one DVD player, and a switch (toggle between S-video and component video) in another DVD player.)

I think the situation is that the video card, like my DVD player, can either create S-video output or  component video properly, but not both.  And since most people don't use component video, it defaults to S-video.

Hope this helps. :-)

---

### Post by reet on 2006-01-05
Audax321, yes it is component video output. There are several cards available now with this option. The card I have is the Leadtek A6600GT TDH. 

mmcmontster, I think you may be right, but I have no idea how to set this option in the xorg.conf file. The "TvOutFormat" Option can only be set to "Composite" or "S-VIDEO". I seem to have the same problem in windows (a lack of component output option). In windows, I have the option of composite, s-video, or SCART. If I choose composite, I get the blue screen like in Linux, and if I choose S-VIDEO, the screen is a brown color. I have come to the conclusion that there has to be a driver option for component video, since the terminal has the right colors, as does the windows loading screen.

---

### Post by reet on 2006-02-18
Just thought that I'd update this thread to say that the problem was with the card, and was resolved by a bios update released on Jan 16. There are bios updates for several Leadtek cards on [their website]("http://www.leadtek.com.tw/eng/support/list_driver.asp") which address the inability for HDTV output to work.

I'm happy now.

---

### Post by coffeebaron on 2006-08-16
I've had the same problem. I've got the same card. I did the bios update, but I've still got a blue screen. What xorg.conf options did you use? I just installed Windows briefly, and it has proper colours.

---

### Post by reet on 2006-08-16
The blue screen occurs when the video card outputs composite video and you have component video hooked up. Here's all the relevant information in my xorg.conf:
```

Section "Monitor"
    Identifier     "TV[1]"
    DisplaySize     414    316  #measurements in mm
    HorizSync       30.0 - 50.0
    VertRefresh     59.0 - 61.0
EndSection

Section "Screen"
    Identifier     "Screen[1]"
    Device         "NVIDIA 6600GT[1]"
    Monitor        "TV[1]"
   DefaultDepth    24
    Option         "NoLogo"
    #Available component video modes: 
    #HD480i, HD480p, HD576i, HD576p, HD720p, HD1080i, HD1080p
    Option         "TVStandard" "HD480i"
    Option         "UseDisplayDevice" "TV-0"
    Option         "TVOverScan" "0.6"
    SubSection     "Display"
        Depth       24
        Modes      "800x600" "640x480"
    EndSubSection
EndSection

```
For more information on setting up Xorg with the Nvidia drivers, see the [README]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/index.html").

---

### Post by coffeebaron on 2006-08-16
Thanks. Worked perfectly.

---

