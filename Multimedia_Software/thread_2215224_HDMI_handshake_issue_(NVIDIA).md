---
title: "HDMI handshake issue (NVIDIA)"
date: 2014-04-05
forum: Multimedia Software
---

### Post by sydbat on 2014-04-05
My HTPC setup:
- 12.04.3 64bit, using Gnome 3
- Nvidia 220GT 1GB (using HDMI via Samsung HW- C560S home theatre receiver)
- 5GB Ram
- Intel Core 2 Quad @ 2.6Ghz
- Gigabyte ga-p35-ds4 motherboard

This is something that is more annoying than anything. Whenever I go to listen to music (in all media players, and editing software) or watch video (again, all media players, editing software and online), there is a 3 to 5 second delay before the sound begins. It is especially annoying when this happens between songs in a media player or when I am trying to edit sound. When I am watching something online, if I pause the video for more than 10 seconds, the delay in sound is there when I resume play (except with Netflix). Pulseaudio, ALSA, Jack...it doesn't seem to matter what sound system I use, it is all the same.

This week there was a kernel update. After rebooting, the HDMI sound was persistent (on all the time) and I had the instant sound equivalent of the analogue 3.5mm plugin on my other, non-HTPC. I thought that the latest kernel had fixed whatever the delay-sound issue was and I was able to edit several sound files and video without issue. I found out last night that this was not the case. I was going to watch something online and noticed that the sound was not synced with the video. I decided to kill Pulseaudio and let it regenerate. This brought back the 3 - 5 second sound initialization delay. Sure, the sound was synced again, but the annoyance was back.

My question is - What Pulseaudio (or other) file needs to be configured to allow instant sound over HDMI? 

I had asked a very similar question a few months ago on Ask Ubuntu, but never got an answer. I hope that someone here will be able to help me out.

PS. The only other item connected to this home theatre setup that has the same 3 - 5 second delay issue is our HD satellite PVR (Bell 9241). It runs Linux too, which makes me wonder if this is a completely Linux issue, as other HDMI connected items do not display this behaviour.

EDIT - [s]There is also something strange with Totem. When the sound was persistent this week, Totem worked perfectly. It played MP3's and other files without issue. However, before this week (and now), Totem will not play MP3's (or much of anything). It "skips" through without any sound at 4 or 5 times the speed. On the receiver, it looks as though it wants to be DTS off and on, but no sound whatsoever. I wonder if this has something to do with it. Would removing Totem (if at all possible) be a solution??[/s] Turns out this was a setting in pavucontrol under "Output Devices". Unchecked 'MPEG' and 'EAC3' and Totem started to work fine. Weird.

Also, if I keep pavucontrol open, a lot of the issues disappear. Why?

---

### Post by sydbat on 2014-04-07
Bump.

Also, Bueller...

---

### Post by sydbat on 2014-04-08
OK...so I need pavucontrol open for consistent sound. Strange. 

My new question is - how do I autostart pavucontrol? I would also like to have it in the bottom hidden panel (Gnome 3) like many other autostart items (bluetooth, dropbox, etc). 

Thanks.

---

### Post by sydbat on 2014-09-07
I will be marking this issue solved, because I found a solution!

I was looking up a seemingly unrelated sound issue (how to play audio from analogue line-in to HDMI out) and found that the solution provided works for my OP.

From this post - [http://ubuntuforums.org/showthread.php?t=1324135&p=8308073#post8308073](http://ubuntuforums.org/showthread.php?t=1324135&p=8308073#post8308073) - the solution is:

> [I]To add the loopback module to the running instance of Pulse Audio I used the command:
$ pactl load-module module-loopback

To make the module automatically load in the future, I used the command:
$ sudo sh -c ' echo "load-module module-loopback" >> /etc/pulse/default.pa '[/I]

This keeps the audio connection alive at all times through HDMI. Why this is has to be enabled manually, I cannot say. But once it is, no problem with delayed audio when starting an app, or audio dropping between media in every media player. This makes things exactly like having an analogue speaker hookup, but with full digital 5.1 surround HDMI.

---

