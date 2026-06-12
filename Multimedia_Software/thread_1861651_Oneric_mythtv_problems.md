---
title: "Oneric mythtv problems"
date: 2011-10-15
forum: Multimedia Software
---

### Post by moaxey on 2011-10-15
I'm having a couple of annoying problems with mythtv in 11.10

- display sleep occurs during viewing
- playback of all hd programs is full of annoying pink vertical lines

---

### Post by BicyclerBoy on 2011-10-15
The display sleep sound similar to a bug couple years ago with the method used to interact with the desktop manager.

Have you had MythTV working with 11.04 ?

What video h/w ?
video h/w driver ?
What playback method do you use in MythTV ?

If you had same problems with 11.04 or never used it then could try compiz composite settings manager ccsm..

---

### Post by rjg_munga on 2011-10-16
I have the exact same problem after upgrading from Ubuntu 11.04 to 11.10.
The recordings play fine outside of mythtv.

I am running Mythtv 0.24 and playback was fine in ubuntu 11.04.

Not sure if this is related but I get these errors in the mythwelcome log
2011-10-17 11:40:05.761 VideoOutput, Error: Couldn't load deinterlace filter none
2011-10-17 11:40:05.761 Player(2): Failed to enable deinterlacing

---

### Post by BicyclerBoy on 2011-10-16
I'm not using 11.10 or MythTV on 10.04 or 11.10 but..

From a post in the 3rd-party-projects/mythbuntu forum:
Trying changing the TV playback profile to ffmpeg & XVideo.. 
Check/change your de-interlace settings..

This really is only helpful if you are forced to use CPU decoding.

---

### Post by rjg_munga on 2011-10-17
OK this is what I had to do to get it working again, its not perfect but its 99% there.
In the Mythtv menu I changed the following.

  	 	 	 	 	 	  [FONT=Courier 10 Pitch][SIZE=2]Utilities/Setup[/SIZE][/FONT]
                                     [FONT=Courier 10 Pitch][SIZE=2]|-> Setup[/SIZE][/FONT]
                                                          [FONT=Courier 10 Pitch][SIZE=2]|-> TV Settings[/SIZE][/FONT]
                                                                                            [FONT=Courier 10 Pitch][SIZE=2]|-> Playback [/SIZE][/FONT] 
                                                                                                                      [FONT=Courier 10 Pitch][SIZE=2]|-> Profiles page 3/8[/SIZE][/FONT]
 

 I am using CPU-- Playback profile and made 2 changes to that profile;[FONT=Courier 10 Pitch][SIZE=2] [/SIZE][/FONT] 
 [FONT=Courier 10 Pitch][SIZE=2]Decoder: from libmpeg2 -> Standard[/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]Video Render: from xv-blit -> opengl[/SIZE][/FONT]
 
I hope it works for others.

---

### Post by &lt;mike&gt; on 2011-12-06
Awesome! Thanks so much for that.
I'm using the cpu++ option, with decoder standard and renderer vdpau, primary and fallback interlacers set to none.
Not sure what I changed exactly,
FTR, this is using Ubuntu 11.10, with 

MythTV Version   : v0.24.1-80-g1de0431
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20110505-1
QT Version       : 4.7.3
Options compiled in:
 linux profile using_alsa using_oss using_pulse using_pulseoutput  using_backend using_bindings_perl using_bindings_python using_dvb  using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv  using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video  using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11  using_xrandr using_xv using_bindings_perl using_bindings_python  using_mythtranscode using_opengl using_vdpau using_ffmpeg_threads  using_live using_mheg


and a Hauppauge 2200 card

---

### Post by BicyclerBoy on 2011-12-06
You can't use vdpau render if using CPU++.

Can't use vdpau without supporting nVidia GPU h/w.
If you have nVidia 8200 - GT210,220.240,430,520...you should use VDPAU.
IHO Broadcast TV is unwatchable without de-interlacing..

---

### Post by pcooley on 2011-12-17
Just wanted to say I had this same wavy line issue on the 'do-release-upgrade' from 11.04 (Natty Narwhal) -> 11.10 (Oneiric Ocelot).

The above solution worked for me.  It appears the xv-blit video render was the problem.  Using opengl worked for me.

---

