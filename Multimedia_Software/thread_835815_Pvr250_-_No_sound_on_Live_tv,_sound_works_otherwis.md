---
title: "Pvr250 - No sound on Live tv, sound works otherwise"
date: 2008-06-20
forum: Multimedia Software
---

### Post by darpified on 2008-06-20
I just installed mythbuntu on my media center PC,
with a Happauage WinTV 250 tuner card, and audigy 2 sound card.

The problem is that Live TV (and any recordings) have absolutely
no sound in the mpg files.  Even playing on other computers.

I have placed the newest updated firmware from ivtv's site
in /lib/firmware/2.6.24-19-generic, checked to make sure
they were loaded.

did modprobe -r ivtv followed by
modprobe ivtv to load it back in as the module.

Starting up mythtv leads to the same result for the recordings.

To reduce the variables, I then unloaded and reloaded the
module and used v4l2-ctl to set the proper video 
input/output on the tuner card (in my case, S-Video)
with v4l2-ctl -i 1
Then 'cat /dev/video0 > test.mpg'

This resulting mpeg had the audio correctly embedded, on the
media center and other standalone machines.

As soon as I start the mythtv frontend to record new video,
it returns to the previous state of no sound.

Where should I be looking to further troubleshoot this?

Frankly, I'm kinda stumped, I've tinkered around to find if
there are some older firmwares or modules, but can't particularly
find anything suspicious.

Thanks for any help,
RP.

running
  Mythbuntu 8.04 2.6.24-19-generic

---

### Post by cshen12 on 2008-06-29
I just installed updates onto Mythbuntu 7.10 this week and am experiencing the same problem.  I have the latest modules and ivtv is loading fine.  I get good audio from everything else in Mythbuntu, I get good video from my PVR-250 card but no audio, no audio controls either (e.g., no mute, no volume control through keyboard F10, F11 or through the infrared).

This started happening after updating from patches this week.

I'm stumped.

---

### Post by darpified on 2008-06-29
I beat my head against the wall for quite some time.  I could find many people who were suffering from the problem as well.

I was going to take the approach of taking the source and
stripping out the video stuff, but it was too far outside my
comfort zone and I lacked the time to work on it.

I downloaded Knoppmyth, and it worked without a hitch out
of the box.

It's not my preferred solution, but mucking about with modules
and such is a little bit more than I can handle.


Sorry I can't help,
If by chance you can get it functioning, I'd love to hear the solution.

ps,
  My KnoppMyth kernel is 2.6.18-chw-13, running

~$ mythfrontend --version
Library API version     : 0.20.20070821-1
Source code version     : 14463M
SVN Branch              : branches/release-0-20-fixes
Options compiled in:
 linux release using_xvmcw using_v4l using_oss using_alsa using_arts using_jack using_ivtv using_firewire using_dbox2 using_hdhr using_ip_rec using_freebox using_live using_lirc using_joystick_menu using_dvb using_x11 using_xv using_xrandr using_xvmc using_xvmc_vld using_opengl_vsync using_opengl using_frontend using_backend

It's currently working fine, a little harder to setup than the Mythbuntu,
but it is working.


Like I said, if you manage to get Mythbuntu working, please let me know :)

Good luck!

---

### Post by Mr.Gosh on 2010-04-13
Well this is strange!
I tried mthbuntu 9.xx and it was much more that what i call a nice linux distribution BUT
neither my bttv, my pvr350 or my pvr250 were able to get them to work!

no channel scan, no nxtvepg recognition no nothing - the only thing that worked out of the box was my terratec cinergy t2 dvb-t usb card.

so i tried the mysettopbox from the old days and there was a new version called linhes R6.02 something...

And what do i see - the opposit.
A System that doesn't switch the keyboard layout into something not amerikan in the X11 it doesn't have an internationalisation, no proper non ntsc switching (you have to set in 13 locations to pal and proper 768x576) but at least the pvr250 and 350 work out of the box.

well the dvb-t card dosn't... :(

So i can select between "partially" and "not ewen"

I can't believe that there are no pvr users out there anymore - and how do you german guys get epg into analog mediacenters?


THX anyway...

---

### Post by WinterRain on 2010-04-13
I have a pvr150, (essentially the same as 250/350) but watch tv with VLC player. Let me know if you want info on getting it going that way.

---

