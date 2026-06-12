---
title: "LifeCam Cinema on 9.04"
date: 2009-10-08
forum: Multimedia Software
---

### Post by pluscool on 2009-10-08
I'm have a LifeCam Cinema. working video out of the box on 9.04 (tested in skype, cheese: ok widescreen format, ok resolution and colors). Audio is the problem. 
When I made a skype test call I talk and whistle. I could heard the whistle very low but no voice at all.
Any ideas how to fix audio here?

---

### Post by herbertportillo on 2009-12-29
I have one of these, too.

If you go to Sound Preferences (System -> Preferences -> Sound) and click on the "Input" tab, you'll see a list of input devices at the bottom. Choose the Lifecam for sound input. Then raise the input volume by dragging the bar to the right and make sure the mute option isn't checked. Test the sound out by clapping. The input level should show when sound is made. Cheers.

---

### Post by kestal on 2009-12-30
> **herbertportillo said:**
> I have one of these, too.

If you go to Sound Preferences (System -> Preferences -> Sound) and click on the "Input" tab, you'll see a list of input devices at the bottom. Choose the Lifecam for sound input. Then raise the input volume by dragging the bar to the right and make sure the mute option isn't checked. Test the sound out by clapping. The input level should show when sound is made. Cheers.

though the original thread is from october, thanks for replying. Whats the quality of the video itself (as well as FPS?). whats the highest resolution with 30fps when recorded in Ubuntu? I've heard that the lifecam cinema has a buzzing issue from the microphone, does that persist in Ubuntu?

---

### Post by herbertportillo on 2010-01-03
I can record 720p-quality video at 30 fps with the LifeCam Cinema on Ubuntu. I use a program called guvcview. Cheese freezes when recording video at that resolution but works well with lower resolutions like 640x480.

As to the microphone buzzing, I don't really know anything about that. The microphone works fine on Ubuntu. Sound Recorder, Skype, they all work well with the microphone. However, I use Karmic. Maybe there is a little issue with Jaunty, I don't know.

---

### Post by sezal on 2010-03-11
> **herbertportillo said:**
> I can record 720p-quality video at 30 fps with the LifeCam Cinema on Ubuntu. I use a program called guvcview.

How you were able to get 30fps?
Both guvcview/luvcview shows 10fps.
Core of the problem that I can't turn off auto exposure! Under Win7 everything works fine and I was able to get superb 720p/30fps.

Linux laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux

Have you installed newest uvcvideo driver from sources? Could you please let me know what kernel you are running on?

---

### Post by sezal on 2010-03-15
> **sezal said:**
> How you were able to get 30fps?
Both guvcview/luvcview shows 10fps.
Core of the problem that I can't turn off auto exposure! Under Win7 everything works fine and I was able to get superb 720p/30fps.

Linux laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux

Have you installed newest uvcvideo driver from sources? Could you please let me know what kernel you are running on?

update:
I was able to get 1280x720x30fps with MJPEG rather than YUYV (probably due to USB2.0 bandwidth limitation) + good lighting conditions! However more interesting thing that I can't actually get 1280x720x30fp on Windows as I stated in my previous post. Core of the problem that I was using generic USB video driver and it was showing me 30fps however actually it was 10fps only. And the last thing - even after installing original Microsoft's driver, upgrading camera's firmware it still allows me get 1280x720x10fp only. After googling I've made conclusion that this fact makes crazy many people. Probably it's some king of joke from Microsoft (they doesn't fully support own webcamera). I so happy that i'm not using Windows anymore :)

---

