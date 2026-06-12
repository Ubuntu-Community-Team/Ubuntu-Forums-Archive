---
title: "Force 1080p output 9800gt hdmi out?"
date: 2010-04-30
forum: Multimedia Software
---

### Post by pharcycle on 2010-04-30
Hi guys, 

I'm having trouble getting 1080p out my xfx 9800gt that has an onboard hdmi socket. No doubt my HDTV is 1080p (panasonic TH-427PZ70B a few years old now), and it will do and has run at 1080p 60hz.   

It auto detects the display as simply panasonic-tv and outputs at 1080i. As I've been running mythtv with tv tuners this actually worked quite well as dvb-t is interlaced anyway and most ofthe HD video files I play are 720p. However I would like to run it at 1080p for all the usual reasons- especially as I have some 1080p files I'd like to enjoy in all their glory!!

This doesn't seem to be ubuntu specific as mandriva behaves the same, and makes no difference if I use the open source (default with 9.10), the official nvidia package or as I've just tried 10.04 with default and nvidia.

I've searched around for nvidia hdmi 1080p etc but can't seem to dig up anything useful. Surely I should be able to force the graphics card to output standard 1080p 60hz?

Should I be able to do this through xrandr by setting a modeline or in xorg.conf or nvidia control pannel!?

Cheers guys for any help. Thanks
dave

---

### Post by LinuxURU on 2010-05-05
Yes, I would like to know as well.

I have a Samsung 46" LCD TV running from a laptop using a GTX280.

In Windows the monitor runs fine as 1920x1080p @60Hz, but in Ubuntu 10.04, it only does 1920x1080i @60Hz.

I can make it run 1920x1080p @ 24Hz, but the colors on screen look weird.

Anyway, I too would appreciate knowing how to force the output to be 1920x1080p @ 60hz

I hope some kind soul will reply.

Many thanks

---

### Post by pharcycle on 2010-07-06
Well, been a while... many ubuntu installs later i still have this problem.

I managed to get it to go away by using a custom edid through edid_disable_exts and telling xorg to use that one....

That was a few installations ago and now i can't get it to work again! I tried to open the edid generated through the nvidia x server settingns manager with the Phoenix tool but that couldn't open it!

Anyway, bumping this up really as i found my own post while searching (again!) for a solution!

Thanks if anyone can suggest something!
Dave

---

### Post by pharcycle on 2010-07-11
Hi, well think i fixed it and was quite trivial really after i read most of the help for nvidia xconfig!

i killed x and ran

```
sudo nvidia-xconfig --tv-standard=HD1080p
```now in the nvidia-settings manager if i choose 60 or 24Hz its progressive and 50Hz is interlaced. I have no idea if its intentional however I believe that live TV like BBC HD is 1080i @ 50Hz and for blue ray is 1080p@24Hz and everything else i want at 60Hz progressive.

<edit> also had to disable flat pannel scaling (which i wasn't using anyway but is on by default).


Anyways i guess i should have just read the manual first! I had faffed about with no-edid options, custom using edid_disable_exts (which did work originally then i couldn't get it to do so again!) and custom mode lines from a database of nvidia ones, but they didn't work well at all!

Dave

---

