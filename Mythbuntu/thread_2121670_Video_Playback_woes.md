---
title: "Video Playback woes"
date: 2013-03-02
forum: Mythbuntu
---

### Post by GuiGuy on 2013-03-02
My relationship with mythbuntu, ubuntu et al is getting frayed, so please excuse if I sound frustrated:

I mentioned video playback problems introduced on my AMD/ATI backend/frontend after an [update that ran about four weeks ago]("http://ubuntuforums.org/showthread.php?t=2109970"). 

I have now managed to fix it for live TV by setting "[Separate video modes for GUI and TV playback]("http://www.mythtv.org/wiki/User_Manual:JudderFree")&#8221; as described.

Video playback on live TV is brilliant again. Great images, stutter & artifact free. I believe AU TV content is generally sent out at 50hz. However, when I try to play other video content, which typically runs at 24hz, the displayed image moves half way down the screen, so the top of the screen is black, half of the vidoe image is displayed and the the other half is "off screen".

I have been unable to resolve this, but it clearly seems to be some sort of sync issue.  At the moment the only solution is to toggle

[LIST]
 Setup -> Setup -> Appearance >  &#8220;Video Mode Settings&#8221; page, and check &#8220;Separate video modes for GUI and TV playback&#8221; 
[/LIST]

The picture played with &#8220;Separate video modes for GUI and TV playback&#8221; =off is of course, crap as it stutters along. 

Does anyone have any ideas what I might try?

---

### Post by GuiGuy on 2013-03-02
I just found this from playing mythfrontend -v play
> 2013-03-03 08:52:21.904495 I  VSYNC: DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2013-03-03 08:52:21.904512 E  VSYNC: RTCVideoSync: Could not open /dev/rtc: 
			eno: Permission denied (13)

The issue I'm having does seem VSYNC related. Can someone explain the error to me please and hin at a solution?

---

