---
title: "Is there any screencasting software that actually works?"
date: 2013-11-13
forum: Multimedia Software
---

### Post by halfbeing on 2013-11-13
Is there any screencasting software that actually works? With both recordmydesktop and Kazam I find that most of my recordings are simply not saved. They disappear into thin air. With recordmydesktop I have to wait a very long time before I know for certain that the file has not been saved. When recordmydesktop does succeed in saving something the chances are that the beginning of the recording will be missing. And if I do succeed in getting a recording with Kazam I find that the video is badly corrupted. I need to do a screencast for tomorrow and I'm tearing my hair out trying to find a way to do it.

---

### Post by TheFu on 2013-11-13
ffmpeg 
Here's an article [http://www.commandlinefu.com/commands/view/5230/capture-screen-and-mic-input-using-ffmpeg-and-alsa](http://www.commandlinefu.com/commands/view/5230/capture-screen-and-mic-input-using-ffmpeg-and-alsa)

---

### Post by FakeOutdoorsman on 2013-11-13
> **TheFu said:**
> ffmpeg 
Here's an article [http://www.commandlinefu.com/commands/view/5230/capture-screen-and-mic-input-using-ffmpeg-and-alsa](http://www.commandlinefu.com/commands/view/5230/capture-screen-and-mic-input-using-ffmpeg-and-alsa)

That command suggests using "-sameq". This option does not mean "same quality", and definitely should not be used with x11grab, and also has been removed from ffmpeg.

A better guide is [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719).

---

