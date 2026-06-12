---
title: "Radeon 2100 (796e) &amp; GA-MA74GM-S2 jerky video solved"
date: 2008-10-03
forum: Multimedia Software
---

### Post by borek on 2008-10-03
I added the following three options to my xorg.conf file

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"

        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "TexturedVideo" "on"

EndSection

and in VLC player I used the XVideo extension output module.

I do not know if all of these things are required but using them means that my Ubuntu 8.04 video no longer looks like it is arriving from beyond the 91st dimension. 

Maybe this post will help other users of this motherboard & integrated graphics card and save them the hassle of buying another card.

---

### Post by jonnybignote on 2009-10-01
Hi, sorry to drag up an old post but I'm wondering if you still have any insight into this - I have the exact same motherboard GA-MA74GM-S2 and am having trouble getting graphics fast enough for mythtv.  I'm just wondering what else you have in your xconf file?  I'm not getting anywhere currently with this issue...

Thanks in anticipation

---

### Post by borek on 2009-10-02
My linux machine is not available at the moment. I have not used mythtv. If vlc player plays back well on your machine then at least the vlc jerky video problem is solved.

I can send you a copy of the xconf file when the machine is up. Just not sure when  at the moment. Sorry for the delay.

---

### Post by jonnybignote on 2009-10-02
ok - thanks

---

### Post by borek on 2010-01-03
Attached is the xorg.cong file I am using.

I had to change the file extension to .txt in order to upload it.

Let me know if it helps.

---

### Post by jonnybignote on 2010-01-03
Hey - thanks for that though I'm not sure I remember the original issue I had - I think it was to do with tearing and there is a well known line to add ( I don't remember it off hand) 

Thanks again

---

