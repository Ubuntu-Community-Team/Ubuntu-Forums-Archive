---
title: "MPlayer can't find output device (-vo)"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by gee_off on 2007-02-21
Hi, I'm having a problem with MPlayer. Every time I try and open a file I get:

"Error opening/initializing the selected video_out (-vo) device."

I've done some research and the MPlayer site seems to indicate it's a problem with my mplayer.conf file, so I tried opening it with gedit and changing the vo = vx (or xv or xm or somethingorother, I can't remember at the moment) to the one recommended by the site, cvidix, for people with NVIDIA cards.  No effect.  On the forums I found someone with a simmilar problem and they were told to try gediting their gui.conf file, which I also tried (for some reason it was set ti xvidix) again to no effect.  So I've since tried a few combinations, all to no effect and so I'm hoping someone here knows what to do.

currently at **gedit ~/.mplayer/gui.conf** I have:

enable_audio_equ = "no"
vo_driver = "cvidix"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
vo_dxr3_device = "/dev/em8300-0"
v_framedrop = "0"
v_flip = "-1"
v_ni = "no"
v_idx = "-1"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "alsa"
ao_volnorm = "no"

(etc.)

and at **sudo gedit /etc/mplayer/mplayer.conf** I have:


##################
# video settings #
##################

# Specify default video driver (see -vo help for a list).
#vo= cvidix

# Use SDL video with the aalib subdriver by default.
#vo = sdl:aalib

(etc.)

Thanks in advance for you help.

---

### Post by tharsan on 2007-02-21
try using

> 
vo_driver = "xv"


in line 2 of gui.conf

---

### Post by gee_off on 2007-02-21
Thanks, works fine now.

---

### Post by sagara on 2007-03-20
> **tharsan said:**
> try using

in line 2 of gui.conf

tharsan, your suggestion also worked for me too, thx!
Would you mind explaining what caused the problem?
mplayer was working fine for me using **vo_driver = "xmga**", but after installing VLC it broke.  This fix did the trick.

---

