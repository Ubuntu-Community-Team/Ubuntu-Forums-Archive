---
title: "nVidia: Screen tearing on dual-monitor set-up"
date: 2011-03-29
forum: Multimedia Software
---

### Post by veroslav on 2011-03-29
Hi all,

first of all, I apologize for the size of this post, I really just want to give you as much details as possible as to what
I did in order to try and fix this issue. I have searched and read a lot of threads on this issue, but somehow nothing has worked for me, that is why I am posting a new thread on the same topic.

I have the following dual monitor set-up:
- LCD Monitor 23" (primary output through DVI, resolution 1920 x 1080, 60 Hz)
- LCD TV 42" (output through a DVI to HDMI adapter)

I am running Ubuntu 10.10. My graphics card is an nVidia GeForce GTX 260 (Driver Version: 260.19.06) and I have enabled the proprietary driver. Compiz is enabled and the visual effects are set to 'Extra'.

At first I was using only the LCD Monitor for the output (through DVI), and experienced tearing when watching videos. I managed to solve it by changing the following in CompizConfig Settings Manager:

System -> Preferences -> CompizConfig Settings Manager -> General Options -> Display Settings

Texture Filter - Fast
Lighting - Checked
Detect Refresh Rate - Unchecked
Refresh Rate - 60
Detect Outputs - Unchecked
Overlapping Output Handling - Smart
Outputs - 1920 x 1080
Sync to VBlank - Checked

However, when I connected the tv through HDMI and wanted to have dual output set-up, I experienced the tearing on the tv. The LCD monitor is still fine, no tearing.

I've tried to modify the following settings in the NVIDIA XServer Settings tool with no luck:

X Server XVideo Settings : Checked 'Sync to VBlank' for the TV as the "Sync to this display service"
OpenGL Settings: Checked 'Sync to VBlank'

The following are the settings for the tv output (X Server Display Configuration):
TV: 
Configuration = TwinView
Resolution = Auto Auto
Position = Absolute +0+0

The only way I found to prevent the tearing on the tv is to disable the compiz effects ('None'), but I would really like to be able to keep my effects set to 'Extra', if possible. I noticed that the TV has a refresh rate of 50,00 Hz and 1920x1080 resolution, according to the information
displayed in the X Server Settings tool, and I tried to use these values directly in the X Server Display Configuration but it made no difference.

I also read somewhere that the settings I changed for the LCD Monitor in CompizConfig Settings Manager override the NVIDIA XServer Settings, could this explain why I get the tearing on the tv? What can I do instead? I would like to keep my tearing-free set-up for the LCD monitor.

I tried to disable the LCD monitor and only use the tv for the output, as I've read that many people have managed to fix the tearing problem in this way, however, this only caused a more jerky playback. The tearing was still there unfortunately. I disabled the LCD monitor in this way (is it correct?):

X Server Display Configuration -> Configuration -> Configure... -> Disabled

Could somebody please suggest me some more things I could try out? I would really appreciate it, because right now I don't know what else to try.

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by veroslav on 2011-03-31
bump

---

### Post by change_mode on 2011-05-16
This reply may be late, but just for the record: it works when you run the second monitor on a seperate x-screen.

---

