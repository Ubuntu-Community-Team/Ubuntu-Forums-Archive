---
title: "Terrible Video Quality"
date: 2007-11-30
forum: Mythbuntu
---

### Post by nighthawk98tj on 2007-11-30
Hi All,

I am working to setup a mythbuntu box with a PVR150 and GeForce FX 6200 over S-Video.  However, I am experiencing terrible video quality, including the following issues:

1.  Washed out colors on TV
2.  Fuzzy output on TV
3.  Two horizontal wavy lines on the screen that cause any video below them to "wiggle" along that line

Does anyone have any suggestions here?  I cannot seem to make any significant progress here...

Thank you!

Tim

---

### Post by uopjohnson on 2007-12-01
You need to isolate the problem in order to fix it.  Try these things:
1) Plug in another TV to the same cable to test the line.
2) Capture video off the cable without using myth and view it to see if myyth is the problem.  Here's how:
Open the terminal and type
```
cat /dev/video0 > ~/test.mpg
```
I'm assuming here that your card is at /dev/video0 which is probably correct if you only have one card.  Open te resulting test.mpg which will be in your home folder and see how it looks.  
3) Open the test.mpg on another computer if possible to see how it looks there.
4) Record something in myth and then open it on another computer.  This is really easy if you have mythweb enabled because you can just download the mpg from your recordings there.  If you don't have mythweb then you will need to find a recording in your recordings folder and move it to another computer.  They are titled something like 1006_20071130190000.mpg

You should also ensure you have enabled the restricted video drivers because those are much better for nvidia systems. 
Let us know how that works out and we will be closer to finding your problem.

---

### Post by nighthawk98tj on 2007-12-02
Thank you for the detailed response.

I have improved the quality to an acceptable level for now with the nvidia-settings tweaks and quality tweaks within MythTV.  I believe the squiggly line problem has to do with running the S-Video through a cheap converter box to convert it to coax, since my TV does not have an S-Video in.

Thank you for your help... I suppose now I need a new TV.

Tim

---

