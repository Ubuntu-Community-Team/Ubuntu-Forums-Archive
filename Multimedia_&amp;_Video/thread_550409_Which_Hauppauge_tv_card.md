---
title: "Which Hauppauge tv card?"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by Red Knuckles on 2007-09-13
I'm going to setup mythtv and wonder if it makes a difference which Hauppauge tv card I purchase. I have Comcast Cable and Comcast Internet. At Newegg they have:

[http://www.newegg.com/Store/SubCategory.aspx?SubCategory=47&name=Video-Devices](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=47&name=Video-Devices)

The WinTV-PVR-150-MCE  which lists as 'Fm-in, TV-in,and S-VIDEO-in'

and WinTV-PVR-150 which lists 'CATV-in+Video-in' and 'Audio-out' and 'PCI-interface'. Which should I buy? Does it matter? I think I would prefer the MCE version but don't know enough yet. Aren't they all 'PCI interface'?

---

### Post by Syke on 2007-09-13
Either should be fine for TV. The MCE edition has FM radio, but I don't know if the FM radio works in Linux.

---

### Post by wolfen69 on 2007-09-14
i use the pvr-150 and it works great. you just need to download ivtv-utils after you install it. i use VLC to watch TV with it. PM me if you need instructions how to work it in vlc. ( i wouldnt have figured it out without someones help) plus there's a cool desktop "remote control" (CSMonkey)  that makes life easy for channel surfing.

---

### Post by wolfen69 on 2007-09-14
i decided to post the how to:

sudo apt-get install ivtv-utils (drivers)

open VLC 

File -> open Capture Device -> PVR -> OK

then you can do (in terminal)

ivtv-tune -h

to see the options which control the card. The interesting ones are

ivtv-tune -d(input number)

which changes the card's input from composite to s-video, and

ivtv-tune -c(channel number)

which changes the channel.

for a cool desktop tv remote, go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click:open with java.

---

### Post by rsambuca on 2007-09-14
> **wolfen69 said:**
> ivtv-tune -d(input number)

which changes the card's input from composite to s-video, and


Actually, that command won't change input on the card, it just changes the video input.  To change from tuner or to composite to s-video, you will require the command

v4l2-ctl -d /dev/video0 --set-input=2

In this case, the /dev/video0 would have to be your tuner card (mine is actually video1 since my webcam gets recognized as video0), and the --set-input=2 command sets the actual hauppauge card input to composite.

---

### Post by Red Knuckles on 2007-09-14
Thanks Syke and wolfen69 for the info. I've ordered the card and will use wolfen69's How To when I get it. Will post back when I get it working.

---

