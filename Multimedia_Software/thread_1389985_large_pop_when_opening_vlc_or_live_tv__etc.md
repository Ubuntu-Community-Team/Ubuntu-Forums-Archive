---
title: "large pop when opening vlc or live tv  etc"
date: 2010-01-25
forum: Multimedia Software
---

### Post by rileyp on 2010-01-25
Hi all my mythfrontend make a horrible pop when opening a av file  no matter what app I use.
I have edited  the last 2 lines in /etc/modprobe.d/alsa-base.conf  as per
[http://www.ubuntugeek.com/ubuntu-tip-how-to-fix-crackling-noise-on-hda-audio-cards-in-ubuntu-9-10.html](http://www.ubuntugeek.com/ubuntu-tip-how-to-fix-crackling-noise-on-hda-audio-cards-in-ubuntu-9-10.html)
and it has reduced by not doing it when I change channels but when I close and open myth or xbmc or vlc it still does it?
I am using a 5.1 surround system connected by 1/4 inch plugs and rca adaptors
I dont know how to configure alsa for 5.1 either?
as The volume levels are not there ike in my other pc's however windows runs 5.1 on the same pc perfectly
I think it has something to do with the duality of the plugs (ie they can be line input,micropone input or subwoofer output,centre speaker s urround left and surround right.
Any help much apprecitaed

---

### Post by miki4242 on 2010-01-25
@rileyp

Are you using PulseAudio?
To find out, please run `pgrep -l pulse` in a terminal. If you are using PulseAudio, you can do this:

Edit /etc/pulse/default.pa (or copy this file to $HOME/.pulse/default.pa and edit it there).
Comment out the line that reads:

load-module module-suspend-on-idle

so it becomes:

#load-module module-suspend-on-idle

Then log out and log back in again (you may need to reboot if the change doesn't take effect immediately.)

This works for me (no POPs) even without changing /etc/modprobe.d/alsa-base.conf.

--Alain

---

### Post by rileyp on 2010-01-27
Thanks for your response
I'm using alsa not pulse.
The solution I linked to has actually worked a lot better than I expected as I hadn't done the reboot although I still get a pop when mythbuntu starts. I think I will be hard pressed to fix that.
so I consider this problem now fixed...

---

