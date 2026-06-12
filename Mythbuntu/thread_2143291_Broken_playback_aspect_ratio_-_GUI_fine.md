---
title: "Broken playback aspect ratio - GUI fine"
date: 2013-05-08
forum: Mythbuntu
---

### Post by d2a on 2013-05-08
Have an otherwise nicely set up mythbuntu 12.04 running 0.25, regularly updated.

However, I've just broken something and I'm hoping it's an easy fix - grateful for any help even if it's just to point out how big an idiot I am...

Before issue arose, I had a 1024x768 desktop, running out of the svideo on my nvidia 8400gs, into a widescreen CRT. TV out was scaled and adjusted to fill entire tv using the following in xorg.conf:
```
Option         "metamodes" "TV-0: 1024x768 { ViewPortIn=1024x768, ViewPortOut=652x412+48+33 }"
```
and the DisplaySize was also set to 272 153

No aspect override or zoom settings were applied in myth setup and so all video was displayed correctly - in live tv recordings and mythvideo. If it was 4:3 content it displayed with black columns left and right, 16:9 and it filled the screen

Today I tinkered with mupen64plus emulator. At one point I ran it full screen with a 640x480 resolution, which resized the display and meant after exiting mupen i was left with a very small desktop. I went to the applications menu and ran Display settings to reset the desktop to 1024x768. This got me my desktop back, allbeit without my metamode adjustments, and then I restarted the box.

After restart, the myth gui still appears correctly but all 16:9 video is displayed squashed. 4:3 video is zoomed to fill.

Can anyone make a guess as to what's changed and how I can get my setting back? So annoyed with myself as I was just about to back up all my settings as I'd finally got a stable setup I was happy with ](*,)

Thanks

---

### Post by d2a on 2013-05-08
A ha! I think I've solved my own issue. I checked the files that had changed in the last few hours and removed 

```
.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml

```

after a reboot the myth display was back to normal. not sure why but glad to get it back!

---

